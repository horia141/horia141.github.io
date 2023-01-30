---
published: true
layout: post
date: '2023-01-30 07:00'
categories: post
tags: career management tutorial
comments: true
math: true
title: 'Job Of A Manager'
---
The following is a repost of an internal training I did for managers in my team at Bolt. All of us are pretty new to job, and I saw a lot of common points of confusion pop up. I thought it worthwhile to lay down more concretely the expectations on managers in Bolt engineering. Turns out the resulting doc has a wider applicability. So after much procrastination I’m putting it on the blog for more folks to enjoy.

# Introduction

Being a manager is … different. I’ve collected a bunch of my thoughts on the topic. There’s a small attempt at an overarching framework, but overall the document is guided by what I saw as points of confusion in my many chats with folks around the organization. Some topics apply to the whole profession of management. Others to engineering management in particular. Still, others are specific to Bolt. I’ve tried to call them out as such.

You can probably guess that the document is far from comprehensive. Seek out our [recommended reading list](https://horia141.com/career/2022-05-22-my-suggested-reading) for a glimpse at how deep the rabbit hole goes.

# Why Are Managers Needed?

In the world of perfectly spherical humans in a void, there’s no need for managers. Every action can be done by a single individual at blazing speed and maximum competency. The CEO could run the show all by themselves and have time for a hobby or ten.

In the *real* world of imperfect slow distractible squishy humans, folks need to work together to achieve anything meaningful. **They form organizations that can *do things* above and beyond what any one member could do**. But working together does not come easy. There’s planning to do, work to be assigned, and processes to establish. There is a *coordination cost to pay*. **Manager is the name for the person doing these activities and making sure the organization can function**.

A natural way to tackle many problems is to break them down into subproblems. These can be further broken down, until you reach a point where the problems are solvable by a regular human. The structure of the problem thus tends to be recursive and hierarchical. It’s also natural to structure the organization to match the form of the problem. **Thus organizations tend to be recursive and hierarchical**. There’s one person at the top - the CEO - responsible for solving the whole problem. They have a number of *reports* responsible for solving particular subparts of the problem. And so on until you get to *individual contributors* who have no reports, and handle the smallest units of work. The managers form in any case a hierarchical structure of reports, and own various bits of the whole problem.

The above is, of course, a great simplification. And it might work for a 19th century factory. But doesn’t apply as easily to 21st century technology companies. In technology companies, problems take the form of [product domains](https://horia141.com/career/2022-06-05-the-notion-of-teams). They’re solved by [engineering hierarchies](https://horia141.com/career/2022-06-16-the-notion-of-hierarchy). **But the managers involved in the process are also responsible to a degree in defining the problem themselves. They are also leaders**. As such they play dual roles as folks who identify problems, offer solutions, set vision, and strategy. But also as folks who execute the operational side of planning, scheduling, staffing, team development, etc.

To add to the complexity of the situation, product domains have many facets and a sort of specialization occurs. A problem has several leaders then, all focused on particular aspects - product management, engineering, design, research, etc. **As an engineering manager, you will usually be *the manager* in the team, having several reports**. You work closely with an individual contributor product manager, or a designer or two. You and the product manager will share many responsibilities, but people management will fall on you in particular.

**The key thing to remember is that your job is to keep the product domain working.** This means delivery through the team. And also successful partnership with your product domain owners. And also successful working with the rest of the organization. There is no manager who is successful on their own. To the point, it’s hard to speak of a manager's performance. Rather it’s the team’s performance. **They’re succeeding if their team and product domain are succeeding. They’re failing if their team is failing. They’re failing if their product domain is failing.**

The view presented here is rather the "modern approach to engineering management". It comes from places such as the FAANGs, and further down in history from luminaries in Silicon Valley. It is the approach that high-performing organizations take. It emphasizes people over processes. It assumes you are working with a highly skilled and highly scarce individual contributor - the engineer. It is very much a theory Y of management. It is people-oriented rather than outcome-oriented. It does require the EM to stay technical and be an actual engineer.

It is not the only way of going about things. Many organizations operate in a different fashion. But this document won’t go into those details.

# What Does A Manager Do?

Again, in very broad terms a manager is the owner of some part of the organization. And therefore some part of the problem, the organization is solving. This ownership has management and leadership facets. The management one is about building teams, ensuring delivery, ensuring quality, providing *control,* helping out with planning, scheduling work, *etc.* While the leadership component is about setting the vision, establishing the strategy, defining the problem itself, etc.

The above translates quite directly into the day-to-day and quarter-to-quarter activities expected of you. In the interest of padding this document even further and eventually getting a book deal, I’ll go over them.

## Vision / Strategy / Planning

**As a manager, you are responsible for the vision and strategy of your team. You are usually not *solely responsible**.* And you’ll have a PM working alongside you to form the team’s *leadership core*. For many teams, they will have priority in setting the vision, establishing the strategy, defining KPIs, and planning and prioritizing the work. This is natural and by the design of our organization. But you shouldn’t abdicate responsibility here. You’re not a *feature factory.* The rule of thumb is a `70%-30%` ownership split.

**Conversely, if things go wrong from this angle, it’s gonna fall on you too.** Of course, there are many aspects here.

The major efforts that you’re expected to participate in are:

You are succeeding here if you manage to create a vision that is compelling within and outside the organization. More prosaically, if the company gives you the resources to build the stuff you say you have to build. Conversely, you are failing if you wait for a *top-down* vision/strategy/plan from the *higher-ups*, or if you consider yourself just the feature factory, or if the team doesn’t buy it, or if other teams don’t buy it, or if there’s no clear path to company success via team success, or if the organization doesn’t buy it, etc.

## Building The Team

**The team is the means through which you do your work in the end. Having a good team is the way in which you do good work**. The coarse-grained thing you need to do here is the classical hire/promote/fire decision.:

- **Hire** is about who you accept into the team. **Not everyone who passes the hiring bar makes sense to your team**.
    - There’s the whole discussion here of structuring your team which means ensuring you have the right skills to deliver on your goals.
    - But an orthogonal thing to consider is how will a potential new joiner interact with the other folks in the team
        - Are they similar to the team in the way that matter to the team - same work ethic, the same level of care about the product, same approaches to technology, etc
        - Are they different to the team in a way that enriches the perspective of the team - life experience, ethnicity, etc
- **Promote** is about who you give extra responsibilities to in the team.
    - You need to consider both the formal career ladder as well as the more informal TL/Group TL roles.
    - This absolutely ties into the structuring of the team discussion.
        - But extends to the values part - values are those things that people get rewarded for doing in the end
        - As well as the distribution of the limited resources that you have at your disposal.
- **Fire** is about who you decide to let go of the team.
    - There’s the traditional meaning of letting go of bad performers.
    - But it can also mean letting go of strong performers who cannot achieve their career aspirations in your team. Of course, if they want to leave the team too.
    - And it can also mean letting go of folks who aren’t living up to their potential. This is a subtle and tricky point. And it ties in with issues of team structuring, compensation, compensation debt, etc.

As a baseline behaviour you need to provide a safe space - a place with psychological safety and structure and a shield from the storms outside the team’s perimeter.

You are succeeding here if you manage to build a team to support the delivery goals that you have, it has a low attrition rate, people are generally happy, etc. Conversely, you are failing if you don’t manage to do this, the team is underpowered for their delivery goals, or the team is overpowered for their delivery goals, there’s a higher attrition rate, Peakon scores are bad and not improving, or they’re good but falling.

## Growing The Team

The hire/promote/fire discussion is big and shiny. It’s easy to consider it as the main concern of building the team. **But in fact, taking care of the growth and development of the folks you have is equally if not more important.** This is fine-grained work in this way. You need to do it continuously across time. But whereas hiring has very clear budget constraints, upskilling your folks suffers no such limitation.

The organization *mandates* that you do several things here as a baseline. These are **regular 1:1s** and **periodic performance reviews**. I won’t go into more details here, as these topics have been well-covered in other materials.

Things like delegating some of your tasks to a TL, or creating special roles for folks with special skills (DB owner, Spark expert, etc.), are also ways you can grow your team here.

You are succeeding here if you manage to build a team that isn’t static. Folks feel they are growing and stretching themselves, and there’s a strong part of doing more with less. Conversely, you are failing if you don’t manage this, folks feel like they’re not growing, you’re not using folks to their full potential, etc.

### Acting As Coach And Trainer

When your reports have particularly tricky roles → people manager, tech lead, group tech lead, etc. you should also consider on the job training to be part of your duties.

This can come in the form of recommending particular books or courses the report should take.

But it should also come in the form of specific training sessions carried out by you, or periods of high-feedback on their work.

Many times you are one or two steps ahead of them in the career journey. So it’s very likely their current mental state is fresh for you, and a lot of these skills aren’t yet “muscle memory”. Hence you are in a good position to teach.

Many times, teaching and being more involved in their handling of issues, are learning opportunities for you too. The student teaches the master.

### Getting People Up To Speed

From time to time we take candidates for product engineering which come from a non-traditional background. We’ve hired Windows desktop, iOS, Android, embedded, etc. developers as “backend devs”. This type of work and the technical and organisational infrastructure we have have allowed us to do these things.

And some of the folks we hired this way have great success. Others not so much. At best we get someone of middling performance. At worst we part ways.

This transition is not a given, and the candidate needs to expend some effort getting themselves up to speed with the patterns, processes, approaches, technologies, and broadly “ways of working” in backend and fullstack development. **They need to do this in about one-two quarters**.

It’s also your job, as the manager, to make sure that they understand this, and that they have some reasonable learning and development plan in place to do so. It is very much the idea that they are proactive on this, and not just coast along at the speed of regular project delivery.

If you find that they are not willing to do this, or that they are not up for it, then it’s best we not hire them at all, or part ways as soon as this becomes apparent.

**A failure scenario is having a person with 2+ years of experience in the company which you must treat in a different way than your other midlevels or seniors because of their skills gap.**

This of course doesn’t apply if you’re hiring somebody for a very particular skillset, and don’t expect general contributions.

## Partner To Their PM And Other Team Leadership

As mentioned above, the notion of teams (groups of people that solve problems together) and the notion of hierarchy are somewhat disjoint. Folks across different management lines will form a team and you’ll partner with a PM and possibly other folks to lead the team.

Naturally, this must be a good and productive partnership. A house divided against itself cannot stand. There’s a lot to be said about this relationship. This doc is already too long. [I’ll let Greg take this over](https://newsletter.pragmaticengineer.com/p/working-with-product-managers-advice-from-pms).

You are succeeding here if you have a good relationship with your PM. If I don’t hear anything about trouble. Conversely, you are failing here if there are tensions, if one is picking up the slack for another, if there’s misalignment, and if it starts to influence the team negatively.

## Partner To Other Teams

Teams don’t exist in a vacuum. There’s other teams around them who they need to cooperate with to solve the bigger problems.

Just like folks need to work together in a team, teams need to work together. On the one hand within the confines of their group, and on the other hand with other random client or partner teams. There’s the L2 management and TL hierarchy to make this work, but in the end it requires cooperation and goodwill between the teams.

You are succeeding here if you have a good rapport with the other teams, if they can depend on you for changes and you can depend on them for changes, if there’s no animosity between the teams, etc. Conversely, you are failing if there are tensions, or if there’s never bandwidth for the others’ requirements, if there’s a blame game going on in every interaction, etc.

## Managing Delivery

The most *managerial* aspect of your job is very likely *managing delivery*. **This means making sure work gets done on time and on budget and with an acceptable level of quality.**

If the vision and planning part is about establishing what needs to get done in the long and short term. And if the building and growing of the team is preparing the folks who are going to do the work. Then this part of your job is about mapping the work to the team.

The following section is _too grounded_ in the way Bolt works. It has some generalities, but is by no means universal. 

- Sequencing of work
    - After quarterly planning, there’s an unordered list of items to tackle
    - The team needs to do enough exploratory work to understand the scope of the work and the major dependencies within and outside the team
    - It’s on you to make sure this happens and there’s as much derisking going on as it’s safe to do
    - You know you’re doing a good job here when the work goes as planned. Conversely, if there are always unforeseen issues, or unaccounted complexities, or (heaven forbid!) unknown dependencies on overbooked teams, you’re not doing a good job.
- Assigning the work to individuals
    - Work assignments happen once the work is sufficiently explored
    - You have multiple constraints to satisfy, so this is not an easy problem
    - You want to assign the work to folks such that it has the maximum chance of getting done
    - At the same time, you want to spread knowledge of the various subdomains and systems across the team
    - You also want to assign stretch goals to folks to allow them to grow in the directions they want
    - There’s also team duty, unplanned work, regular quality checks, and engineering work to be fitted in
    - You know you’re doing a good job here when folks are capable of finishing the work they set out to do. Conversely, if folks are overwhelmed by this work, or underwhelmed by it, you’re not doing a good job.
- Ensuring that the work is progressing
    - We don’t have a high-pressure culture, but it is worthwhile to check and debug if the work is getting done in the way you estimated it would
    - Things like design docs and pushing upfront the hard decisions work here. As well as periodic progress reports, daily standups, discussion of issues, helping to unblock people, encouraging multi-tasking, etc.
    - You know you’re doing a good job here if folks can continuously progress on their work. Conversely, if folks are blocked, or they waste time on dead ends or make designs that are too complex, you’re not doing a good job.
- Verifying that the work is done
    - This is a joint PM and EM effort
    - But it is the team’s leadership responsibility to give the final seal of approval of a particular roadmap item. PMs can focus on the product aspects and EMs on the engineering ones.
    - You know you’re doing a good job when there is a clear definition of done and it’s respected and there’s little/no bugs or issues after calling it finished. Conversely, if there are revisions to do, constant bugs to fix, production fires to address, you’re not doing a good job.

This part of the work can be said to be about *project management*. And in some companies, it is handled by dedicated *project managers*. Not at Bolt though. The EM is the main project manager. You can delegate some of this work to a TL, or to a particular person as a feature lead.

You are succeeding here if you are delivering the roadmap items you said you would deliver in the time you said you would deliver them and with the resources, you said you would spend at the level of quality you said you’ll achieve. You are failing here if you’re consistently not doing this. Work falls behind, or doesn’t get done, or gets done in a buggy way, or gets done in a too complex way, or needs to get redone after MVPs, etc.

## Technological Ownership

Most engineering teams build and operate *systems.* These are the collection of programs which make Bolt happen.

The building of these systems needs to happen to a generally high degree of quality, and their operation needs to happen such that outages or other business impacting events are rare. High quality here usually means maintainable and easy to extend systems. As a litmus test, if a feature A takes you one month to implement in one year, it should take you one month (or less) in the next year. Similarly, doubling the size of the team should double the size of the output of that team. High operability here usually means building robust and resilient systems. This is measured by uptime, SLA violations, incidents frequency, impact of incidents, data loss, security incidents, etc.

There’s several key activities you are the driver of:

- The engineering roadmap items
    - These are team specific efforts meant to increase the quality of the code in our systems
- The migrations to various new technologies
    - These are organizationally driven efforts meant to increase the global stance of the company
- The improvement of the operational stance of the team
    - These are team and organization efforts around alerting, chaos testing, error cleanup, adding metrics, etc.

You are succeeding here if you are building resilient and maintainable systems. You are failing here if your systems are buggy, hard to operate, always crashing, hard to extend, and new projects tend to always be delayed!

## Externals Management

Some teams rely on a particular vendor to do their job. Still, others engage an external community like the contributors of an OSS project. All of these and more are team-level interactions that need to be managed. It falls to the leadership of the team, and many times to the engineering manager, to make sure they get done.

## Participation In Company Processes

The organization will rely on you more than on others for the execution of the various processes keeping it in line. They’re non-negotiable most of the time, so you’ll be involved regardless. Two are very important and I’ll mention them here.

Interviews are how we check candidates before accepting them into the organization. You’ll have a mandatory role as a “hiring manager” (i.e. filling out the “hire” from the "Building The Team" section). But you’ll often be a coding or system design or EM interviewer. **It should be table-stakes behavior to participate in the interview process, even though it’s formally optional at Bolt.**

One formal power you have as a manager is that you get to work with salaries. Both your team’s salaries and the overall salary process. But the main rule here is that you want compensation to follow the performance. First in the gross sense - folks with higher output should get promoted which should get higher performance. Then in the finer sense - within a band folks should have performance proportional to pay. And in the sense that you first need to prove performance, and then adjust pay accordingly. Your role as a manager is to ensure performance makes sense and is correlated with pay in your team.

## Everything Else

Coming back to the point about ownership. In the abstract, you should do everything to ensure your organization succeeds. Things me and other managers at Bolt have done that we didn’t sign up for:

- Organizing team events
- Office improvements
- Figuring out CO2 leaks in the parking lot
- Console folks through illnesses
- Walk through family problems
- Debug visa issues
- Helpout with salaries payments
- Work on a script for our ads
- Chaperone for visiting higher-ups
- Sourcing candidates
- Last-minute conference participation
- HR work
- Company process work
- Dealing with wars, conflict, etc. when you have folks on both sides

## A Note About Other Companies

The above are quite common to tech companies of a certain type. But they’re not the only way to roll. Agencies/consultancies and by extension outsourcing companies, will have a slightly different model. There the people aspect is separate from the product and technical ownership aspect. As such, a single manager might have 20-30 direct reports for whom he thinks about career growth, coaching, etc. Teams are formed from these and other reporting lines to work on various projects. A project manager or product owner will usually own the product vision and the technical ownership aspects.

## A Final Word About Power

I want to say a final word about *power*. As a manager you have it! Specifically you have power derived from the hierarchical nature of the organization. And those at the top of the hierarchy have more power than those at the bottom of the hierarchy. The CEO has the most power and they can do anything.

But to be honest, **visibly** **using power is an anti-pattern**. It should be the last tool at your disposal. Ordering someone to do something represents both a failure of yours to convince the other through reasoned argument that the course of action is the right one, and a failure of the other to be flexible and open to your point of view, and a failure of the organisation to empower you to make this point across. I hope you feel this intuitively too, but there’s a whole bunch of literature to study here.

# How Does A Manager Fit Inside The Organization?

The previous section covered your role with respect to your own team. But managers are a crucial part of the wider organization. As such you play an interesting role in the global context too.

## Enforcer

You can view any organization as concentric circles emanating from the CEO. The CEO is the center, their reports in the first circle, their skip-reports in the second, and so on. As a manager, you are somewhere in a more central circle than individual contributors. Roughly the circles correspond to performance, experience, and responsibility. It’s a crude analogy, but even as an L1 manager, you’re in the top-20% of the org helping it succeed. As L2 managers you’re in an even more select crowd, etc.

Being more central means you’re supposed to take a different type of view on some “organization-vs-individual” topics. If you consider that the CEO has just the organization’s best interests at heart, and an individual contributor has just their own individual interests at heart, you as a manager are somewhere on that scale. Where exactly? Depends on how close or far you are from the CEO. But you should definitely not think of issues simply from the IC angle. **You are rather an enforcer of the diktats of the company!**

For example, our processes have an elaboration and an implementation phase. You may or may not be part of the elaboration phase. And you may or may not agree with what has been elaborated. **But you must “disagree and commit” to the implementation phase**. And especially present a unified front for the wider organization.

I hope the last sentence has stirred you a bit. It’s not an approach that comes easily. And “disagree and commit” sounds very much like “just following orders”. But organizations cannot function well in split-brain mode. Hence it’s vital everyone works the same way. It’s on the leadership to arrange things in such a way that the elaboration phase is inclusive and gives folks a chance to shape it in a way they think is important. But even so, not all suggestions will be heeded. And in some cases, this ideal of inclusivity won’t even be attempted. Hence it’s quite likely that you’ll encounter at least one process with which you disagree.

**Conversely, disagree and non-commit is not an option**. It’s essentially not doing your job, and that doesn’t go over well.

To add even more complexity to your life, you're also supposed to be your team's voice to the organization. This is distinct from *your* voice. The interests of your team might be different from yours from time to time. And certainly, the interests of your organization will be different from those of the wider organization. So you must also navigate this tension, and know when to fight for your group as well.

## Supporter And Leader

We all know the mantra “management is different from leadership”. At Bolt, the two come as a package, however. We expect engineering managers to first show leadership. This means handling issues of strategy, vision, teaching people to yearn for the vast and endless sea, etc. We secondly expect them to be good managers. This means handling issues of control, predictable delivery, planning, budgeting, staffing, etc.

But there are formal leadership roles outside the management track. Our Staff and Principal engineers also need to show a lot of leadership, and the same for folks wearing the TL and GTL hats. But we expect and encourage leadership in many other situations. Anytime you do something outside “business as usual”, whether you’re a CS agent or junior developer, you’re showing leadership.

Depending on the context, you’ll need to wear one, the other, or both hats.

## Role Model

A manager should also be a role model of those organizational behaviors that are valued. In our case, our operating principles. This is initially straightforward, as you’re hired or promoted based on these things, besides your “technical” contributions. But as the nature of your work starts to shift, you must still keep these things in mind.

For example, manifestations of our “we challenge each other, but mean well” principle are the practice of code reviews and the practice of quarterly reviews. Both are open to anybody really, you shouldn’t be upset when a valid point is raised. Yet I’ve seen folks accept drive-by code reviews much easier than drive-by quarterly reviews. That shouldn’t be the case. As a manager, you should accept the former, just as well as the latter.

There’s another take here. There are some things you can no longer do like you could do as an IC. Things like:

- Getting drunk at parties
- Making stupid jokes
- Having “opinions”

At the very least, from a self-interested approach, you don’t wanna be the one like “he/she is a good manager, too bad he/she …”

# My Expectations

A common question that engineering managers at Bolt have asked is “how do I know I’m doing a good job?” The following is my take on it. I believe it is principled. That means it has support from the theoretical description outlined in the previous sections. And it is also common practice at Bolt and in the wider industry. Indeed, my manager has more or less the same expectations of me, and his manager of his, and many other managers of their reports.

The core point to remember is that there is no notion of individual performance. There is no "how am I doing?". It's rather, "how is the team doing?". If the team is doing great, then it's super! Regardless of what you actually contribute to it. If the team is not doing great, then it's bad! Regardless of how good you're doing yourself. Of course, this is gonna be hard to do without your help.

Then, as a simplification, the team is doing great if the manager is doing the job of a manager great. Just so we have things explicit, I prepared a bunch of explicit topics.

# The Management Career

As hinted, engineering management is a career in itself. Thus there are a lot of habits and customs surrounding it. In this section, I want to cover a bunch of them. This is the most Bolt-agnostic section.

## Is Management A Promotion Or A Lateral Career Move?

**Yes**.

Management is an activity anyone can do. Same as leadership. Engineering managers are engineers who specialize in building the sociotechnical system which actually does the work. They get extra leadership cookies too! So it is a different career track, just like SRE, or data science is.

So in one sense, becoming a manager is a lateral move since you are leaving one type of job - directly coding and building systems, to another type of job - leading and managing people who code and build systems. And it's expected that you'll not be good at it for some time.

But in another sense, it is a promotion since you are brought into a more central position in the organization.

There are many places where we are split brained around this thing

- We'll commonly call the change a promotion
- But then we'll not offer a substantial compensation increase
- We'll allow the better performing folks to try for manager roles
- But then place no such restrictions on the IC track

This is a particularly engineering and "professional" way of looking at things. In other divisions of the company, the move to management is absolutely a promotion. Indeed, there's only one path to career progression in these cases and that's taking on a manager role.

The above, coupled with the historical context means that being a manager is seen as a prestigious job. We know better, but there's an important and complex organizational angle at play too. We need high-level ICs just as much as we need EMs. We'll be lacking in the former if we just glorify the latter.

## Who Gets To Be The Manager?

In light of the above, the next question to ask is who gets to be the manager? I’ll assume we’re speaking about a “you” which is different from the “you” in the rest of the document. Cause you’re already a manager.

The first and crucial test to pass is that you should want to try this out. There are options for high-performing folks, and management is absolutely not the only game in town. As this document makes abundantly clear, management is a different and difficult job. If you’re only going in for the respect or the money or the power, you’re gonna have a bad time. If you like people and people problems, if you like building an organization, or if shaping how the company does work sounds interesting, then … you should still think it through.

The second test is whether you’re senior and experienced enough as an engineer. The level at Bolt is Senior Software Engineer who’s some quarters away from their promotion or hiring. Arbitrary or not, we have it.

Then you have to be someone with a track record of great performance in the team. Not necessarily the strongest in the group, but not in the “bottom half” either! Perhaps you were the TL, or someone responsible for some big projects, or someone to whom the team turns when things go down.

Finally, there needs to be an agreement between a number of people that this thing is a good idea. Besides your manager, there is also your manager’s manager, the PM of the team (if any) and their manager. If there’s other stakeholders they’ll be consulted too. Of course, the people you are going to manage will have a say in the decision. Strong objections from any can tank the process, or at least cause it to be restricted and treated even more cautiously.

With regards to where we source the manager, there is a priority list of sorts. In higher to lower priority, we have:

- From within the team.
    - Pros: knows the product, knows the systems, knows the team
    - Cons: inexperienced manager, might cause tensions
- From within the company, but already EM or clearly on the path to be one
    - Pros: knows the people, knows the way we work at Bolt
    - Cons: relatively-inexperienced manager, doesn’t know the product or systems
- From outside the company, but already EM with several years of experience
    - Pros: experienced, brings a fresh perspective, etc
    - Cons: doesn’t know the company, the product, or the team

As you can see, the more we know of a person as a member of Bolt, the more we’re OK with offering space for them to grow into the manager role. Conversely, folks brought in from the outside need to have demonstrated experience.

Now, there’s always going to be exceptions here. We’ve had Middle SWEs with reports or Seniors skipping straight to L2 management in the past. Don’t count on it for the future.

## The Evolution Of A Manager

Associated with the management career is a *management career path*. What we’re doing at Bolt is fairly standard across the industry. In this section I want to sketch how a “traditional” management career run looks like. In my view it has two distinct phases - your first exposure to being a manager and the second and longer part of going deeper into the path. I’ll cover them in the sections that follow. And throw in a bonus wildcard career option.

### From IC To Seasoned Line Manager

You start out as an IC in a team. You do a good job and it’s externally recognized as such. At some point, the previous manager may be moving, or there’s a subteam coagulating across some well-defined ownership. In any case there’s a need for someone to take the manager role. You volunteer and are appointed. There’s a shared understanding that this is a test period. You need to see if the role is actually what you want, and the organization needs to see if you’re actually good at it.

The initial team is very small. It’s just 2 to 4 people. Your title is still Senior SWE. You’ll be both TL and people manager in the group. And you’re still expected to do IC work for the most part. But you have some extra responsibilities around quarterly and yearly planning, and get to have a bigger say in the processes of the team.

Three to six months into your journey is the time to reflect on how things are going. There’s four possible outcomes.

- **If you enjoy the new type of work and the team is doing wel**l.
    - This is the *best* outcome and frankly the one *we hope for.*
    - You’re unblocked for the formal “promotion” to EM. This can happen as soon as *right away* if the team is large enough
- **If you don’t enjoy the new type of work and the team is doing well**
    - This is a *solid* outcome in the end. You tried something, gave it your best shot, and found out it didn’t fit with what you wanted to do.
    - The plan here is to step down from leading the team. Your manager needs to find a replacement. Depending on the situation you may be asked to keep running the team for a little while, just until a new manager can be found.
- **If you don’t enjoy the new type of work and the team is not doing well**
    - Then it’s a very clear win-win scenario to step away from managing the team. It’s not a *good outcome* but it is one we’re prepared for
    - Your manager needs to find a replacement ASAP. There’s a strong bias for not continuing the setup any longer than it needs to.
- **If you *do* enjoy the new type of work but the team is not doing well**
    - This is a *tricky case.* It hasn’t happened that often, as usually, folks tend to not like the stuff they’re not good at.
    - We have a bias for this thing not to go on. We’ll take it on a case-by-case basis, and study the whole situation, though.

Assuming you were in the first case, the team will continue to grow and you’ll grow as a manager too.

After a while, usually after 6 or 7 direct reports, it’s a good practice to delegate the technical ownership aspects of your job to a TL.

The next step is to handle the scaling as the team grows. Up till 10 to 12 direct reports is where the story remains the same, we expect you to scale.

### Beyond Line Manager

The individual contributor to line manager transition is a massive move. It can seem like a tremendous effort. But it’s really just the *start of the journey* down the management career path.

In engineering, at Bolt and many other technology companies, this usually takes the following form:

- Engineering Manager (EM) – the line manager position. Around 3-8 direct reports.
- Senior Engineering Manager (SEM) – a manager of managers or L2 manager. You’ll be responsible for a larger group of people, will own a larger product scope, will have manager reports, and also a team of teams. Around 3-8 direct reports, and team size between 15-50.
- Director of Engineering (DoE) – either an L2 manager or L3 manager. You’ll be responsible for a large group of people (50+), will own a complex and large product scope, will have manager and SEM reports, and very likely will have multiple large subteams. You’re also increasingly responsible for the external presence of the company, recruiting efforts, etc. Around 3-8 direct reports, and team size between 50-100.
- Vice President of Engineering (VPE) – currently the one person responsible for the whole of engineering.

Growth here means managing larger and larger teams successfully. The EM to SEM transition is another hard one. Not as big a delta as the IC to EM one for sure, but definitely not negligible either. And again you could say it is another type of job. As such, I’ve carved out a special "L2 Considerations".

You’ll start out as an EM of a team. You do a good job and it’s externally recognized as such. The team will start to increase in size beyond the 10 recommended maximum size. You’ll start breaking off smaller subteams of 2 to 4 people, with their own trainee manager. Pretty soon you’ll have your first report who has other reports, and your first skip-level reports. Things go well and several other teams spin-off. You’re delegating more and more to the new managers, and you might even have a GTL helping you out. Some of the managers have big enough teams that you and your manager can have the EM transition discussion with them.

Six to twelve months into your journey is the time to reflect on how things are going. Since this is still a big transition we’re not just going on inertia and we’ll do the same kind of analysis as before at the IC to EM transition. There are four possible outcomes.

- **If you enjoy the new type of work and the team is doing wel**l.
    - This is the *best* outcome and frankly the one *we hope for.*
    - You’re unblocked for the formal “promotion” to SEM. This can happen as soon as *right away* if the team is large enough
- **If you don’t enjoy the new type of work and the team is doing well**
    - This is a *solid* outcome in the end. You tried something, gave it your best shot, and found out it didn’t fit with what you wanted to do.
    - The plan here is to step down from leading the larger team and focus on a smaller team. Your manager needs to find a replacement. Depending on the situation you may be asked to keep running the team for a little while, just until a new manager can be found.
- **If you don’t enjoy the new type of work and the team is not doing well**
    - Then it’s a very clear win-win scenario to step away from managing the team. It’s not a *good outcome* but it is one we’re prepared for
    - Your manager needs to find a replacement ASAP. There’s a strong bias for not continuing the setup any longer than it needs to.
- **If you *do* enjoy the new type of work but the team is not doing well**
    - This is a *tricky case.* It hasn’t happened that often, as usually, folks tend to not like the stuff they’re not good at.
    - We have a bias for this thing not to go on. We’ll take it on a case-by-case basis, and study the whole situation, though.

Assuming you were in the first case, the team will continue to grow and you’ll grow as a manager too.

Besides the path of naturally growing the team, there’s also the option of taking over another fully formed team, when there’s some reorg-type event happening. It happens from time to time. If you view career progression as a *goal in itself*, then this is essentially *luck*. It used to happen a bit at Bolt, and it’ll for sure happen to a degree in the future. Less and less as we grow so don’t count on it. We’re at a stage where many teams are similar-ish in scope, so managers of close teams are rather matched in skill. So a would-be decision-maker might choose an external and experienced SEM in situations like this one.

After the SEM transition things have an inertia of their own. Being a SEM for a team of 20 people is not *radically* different from being a SEM for a team of 40 which is again not *radically* different from being a DoE for a team of 60. You still need to keep up, but if there are issues they’d have shown up somewhere on the path and not just at the DoE promotion checkmark.

As discussed in the < internal doc >, these sorts of promotions are critical. You are part of the top-5% of the org with regards to centrality. If things are not going well you can do a lot of damage. So the analyses that are done tend to be rather binary after a while.

- **If the team is doing well**. Then all is good
- **If the team is not doing well**. Then this is a *big problem*. Tens of engineers are affected. Complex and important products are mismanaged. Your manager will tend to act swiftly as this is a *big problem* for them too!

### But Wait There’s More – Career Pendulums

*Up* is not the only career progression option. The [engineer/manager pendulum](https://charity.wtf/2017/05/11/the-engineer-manager-pendulum/) highlights another way of tackling career growth by alternating between IC and EM roles. Experiences from one inform the other, and you end up being an overall better engineer than if you just focused on the other side.

It doesn’t go as far as saying that experience in management is a prerequisite for the higher levels of the IC track, but at Bolt at least there is a fair share of Staff+ engineers who are former managers.

## L2 Considerations

An implicit belief of most of this document is that being a manager is different from being an individual contributor. 	Especially when we’re comparing the common situation of line management vs being a senior software engineer.

What doesn’t get enough airtime is that being an L2 manager is different from being an L1 manager. Here L2 manager means a manager of managers, with little to no individual contributors or notion of a team. So something like a manager of 10 total people with one subteam of 3 wouldn’t count, but a manager of 15 total people with three subteams of 5 would.

The biggest and clearest difference is that there are more people. More people means more problems.

- But then you’re leading a group of several teams, roughly related. Each team does its thing, but it’s harder for the group to feel like a unit. There still should be some [overarching structure](https://horia141.com/career/2022-06-16-the-notion-of-hierarchy) but the bounds are much weaker overall.
- Since the domain itself is larger, it becomes harder to grok it completely. In a single team you can keep a tab on all projects, but in larger teams only on the key projects. You’ll have a passing familiarity with some, and perhaps not even know about others.

The way to scale here is to delegate and create the structures for others to succeed. Getting involved in every tech discussion, or unblocking every project, or reviewing random code or design docs is a recipe for trouble in general.

The relationship between you and your reports will change too. They will be managers of various skill levels, and higher-level engineers (often acting as Group TLs for your group).

- For one, your 1:1s will become more operational. There are goals to catch up on, updates to provide, context to be shared, etc. Spending the meeting talking about the latest movie or *generally bonding* will become later and later.
- Then you’ll need to allow for autonomy and room to grow. There’s a spectrum of sponsoring, mentoring, and coaching, and you need to find the sweet spot for each person or each situation. Furthermore, your managers are also responsible for their slice of the problem, hence they have a right to a sort of ownership shield to run their show as they see fit, as long as they’re meeting the expectations.

At Bolt in particular, you’ll be more exposed to company processes, or take a more active role in salary discussions, or worry about a new site being opened and the projects to staff it with, etc. In principle, you are much more central to the organization than before.

There’s going to be a new class of decisions you are responsible for:

- Final word on hiring in any team
- Salary decisions on new joiners
- Important word on salary increases in compensation review
- Some promo decisions (Junior->Midlevel, Midlevel->Senior) and heavy involvement in others

Finally and perhaps most annoyingly, you are out of the area of quick wins. An IC can ship a feature in a day, an EM can ship a project in a month, but as an SEM you’re looking at multi-quarter timelines for the kinds of work you’re expected to do. Things like hiring mobile devs in a previously backend team, restructuring the way a particular team works, adopting an experimental technology from Foundations (our infra group), etc.

With all of the above, there’s a lot of room for the specifics of the team and individual to factor in. Highly technical teams will require highly technical L2 managers. Folks who’ve been historically involved with certain projects or technology can still contribute as L2 or above managers, whereas the same expectation wouldn’t hold for new joiners. Play it by ear and optimize for what works for you.

The good news is that the L2 to L3 and beyond transitions are much smoother. Perhaps just the final transition to being an executive and fully responsible for engineering (or so I’m told). But if you can master operating as a manager of managers you can confidently say you have a knack for this management thing. And while folks won’t hurry to offer you those sweet FAANG SVP positions, they’ll at least recognize it’s a difference in scale and years of experience, rather than in the substance.

### Who Gets To Be The L2 Manager?

In light of the above, the next question to ask is who gets to be the L2 manager?

There are three important situations to discuss.

- If we have a team that will grow such that it’ll split into coherent teams and will need an L2 structure, then the current L1 manager is the *first in line* and the discussion in "Beyond Line Manager" happens. If the teams aren’t coherent enough, then they may or may not stay with the same manager. It’s a case-by-case discussion.
- If we have a team that will grow such that it’ll split into coherent teams and will need an L2 structure, but the current L1 manager doesn’t want or cannot handle the extra responsibility, then we will **look for a company-wide or external hire.** At least with 99% probability.
- If we have several existing and established teams that we want to group together for coherence reasons, then we have a whole other discussion.
    - If there is one clear leader in the group, who is close to L2 management or already at that level, then that’s a natural choice. This is rather like moving some teams under a new manager.
    - If there is no clear leader in the group, then we have all the below discussions.

With regards to where we source the manager, there is a priority list of sorts. In higher to lower priority, we have:

- From within the team.
    - Pros: knows the product, knows the systems, knows the team
    - Cons: inexperienced L2 manager, power-dynamics shift, can lead to the Trojan war
- From within the company, but already SEM or clearly on the path to be one
    - Pros: knows the people, knows the way we work at Bolt
    - Cons: doesn’t know the product or systems
- From outside the company, but already SEM with several years of experience
    - Pros: experienced, brings a fresh perspective, solves a political situation in a neutral way, etc
    - Cons: doesn’t know the company, the product, or the team, very hard to find

As you can see, the more we know of a person as a member of Bolt, the more we’re OK with offering space for them to grow into the manager role. Conversely, folks brought in from the outside need to have demonstrated experience.

## Some Things You Noticed Are Funky That Really Are Funky

If you’ve been in the EM role for a while you’ve probably noticed some things that are funky. I’m here to confirm that they are indeed funky. In no particular oder.

**You aren't necessarily the best-paid person on the team**. At Bolt and many other companies, the salary band structure places EM at the SSWE level. This means that if you have Staff or above ICs reporting to you they *will* have higher total compensation. But even within the SSWEs and equivalent in the group, there might be folks earning more. If perhaps they have high performance, while you only have solid performance. Or if some of the other sources of “noise” rear their head: better negotiation skills, more leverage at negotiations, various compensation debt situations, etc.

**Career progression is linked to some things you can't control**. Things such as the size of the team. Successful execution as defined above with a team of a certain size is the main criteria for the promotion. This is not a simple thing of course. But team size is outside your control. It depends on your project, and on the capability of you and your PM to convince leadership that the team should grow. After that, there are the natural limitations of growing a team. Or market forces or world events halting hiring. So you might find yourself ready and capable of taking on a bigger challenge, but the challenge simply not showing up.

Indeed some companies have more fine-grained management levels. And we’ll for sure get there too as our company grows. But at the end of the day, there's only so much you can do as an L1 manager or L2 manager.

**In general career progression means running bigger and bigger organizations**. Or at least being closer to the executive level and “calling more of the shots”. **There's no simpler solution for folks who can't or won't run bigger orgs.** But managing bigger teams is different from the line management folks start with. And these bigger teams are rarer. There are N/10 EM positions. But only N/50 L2 EM positions and so on. Furthermore, there aren’t *that many* companies needing L2 managers (for real) or L3 managers, etc. Power laws all the way!

There's no standard middle path either. As seen above you can go all-in on technical growth or org growth. But not both at most organizations. Perhaps in infrastructure groups or at large companies, it's more common to see Staff+ engineers with reports. But overall it's not a common occurrence.

**You will become distant from the technical aspects**. Sure you might not notice it in your first year or your third year. But you’ll definitely see it when the industry starts to move, and especially when you get deep enough into the rabbit hole that you don't touch code at all at work. This occurs somewhere on the path to L2 management. If you end up not linking the career path itself you might end up having a hard time returning to IC work.

Especially for folks who see management as a *promotion,* it’s very tempting to make the jump *before* you’re an experienced engineer if given the chance. It opens you up to problems should you choose to go back.

# Extra Skills

There are some very common extra skills managers need to pay attention to. I’d be remiss if I didn’t mention them here.

These are:

- **Public speaking** → in so much as there are “career cheat codes” this one is it. Even being decent here offers many advantages.
- **Presenting** → a special type of “public speaking” that is very common in corporations. Backed by a slide show, you’re out to inform, convince, or justify. Presenting to executives deserves a special shout-out here as a nifty subskill.
- **Writing** → as we transition from an oral and Slack culture to a written one, being able to write well is another superpower. Being able to write concisely is a holy grail few achieve. Not me.
- **Influence without power** → even when you do have the power you don’t want to use it. And in most situations as a manager, you won’t have power. Being persuasive, seeing the other person’s point of view, negotiating are important skills to master.
- **Candid communication** → tough discussions don’t come easy. Even when we commit to having them, they tend to go sideways. Knowing how to have high-stakes conversations with folks is another good superpower to have.
- **Giving feedback** → giving good feedback is an art. Both the delivery and the content are hard to do right. But it’s your number one tool in improving your team, as well as the group as a whole.

# Conclusion

There you have it: 10000 words on management and it's barely scratching the surface. I hope you at least have a better overview
of the job than at the start. If you'd like to learn more, [the reading list](https://horia141.com/career/2022-05-22-my-suggested-reading) is
a good place to dig deeper. If what you've heard about management sounds like your cup of tea - whether as a
manager or as an individual contributor being subjected to said manager - then head on over to
[our careers page](https://bolt.eu/en/careers/teams/engineering) and check out our openings. We are hiring!
