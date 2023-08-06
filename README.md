This project is prepared by Vue Forge Online Conference; 
Thank you for presenting such a beautiful project for 2 days online and free of charge.

# How to Get Started

## DevNet Setup
### Ecko Wallet Browser Extension

1. [Download Ecko Wallet Browser Extension](https://chrome.google.com/webstore/detail/eckowallet/bofddndhbegljegmpmnlbhcejofmjgbn) (currently only available for [Google Chrome](https://www.google.com/chrome/dr/download/?brand=AYYF&geo=US&gclid=Cj0KCQjwiIOmBhDjARIsAP6YhSVdAKMAxSIH-7oI3AnI9Gv7UdQtRnm8WVfsSRNPDubT0xPPJfAjFuwaAtfkEALw_wcB&gclsrc=aw.ds))
2. Run through all the steps for the extensions setup wizard (choose “Create New Wallet” if you’ve never used Ecko Wallet before)
3. At the conclusion of the wizard setup, you can close the tab and use the extension pop-up moving forward.

### Setup the Local Devnet and Connect Wallet

1. Run the following command in the project folder to start the dev network. (You can stop the network with `ctrl + c` but make sure you have it running while we’re developing)

```sh
yarn kadena:devnet
# or
npm run kadena:devnet
```
The devnet runs on port 8080, so ensure it’s free

2. Open the Ecko Wallet Chrome extension to connect it to the dev network started by the previous command. 
3. Choose the “Settings” button from the bottom menu
4. Next, choose “Networks”
5. Click the “Add a New Network” button.
6. Fill in the network details as follows:
    1. Network Name: DevNet
    2. New RPC URL: [http://127.0.0.1:8080](http://127.0.0.1:8080/)
    3. Block Explorer URL: [http://127.0.0.1:8080](http://127.0.0.1:8080/)
    4. Network Id: fast-development
7. Click the “Save” button
8. Next, close the extension and open it again to get to the wallet view. Then select the “DevNet” network from the dropdown in the top left corner.
9. Create a wallet by selecting the vertical three-dots menu in the top right-hand corner, and choosing “Create Wallet”.
10. Congrats, Ecko Wallet is setup to work with the devnet! 🎉

## Fund Account
Next, we need to fund our account on the devnet so we have some digital money (KDA) to work with while we’re developing
1. Copy your public key from the Ecko Wallet Extension by clicking on it in the top right corner of the extension pop-up
2. Go back to the terminal in the project folder
3. In a new terminal tab, run the following command to fund your account

4. After the required dependencies download, you will be presented with the 2 following prompts:
    1. What account would you like to fund? The answer here is your public key copied in the last step (note it should start with `k:`)
    2. What public key would you like to use? This is the public key WITHOUT the `k:`.
  
```bash
yarn kadena:cli --profile=./.fund-profile.json
# or
npm run kadena:cli -- --profile=./.fund-profile.json
```

5. If the above command fails, go back to your terminal tab where the devnet is running, stop the process with ctrl + `, and restart it with npm run kadena:devnet.

6. Awesome! 💪 Your account is now funded with 100 KDA on the devnet. You can view your account balance in the wallet. You should see the KDA balance as well as the USD equivalent.

## Local Setup

1. Ensure you have [docker installed](https://docs.docker.com/get-docker/) and running
2. Clone the repo or [![Run with VS Code](https://badgen.net/badge/Run%20with%20/VS%20Code/5B3ADF?icon=https://runme.dev/img/logo.svg)](https://runme.dev/api/runme?repository=https%3A%2F%2Fgithub.com%2Fvueschool%2Fforge-4-poc.git&fileToOpen=README.md)

```sh
git clone repo
```

3. Start on the boilerplate branch

```
git checkout boilerplate
```

4. Install the dependencies

```sh
yarn
# or
npm install
```

5. Start the Supabase service

```sh
yarn supabase:start
# or
npm run supabase:start
```

6. The needed supabase environment variables will print after the service has started. Duplicate .env.example to .env and provide the following variables from the terminal print out.

```sh
# this can stay the same
SUPABASE_URL="http://localhost:3000"
# anon key the terminal print out
SUPABASE_KEY="<your anon key>"
# service role key from the terminal print out
SUPABASE_SERVICE_KEY="<your service_role key>"
```

You can also retrieve these at any time by running the following:

```sh
npx supabase status
```

7. Migrate and seed your database with initial schema and values by running:

```sh
yarn db:reset
# or
npm run db:reset
```

8. Start the dev server

```sh
yarn dev
# or
npm run dev
```