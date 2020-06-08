# ethereumissue
Scripts for replicating Ethereum Issue:

Steps:

Client.py sends transaction which invokes the createTest() method in smart contract multiple times.

Network Setting:

I tested in Private Network Proof of Authority Clique but I guess this should be the case irrespective of consensus

1) Client invokes createTest() method in main.sol contract, which consumes ~40900 gas.

2) So Setting Block Gas Limit to accomodate more txs 40900 * 12000 (txs) = 490800000  specified in Genesis.json

3) Also gas target & gas limit in miner witch when starting geth binary is set to 490800000 to have a uniform gas limit

4) Other settings is normal, I had block period 2

5)My RPC mode of sending transaction to geth client is via websocket, so please enable it in geth options

Client Setting:

1) Deploy the contract main.sol in the directory

2) Change the contract address in the client file

3) Change the no of threads in the client which I set to 10000. Its quite high which i got by changing ulimit parameter in my linux machine. To replicate the scenario its better to set as 10000

4) No of transactions to be sent by the client is mentioned in the client which can be changed (Default 200000)

5) Since client is a python script some dependencies need to be installed like below.

apt-get install -y python3-pip python3-dev

python3 -m venv poa
source poa/bin/activate
pip install wheel
pip install web3
pip install pandas
pip install websocket_client
pip install typing-extensions

Then execute python3 client.py to start the client execution
