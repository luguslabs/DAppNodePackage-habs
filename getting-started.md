Welcome to Archipel.

You can check you archipel status and retrieve peer_id by switching to logs. 

Peer_id will be needed to add the --bootnodes option into the CHAIN_ADDITIONAL_PARAMS env parameter of your archipel chain.

You need to configure an accurate bootnodes list and share it manually between the 3 DAppNodes operators of your archipel.
Exemple a acurate bootnode list option :

`--bootnodes /ip4/$NODE1_IP/tcp/30333/p2p/$NODE1_PEER_ID --bootnodes /ip4/$NODE2_IP/tcp/30333/p2p/$NODE2_PEER_ID --bootnodes /ip4/$NODE3_IP/tcp/30333/p2p/$NODE3_PEER_ID`

Share of public key identities of the 3 archipel node must be also done. offchain IRL. to valorize those 2 env variables : 
ARCHIPEL_AUTHORITIES_SR25519_LIST=`<SR25519 Public Key Node 1>,<SR25519 Public Key Node 2>,<SR25519 Public Key Node 3>`
ARCHIPEL_AUTHORITIES_ED25519_LIST=`<ED25519 Public Key Node 1>,<ED25519 Public Key Node 2>,<ED25519 Public Key Node 3>`

When all parameters above are shared and exchange between 3 nodes operator. 
Update env variable into the DAppNode interface et restart service. you must see 2 peers connected to your Archipel chain in logs.
You should also see 2 nodes of your external service in passive mode and 1 node of tyour external service in active mode.
