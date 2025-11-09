# 3-stage-of-ERC-8004-raters
Through this repository, it aims to solve the problem why / how ERC-8004 raters will give true score and value to the Agent

# What is ERC-8004?
ERC-8004 is an Ethereum standard that provides the trust and coordination layer for autonomous AI agents. It extends Google’s A2A (Agent-to-Agent) communication protocol by adding blockchain-based mechanisms for identity, reputation, and validation — allowing AI agents to collaborate across untrusted networks without requiring centralized control or pre-existing trust relationships.

🔑 Core Components

ERC-8004 introduces three lightweight smart-contract registries:

Identity Registry – assigns each agent a unique AgentID and links it to its Agent Domain and Ethereum address, enabling a global namespace for agents.

Reputation Registry – manages feedback authorization between agents, with actual reputation data stored off-chain for flexibility.

Validation Registry – records verification requests and results using cryptographic proofs or economic staking, allowing trust models to scale by value or risk level.

# What is raters in Reputation Registry?
In ERC-8004, raters refer to the client agents who provide feedback and ratings within the Reputation Registry after a task is completed.

Here’s how it works in the protocol:

Server Agent Pre-Authorization – When a server agent accepts a task, it uses the on-chain function AcceptFeedback(AgentClientID, AgentServerID) to authorize a specific client to rate it later. This emits an AuthFeedback event containing a FeedbackAuthID.

Raters (Client Agents) – These client agents act as raters. They create off-chain feedback attestations stored in their Agent Cards under a FeedbackDataURI. Each feedback record includes details such as:

Rating (numerical score, e.g. 95)

TaskId and AgentSkillId (context of the job)

ProofOfPayment and other metadata

Off-Chain Reputation Calculation – ERC-8004 only records the authorization on-chain (for auditability). The actual ratings provided by these raters live off-chain, allowing flexible and sophisticated reputation algorithms and aggregation by third-party services.

In short, raters in the Reputation Registry are the client agents who provide task feedback to server agents. They are the ones who generate the data used to build decentralized, verifiable reputation scores across the agent network.

# If raters lies or give unreal score, the reputation registray can't function normally. So how we can solve this problem? Why and how the raters can give a true and real score? Here is the thinking on this problem. 
