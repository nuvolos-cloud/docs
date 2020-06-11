---
description: The in-depth guide to the role system
---

# Roles

Nuvolos has a role system that is directly mapped to the structure of Nuvolos. On each structural level, a variety of roles exist with different actions available for different use cases.

In order to fully understand the role system, the [structure of Nuvolos](../our-features/data-organization/) is a suggested read.

## Organization level roles

As described in detail, organizations are cost and accounting centers. On the organization level, the following four roles exist:

### No role

If a user has no role in an organization, they cannot view any content contained in the organization. If a user has a role, it can be[ revoked](organization-management/revoke-user-access.md) by an organization manager.

### Member

An organization member is any user who has been invited in any capacity into any space in the organization.

* Members are able to view **Public** spaces in the organization. 
* Members are able to view any content in the organization they are specifically invited to. 
* The membership role signifies that a connection has at least at one point in time existed between the user and the organization.

### Faculty

An organization faculty member is a user who has the ability to control resources in the organization. 

* Faculty members can create spaces and invite users to the spaces they have created. Any user who creates a space automatically becomes _space admin_ of that space. 
* Faculty members can view **Public** and **Faculty only** spaces as well as any content they are invited to. 
* The faculty role is powerful in the sense that it has the ability to propagate licenced content to other users.

### Manager

An organization manager is a user who has the ability to view resources in the organization as well as control membership.

* Organization managers can create spaces and invite users to the spaces they have craeted. Any user who creates a space automatically becomes _space admin_ of that space. 
* Organization managers can view all content in the organization however they can modify content where they received explicit invitation to do so. 
* Organization managers can invite additional Faculty to the organization. 
* Organization managers can revoke access to the organization resources. 



## Space level roles





## Instance level roles

Becoming a super hero is a fairly straight forward process:

```
$ give me super-powers
```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}



