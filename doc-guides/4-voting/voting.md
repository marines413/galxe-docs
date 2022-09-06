---
sidebar_label: Custom Voting with Galxe NFT
sidebar_position: 1
slug: custom-voting-with-galaxy-nft
---
# Custom Voting with Galxe NFT

We utilize [Snapshot](https://snapshot.org/#/) for NFT voting, check the doc [Home - snapshot](https://docs.snapshot.org/) if you are unfamiliar with snapshot voting.

To use NFTs claimed from Galxe to vote, you can plug “galaxy-nft-with-score” strategy into your proposal to do so. For testing the strategy, please use the playground: <https://snapshot.org/#/playground/galaxy-nft-with-score>

1. Choose chain: we only support Polygon for now.
2. Input Snapshot: it’s same as block number, NFT ownership is count for that block number, so the voting power won’t be changed if NFT is transferred after block number.
3. Select the strategy from your Snapshot Space admin

   ![snapshot-vote.png](assets/snapshot-vote.png)
4. Setup strategy parameters:

   ```json
   {
     "symbol": "SUPA", // Voting power unit shows in proposal
     "params": {
       "NFTCoreAddress": [
         "0x86835C3B8fA69f8F31C72477C7776A3B61dbAC92" // NFT contract address
       ],
       "blacklistNFTID": [
         "4" // NFT token IDs that won't have any voting power of the NFT contract
       ],
       "configs": [
         {
           "name": "Basic", // NFT name of Galxe
           "cumulative": false, // If user have multiple same NFT, does the voting power cumulate.
           "votingPower": 1 // Voting power that this NFT has
         },
         {
           "name": "SuperUMAn",
           "cumulative": false,
           "votingPower": 10
         },
         {
           "name": "UMAster",
           "cumulative": false,
           "votingPower": 20
         },
         {
           "name": "Alumni",
           "cumulative": false,
           "votingPower": 1
         }
       ]
     }
   }

   // In this example
   // If user A has 2 Basic NFT and user B has 1 UMAster and 1 Alumni NFT
   // User A voting power will be 2, User B voting power will be 21
   ```
5. Addresses: Input some addresses to test how much voting power the address have. You are good to go!