---
share: true
created: 2023-10-30T14:29
updated: 2026-08-06T15:36
---
Khái niệm:: 

Why don't some security people concern what

For brevity, I'll name the security-mind person Alice, and the non-security-mind person Bob. Bob is also running a business. He means no harm to his users, and has a level of awareness on security, but for Alice that's not suffice. Alice of course wants Bob to pay more attention and resource on security. However Bob see that there are other things to be prioritized than security, and has no budget for it. It's also unlikely that Alice would actually help him for free. What she can spend is discussion.

For clarity, security through obscurity here means that security through *only* obscurity.

Alice can point out attack vectors that Bob is in ignorance.

if she don't care about these, her legitimate concern will likely fail. 

Of course the best case is the product is bulletproof: a car that never get crash, a nuclear reactor that never get explode, and a hosting that never get compromised.
I bet even Alice still do security by obs

At the end of the day, it requires a malicious actor in order to carry out a SQL injection attack. To take your engineers to court example to the ultimate extreme -- sure the engineers built the bridge safely to withstand thousands of tons of cars, but they didn't build it to withstand someone driving a car full of thousands of pounds of explosives on it, then detonating. Should we then say every bridge should have a built in scanner to make sure only "clean" cars pass? In this same analogy, the Database functions correctly, until someone decides to drive a bomb-filled car into it.


# When is accepting risks acceptable?
## Motivation
I understand that many companies just want to cut cost at much as possible. Greed usually be the one to blame, but I think usually these are fairer to be blamed on:
- Externality: the person who make decisions is not the person who face the consequences of that decision
- Ignorance of security: you don't know what you don't know
- The path of least resistance is usually unsafe: if the right thing to do is the easy thing to do, then we don't need the concepts of "rightness" and "easiness" at all

I think while we can sympathize with these cases (because they are all human factors and definitely can happen to any of us), we don't accept to let them happen. The solution is regulation, but sadly both the law and the enforcement usually aren't enough.

However, security is not free, and there are threat models that accepting the risks is acceptable. At least to me, if financial situation is insecure and the risk is not critical, then I think it's acceptable to not spending resource to it, even though it's not ideal. In general, as the users are the one take the consequences of the action the provider takes, they should be the one to make the decision, not the provider or the security person. If they can accept the risk, then we should respect that.

Some other equivalent questions:
- At what threat model that doing nothing is acceptable?
- When is not preventing the risk acceptable?
- What risks have acceptable probability or acceptable impact?
- What risks can we expect the users to take?
- What risks are acceptable to ignore?
- What risks whose cost are acceptable?
- When is security through *only* obscurity acceptable?

At the end of the day, quantitative data is hardly achieved, and can always be questionable.

(I mostly interact with webapps/SaaS so the question reflects that. However I want the answers to be inclusive to other cases.)

## Definition of "acceptable" 
The lack of action is acceptable is when the users find it acceptable. To account for the fact that different people have different levels of acceptable, I'll say more than half of the users have to agree with that. Now, as quantitative data is usually not available or even possible, unfortunately in practice the one who make the decision hardly be the users but the provider. To cover for this asymmetry in power, I'll refine the definition to this:

> Accepted by one certified security person that half of the users would accept to spend resources for other operations and doing nothing to fix the security issue or just through only obscurity, had the user had the knowledge of security person (the mind) and been in the position of the provider (the heart)

This definition covers these ideas:
- In theory, the users make the decision
- In practice, the security person and the provider make the decision
- The concerns of the security person and the provider are accounted. They have more security knowledge and understand the situation than the users
- Inaction is only acceptable when the provider isn't financially secured yet or when it is truly that the users aren't harmed, not because of greed or human factors of the provider

Here is how it works:
1. The security person will do risk analysis on the issue: 
    - If the analysis conclude that that the users won't be harmed, the provider can do nothing
    - If no, continue to step 2
2. The provider will explain their situation to the security person
3. The security person will estimate how the users would judge the situation, had the user had listened to both the security person and the provider
    - If more than half of the users would vote acceptable, the provider can do nothing
    - If no, the provider have to fix the issue

Here is one way to estimate how users would judge the situation: the security person will put herself in the position of the provider, and guess how likely she would do nothing. The chance that she would do nothing will be equivalent with the percentage the users vote acceptable.

Any better procedure is welcomed to be used.

## Example cases
*Cases in italic is only applicable when the cost to solve the issue makes the financial situation insecure.* Usually it's about hiring a staff dedicated for security, as all other staffs either have insufficient knowledge, or overwhelmed with other tasks, that if they stop doing them the financial situation will be insecure.

