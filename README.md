# Steam P2P Trading
Documentation for player to player trading on Steam. Tasks list.

## Technology
Most likely NodeJS for backend logic, and a relational database (this is still open for debate).

## Timeframe
One month.

## Idea
 System that would be able to confirm successful trade between two users. 
## Prerequisites
  - SteamIDs of users involved in a trade
  - Items that are being traded, and their information (classID, assetID, float, etc...)
  - Exact time when the trade has been initiated.

## Algorithm
   (1) Insert trade information in database when user initiates it.
   (2) Poll both users inventory, in order to check if trade has been completed.
   (3) When the offer has been confirmed as accepted, update database

### (1) Insert trade information in database when user initiates it.
 - Firstly, fetch user's inventory and display it to him. He selects items he's willing to trade.
 - Take items info from his inventory, and log it in database
### (2) Poll both users inventory, in order to check if trade has been completed.
  - Do polling every X seconds of both user inventories.
  - Check if all itemIDs are on player that should receive it. If true, trade has been accepted.
  - If not, compare if any of itemIDs matches. If any of them matches, that most likely means trade has been accepted (but still can't be guaranteed!). Now compare item names, stickers attached, floats. All of this info guarantees succesful trade.
  - Do polling for few minutes, after that period, if offer isn't accepted cancel it.
### (3) When the offer has been confirmed as accepted, update database
  - Stop polling and update database. Offer has been accepted.
  

## Security checks
  - Offer time needs  a limit of like 10 minutes, as we can't keep polling for decades
  - Make sure users are not able to exploit anything by manipulating some of the item's information
  - Add proxies. There's going to be tons of Steam inventory HTTP requests so proxies are a MUST.

  




