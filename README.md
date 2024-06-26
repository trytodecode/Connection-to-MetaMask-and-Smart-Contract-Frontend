# Smart Contract Management 

we are creating contract and connecting with metamask wallet 

## Description

In this we create metamask and contract and deploy it using front end . we can perform contract function in our frontend . metamask wallet will be connected to ganache and then we know how to deploy solidity code in front end .

## Getting Started

### Installing

* first of all create metamask wallet
* create ganache enviroment 
* connect ganache to metamask
* create index.html ans server.js and deploy the code 
* open  remix ide and create basic solidity code to deploy 
* then deploy the code in web 3 to execute the solidity function

### Executing program

* first of all clone the repository in your local pc 
* remeber to install ganache in your machine 
* make sure you meta mask wallet is connected 
* go to index.html 
* run the  file to the browser
* If you prefer to use a different version or host the library locally, update the script tag accordingly.

* Click the "CONNECT TO METAMASK" button. This will prompt you to connect your MetaMask wallet to the browser.

After connecting to MetaMask, your Ethereum account address will be displayed.

* Click the "CONNECT TO CONTRACT" button. This will connect to the specific smart contract using the provided contract address and ABI.

Once connected to the smart contract, the message "connected to smart contract" will be displayed.

* You can now use the "GET MESSAGE FROM THE CONTRACT" button to retrieve the message stored in the smart contract. The message will be displayed below the button.

 *Similarly, you can use the "GET NUMBER FROM THE CONTRACT" button to retrieve the number stored in the smart contract. The number will be displayed below the button.
```
code blocks for commands
<!DOCTYPE html>
<html>
<head>
    <title>SMART CONTRACT TEST</title>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/web3/1.2.7-rc.0/web3.min.js"></script>
    <style>
        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
            color: #333;
            text-align: center;
            padding: 50px;
        }
        h1 {
            color: #333;
        }
        .container {
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
            padding: 20px 40px;
            margin: 20px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 15px 32px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 20px;
            margin: 10px;
            cursor: pointer;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #45a049;
        }
        input {
            width: calc(100% - 22px);
            padding: 10px;
            margin: 10px 0;
            box-sizing: border-box;
            font-size: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        p {
            font-size: 18px;
        }
    </style>
</head>
<body>

    <h1>Smart Contract Interaction</h1>

    <div class="container">
        <button onclick="connectMetamask()">CONNECT TO METAMASK</button>
        <p id="accountArea">Connection Status: NOT CONNECTED to Metamask </p>
    </div>

    <div class="container">
        <button onclick="connectContract()">CONNECT TO CONTRACT</button>
        <p id="contractArea">Connection Status: NOT CONNECTED to Smart Contract</p>
    </div>

    <div class="container">
        <button onclick="readWord()">GET DATA FROM CONTRACT</button>
        <p id="dataArea">Data Status: NO Data from Smart Contract </p>
    </div>

    <div class="container">
        <button onclick="changeWord()">CHANGE DATA ON THE SMART CONTRACT</button>
        <input type="text" id="inputArea" placeholder="Enter new data...">
    </div>

    <script>
        let account;
        const connectMetamask = async () => {
            if(window.ethereum !== "undefined"){
                const accounts = await ethereum.request({method: "eth_requestAccounts"});
                account = accounts[0];
                document.getElementById("accountArea").innerHTML = `Account is: ${account}`;
            }
        }

        const connectContract = async () => {
            const ABI = [
                {
                    "inputs": [
                        {
                            "internalType": "string",
                            "name": "_word",
                            "type": "string"
                        }
                    ],
                    "name": "changeFlower",
                    "outputs": [],
                    "stateMutability": "nonpayable",
                    "type": "function"
                },
                {
                    "inputs": [],
                    "name": "getFlower",
                    "outputs": [
                        {
                            "internalType": "string",
                            "name": "",
                            "type": "string"
                        }
                    ],
                    "stateMutability": "view",
                    "type": "function"
                }
            ];
            const Address = "0xF35E9a2c390811E71Eef5E2391af46bd4e3D4FAA";
            window.web3 = await new Web3(window.ethereum);
            window.contract = await new window.web3.eth.Contract(ABI, Address);
            document.getElementById("contractArea").innerHTML = "Connection Status: Success";
        }

        const readWord = async () => {
            const data = await window.contract.methods.getFlower().call();
            document.getElementById("dataArea").innerHTML = `Word is: ${data}`;
        }

        const changeWord = async () => {
            const myEntry = document.getElementById("inputArea").value;
            await window.contract.methods.changeFlower(myEntry).send({ from: account });
        }
    </script>
</body>
</html>


## Help

* remeber you metamask wallet is created 
* browser shield should be off
* remember to ensure compiler version
* custom-external enviroment should be choosen in remix 

## Authors



kumar sanjeev  
https://www.linkedin.com/in/kumar-sanjeev-150965230/


## License

This project is licensed under the [NAME HERE] License - see the LICENSE.md file for details
