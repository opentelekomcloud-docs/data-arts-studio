:original_name: dataartsstudio_03_0241.html

.. _dataartsstudio_03_0241:

How Can I Access APIs of DataArts DataService Exclusive Using Domain Names?
===========================================================================

The APIs can be accessed using domain names which are bound to the DataArts DataService Exclusive cluster.

-  Binding a private domain name: A private domain name takes effect in a VPC. When a private domain name is bound, it is associated with a private IP address. Then you can call APIs using the private domain name in the same VPC in the private network.

   On the **Clusters** page, locate a cluster, click **More** in the **Operation** column, select **Bind Private Zone**, and enter a custom private domain name. DataArts DataService invokes the DNS service to associate the private domain name with the private IP address. Each tenant can add up to 50 private domain names in all projects.

   The private domain name supports various domain name levels and must comply with domain name naming rules.

   -  Domain name labels are separated by dot (.), and each label does not exceed 63 characters.
   -  A domain name label can contain letters, digits, and hyphens (-) and cannot start or end with a hyphen.
   -  The total length of the domain name cannot exceed 254 characters.

-  Binding a public domain name: A public domain name is resolved on the Internet. When a public domain name is bound, it is associated with a public IP address. Then you can call APIs using the public domain name on the Internet. On the **Clusters** page, locate a cluster, click **More** in the **Operation** column, select **Bind Public Zone**, and enter a registered domain name. DataArts DataService invokes the DNS service to associate the public domain name with the public IP address. To bind a public domain name, ensure that **Public Address** has been enabled during cluster creation and an EIP has been bound to the cluster. Otherwise, the public domain name cannot be bound to the cluster. In addition, each tenant can have up to 50 public domain names.

   The public domain name can include a primary domain name and its subdomain name, for example, abc.example.com.
