---
layout: learn
permalink: /:collection/:path.html
---
# Radiks the data indexer

The Blockstack Radiks feature enables Blockstack decentralized applications (DApps) to index and store across data belonging to multiple users. Radiks works with Blockstack's Gaia Storage System.  Using Radiks, you can build multi-player DApps that:

- index, store, and query application data
- query a user's publicly saved data
- display real-time updates that reflect in progress changes
- support collaboration among sets of users

  

## Why use Radiks?

Many applications server data that users create to share publicly with others, Facebook, Twitter, and Instagram are examples of such applications. Decentralized applications that want to create comparable multi-user experiences must ensure that anything a user creates for public sharing is likewise still under control of the creator in the user's Gaia storage.  

For example, if Twitter were a decentralized application where many different users creating their own tweets and those tweets are stored in each user's own Gaia storage. In such a situation,a developer needs a way to track of everyone's tweets, display tweets in user timelines, and perform searches across tweets. Radiks exists to support these kinds of scenarios in that it allows applications to query across multiple user data, using complicated queries like text search, joins, and filters. 

Radiks allows applications to query data in a performant and flexible way. Each application that wishes to index and query in this way requires its own Radiks server.

## How Radiks works with application data

Radiks consists of a database, a pre-built server, and a client. Each application adds Radiks client library  to their application. With this library a developer models their application data. The model defines an application data schema for the Radiks server. Then, you can use calls to this model to write and query data that use that schema. Whenever an application saves or updates data on behalf of a user, Radiks follows this flow:

1. Encrypts private user data on the client-side.
2. Saves a raw JSON of this encrypted data in the user's Gaia storage.
3. Stores the encrypted data on the Radiks server.

Radiks stores public data and sensitive, non-private data. Radiks encrypts sensitive data by default before the data leaves the client. Your application can query Radiks for public data and then decrypt the sensitive information on the client.  This means that the Radiks server is only able to return queries for unencrypted data.

## How Radiks authorizes writes

Radiks must ensure that user's own any data they are writing. To ensure this, Radiks creates and manages *signing keys*. These keys sign all writes that a user performs. Radiks-server validates all signatures before performing a write. This guarantees that a user is not able to overwrite another user's data.

Radiks-server also is built to support writes in a collaborative but private situation. For example, consider a collaborative document editing application, where users can create organizations and invite users to that organization. All users in that organization have read and write privileges to the organization data. These organizations have a single shared key that is used to sign and encrypt data. 

When an organization administrator needs to remove a user from the group, they'll revoke a previous key and create a new one. Radiks is aware of these relationships, and will only support writes that are signed with the currently active key related to an organization.

## Is Radiks decentralized

Although Radiks applications rely on a centrally-hosted database, an application using Radiks remains fundamentally decentralized. A DApp that uses Radiks has these characteristics.

<table class="uk-table">
  <tr>
    <td>Built on decentralized authentication</td>
    <td> Radiks is deeply tied to Blockstack authentication, which uses a blockchain and Gaia to give you full control over your user data. 
  </tr>
  <tr>
    <td>No data lock-in</td>
    <td><p>All user data is first stored in Gaia before encrypted with the user's keys and stored in Radiks. This process means the user still controls their data for as long as they need to. If the application's Radiks server shuts down, the user can still access their data. And, without application to the user's signing keys, the application cannot decrypt the data. Users may also backup or migrate their application data from Gaia. 
</p></td>
  </tr>
  <tr>
    <td>Censorship resistance</td>
    <td><p>All data is also stored in Gaia; no third-party can revoke access to this data.
</p></td>
  </tr>
  <tr>
    <td>Maximum privacy</td>
    <td><p>All data is encrypted on the client-side before being stored anywhere using Blockstack authorization. The application host cannot inspect, sell, or use user data in any way that a user doesn't explicitly authorize.
</p></td>
  </tr>
</table>

If you are not familiar with Gaia or Blockstack authentication, see 
[read the Gaia documentation](({{site.baseurl}}/storage/overview.html) and [start with the overview of Blockstack auth](overview_auth.html).
