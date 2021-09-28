# blockchain-developer-bootcamp-final-project

Creation of a marketplace where it will be possible to buy, sell, reserve for a future purchase, one NFT of one collection. This by estimating its market price for the present, past or future time in relation to the other NFTs in its collection.

The price of an NFT in a collection and in relation to other collections of NFTs is a problem that is not often addressed. A site like rarity.tools, for example, offers scoring tools and other measures to estimate the value of an NFT, nevertheless, the relation to the price remains, to my knowledge, unexplored. This being said, giving an ideal price to an NFT is a complex data analysis task and a project in itself. I will simplify it to give an idea of what it could be. 

Displaying the 10000 collectibles on a screen to select one, in a comprehensive manner, is a difficult task too. Here also, some simplifications and tradeoffs will be made. 

This project will be restricted to one NFT collection that has one already existed market: an OpenSea collection, The Bored Apes, The Cool Cats, or else, nevertherless it seems not easy to interact with their smart contracts and to have their logs, maybe the Cryptopunks and the Cryptopunks smart contract market.

The choice, for that project, is to be concentrated on the smart contract, its logic, and what is around it, even if, the analysis and its visualization have to be more simplified than their description below. If it seems, that this kind of project has economic potential, more profound research could be done. 

DESCRIPTION

Price estimation 

  The estimation of the market price for a time period, a relevant period for the used market, will be done by using:

    the price of the NFTs sold between this time period
    the rarity score of each NTF of the collection (see COMPLEMENTS, Rarity score, a blog post about the formula)
    The application of an algorithm that will cluster NFTs of similar scores around certain prices, and then by extension, cluster groups of NFTs between prices.
    The clusters thus obtained can be considered as groups of NFTs around and between prices defined by the market.

Without a doubt, there will be outliers on the price curve, some NFTs with a higher score will be cheaper than some with a lower score. In this case, the user will judge for himself...

The determination of the future price will be done by simple calculation of trajectory applied on the clusters, past prices' history will be take into account. 

Choice of 1 NFT
  
    The clustering visualisation will be display on screen, the user will have the ability to restrict it by selecting a price range. 
    The price, the numero and the score of one NFTs will be displayed when the mouse will be on that NFT. 
    Distinctive signs will be apply on the NFTs free to purchase, the ones sell between the selected period and the others.
    The future prices will be display as figures for specific clusters. 

 Trade
 
  Buy:
  
    User Inputs -> numero, price
    Check availability
    
  Sale (set up for a):
  
    User Inputs -> numero, price
    Check possession
    can be canceled
    
  Purchase one NFT by blind reservation:
  
    User input -> minimum score, maximum price
    Reservation by escrow
    can be canceled
    purchase when inputs are checked
    take some fees

COMPLEMENTS

Rariti.tools: https://rarity.tools/

Rarity score: https://raritytools.medium.com/ranking-rarity-understanding-rarity-calculation-methods-86ceaeb9b98c

OpenSea: https://abidocs.dev/dapps/opensea, https://docs.opensea.io/reference/api-overview

Cryptopunks smart contract: 0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB

The knn algorithm with an already written script, with a few modifications, will be used for the data analysis
 

 Data collection for Price estimation and data visualisation
  
    Historic prices data, numero and score will be store on the node.js server
    For each new NFT on sale and each new sale: 
      Collect price, numero and necessary data for a purchase on the Ethereum logs, or by the OpensSea Standard API

 Data collection for smart contract purchase blind reservation`

    The metadata collection will be store on IPFS
    Compute the score of each NFT, and store it on IPFS (one shot, but how to compute in a secure way?)
    For each new NFT on sale: 
      Collect price, numero and necessary data for a purchase on the Ethereum logs. 
      Transmission by an Oracle to our smart contract: numero, price, score, and all the necessary data for a purchase


 
