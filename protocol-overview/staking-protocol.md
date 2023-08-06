---
description: >-
  Introducing Rosa Finance’s staking protocol, a transparent way to empower
  users to stake their ROSA tokens, unlock lucrative rewards, and earn a share
  of protocol revenues.
---

# Staking Protocol

## Overview

Rosa Finance introduces a robust and innovative staking infrastructure that inspires active engagement and contribution towards the protocol's expansion and stability. Stakers interact with the protocol by pledging their ROSA tokens, and in return, they accrue rewards over time in proportion to their stake. Rewards, delivered in ROSA and CHR tokens, are distributed on a weekly schedule. The protocol further extends its utility by introducing stROSA, a token that symbolizes staked ROSA in the network.

## **stROSA: The Staking Derivative**

Rosa Finance's dynamic staking system incorporates a mechanism for stakers to represent their staked ROSA as a staking derivative token within the system: stROSA. Users can mint (i.e., stake) or burn (i.e., unstake) these tokens, managing their holdings to align with their personal investment strategy and financial targets.

## **Reward Generation: ROSA and CHR Tokens**

Stakers are entitled to two types of rewards: ROSA and CHR tokens.

1. Each week, a percentage of Rosa Finance's protocol earnings are converted into ROSA tokens and distributed among stakers. Generated from assets supported by Rosa Finance (e.g., DAI, WETH), this mechanism consistently fuels the demand for ROSA tokens and synchronizes the interests of stakers with the overall platform's success.
2. Alongside ROSA tokens, stakers are also rewarded with CHR tokens. These tokens are produced as a result of Rosa Finance's strategic operations on the Chronos platform. Through a process known as "bribing", Rosa Finance promotes its ROSA/USDC liquidity pool on Chronos, thereby boosting the platform's LP revenue, which is then allocated to stakers in the form of CHR tokens.

## **Claiming Rewards**

Stakers can retrieve their accumulated ROSA and CHR token rewards at their convenience through the Rosa Finance interface. It's important to note that the act of claiming rewards has no effect on the staked ROSA tokens. They remain productive, generating further rewards as long as they are staked.

## **Unstaking and Cooling-off Period**

When stakers choose to unstake their ROSA tokens, they can trigger the process via the Rosa interface. Following the initiation, there's a 7-day cooling-off period before the tokens become available. This period is a conscious design decision to deter short-term opportunistic staking and preserve the ecosystem's equilibrium. During this cooling-off period, reward claims are disabled.

Just-in-time staking (i.e. the practice of staking just prior to a reward disbursement and promptly unstaking afterwards) can perturb the staking ecosystem and affect reward calculations. The 7-day cooling-off buffer is established to discourage such behavior, guaranteeing fair and consistent reward distribution for long-term, committed participants.

Once the cooling-off period concludes, the unstaked ROSA tokens are ready for withdrawal.

## **Mechanisms**

### **Shares and Credits**

The rewards distribution relies on the concepts of "shares" and "credits". The quantity of shares a user holds signifies their relative stake in the overall pool, and rewards are allocated proportionally. The introduction of a reward triggers the computation of a new share index, a numerical representation of reward per share, proportional to the total reward and total shares.

A participant's credit, representing the reward amount they can claim, is calculated from their share quantity and the corresponding share index.

### **Reward Computation**

A user's reward is derived from their shares and the share index, which updates each time a reward is added, signifying the reward-per-share value at that moment. The formula for share index calculation is as follows:

```mathematica
Share Index = (Reward Amount * 2**160) / Total Shares + Previous Share Index
```

The user's eligible reward (credit) is calculated using the **`updateCredit`** function, triggered when a user moves to claim the reward or when a user's stake changes (via mint or burn operation). It's determined by the difference between the current and last share index when the user's credit was updated, multiplied by the user's shares.

```mathematica
User's Credit Increase = (Current Share Index - Last Share Index) * User's Share
```

### **Example**

Consider a scenario with a total of 100 shares in the system and an addition of 50 tokens as a reward. The share index will be updated as follows:

```mathematica
Share Index = (50 * 2**160) / 100 = 0.5 * 2**160
```

Assuming a user owns 10 shares, when they initiate the **`updateCredit`** function either to claim the reward or adjust their stake, the user's credit increment is calculated as follows:

```mathematica
Increase in User's Credit = (0.5 * 2**160 - Last Share Index) * 10 / 2**160
```

If the last share index when the user's credit was last updated was zero, then the user's credit becomes 5 tokens, implying that the user is eligible to claim 5 tokens as a reward.
