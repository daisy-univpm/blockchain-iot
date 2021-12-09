### A two-tier Blockchain framework to increase protection and autonomy of smart objects in the IoT
Enrico Corradini, Serena Nicolazzo, Antonino Nocera, Domenico Ursino, Luca Virgili <br>
Link: https://bit.ly/3pDAWAU

In this repository, we report the generated datasets and description of our approach to create them.
### Abstract
In recent years, the Internet of Things paradigm has become pervasive in everyday life attracting the interest of the research community. Two of the most important challenges to be addressed concern the protection of smart objects and the need to guarantee them a great autonomy. For this purpose, the definition of trust and reputation mechanisms appears crucial. At the same time, several researchers have started to adopt a common distributed ledger, such as a Blockchain, for building advanced solutions in the IoT. However, due to the high dimensionality of this problem, enabling a trust and reputation mechanism by leveraging a Blockchain-based technology could give rise to several performance issues in the IoT. In this paper, we propose a two-tier Blockchain framework to increase the security and autonomy of smart objects in the IoT by implementing a trust-based protection mechanism. In this framework, smart objects are suitably grouped into communities. To reduce the complexity of the solution, the first-tier Blockchain is local and is used only to record probing transactions performed to evaluate the trust of an object in another one of the same community or of a different community. Periodically, after a time window, these transactions are aggregated and the obtained values are stored in the second-tier Blockchain. Specifically, stored values are the reputation of each object inside its community and the trust of each community in the other ones of the framework. In this paper, we describe in detail our framework, its behavior, the security model associated with it and the tests carried out to evaluate its correctness and performance.

### Setup
We simulated the transactions on HyperLedger Fabric. It is easy to use and can be deployed through Docker containers. We employed an HyperLedger Fabric sample and wrote a smart contract in Javascript to store and read data from HyperLedger. 

Here some resources to install HyperLedger Fabric and create a smart contract:  
- https://hyperledger-fabric.readthedocs.io/en/release-2.0/build_network.html 
- https://medium.com/akeo-tech/step-by-step-guide-to-set-up-hyperledger-fabric-network-b80977c29b8a 
- https://github.com/hyperledger/fabric-samples 

### Simulation
We extracted a portion of the [Ethereum transactions dataset](https://www.kaggle.com/bigquery/ethereum-blockchain) through Google BigQuery. 

We selected a month of transactions and made a mapping between the addresses present there and the devices in an IoT. The number of devices depends on the group size as specified in the paper (for instance, for the group of 10 devices, we selected the most active 10 addresses in the Ethereum transactions dataset, and so on). We iterated over the list of transactions of the involved devices, simulated the transactions, and performed the operations specified by our framework. 

### Files description
**SIM.CSV**

Fields in the sim.csv file:
- Group size (nodes): the number of nodes present in the group
- Ordinary tr.: number of ordinary transactions performed
- Trust tr.: number  of trust transactions performed
- th: the probability of testing a node.
- psize: number of nodes of the trust community (the community nodes mentioned in the framework)
- Ordinary time: time for performing the ordinary  transactions
- Trust time: time for performing the transactions of our framework.
- Tot time: time for performing all the transactions (sum of Ordinary Time and Trust time).
- Tot transactions: total number of performed transactions (sum of Ordinary tr. and Trust tr.).

This csv contains the simulations plotted in Figures 4-5-6-7.

**CONVERGENCE.CSV**

Fields in the convergence.csv file:
- time: time elapsed since the start of the simulation
- 0,1;0,2;0,3;0,4;0,5;0,6;0,7;0,8;0,9: all the probability threshold used during the simulations. The cell value contains the reputation of a malicious node.

### Cite us
@article{Corradini\*21, <br>
  author={E. Corradini and S. Nicolazzo and A. Nocera and D. Ursino and L. Virgili},<br>
  title={{A two-tier Blockchain framework to increase protection and autonomy of smart objects in the IoT}},<br>
  journal={Computer Communications},<br>
  volume={181},<br>
  pages={338--356},<br>
  year={2021},<br>
  publisher={Elsevier}<br>
}
