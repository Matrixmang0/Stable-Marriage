# Marriage Problem
## Problem Statement

Imagine you're in a village with $$N$$ women and $$N$$ men, and they're all eager to tie the knot, looking for their perfect match. Your task is to pair up $$N$$ men with $$N$$ women. The goal: ensure their marriage is **STABLE**, meaning they're happy with each other and maybe not elope for that extra flair.

> You can picturize UNSTABLE like the wobbly relationships in the movie **Kabhi Alvida Naa Kehna**, if you catch my drift 😉

##### So, now think how will you go about solving this stable marriage problem ?
#

To tackle this stable marriage problem, let's consider that each man has a priority list, ranking the women he wishes to settle down with. Similarly, each woman has her own list of preferred men.

Now, you might think, why not just pair up all the men with their top choice women? Sounds simple, doesn't it? But, alas, it's not that straightforward. Let's dive into the intricacies.

Imagine  a man $$M_1$$ has $$W_3$$ as his first choice. If we hastily tie the knot without considering $$W_3$$'s preferences, we could end up with a shaky union. What if $$M_1$$ is at the bottom of $$W_3$$'s list? That doesn't sound like a recipe for a stable marriage, does it?

Indeed, it's not a stable pair. In this scenario, W10 might be tempted to elope with a man who ranked higher than M1 in her list. The horror!

Now, we need a solution that prevents such escapades and ensures a stable marriage for all. Let's put our thinking caps on.

### Algorithm

The algorithm for this problem suggests that men should propose to their top-choice women, and then the women decide whether to accept the proposal or keep the man on standby.

##### CASE I

If a man who proposed to a woman is also her top choice, the woman happily accepts the proposal, and they both settle down.

##### CASE II

Now, what if the man who proposed is not the woman's first preference?

In this case, the woman politely keeps the man on standby and patiently waits for someone who is at the top of her list to propose.

The process continues until it stops, at which point the woman must accept the proposal from the man she kept on standby.

Sounds complicated..? Phew.

Let's break it down with a simple example. For the sake of simplicity, let's consider three women and three men, each with their preference lists:

Here, $$W_1$$ has $$M_3$$ as her first choice, $$M_2$$ as her second, and $$M_1$$ as her last option. The similar ranking goes for the other women and men.

Now, let's grasp this problem by observing how the algorithm unfolds from a _**Balcony Approach**_.

Imagine every woman $$W_1$$, $$W_2$$, $$W_3$$ is standing on the balcony, eagerly waiting for men to propose. If a woman sees a man who proposes to her and happens to be her first preference, she happily accepts the proposal, and the two of them make their exit. Once a woman is married, she no longer entertains proposals, and a married man stops proposing to other women.

It's as simple as that.

##### STEP 1:
#
$$W_2$$ receives two proposals from $$M_1$$ and $$M_3$$, with $$M_1$$ being her first preference. She accepts the proposal, and now $$M_1$$ and $$W_2$$ are happily married. Meanwhile, $$M_3$$ faces rejection from $$W_2$$ and moves on to propose to the next woman on his preference list.

As for $$W_3$$, $$M_2$$ is her second preference. She patiently waits for her first preference to propose, keeping $$M_2$$ on standby. However, $$M_2$$ is not rejected, so he remains in the standby position without proposing to anyone else.

##### STEP 2:
#
$$M_1$$ approaches $$W_3$$ because $$M_1$$ is $$W_3$$'s first preference. Consequently, $$M_1$$ and $$W_3$$ get married, leading to $$M_2$$'s rejection.

Since both $$W_2$$ and $$W_3$$ are now married, $$M_2$$ has only one option left to propose to $$W_1$$. Due to $$M_1$$ and $$W_3$$ being already married, $$W_1$$ has no choice but to accept $$M_2$$'s proposal. Rejecting them would result in the forbidden pairing of $$M_2$$ and $$W_1$$.

Notably, both $$M_2$$ and $$W_1$$ end up with their second preference, which isn't too bad.

In the final pair, we have a stable combination:

- $$W_2$$ and $$M_3$$ are happy as they got their first preferences.
- $$W_3$$ is content as well.
- $$M_1$$ would prefer $$W_2$$ over $$W_3$$, but since $$W_2$$ is already happily married, $$M_1$$ has to stay with $$W_3$$.

Everything seems to make sense, right?

$$W_1$$ would prefer to settle with $$M_3$$, but since $$M_3$$ is happier with $$W_2$$, $$W_1$$ has no choice but to stay. The same goes for $$M_2$$.

Hence, the entire system of combinations appears **STABLE**.

With the algorithm now complete, a question arises: _Who benefits more the proposers or those who accept and reject?_

Alternatively, the strategy or algorithm we've just witnessed can be reversed. Women could propose to men, and men would then choose or wait. What if we approached the same example from the opposite perspective?

Let's see what unfolds, addressing the question we raised earlier.

As it turns out, the ones making the choices have the upper hand, unlike the proposers who are always at the mercy of those accepting or rejecting them. Let's take a moment to ponder why this is the case.

It's because the choosers work their way down their preference list from top to bottom. At each point, they only settle for the next person on their list if they face rejection. And mind you, this rejection only happens if a man higher on the woman's preference list makes a grand entrance.

So, here's the revelation: the proposer knows they can't get a better deal than where they're currently biding their time. But, alas, that's not the situation for the person in the "balcony" (making the accept/reject call).

Anyone who shows up may or may not be at the top of the person's preference list. However, if nobody else turns up, it means that person has to settle with the current option, doesn't it?

Therefore, we reach the conclusion that the **one who proposes enjoys more benefits than the one who accepts**.

##$ Complexity

Let's not dwell on this for too long, but here's a quick insight.

In a nutshell, the complexity is $$O(N^2)$$. But why?

Well, think about it. In this algorithm, the worst-case scenario is when a man has to go through his entire preference list. That means he might have to visit N-1 women before finding his match. And this scenario could unfold for all the men. Therefore, the upper bound worst case complexity is $$O(N^2)$$.