---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "genesyscloud_outbound_callabletimeset Data Source - terraform-provider-genesyscloud"
subcategory: ""
description: |-
  Data source for Genesys Clound Outbound Callable Timesets. Select a callable timeset by name.
---

# genesyscloud_outbound_callabletimeset (Data Source)

Data source for Genesys Clound Outbound Callable Timesets. Select a callable timeset by name.

## Example Usage

```terraform
data "genesyscloud_outbound_callabletimeset" "callable_timeset" {
  name = "Example Callable Timeset"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Callable timeset name.

### Read-Only

- `id` (String) The ID of this resource.


