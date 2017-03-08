---
published: true
title: NPM Prepack And Publish
layout: post
date: 2017-03-03T16:16:05.000Z
categories: post
tags: npm prepack publish javascript typescript
comments: true
math: false
---
The other day I published a small package to [GitHub](https://github.com/horia141/npm-prepack-publish) and [NPM](https://www.npmjs.com/package/npm-prepack-publish). This post serves as documentation and tutorial.

I wanted to have better control over what files are included into an NPM package. The classical approach to building a package is to call [`npm pack`](https://docs.npmjs.com/cli/pack). This includes files from the current directory, and is controlled by the [`files`](https://docs.npmjs.com/files/package.json#files) field in `package.json`. My main goal was to make imports super easy. But many times the structure of the current directory and the simplicity of `npm pack` caused issues.

For example, a common directory structure I use is:

{% highlight bash %}
- package.json
- README.md
- src
  - index.ts
  - dependency.ts
- fonts # some data files
  - font.woff
- out # generated by the build process
  - index.d.ts
  - index.js
  - dependency.d.ts
  - dependency.js
{% endhighlight %}

There's four types of files here. Source files in `src` are in source control. Being TypeScript they aren't particularly interesting for other users of the package though, so they shouldn't be put inside it. Config files like `package.json` are included in the package because they're required by NPM. Extra data files, such as the ones in the `fonts` directory are included. Furthermore, it makes sense for the whole directory to be included. Finally, output source files, in `out` should be included in the root of the archive. This makes it easy to use the package like so:

{% highlight js %}
import { foo } from 'my-package'
import { bar } from 'my-package/dependency'
{% endhighlight %}

The structure inside the archive we'd like to have is:

{% highlight bash %}
- package.json
- README.md
- index.d.ts
- index.js
- dependency.d.ts
- dependency.js
- fonts
  - font.woff
{% endhighlight %}

Unfortunately, `npm pack` flattens any directory specified in the `files` property. So it can produce just something like:


{% highlight bash %}
- package.json
- README.md
- index.d.ts
- index.js
- dependency.d.ts
- dependency.js
- font.woff
{% endhighlight %}

This _is_ workable in the small scale. But after a while one is bound to end up in trouble. File collisions might happen, there's a difference between the structure on disk and the way the code accesses the files etc.

Furthermore, in a situation like the following:

{% highlight bash %}
- src
  - client
    - client.js
  - server
    - server.js
  - misc
    - misc.js
{% endhighlight %}

It's hard to obtain something like:

{% highlight bash %}
- client
  - client.js
- server
  - server.js
{% endhighlight %}

You have to specify either `src` in `files`, and end up with `misc`, or `src/client` and `src/server` and end up with a flattened hierarchy which leads to the same issues as above.

To solve these issues I wrote `npm-prepack-publish`. It's actually a bash script, but it's useful nonetheless thanks to NPM scripts. It also does both the packing and publishing to NPM, or whatever repository `NPM_CONFIG_REGISTRY` you've set.

Before using it, the `NPM_TOKEN` environment variable needs to be set. Actually using it is just a matter of calling `$(npm bin)/prepack-publish` from the command line, or from a CI runner, or wherever. An example is the [`.travis.yml`](https://github.com/horia141/npm-prepack-publish/blob/master/.travis.yml) config file for the package itself.

To configure how the archive is built, you need to specify the `filesPack` option in `package.json`. This is a dictionary, unlike `files`. The keys are files and directories and the values are how they're packed. Here's how the original example would look like:

{% highlight json %}
...
"filesPack": {
  "package.json": "f:package.json",
  "README.md": "f:README.md",
  "fonts": "c:fonts",
  "out": "e:."
}
...
{% endhighlight %}

This configuration will instruct `pack-and-publish` to copy the files `package.json` and `README.md` to the archive as is, and place them at the root of the archive. You can place them in other directories, and the files will be renamed, as well as change their names. The `fonts` directory will be copied as is to the archive. Finally, the contents out `out` will be expanded and placed in the root directory. The output will be:

{% highlight bash %}
- package.json
- README.md
- fonts
  - wont.woff
- index.d.ts
- index.js
- dependency.d.ts
- dependency.js
{% endhighlight %}

This is exactly the desired behaviour. I'm still torn on whether I should separate the pushing from the packing though. Perhaps people will find utility just in the packing.