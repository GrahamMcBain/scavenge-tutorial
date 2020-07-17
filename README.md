# Build a blockchain based Geo Guessing Scavenger Hunt game in 5 minutes

In this simple tutorial you'll create a geographic guessing game. In reality you'll be creating your own blockchain and token using the Cosmos SDK! 

### Prerequisites

- Have [Go installed](https://golang.org/doc/install)



### Lets's Configure our app

- Fork and clone this repository

- Navigate to the ```scavenge-tutorial```  folder in your terminal 

- Run ```make``` inside the folder

- From this directory run the initialization script

``` ./init.sh```


## Fire up your blockchain

- Open a second terminal window and run the following command

```scavengeD start```

You should now see the "blockchain" producing blocks in your terminal. The output will look like this:

``` s
I[2020-07-16|12:53:32.157] starting ABCI with Tendermint                module=main 
I[2020-07-16|12:53:37.397] Executed block                               module=state height=528 validTxs=0 invalidTxs=0
I[2020-07-16|12:53:37.401] Committed state                              module=state height=528 txs=0 appHash=86B6A9AF1278A8F7F130F0AFB29086D99976CD91187D1DD98D1A27AE10ED3862
I[2020-07-16|12:53:42.428] Executed block                               module=state height=529 validTxs=0 invalidTxs=0
I[2020-07-16|12:53:42.431] Committed state                              module=state height=529 txs=0 appHash=ADFC059D4C8FD43924CD043A2D1311F83EB61FBF55A53816E0BDC1D3FCCA015F
I[2020-07-16|12:53:47.461] Executed block                               module=state height=530 validTxs=0 invalidTxs=0
I[2020-07-16|12:53:47.464] Committed state                              module=state height=530 txs=0 appHash=3D1C9185AC13D471E38F62BCA42FDAA78232A858A39E0338944F00E49CEE14AA
I[2020-07-16|12:53:52.504] Executed block                               module=state height=531 validTxs=0 invalidTxs=0
I[2020-07-16|12:53:52.508] Committed state                              module=state height=531 txs=0 appHash=EC4FF9E04776651F6445977D62DD0704D0D98723467F2E7C50642B30DB5866DC
```

## Creating a Geo Scavenger Hunt

Now you can switch into the first terminal window where you should be in the route directory of your application. Let's create a Geo Scavenger Hunt! 

Using the command below you are telling the ```scavengeCLI``` tool that you want to create a transaction on the ```scavengeHunt``` blockchain (the one you have running in another terminal window). You're then calling the ```createScavenge``` function and passing three parameters. Finanlly you're adding a flag to denote which user is creating this transaction:

- ```69foo``` is the amount of "foo" token you want to offer as a bounty for this scavenger hunt
- ```"93001"``` is the correct solution for this Scavenger Hunt
- ```"This zip code contains the Mission San Buenaventura as well as two of Californias Channel islands"``` Is the Description of this Scavenger Hunt
- ```--from me``` is the flag you use to denote which of the already created users is publishing this Scavenger Hunt to the blockchain

## Create the Hunt
Now that you understand what it means, copy and past this command into your terminal window:


```scavengeCLI tx scavengeHunt createScavenge 69foo "93001" "This zip code contains the Mission San Buenaventura as well as two of Californias Channel islands" --from me```

You should receive some confirmation message that looks like this:

                ```
                {
                "height": "0",
                "txhash": "3D088632B1C523EF2754153F5454E8FA464AE69747A4BD8ABC01A3428C31C185",
                "raw_log": "[{\"msg_index\":0,\"success\":true,\"log\":\"\",\"events\":[{\"type\":\"message\",\"attributes\":[{\"key\":\"action\",\"value\":\"CreateScavenge\"}]}]}]",
                "logs": [
                    {
                    "msg_index": 0,
                    "success": true,
                    "log": "",
                    "events": [
                        {
                        "type": "message",
                        "attributes": [
                            {
                            "key": "action",
                            "value": "CreateScavenge"
                            }
                        ]
                        }
                    ]
                    }
                ]
                }
                ```


## Solving the Hunt
Using the command below you are telling the ```scavengeCLI``` tool that you want to create a transaction on the ```scavengeHunt``` blockchain (the one you have running in another terminal window). You're then calling the ```commitSolution``` function and passing the solution parameter, in this case ```"93001"```

Finanlly you're adding a flag to denote which user is creating this transaction, in this case ``` --from you```

## Post your solution 
Now that you understand what it means, copy and past this command into your terminal window:


```scavengeCLI tx scavengeHunt commitSolution "93001" --from you ```

## Confirm "you" are correct
Copy this command to reveal the solution and cofirm "you" are the winner:


```scavengeCLI tx scavengeHunt revealSolution "93001" --from you```

## Reap your sweet reward
You initially posted a reward of 69foo tokens when this Hunt was posted. The user "you" was initiated with a balance of 1foo, confirm they now have a balance of 70foo buy copying and pasting this command into your terminal:



```scavengeCLI q account $(scavengeCLI keys show you -a)```




You should see an output similar to this:
            ``` 
             {
                "type": "cosmos-sdk/Account",
                "value": {
                    "address": "cosmos1m9pxr3nrra2cl07kh8hzdty5x0mejf44997f79",
                    "coins": [
                    {
                        "denom": "foo",
                        "amount": "70"
                    }
                    ],
                    "public_key": {
                    "type": "tendermint/PubKeySecp256k1",
                    "value": "AxHwDfJwPnyoTrt5o8L7iSCiUzIOsCOPovWicfgAyIZp"
                    },
                    "account_number": "1",
                    "sequence": "5"
                }
                }
                ```

## You are the master of your blockchain
You've done it! You spun up your own blockchain with two users and facilitated an interaction between them! This super fun Geo Guessing Scavenger Hunt is just the tip of the ice berg in regards to what you can create with the Cosmos SDK. 

Now that you've seen the high level, dig deeper into a longer version of this tutorial to built the application yourself. You can also reach out to our team and we'd be happy to help you understand what can be done with our powerful extensible tools. 



