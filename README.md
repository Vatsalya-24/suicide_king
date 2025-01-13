
## Quickstart Instructions ##
Prerequisites/Versions I've used:

* Ubuntu 18.04, Windows 10
* VSCode 1.44.2 (w/ extensions: solidity 0.0.72, Solidity Contract Flattener 0.0.7, Solidity Visual Auditor 0.0.24)
* Node v11.15.0
* npm 6.7.0  
* truffle v5.1.24 (`npm install -g truffle`)
* ganache-cli v6.8.2 (`npm install -g ganache-cli`)

To get the project running:

1. Download git repo locally and optionally _Open folder_ in Visual Studio

2. Terminal #1 - Install project dependencies

`npm install`

3. Terminal #1 - Run ganache-cli and copy-down the mnemonic it generates

`ganache-cli`

4. Terminal #2 - Start truffle,  compile/migrate the project to the blockchain

`truffle console --network develop`

_truffle(develop)>_`migrate --reset`

5. Terminal #3 - Install dependencies and run the react front-end at http://localhost:3000

`cd app`

`npm install`

`npm run start`

## Running on Local Blockchain Forked from Mainnet ##

1. Start Ganache-cli (terminal 1):

`ganache-cli -f https://mainnet.infura.io/v3/3b0206f022a6462cacf91dc79e2b9833 -m "toss seven aerobic pledge lumber yard evil benefit title duty winter initial" -i 999`

2. Connect on Truffle and deploy (terminal 2):

`truffle console --network mainnetfork`

`migrate`

3. Start web app (terminal 3):

`cd app`

`npm run start`

4. Configure Metamask:

Seed with the same mnemonic as you used in ganache-cli, and change network to use localhost:8545 and Network ID 999.

*Note*: Whenever you restart ganache-cli, you may find the proxy connection to the forked mainnet blocks is flakey and may need to restart ganache-cli/truffle over again to chill-out browser console issues. I also suspect reseting Metamask (Settings > Advanced) may go a long way in helping to fix these errors, too.

## Running on Testnets/Infura ##
Create a `secrets.json` file in the project root (same level as truffle-config.js).  It should contain a mnemonic (you can generate via ganache/ganache-cli) and infura API Key (sign-up for free at infura.io)

```
{
  "mnemonic": "toss seven aerobic pledge lumber yard evil benefit title duty winter initial",
  "infuraApiKey": "3b0206f022a6462cacf91dc79e2b9833"
}
```
Then, be sure to start truffle using:

`truffle console --network kovan`

Also support for `ropsten`, but it has been very slow lately.  Like, Bitcoin slow.

And, in your browser be sure to switch Metamask to Ropsten and seed it with the correct mnemonic (Logout and Restore).

