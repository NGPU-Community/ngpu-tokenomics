# NGPU Tokenomics
## Incentive Overall Distribution
+ Computing Power Providers, Ecosystem: 51.0%
+ Investment Institutions: 20.0%

**<span style="color:red;">Foundation, Team, Advisors: 21.0%</span>**

+ Foundation: 7.0%
+ Team, Advisors: 14.0%
## Role Definitions
**Basic Roles**

+ **Computing Power Provider:** Owns GPU computing power and logs into our NGPU platform by installing the client.
+ **Computing Power Demander:** Needs GPU computing power to support their apps or applications.
+ **AI User:** Uses the DAPP provided by the Computing Power Demander and utilizes NGPU computing power after initiating AI tasks.

**Derived Roles**
+ **Staker:** Stakes a certain amount of (USDT, BTC, ETH, etc.) to a specified GPU computing power node, becoming a beneficiary of task incentives for that computing power node.

**<span style="color:red;">Stakers and computing power nodes are integrated. After receiving incentives, the distribution between stakers and computing power nodes is decided by themselves (later, NGPU can provide a staking distribution smart contract to distribute incentives according to the allocation ratio specified in the smart contract).</span>**

## Incentive Definitions
### Network Incentive
To encourage Miners to install the NGPU client and log into the NGPU platform to form a flexible computing power network, NGPU provides network incentives for the cost of forming this network.

+ **Distribution Interval**
```json
Network incentives are distributed every 5 minutes.
```
+ **Computing Power Nodes Eligible for Network Incentives**
```json
To avoid a large number of low-effort computing power nodes, only those that actually distribute work tasks and a certain number of idle nodes will receive network incentives. The number of idle nodes is proportionate to the number of tasks distributed and is randomly selected daily.
Network Incentive Nodes = Nodes that distributed work tasks + Redundant Idle Nodes
```
+ **Single Computing Power Node Distribution Algorithm**
```son
Single Node Network Incentive = Node Computing Power / Σ (Computing Power of all nodes)
```
### Task Incentive
NGPU provides task incentives to computing power nodes that complete AI tasks. The design principle is "the more work, the more rewards."

+ **Distribution Interval**
```json
Task incentives are calculated every hour based on completed AI tasks.
```
+ **Standard Computing Power Node Definition**
```json
GPU Type: Nvidia RTX 4090
Storage: 500GB
Bandwidth: 200Mbps
```
The computing power value calculated by a standard computing power node is called <span style="color:green;">Standard Computing Power Value</span>.

+ **Calculation Formula**
```json
Single Node Task Incentive = Σ ((GPU time consumed by each AI task (seconds) * Computing Power Node Value / Standard Computing Power Value) * Task Incentive Value per Second for Standard Computing Power)
```
+ Task incentives are derived from fees paid by the Computing Power Demander (USDT, BTC, ETH, etc.), converted to platform incentives with NGPU taking a fee.
+ Handling of Redundant Nodes: Part of the task incentive will be distributed to the redundant nodes in the work space when a task incentive is obtained.
## Roles and Incentive Relationships
**Computing Power Provider**

+ **Network Incentive:**  The computing power provider logs into NGPU to form a computing power network. After measurement, the computing power node can periodically receive network incentives.
+ **Task Incentive:** The computing power node can receive task incentives after successfully completing AI tasks.

**Computing Power Demander**

The computing power demander (DAPP party) exists as the payer on the NGPU platform. They can pay (USDT, BTC, ETH, etc.) to NGPU, which converts it to platform incentives and pays the computing power nodes (task incentive) after taking a fee. NGPU will periodically or occasionally buy back and burn incentives from the market to stabilize prices.

**Payment Fees**

+ The computing power demander can pay (USDT, BTC, ETH, etc.), with NGPU taking a fee.

**User (For Statistics Only, No Incentives)**

+ NGPU provides detailed lists of the number and time consumption of AI tasks executed by users. The DAPP party can incentivize users based on these lists, but NGPU does not incentivize users.
## Staking Definition
+ **Computing power nodes must stake to receive incentives (network incentive, task incentive).**
+ **Each computing power node must stake a certain amount of USDT to receive incentives (network incentive, task incentive).**
```json
Single Node Staking Amount = Total Incentive Value (USDT) * Staking Ratio / Number of Computing Power Nodes on NGPU Platform

For example:
1. Total Incentive Amount: 1 billion (USDT)
2. Staking Ratio: 73%
3. Number of NGPU Computing Power Nodes: 20,000

Single Node Staking Amount = 1 billion * 73% / 20,000 = 3650 (USDT)
```
<span style="color:red;">**_The incentive for computing power providers is gradually released, so the staking ratio will vary at different times._**</span>

+ **Stakers can freely choose their staked computing power nodes.**
+ **The staking amount is a factor in the node SLA. A computing power node without staking is at the lowest level.**
+ **Staking Lock Period: <span style="color:red;">7 days (the staking amount per computing power node cannot be greater than or equal to the single node staking amount).</span>**
+ **When a computing power node goes offline, <span style="color:red;">the system will deduct an amount equivalent to 1 hour of task incentive from the staking, and no incentive will be given for that hour.</span>**