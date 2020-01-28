Welcome to Archipel.

You can check you archipel status and retrieve peer_id by switching to logs tab. 

Peer_id will be needed to add the --bootnodes option into the CHAIN_ADDITIONAL_PARAMS env parameter of your archipel chain.

You need to configure an accurate bootnodes list and share it manually between 3 DAppNodes operators of your archipel.
Exemple of an acurate bootnodes list option :

`--bootnodes /ip4/$NODE1_IP/tcp/30333/p2p/$NODE1_PEER_ID --bootnodes /ip4/$NODE2_IP/tcp/30333/p2p/$NODE2_PEER_ID --bootnodes /ip4/$NODE3_IP/tcp/30333/p2p/$NODE3_PEER_ID`

Share and valorize those 2 env variables of public key identities between the 3 DAppNodes operators: 
ARCHIPEL_AUTHORITIES_SR25519_LIST=`<SR25519 Public Key Node 1>,<SR25519 Public Key Node 2>,<SR25519 Public Key Node 3>`
ARCHIPEL_AUTHORITIES_ED25519_LIST=`<ED25519 Public Key Node 1>,<ED25519 Public Key Node 2>,<ED25519 Public Key Node 3>`

When all parameters above are shared and exchange between your 3 nodes operators. 
Update env variables into the DAppNode interface et restart service. Then, you must see 2 peers connected to your Archipel chain in logs.
You should also see 2 DAppNodes in passive mode for the external service (polkadot synch only) and one DAppNodes in active mode for the external service (polkadot in validator mode). 
