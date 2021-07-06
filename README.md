# Blockchain-Test-Network
Homework18

# Instructions

Download GETH and Tools version 1.9.7 to create the test network on the Ethereum network.

Open your terminal, and navigate into the directory where the GETH tools are stored.

Create account for node3 datadir using geth command: ./geth --datadir node3 account new 

Write down the password, public key, and secret key
Node 3 password: 1234
Public address of the key:   0xb019324C1C18576e3059Aa6466a4a17c6eD5D56F
Path of the secret key file: node3\keystore\UTC--2021-07-06T12-41-48.017040800Z--b019324c1c18576e3059aa6466a4a17c6ed5d56f

Create account for node4 datadir using geth command: ./geth --datadir node4 account new 
Write down the password, public key, and secret key
Node 4 password: 1234
Public address of the key:   0x58c447dA34b48Fb1EFC9b9EACC4e8fc58Ae66690
Path of the secret key file: node4\keystore\UTC--2021-07-06T12-42-35.532378300Z--58c447da34b48fb1efc9b9eacc4e8fc58ae66690

Run the puppeth command, to begin setting up your test network: ./puppeth 

Name your network "hw18bank" and click enter.

Select option 2: Configure new genesis and hit enter.

Selection option 1: Create new genesis from scratch, hit enter.

Selection option 2: Clique, proof of authority, hit enter.

Paste both account addresses from the first step one at a time into the list of accounts to seal.

Paste them again in the list of accounts to pre-fund.

"No" to prefund with 1 wei, then specify your network ID and hit enter.

Specify Chain ID as "2222"

At main menu, select "manage existing genesis" option, and then select "export genesis configurations".

Now, initialize each node with Geth using the following commands:

./geth --datadir node3 init hw18bank.json

./geth --datadir node4 init hw18bank.json

Run the first node, unlock the account, enable mining, and the RPC flag using the following command:

./geth --datadir node3 --unlock "0xb019324C1C18576e3059Aa6466a4a17c6eD5D56F" --mine --rpc --allow-insecure-unlock
enode://92a9ad2394ba3b092e76aeb61f209d27ff3eab44a272d9f178d9252d37eefc14a00597f5404cc783a8d7df14ed0dcd15b1a91bfcb26533a580501c7545585ea5@127.0.0.1:30303

Set a different peer port for the second node, unlock, enable mining and use the first node's enode address as the bootnode flag:

./geth --datadir node4 --unlock "0x58c447dA34b48Fb1EFC9b9EACC4e8fc58Ae66690" --mine --port 30304 --bootnodes "enode://92a9ad2394ba3b092e76aeb61f209d27ff3eab44a272d9f178d9252d37eefc14a00597f5404cc783a8d7df14ed0dcd15b1a91bfcb26533a580501c7545585ea5@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

Both nodes are now up and running and mining.

Now we will sse the MyCrypto GUI wallet to connect to the node with the exposed RPC port. 

First, we will create a custom node and connect to the network.

Open the MyCrypto app, then click Change Network at the bottom left.
Click "Add Custom Node", then add the custom network information that you set in the genesis.
Type ETH in the Currency box.
In the Chain ID box, type 2222.
In the URL box type: http://127.0.0.1:8545.  This points to the default RPC port on your local machine.
Finally, click Save & Use Custom Node.

Select the View & Send option from the left menu pane, then click Keystore file.
On the next screen, click Select Wallet File, then navigate to the keystore directory inside your Node3 directory, select the file located there, provide password "1234" when prompted and then click Unlock.
In the To Address box, type the account address from Node4, then fill in amount of 5000 ETH.
Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.
Click the Check TX Status when the green message pops up, confirm the logout
