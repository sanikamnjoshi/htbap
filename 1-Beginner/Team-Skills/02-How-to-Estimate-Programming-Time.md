# How to Estimate Programming Time
[//]: # (Version:1.0.0)
==Estimation takes practice. It also takes labour. It takes so much labour it may be a good idea to estimate the time it will take to make the estimate, especially if you are asked to estimate something big. ⏱️==

> [!note] ⏱️ meta-estimate
> case in point: when maria and I gave an estimate of how long it will take us to come up with an estimate for the QA automation

When asked to provide an estimate of something big, the most honest thing to do is to stall. Most engineers are enthusiastic and eager to please, and stalling certainly will displease the stalled. But an on-the-spot estimate probably won't be accurate and honest.

==While stalling, it may be possible to consider doing or prototyping the task. If political pressure permits, this is the most accurate way of producing the estimate, and it makes real progress.==

When not possible to take the time for some investigation, you should first establish the meaning of the estimate very clearly. Restate that meaning as the first and last part of your written estimate. ==Prepare a written estimate by de-constructing the task into progressively smaller subtasks until each small task is no more than a day; ideally at most in length.== The most important thing is not to leave anything out. For instance, documentation, testing, time for planning, time for communicating with other groups, and vacation time are all very important. ==If you spend part of each day dealing with knuckleheads, put a line item for that in the estimate. 🐦== This gives your boss visibility into what is using up your time at a minimum, and might get you more time.

> [!note] 🐦 knucklheads
> add a line item, but maybe not in those exact words

I know good engineers who pad estimates implicitly, but I recommend that you do not. One of the results of padding is trust in you may be depleted. For instance, an engineer might estimate three days for a task that she truly thinks will take one day. The engineer may plan to spend two days documenting it, or two days working on some other useful project. But it will be detectable that the task was done in only one day (if it turns out that way), and the appearance of slacking or overestimating is born. It's far better to give proper visibility into what you are actually doing. If documentation takes twice as long as coding and the estimate says so, tremendous advantage is gained by making this visible to the manager.

> [!quote] important! do not implicitly pad estimates!
> *"I know good engineers who pad estimates implicitly, but I recommend that you do not. One of the results of padding is trust in you may be depleted. \[...\] It's far better to give proper visibility into what you are actually doing. If documentation takes twice as long as coding and the estimate says so, tremendous advantage is gained by making this visible to the manager."*

==Pad explicitly instead. If a task will probably take one day - but might take ten days if your approach doesn't work - note this somehow in the estimate if you can==; if not, at least do an average weighted by your estimates of the probabilities. ==Any risk factor that you can identify and assign an estimate to, should go into the schedule.== One person is unlikely to be sick in any given week. But a large project with many engineers will have some sick time; likewise vacation time. And what is the probability of a mandatory company-wide training seminar? If it can be estimated, stick it in. There are of course, unknown unknowns, or *unk-unks*. Unk-unks by definition cannot be estimated individually. You can try to create a global line item for all unk-unks, or handle them in some other way that you communicate to your boss. You cannot, however, let your boss forget that they exist, and it is devilishly easy for an estimate to become a schedule without the unk-unks considered.

==In a team environment, you should try to have the people who will do the work do the estimate, and you should try to have team-wide consensus on estimates.== People vary widely in skill, experience, preparedness, and confidence. ==Calamity strikes when a strong programmer estimates for herself and then weak programmers are held to this estimate.== The act of having the whole team agree on a line-by-line basis to the estimate clarifies the team understanding, as well as allowing the opportunity for tactical reassignment of resources (for instance, shifting burden away from weaker team members to stronger).

==If there are big risks that cannot be evaluated, it is your duty to state so forcefully enough that your manager does not commit to them and then become embarrassed when the risk occurs.== Hopefully in such a case whatever is needed will be done to decrease the risk.

If you can convince your company to use *Extreme Programming*, you will only have to estimate relatively small things, and this is both more fun and more productive.

Next [How to Find Out Information](03-How-to-Find-Out-Information.md)