Non-critical security issues:
- When the service is just some HTML pages with simple JS scripts/calculation
- When the service doesn't store user's data, or *only store non-PII data*
- When the service is based on a CMS which is updated regularly (i.e. the service is just a Google spreadsheet, or a WordPress site) 
- *When the vector can't be attacked on mass (i.e. via bots) but individually, and the service is unpopular enough (e.g. less than 100 users)*

Other reasons than security:
- The users have signed a term of service that they accept all the risks of using the service
- There is a survey asking the users where to spend resources, and the top result is not security
- The program is only intended to be used by a small group, not many people (sudden viral) 
- *When the expected cost of attack minus the expected reward for a successful attack is still higher than what an average attacker would be willing to spend*
- *The risk of having an authorized user intentionally leaking the data is higher than from being attacked from an outsider*
- *The provider has already bought security insurance*
- *The cause of the project is meaningful*
- *The project is vibe coding with LLMs*
- *The provider has asked someone they trust on security and that person concludes that accepting the risk is acceptable*

Nguồn:: [U.S. Army Website Hacked](https://www.darkreading.com/cyber-risk/u-s-army-website-hacked)

[](https://chat.stackexchange.com/transcript/message/30721573#30721573 "click for message actions")

@treehau5 my VPS has 500+ failed SSH login attempts in the last twelve hours. Constant attack is the expected state for internet facing services. If your world had an exploding car every 90 seconds, and the bridge company made no provision to handle explosions, would you then consider that a good design? Similarly, if a bank vault just had a fibreboard door and no alarm, would you be happy with the bank? After all, it functions perfectly well to hold valuables - until someone decides to attack it.


"The library system ... is a huge security nightmare" — why can't it fix the problem? I get that an unsecured lib upstream can impact all libs depending on it. But does that mean theoretically there is no way to fix that (besides giving up the idea of dependency chain)? And how does Rust address this? Is there any article to read this in deep?
–[Just a moment...](https://security.stackexchange.com/questions/219872/is-exploit-free-software-possible?noredirect=1&lq=1#comment598700_219898)

human factorThe attacker is bounded:
only by someone with the required knowledge, skill, time and motivation

The tradeoff between how much money/effort is spend on security vs. business and opportunities is individual - and it is not primarily about cutting costs but finding an appropriate balance where the limited money gets spent. And as for your definition of "acceptable" - in many jurisdictions it is not sufficient to somehow make the users click a checkbox that they find anything acceptable but some basic consumer protection is always required and cannot be argued away. Because of this I think the fundamental assumptions your question is based on are wrong.

You've missed a key concept in risk: the **risk owner**. They are the ones who are responsible for determining what is acceptable and taking the consequences when risks materialise. People, even users, can contribute perspectives to the **risk owner**, but all ultimate decisions are theirs, not the people who could be affected. Once you factor this role into your thought experiment, your entire question falls down and your thoughts on how your scheme might play out are naive.

"The security person will do risk analysis" -- based on what? Likelihood and impact on what? Some idealistic notion of a generalised understanding of what "should" happen? Business realities notwithstanding? "conclude that the users won't be harmed" -- define 'harm', who defines what 'harm' is, is only zero possible harm, as interpreted by everyone, acceptable? "provider will explain their situation to the security person" -- you mean the **risk owner**? The one who actually has to pay for everything? That's backwards.

"security person will estimate how the users would judge the situation" -- based on **_what_**? Their personal understanding of what any/every user might consider? Why "half"? Why not 2/3 or 3/4 or 90%? Screw the other people who will be, as you defined it, _harmed_? Are you aware of all the wonderful, well-considered, well-structured risk management frameworks out there? I think you are trying to solve a problem without understanding the decades' worth of solutions for this. Or trying to introduce a solution because you see people not using an existing solution.

Obscurity won't protect against a determined attacker, but it does help against lazy, casual attackers, and there are lots of those. ([source](https://security.stackexchange.com/questions/211189/is-open-sourcing-the-code-of-a-webapp-not-recommended#comment426253_211245))  
→ When you don't expected a determined attacker. 
[risk management - Is this much distrust really necessary? - Information Security Stack Exchange](https://security.stackexchange.com/questions/7338/is-this-much-distrust-really-necessary)

# Is there a list of easy-to-read and easy-to-use practices?
It is [said](https://security.stackexchange.com/questions/286945/is-a-closed-source-saas-more-secured-especially-when-the-team-is-overwhelmed#comment598660_286947) that we don't necessarily have to invest a lot of extra time or money on security because there are easy-to-use countermeasures for a lot of typical vulnerabilities. However, 

Because [we are still using unsafe-by-default systems](https://security.stackexchange.com/a/128414/94500), so basic mistakes are still made. Until we can work on safe-by-default systems, I guess an ideal solution is having a list of easy-to-read and easy-to-use practices for fixing typical vulnerabilities, so that one can switch from the path of least resistance to the path of safely least resistance with least effort.

I can think of some common advices like always use the latest update, write test early or even use TDD, manipulate strings via safe libs or at least via the syntax tree, etc. I know of [OWASP](https://owasp.org/www-project-web-security-testing-guide/), but at a glance it is not easy-to-read and easy-to-use, so it is far from the path of least resistance (require a lot of effort to get to the path of safely least resistance). It is suitable for a [reference](https://diataxis.fr/reference/) or [explanation](https://diataxis.fr/explanation/), while what we need here a [how-to guide](https://diataxis.fr/how-to-guides/).

I mostly deal with web development so I'd like the answers to reflect that, but I don't want them to only focus on it. I don't use LLMs, but I think for most people, especially [barefoot developers](https://maggieappleton.com/home-cooked-software), the path of least resistance now is via LLMs, so we may need to consider that.

# The probability of getting attacked by an unpopular FOSS
# How secure are websites built from website builders?
There are SaaS providers for building and hosting website made with WYSIWYG and LLM-prompt [website builder](https://en.wikipedia.org/wiki/Website_builder), such as WordPress.com, Webflow, etc. I guess these services should be secure-by-default and secure-by-design, e.g. the builders should be guided to generated code to follow [secure coding in JavaScript](https://stackoverflow.blog/2025/10/15/secure-coding-in-javascript/), and the hostings should provide [automated vulnerability detection](https://owasp.org/www-community/Free_for_Open_Source_Application_Security_Tools)? I'm not sure if that's enough to effectively defend [these security threats](https://en.wikipedia.org/wiki/Application_security#Security_threats) or these [likely attacters](https://wiki.owasp.org/index.php/Security_by_Design_Principles#About_attackers):

- Disgruntled staff or developers
- “Drive by” attacks, such as side effects or direct consequences of a virus, worm, or Trojan attack
- Motivated criminal attackers, such as organized crime
- Criminal attackers without motive against your organization, such as defacers
- Script kiddies

Note that these builders allow developers to build a webapp of their own, with login components, not just static pages. I wonder if the security improves if no LLM involves, or the developers don't use these builders at all but just build them from SaaSkit templates (e.g. [this one](https://deno.com/saaskit)), with popular secure-by-default IDE and CI/CD (e.g. [VS Code](https://code.visualstudio.com/docs/copilot/security) and [GitHub](https://docs.github.com/en/code-security)), with the assumption that the developers don't know much about security.

# Meta: How much misreading the material be acceptable?
First, I'd like to say that I don't mean to troll or spam the site. I want the site to be healthy, be it for selfless or selfish reasons. I welcome your criticism, downvotes and close votes. Sure, they are not ideals to me, but I still learn a lot from them. I understand the burden of moderating the site, and I appreciate your effort. 

My purpose in this post is to have a better place to discuss my behaviors and the complains. The complains have been scattered in various questions, in the comment format, so it's hard to follow and reply. I hope you can see that I do do reflection, and we can have some agreements.

I guess it's best to explain myself based on one question, to avoid me being too ranty. I'll pick [the last one](https://security.stackexchange.com/questions/286982/is-it-possible-for-a-website-builders-to-build-a-secured-website?noredirect=1#comment598807_286982). 

> And then you list a bunch of certifications to ask if those mean the product of the product is secure. When you ignore the statements by this vendor.
> And you **_skip right over_** the guide they publish on that very webpage about security that explains all the ways someone using Webflow could violate security. 
> you didn't spend 60 seconds to read the page you linked

I use a time tracker so I have a solid number for how much I spend time for this. From 2:20 pm to 3:14 pm I was rewording the question, I spent a total amount of [13.5 minutes](https://i.vgy.me/cu19tK.png) on reading security pages of Webflow. None of them had the keyword I was looking for: the security of the product of the product (POP). Even after you say the comment I reread it 2 times and still don't see where it's addressed

(Embarrassingly, after really forcing myself to look at the animated screenshots and read the detailed texts underneath the keywords, I start to realize that it does seem talking about POP security. I take my problem on this. I'll discuss about this later.)

I still fails to see where the text "explains all the ways someone using Webflow could violate security". Much appreciated if you screenshot it.

> You appear to be approaching all your posts with a steadfast set of assumptions and biases, and you don't use the tools you have in your hands to challenge your own foundations

I suggest using the word "mental model" for a better description. I think there are 3 different mental models and behaviors intertwiningly here:
- Mental model on security 
- Mental model on asking questions
- Behaviors on reading materials 

I think we all agree that while our ultimate goal is to have the most accurate mental model on security, the ability on reaching that depends on the other ones. Even if I have the most steadfast (and wrong) beliefs on security, with the other ones working properly I will soon having them updated. 

Honestly, I think I have them as how others have them.

## Mental model on asking questions
I was asked to read the FAQ [how to ask](https://security.stackexchange.com/help/dont-ask) or [what to not ask](https://security.stackexchange.com/help/dont-ask) pages. They are useful to guide newcomers of SE, but after that I don't think they are much useful for newcomers of the field to stop asking for subjective questions (or opinions or open-ended discussions), besides the obvious ones, which the FAQ has made clear of. Without a deep understanding on the field, in eyes of the newcomers every question they make is objective. For example, how can I know that "there is no generalized statement possible about arbitrary website builders", or one "can't just take a quick glance at some product and magically see whether it meets specific security goals or has vulnerabilities" before asking the question? If I don't even know what I'm assuming, how can I challenge it? Bad questions (for the QA format) is a result of lack of knowledge on the field. I don't think this is avoidable, even with best attempt to avoid that.

## Reading material behaviors
From [Text Scanning Patterns: Eyetracking Evidence - NN/G](https://www.nngroup.com/articles/text-scanning-patterns-eyetracking/):
> On the web, people don’t read every word on a page; instead, they scan. They naturally attempt to be efficient and put in the least possible work for achieving their goal. They have learned that scanning can deliver almost the same amount of information as reading, but with significant less time and effort.
> 
> How people read on the web is highly contingent upon:
> - Their task
> - Their assumptions from previous experiences with the internet, site, or brand
> - The page layout
> - The type of page content (e.g., text versus images)

You may be interested to read the full article to understand the 4 patterns that people use to scan text on the web (listed in increasing order, worst to best, of effectiveness): F-pattern, Spotted pattern, Layer-cake pattern, Commitment pattern.

In my scenario:
- My task: how does POP defend [security threats](https://en.wikipedia.org/wiki/Application_security#Security_threats) (broken access control, injection, etc.) or follow [secure coding](https://stackoverflow.blog/2025/10/15/secure-coding-in-javascript/) (cross-site scripting, inline script, etc.)?
- My assumptions from previous experiences: the Webflow page is to give an overview/summarize the security of the service, not to give full analysis. It's also a mean to advertise the service, with the target is normal users, not techy ones.

I have no data to know which scanning pattern I did, but apparently it wasn't the commitment pattern. I think this is justified, as I don't see the keywords it presents are relevant to my task.

Do I do commitment pattern elsewhere? Yes. If the page is in the format of an article, then I'm more likely to read it carefully. An example is how I get the link to [this book](https://www.cs.auckland.ac.nz/~pgut001/pubs/book.pdf): I read every comment on a lot of questions to get a link to it. [A long article usually have a higher benefit/cost ratio](https://www.nngroup.com/articles/write-articles-not-blogs/). While I don't have the data to back up my claim, I can say with high confidence that before asking any question usually I've read all materials that I think are relevant.

---

In general, I think your expertise in the field gives you an advantage to scan text, even when the page is doesn't contain the keywords you need. Perhaps even with the same *eye movement* of the novices, you can still make a better judgement than them? Perhaps had you been in a field that you don't know much, you would have done the same? Perhaps you are portraying [the curse of knowledge](https://en.wikipedia.org/wiki/Curse_of_knowledge)? In the case they miss any information, would a more helpful feedback would be asking them this question "the page says xyz, why don't you think it answers you?"?


I'm kinda done here. For weeks we have been providing info, you've misread it, you've come to erroneous conclusions, and then we have to walk you through what we've provided to get you to absorb what you've read to understand that your questions and conclusions don't make sense. And in one case, you found info all on your own, misread it, came to erroneous conclusions, and then got upset when the post was deleted for being utterly irrelevant because you didn't understand what you, yourself, posted. There's nothing for us to do here, All next steps are yours.

I was answering your first question. I didn't see your new edit. As for the purpose of the post, by "discuss my behaviors", and the implication is that we should discuss about the complains. You ask me to challenge my foundation, so I wrapped that inside "my behaviors". If making it explicitly is necessary, then I'll update the question. And I didn't upset at all. I just wonder why deleting is a better course than downvoting it. – 
No, you're not listening. Again. There is no point in updating this post. 1. This is off-topic. 2. I'm done. 3. This is a you thing to address as a foundational issue you need to address and a 3rd party on a forum can't help you.
