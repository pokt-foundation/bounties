### Pocket Network DAO Global Bounty - Build an Off-chain Discord Voting Bot

### Prize Bounty
500 DAI + 3000 POKT

### Estimated Time Commitment
1 day

### Challenge Description

We already have token-gated Discord role management using tools like Collab.Land and Agora.Space and emoji reaction voting using tools like the [Aragon Witnet integration](https://blog.aragon.org/aragon-partners-with-witnet-for-gasless-dao-management-on-discord/). However, we can't use these token-gated roles for emoji voting unless voting takes place in a private channel, which is less transparent for non-voting members of the community. Discord can gate the permission to add a new emoji to a message but not to +1 an existing emoji, so even non-role-holders can add their reaction and thus render the count useless, unless we can somehow count the role-holders that reacted...

Starboard is a popular Discord bot that is used to surface highlights in servers, by measuring the number of reactions of a specified emoji and, when a specified emoji count is reached, embedding links to the message in another read-only channel. In theory, we could fork this bot and add more complex rules about when the threshold is satisfied, such as:
* **Voting**: Count only the reactions from specified roles, e.g. @Voter. Bonus points if we can auto-delete the reactions of non-role-holders, so that members can accurately track the progress of the vote count.
* **Majority Voting**: Rather than a fixed number of reactions, make the number a % of members who have the role.
* **Conviction Voting**: Increase the weight of the member's vote over time.
* **Quadratic Voting**: Give each member a limited number of reactions, track how many reactions members have given to active proposals, then weight accordingly.

*Note: This all relies on being able to see the roles of members who reacted and we're not 100% sure that Discord's API exposes this data. This should be confirmed before diving deeper down the rabbit hole. See the DiscordJS ReactionManager docs linked below.*

The bot could allow us to configure the following options using commands/reactions in Discord (already included in Starboard codebase):
* Voting channel
* Role(s) whose votes will be counted
* Type of voting we want to use - e.g. fixed number (Starboard default), majority voting (% of role), conviction voting, quadratic voting, etc
* Voting-type parameters - e.g. for majority voting, X% approval, % quorum (if no quorum specified, make % approval a % of role-holders who reacted, not all role-holders)
* Vote weightings - including simple multipliers on roles, on-chain data (could integrate with Snapshot to make use of strategies), quadratic voting, conviction voting, etc.
* Voting deadline, i.e. time after which success/failure of the specified threshold condition is locked in
	* *Bonus: tie the deadline to the native Discord Threads feature, if the associated Thread on the proposal expires due to inactivity, the vote count locks in.*

The bot could also have features such as:
* Auto-adding the specified voting reactions to every message that is posted to the voting channel, so that voters just need to click once.
* Above embedded messages in the successful proposals channel, insert data about the vote, e.g. of the roles whose votes are counted, how many voted, what was their % approval/rejection, etc.
* Save vote data (including member usernames/IDs) to IPFS or Arweave once success conditions are met, so it can be used as proof to resolve on-chain with optimistic governance tools like Gnosis SafeSnap or the Aragon Witnet integration [here](https://blog.aragon.org/aragon-partners-with-witnet-for-gasless-dao-management-on-discord/)

### Submission Requirements
A working MVP that can restrict the vote count to specified roles and do majority voting (% of role-holders), per the description above, then cross-post successful proposals to a specified channel.

### Judging Criteria
If there are multiple submissions, we'll award the bounty to the submission that includes most of the functionality outlined above, with more weight given to functionality that enables more variety of voting use cases and/or is harder to implement.

### Deadline for Submissions
12th Nov

### Winner Announcement Date
15th Nov

### Resources
* [Open-source Starboard bot](https://github.com/CircuitsBots/Starboard)
* [Discord.JS ReactionManager docs](https://discord.js.org/#/docs/main/stable/class/ReactionManager)
* [Our Discord](https://discord.gg/pokt)
