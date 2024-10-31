# Chain Abstraction

Plurality Network has baked in chain abstraction in its protocol. Let’s understand how that works:

## Multi-Chain Wallets and Signatures

Plurality internally uses MPC wallets that get created on a set of nodes that do not belong to any blockchain - rather they exist independently and create a set of keys capable of performing signatures on multiple chains.&#x20;

This means that when a user signs up through their email, internally the key pair that gets created for them does not belong to a particular chain but rather can sign on any chain (subject to some restrictions).

For the end user, this means that users do not have to worry about chains and they get completely abstracted from the end user.

## Gas Sponsorships and Dust Wallets

Now the big question comes, if a user has created a multi-chain wallet through our MPC solution, and they don’t even know there is a wallet or a chain behind it, how would they then figure out that they need tokens to pay for transactions?

That’s where Gas sponsorship and dust wallets come into play. We allow dApps to sponsor gas for their users through our system. Moreover, we can also support dust wallets for first time users. This allows users to seamlessly use the system like a web2 platform without having to worry about the technicalities of web3 transactions

## Seamless Fiat-to-Token Integration

We allow users to simply upload fiat into their wallet that gets automatically converted to required token that’s required

## Liquidity Aggregation

As the next phase of the protocol, we will allow aggregation of all the remaining token balances of the user on different chains and swap them to convert to the required token that could be used for transaction fees.&#x20;

\
