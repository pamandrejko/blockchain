---

copyright:
  years: 2019
lastupdated: "2019-08-21"

keywords: release note, latest changes, Hyperledger Fabric

subcollection: blockchain

---

{:note: .note}
{:important: .important}
{:tip: .tip}
{:shortdesc: .shortdesc}
{:pre: .pre}
{:external: target="_blank" .external}

# Release notes
{: #release-notes-saas-20}

Use these release notes that are grouped by date to learn about the latest changes to {{site.data.keyword.blockchainfull}} Platform for {{site.data.keyword.cloud_notm}} which is built on Hyperledger Fabric v1.4.1.
{:shortdesc}

## 21 August 2019
{: #08-21-2019}

**Peer node patch `1.4.1-3`**

With this patch, you now have the ability to upload additional admin identities for a peer. See [Adding new peer admin certificates](/docs/services/blockchain?topic=blockchain-ibp-console-organizations#ibp-console-organizations-new-admins) for more information.

**Select peer zone** ({{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}} only)  

If multiple zones are configured in your {{site.data.keyword.cloud_notm}} Kubernetes cluster, you can now use the console UI to select the zone where the peer is deployed. This capability is important if you are configuring [multizone HA for peers](/docs/services/blockchain?topic=blockchain-ibp-console-ha#ibp-console-ha-multi-zone).

**Peer database support now includes LevelDB**

You now have the option to choose between CouchDB and LevelDB for your Peer database. For more information, see [LevelDB vs CouchDB](/docs/services/blockchain/howto?topic=blockchain-ibp-console-govern-components#ibp-console-govern-components-level-couch).

**Certificate Authority (CA) updates**   

The console UI no longer uses enroll IDs and secrets for management of a CA. After you create a new CA, you are now responsible for generating the admin certificates by using the **Associate identity** button. Existing CAs are not affected. See [Associating the identity of the CA admin](/docs/services/blockchain?topic=blockchain-ibp-console-identities#ibp-console-identities-ca-identity) for more details.


## 12 August 2019
{: #08-12-2019}

**Beta trial of the {{site.data.keyword.blockchainfull_notm}} Platform ends**

The Beta trial of the {{site.data.keyword.blockchainfull_notm}} Platform, which began on February 12, 2019, has officially ended. All of the beta instances of your console and the components that you deployed into your Kubernetes cluster using the beta console will be deleted.

**Peer node patch `1.4.1-2`**

This patch contains a security fix for the peer couchDB container.

## 10 July 2019
{: #07-10-2019}

**Ordering node patch `1.4.1-2`**  

This patch fixes a problem that occurs when ordering nodes restart. The genesis block is updated which prevents the ordering node from communicating with the other nodes in the ordering service. You can apply this patch to all existing ordering nodes in your ordering services by following these [instructions](/docs/services/blockchain?topic=blockchain-ibp-console-manage-console#ibp-console-manage-patch) to update each ordering node. All new ordering nodes that you create will automatically include this fix.

**Anchor peer removal**  

You now have the ability to remove anchor peers from a channel.

**Miscellaneous bug fixes**  

Bug fixes and translation updates.

## 24 May 2019
{: #05-24-2019}

**Raft consensus protocol**  

The five node Raft ordering service, recommended for production networks, is now available. In addition, for development and testing purposes, you can deploy a single node Raft ordering service.

## 9 May 2019
{: #05-09-2019}

**Introducing {{site.data.keyword.blockchainfull_notm}} Platform Console APIs**

APIs are now available to provision, edit, and delete peer, orderer, and CA nodes, making it possible to script the building of your blockchain network. Use the documentation in the [{{site.data.keyword.cloud_notm}} API documentation repository](/apidocs/blockchain#introduction){: external} to learn more about the APIs and try them out. In addition, see the topic on [Building a network with APIs](/docs/services/blockchain?topic=blockchain-ibp-v2-apis) for instructions on how to use the APIs to build out your network.  

**Channel governance**  

Channel governance updates allow policies to be reconfigured. You can also control which channel members need to sign a channel update and you can orchestrate signature collection.

## 17 April 2019
{: #04-17-2019}

**Ability to size and scale node resources**  

When you deploy a node you now have the ability to specify the amount of CPU, memory, and storage to your containers, where applicable. You can later scale their resources up or down at a later time according to usage patterns. For more information, see [Allocating resources](/docs/services/blockchain?topic=blockchain-ibp-console-govern-components#ibp-console-govern-components-allocate-resources).

**Use of {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM)**  

IAM is used to control user access to the console UI as well as restricting the actions they can perform in the UI.  See this topic for information on how to [add and remove users from the console](/docs/services/blockchain?topic=blockchain-ibp-console-manage-console#ibp-console-manage-console-add-remove).

## 3 April 2019
{: #04-03-2019}

**Support for external CA**

When you add a peer or orderer node, you have the option to use certificates from an external CA, one that is not hosted by {{site.data.keyword.IBM_notm}}. See this topic on [Using certificates from an external CA with your peer or orderer](/docs/services/blockchain?topic=blockchain-ibp-console-build-network#ibp-console-build-network-third-party-ca) for more information.

**Tuning orderer performance**

New orderer tuning parameters are available in the console to give you more control over your orderer throughput and performance. See this topic on [Tuning your orderer](/docs/services/blockchain?topic=blockchain-ibp-console-govern-components#ibp-console-govern-components-orderer-tuning) for instructions on how to configure the parameters.
