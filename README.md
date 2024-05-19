# Decentralized-Voting-System-Using-Ethereum-Blockchain

#### The Decentralized Voting System using Ethereum Blockchain is a secure and transparent solution for conducting elections. Leveraging Ethereum's blockchain technology, this system ensures tamper-proof voting records, enabling users to cast their votes remotely while maintaining anonymity and preventing fraud. Explore this innovative project for trustworthy and decentralized voting processes.

## Features
- Implements JWT for secure voter authentication and authorization.
- Utilizes Ethereum blockchain for tamper-proof and transparent voting records.
- Removes the need for intermediaries, ensuring a trustless voting process.
- Admin panel to manage candidates, set voting dates, and monitor results.
- Intuitive UI for voters to cast votes and view candidate information.

## Requirements
- Node.js (version – 18.14.0)
- Metamask
- Python (version – 3.9)
- FastAPI
- MySQL Database (port – 3306)

## Screenshots

![Login Page](https://github.com/abhi07rana/Decentralized-Voting-System/blob/main/public/login%20ss.png)

![Admin Page](https://github.com/abhi07rana/Decentralized-Voting-System/blob/main/public/admin%20ss.png)

![Voter Page](https://github.com/abhi07rana/Decentralized-Voting-System/blob/main/public/index%20ss.png)

## Installation

1. Open a terminal.

2. Clone the repository by using the command:
    ```bash
    git clone https://github.com/abhi07rana/Decentralized-Voting-System.git
    ```

3. Download and install [Ganache](https://trufflesuite.com/ganache/).

4. Create a workspace named **development**, in the truffle projects section add `truffle-config.js` by clicking `ADD PROJECT` button.

5. Download [Metamask](https://metamask.io/download/) extension for the browser.

6. Now create wallet (if you don't have one), then import accounts from ganache.

7. Add network to the Metamask. (Network name - Localhost 7575, RPC URL - http://localhost:7545, Chain ID - 1337, Currency symbol - ETH)

8. Open MySQL and create database named **voter_db**. (DON'T USE XAMPP)

9. In the database created, create a new table named **voters** in the given format and add some values:
    ```sql
    CREATE TABLE voters (
        voter_id VARCHAR(36) PRIMARY KEY NOT NULL,
        role ENUM('admin', 'user') NOT NULL,
        password VARCHAR(255) NOT NULL
    );
    ```

    Sample values:
    ```sql
    +--------------------------------------+-------+-----------+
    | voter_id                             | role  | password  |
    +--------------------------------------+-------+-----------+
    | <UUID>                               | user  | <password>|
    +--------------------------------------+-------+-----------+
    ```

10. Install truffle globally:
    ```bash
    npm install -g truffle
    ```

11. Go to the root directory of the repo and install node modules:
    ```bash
    npm install
    ```

12. Install python dependencies:
    ```bash
    pip install fastapi mysql-connector-python pydantic python-dotenv uvicorn uvicorn[standard] PyJWT
    ```

## Usage

#### Note: Update the database credentials in the `./Database_API/.env` file.

1. Open terminal at the project directory.

2. Open Ganache and its **development** workspace.

3. Open terminal in project's root directory and run the command:
    ```bash
    truffle console
    ```
   Then compile the smart contracts with command:
    ```bash
    compile
    ```
   Exit the truffle console.

4. Bundle `app.js` with browserify:
    ```bash
    browserify ./src/js/app.js -o ./src/dist/app.bundle.js
    ```

5. Start the node server:
    ```bash
    node index.js
    ```

6. Navigate to `Database_API` folder in another terminal:
    ```bash
    cd Database_API
    ```
    Then start the database server by following command:
    ```bash
    uvicorn main:app --reload --host 127.0.0.1
    ```

7. In a new terminal, migrate the truffle contract to local blockchain:
    ```bash
    truffle migrate
    ```

You're all set! The Voting app should be up and running now at http://localhost:8080/. 

This project has incorporated insights from Farhan Khan's article refer to this (https://www.linkedin.com/pulse/using-ganache-ethereum-emulator-metamask-farhan-khan/) on LinkedIn for the usage of Ganache Ethereum emulator and Metamask. For detailed instructions on utilizing these tools, please refer to the mentioned post. 

## Code 

    ├── blockchain-voting-dapp            # Root directory of the project.
        ├── build                         # Directory containing compiled contract artifacts.
        |   └── contracts                 
        |       ├── Migrations.json       
        |       └── Voting.json           
        ├── contracts                     # Directory containing smart contract source code.
        |   ├── 2_deploy_contracts.js     
        |   ├── Migrations.sol            
        |   └── Voting.sol                
        ├── Database_API                  # API code for database communication.
        |   └── main.py                   
        ├── migrations                    # Ethereum contract deployment scripts.
        |   └── 1_initial_migration.js    
        ├── node_modules                  # Node.js modules and dependencies.
        ├── public                        # Public assets like favicon.
        |   └── favicon.ico               
        ├── src                           
        |   ├── assets                    # Project images.
        |   |   └── eth5.jpg              
        |   ├── css                       # CSS stylesheets.
        |   |   ├── admin.css             
        |   |   ├── index.css             
        |   |   └── login.css             
        |   ├── dist                      # Compiled JavaScript bundles.
        |   |   ├── app.bundle.js         
        |   |   └── login.bundle.js       
        |   ├── html                      # HTML templates.
        |   |   ├── admin.html            
        |   |   ├── index.html            
        |   |   └── login.html            
        |   └── js                        # JavaScript logic files.
        |       ├── app.js                
        |       └── login.js              
        ├── index.js                      # Main entry point for Node.js application.
        ├── package.json                  # Node.js package configuration.
        ├── package-lock.json             # Lockfile for package dependencies.
        ├── README.md                     # Project documentation.
        └── truffle-config.js                    # Truffle configuration file.
## License

This project has been adapted from Krish-Depani's Decentralized Voting System repository, with credit for helping to build this code.

