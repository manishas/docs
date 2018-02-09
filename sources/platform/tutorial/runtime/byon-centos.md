page_main_title: CentOS BYON nodes
main_section: Platform
sub_section: Tutorials
sub_sub_section: Runtime
page_title: CentOS BYON nodes overview

# CentOS BYON Nodes

To learn the basics of BYON nodes, please read [this overview](/platform/runtime/nodes/#custom-nodes).

This tutorial page shows you how to attach/delete your CentOS BYON nodes to Shippable, as well as perform periodic maintenance on them.

* [Minimum requirements](#requirements)
* [Viewing nodes](#view-nodes)
* [Adding a node](#add-node)
* [Deleting a node](#delete-node)

<a name="requirements"></a>
## Minimum requirements
The minimum requirements for a CentOS BYON type node that can be attached to Shippable are:

* 1.8GB RAM
* 30GB SSD
* Supported architecture, OS and Docker versions for CentOS

|Architecture|OS|Docker Version|
|---|---|---|
|x86_64|CentOS 7|17.06|

<a name="view-nodes"></a>
## Viewing your nodes

You can view all the currently active nodes in your Subscription by following the steps below:

* Click on the Subscription in the left navbar.

<img src="/images/getting-started/account-settings.png" alt="Add Account Integration">

* On the Subscription page, click on the **Gears** icon and click on **Nodes**. In the **NODE LISTS** section, you can view the list of currently active nodes.

<img src="/images/platform/management/subscription-nodes-list.png" alt="Subscription Nodes view for Shippable DevOps Assembly Lines" style="vertical-align: middle;display: block;margin-left: auto;margin-right: auto;"/>

Please note that if you're using Shippable [On-demand Nodes](/platform/runtime/nodes/#dynamic-nodes/), you will only see active nodes, if any. For BYON nodes, they will always be shown here since they are always on and available.

<a name="add-node"></a>
## Adding new nodes

You can add a new node by clicking the `+` icon on the top right corner of **NODE LIST** panel.

* Since every node should be part of a [Node Pool](/platform/management/subscription/node-pools), you need to select which node pool will the new node be a part of. Read [Node Pool](/platform/management/subscription/node-pools) documentation to learn how to create node pools

* Click on the **Docker version** dropdown and select the version you want installed on your nodes. Please note that the list of available versions is populated based on the type of OS and architecture of the node pool

* Enter a name for the node and its IP address.
<img src="/images/platform/tutorial/runtime/byon-centos-add.png" alt="add node for centos BYON for Shippable DevOps Assembly Lines">

* Shippable does not provide a way to automatically initialize CentOS nodes. The
  only initialization method available right now is manually running the init
  scripts on the node.

* To run the initialization scripts,
    * Choose whether you want to enable swap space on your machine.
    * Click on **Generate initialization scripts** to generate the script.
    * Click on **Download scripts** to download. Copy it to your build machine and
    run them.
    * Check the **I have run this script on my node successfully** and then click
    on the **Save** button.
    * Your node status will automatically show green at this point. We have no way 
    of verifying that the node was in fact successfully initialized so you will
    need to make sure this was the case.

* Once the node has been added, any builds that are queued for the node pool
  which this node is a part of, will be picked up by this node

<a name="reset-node"></a>
## Re-initializing a node

You might want to re-initialize a BYON node for the following reasons:

* The node shows a **New version available** message:

<img src="/images/platform/tutorial/runtime/node-update-available.png" alt="List nodes">

* You made some changes to the node manually and it is no longer picking up jobs
* The node isn't picking up jobs and seems 'frozen' for some reason

To re-initialize a node:

- From your Dashboard, click on Subscriptions in the left sidebar menu and click on your subscription.
- Click on the **Gears icon** on the Subscription page and then on **Nodes**.
- Click on the node in the **NODE LISTS** section.
- Click on the node you want to reinitialize.
- You can reset a node by clicking on the **Re-initialize** button, followed by downloading and running the new initialization script
on your node manually. This action will initialize/install all build components from scratch.

<a name="delete-node"></a>
##Deleting a build node

- From your Dashboard, click on Subscriptions in the left sidebar menu and click on your subscription.
- Click on the **gear icon** on the Subscription page and then on **Nodes**.
- Click on the node in the **NODE LISTS** section.
- Scroll to the bottom of the screen and click on **Delete** to delete your build node. This action is final and cannot be undone.