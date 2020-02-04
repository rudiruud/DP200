Create Azure account

As you've seen, your Azure account is a globally unique entity that gives you access to your Azure subscriptions and services. Authentication for your account is performed using Azure Active Directory (Azure AD). Azure AD is a modern identity provider that supports multiple authentication protocols to secure applications and services in the cloud.

Users, applications, and other entities registered in Azure AD aren't all lumped into a single global service. Instead, Azure AD is partitioned into separate **tenants**. A tenant is a dedicated, isolated instance of the Azure Active Directory service, owned and managed by an organization. 

Azure AD tenants and subscriptions have a one-to-many trust relationship: *A tenant can be associated with multiple Azure subscriptions, but every subscription is associated with only one tenant*. 





