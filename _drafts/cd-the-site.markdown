[talk about the site], maybe link to it etc.

[how the system currently exists] Basically it is a "classic" app. I rent a host from Linode. I run Ubuntu on it and installed lighttpd. I have a repository with the site which I clone locally then run a command lighttpd -D to start it.

It is pretty simple. But it could be better. There is downtime on each upgrade. Upgrades are few and far between but still. I have to log in and run commands. Many things operated from consoles and me doing commands etc.

This is something more than an exercise, but definitely not as complicated as a real web application.

Still, I would like to have CI&CD for it. Ideally, I would like to make some changes, then push them to GitHub. After that an automatic system picks them up, runs tests, and if they pass, does a deploy. The deploy should be automatic and should not involve downtime.

Current system:
- running Ubuntu
- a static web-site
- served by lighttpd
We're gonna keep this.

We're going to add:
- an integration test, which starts the server, and does a wget on the main page and some other pages and sees that some content is returned and a 200 code is produced. Very high-level tests.
- run the thing as Docker containers.
- switch from Docker to GCP. Ran a cluster with Kubernetes and run the containers on this thing.
- use Jenkins for CI&CD.
- use GitHub as the source of truth.

The application needs to be dockerized, in Docker parlance.

Should do:
- AWS IAM
- AWS EC
- AWS load balancing
- AWS cloud watch
- AWS cloud trail