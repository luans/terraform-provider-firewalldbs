---
page_title: "firewalldbs_open Resource - terraform-provider-firewalldbs"
subcategory: ""
description: |-
  
---

# Resource `firewalldbs_open`

The firealldbs_open resource allow you to add the agent ip in the server firewall.
Remember, it must be created before the resource that you want to interact with your database. 
## Example Usage

```terraform

resource "firewalldbs_open" "default" {
  server_name         = "brunoxy-ix4-north-eu-sandbox"
  resource_group_name = "bees-eu-sbx-brunoxy"
  agent_ip            = "192.168.1.1"
}

resource "mysql_user" "users" {
  for_each           = var.database_users
  user               = each.key
  host               = var.server_name
  plaintext_password = each.value.password

  depends_on = [
    firewalldbs_open.default
  ]
}

```


<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **resource_group_name** (String)
- **server_name** (String)
- **agent_ip** (String)


### Optional

- **id** (String) The ID of this resource.

