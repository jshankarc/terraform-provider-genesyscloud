---
page_title: "genesyscloud_architect_datatable_row Resource - terraform-provider-genesyscloud"
subcategory: ""
description: |-
  Genesys Cloud Architect Datatable Row
---
# genesyscloud_architect_datatable_row (Resource)

Genesys Cloud Architect Datatable Row

## API Usage
The following Genesys Cloud APIs are used by this resource. Ensure your OAuth Client has been granted the necessary scopes and permissions to perform these operations:

* [GET /api/v2/flows/datatables/{datatableId}/rows](https://developer.mypurecloud.com/api/rest/v2/architect/#get-api-v2-flows-datatables--datatableId--rows)
* [GET /api/v2/flows/datatables/{datatableId}/rows/{rowId}](https://developer.mypurecloud.com/api/rest/v2/architect/#get-api-v2-flows-datatables--datatableId--rows--rowId-)
* [POST /api/v2/flows/datatables/{datatableId}/rows](https://developer.mypurecloud.com/api/rest/v2/architect/#post-api-v2-flows-datatables--datatableId--rows)
* [PUT /api/v2/flows/datatables/{datatableId}/rows/{rowId}](https://developer.mypurecloud.com/api/rest/v2/architect/#put-api-v2-flows-datatables--datatableId--rows--rowId-)
* [DELETE /api/v2/flows/datatables/{datatableId}/rows/{rowId}](https://developer.mypurecloud.com/api/rest/v2/architect/#delete-api-v2-flows-datatables--datatableId--rows--rowId-)

## Example Usage

```terraform
resource "genesyscloud_architect_datatable_row" "john-smith-2749" {
  datatable_id = genesyscloud_architect_datatable.customer-table.id
  key_value    = "johnsmith@example.com"
  properties_json = jsonencode({
    "identifier" = 2749
    "address"    = "123 Main Street"
    "vip"        = true
  })
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- **datatable_id** (String) Datatable ID that contains this row. If this is changed, a new row is created.
- **key_value** (String) Value for this row's key. If this is changed, a new row is created.

### Optional

- **id** (String) The ID of this resource.
- **properties_json** (String) JSON object containing properties and values for this row. Defaults will be set for missing properties.
