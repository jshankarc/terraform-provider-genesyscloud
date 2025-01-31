---
page_title: "genesyscloud_journey_views Resource - terraform-provider-genesyscloud"
subcategory: ""
description: |-
  Genesys Cloud Directory JourneyView
---
# genesyscloud_journey_views (Resource)

Genesys Cloud Directory JourneyView

## API Usage
The following Genesys Cloud APIs are used by this resource. Ensure your OAuth Client has been granted the necessary scopes and permissions to perform these operations:

* [POST /api/v2/journey/views](https://developer.genesys.cloud/platform/preview-apis#post-api-v2-journey-views)
* [POST /api/v2/journey/views/{viewId}/versions](https://developer.genesys.cloud/platform/preview-apis#post-api-v2-journey-views--viewId--versions)
* [GET /api/v2/journey/views/{viewId}](https://developer.genesys.cloud/platform/preview-apis#get-api-v2-journey-views--viewId-)
* [DELETE /api/v2/journey/views/{viewId}](https://developer.genesys.cloud/platform/preview-apis#delete-api-v2-journey-views--viewId-)

## Example Usage

```terraform
resource "genesyscloud_journey_views" "journey_view" {
  duration = "P1Y"
  name     = "Sample Journey 1"
  elements {
    id   = "ac6c61b5-1cd4-4c6e-a8a5-edb74d9117eb"
    name = "Wrap Up"
    attributes {
      type   = "Event"
      id     = "a416328b-167c-0365-d0e1-f072cd5d4ded"
      source = "Voice"
    }
    filter {
      type = "And"
      predicates {
        dimension = "mediaType"
        values    = ["VOICE"]
        operator  = "Matches"
        no_value  = false
      }
    }
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) JourneyView name.

### Optional

- `charts` (Block List) The charts within the journey view. (see [below for nested schema](#nestedblock--charts))
- `description` (String) A description of the journey view.
- `duration` (String) A relative timeframe for the journey view, expressed as an ISO 8601 duration. Only one of interval or duration must be specified. Periods are represented as an ISO-8601 string. For example: P1D or P1DT12H.
- `elements` (Block List) The elements within the journey view. (see [below for nested schema](#nestedblock--elements))
- `interval` (String) An absolute timeframe for the journey view, expressed as an ISO 8601 interval. Only one of interval or duration must be specified. Intervals are represented as an ISO-8601 string. For example: YYYY-MM-DDThh:mm:ss/YYYY-MM-DDThh:mm:ss.

### Read-Only

- `id` (String) The ID of this resource.
- `version` (Number) Version of JourneyView.

<a id="nestedblock--charts"></a>
### Nested Schema for `charts`

Required:

- `metrics` (Block List, Min: 1) A set of metrics to be displayed on the chart. (see [below for nested schema](#nestedblock--charts--metrics))
- `name` (String) The unique name of the chart within the view.
- `version` (Number) The version of chart

Optional:

- `display_attributes` (Block List, Max: 1) Optional display attributes for rendering the chart (see [below for nested schema](#nestedblock--charts--display_attributes))
- `group_by_attributes` (Block List) A list of attributes to group the metrics by (see [below for nested schema](#nestedblock--charts--group_by_attributes))
- `group_by_max` (Number) A maximum on the number of values being grouped by
- `group_by_time` (String) A time unit to group the metrics by. Valid values: Day, Week, Month, Year.

Read-Only:

- `id` (String) The unique identifier of the chart within the charts list.

<a id="nestedblock--charts--metrics"></a>
### Nested Schema for `charts.metrics`

Required:

- `element_id` (String) The reference of element.
- `id` (String) The unique identifier of the metric within the metrics list.

Optional:

- `aggregate` (String) How to aggregate the given element. Valid values: EventCount, CustomerCount.
- `display_label` (String) Display label of metric.


<a id="nestedblock--charts--display_attributes"></a>
### Nested Schema for `charts.display_attributes`

Optional:

- `group_by_title` (String) A title for the grouped by attributes (aka the x axis).
- `metrics_title` (String) A title for the metrics (aka the y axis).
- `show_legend` (Boolean) Whether to show a legend
- `var_type` (String) The type of chart to display. Valid values: Bar, Column, Line.


<a id="nestedblock--charts--group_by_attributes"></a>
### Nested Schema for `charts.group_by_attributes`

Required:

- `attribute` (String) The attribute of the element being grouped by.
- `element_id` (String) The element in the list of elements which is being grouped by.



<a id="nestedblock--elements"></a>
### Nested Schema for `elements`

Required:

- `attributes` (Block List, Min: 1, Max: 1) Attributes on an element in a journey view. (see [below for nested schema](#nestedblock--elements--attributes))
- `id` (String) The unique identifier of the element within the elements list.
- `name` (String) The unique name of the element within the view.

Optional:

- `display_attributes` (Block List, Max: 1) Display Attributes on an element in a journey view. (see [below for nested schema](#nestedblock--elements--display_attributes))
- `filter` (Block List, Max: 1) A set of filters on an element within a journey view. (see [below for nested schema](#nestedblock--elements--filter))
- `followed_by` (Block List) A list of JourneyViewLink objects, listing the elements downstream of this element. (see [below for nested schema](#nestedblock--elements--followed_by))

<a id="nestedblock--elements--attributes"></a>
### Nested Schema for `elements.attributes`

Required:

- `type` (String) The type of the element (e.g. Event).Valid values: Event.

Optional:

- `id` (String) The identifier for the element based on its type.
- `source` (String) The source for the element (e.g. IVR, Voice, Chat). Used for informational purposes only.


<a id="nestedblock--elements--display_attributes"></a>
### Nested Schema for `elements.display_attributes`

Required:

- `col` (Number) The column position for the element in the journey view canvas.
- `x` (Number) The horizontal position (x-coordinate) of the element on the journey view canvas.
- `y` (Number) The vertical position (y-coordinate) of the element on the journey view canvas.


<a id="nestedblock--elements--filter"></a>
### Nested Schema for `elements.filter`

Required:

- `type` (String) Boolean operation to apply to the provided predicates and clauses. Valid values: And.

Optional:

- `predicates` (Block List) A filter on an element within a journey view. (see [below for nested schema](#nestedblock--elements--filter--predicates))

<a id="nestedblock--elements--filter--predicates"></a>
### Nested Schema for `elements.filter.predicates`

Required:

- `dimension` (String) The element's attribute being filtered on.
- `values` (List of String) The identifier for the element based on its type.

Optional:

- `no_value` (Boolean) set this to true if no specific value to be considered.
- `operator` (String) Optional operator, default is Matches. Valid values: Matches.Valid values: Matches, NotMatches. Defaults to `Matches`.



<a id="nestedblock--elements--followed_by"></a>
### Nested Schema for `elements.followed_by`

Required:

- `id` (String) The identifier of the element downstream.

Optional:

- `constraint_after` (Block List, Max: 1) A time constraint on this link, which requires a customer must complete the downstream element after this amount of time to be counted. (see [below for nested schema](#nestedblock--elements--followed_by--constraint_after))
- `constraint_within` (Block List, Max: 1) A time constraint on this link, which requires a customer to complete the downstream element within this amount of time to be counted. (see [below for nested schema](#nestedblock--elements--followed_by--constraint_within))
- `event_count_type` (String) The type of events that will be counted. Note: Concurrent will override any JourneyViewLinkTimeConstraint. Default is Sequential.Valid values: All, Concurrent, Sequential.
- `join_attributes` (List of String) Other (secondary) attributes on which this link should join the customers being counted.

<a id="nestedblock--elements--followed_by--constraint_after"></a>
### Nested Schema for `elements.followed_by.constraint_after`

Optional:

- `unit` (String) The unit for the link's time constraint.Valid values: Seconds, Minutes, Hours, Days, Weeks, Months.
- `value` (Number) The value for the link's time constraint.


<a id="nestedblock--elements--followed_by--constraint_within"></a>
### Nested Schema for `elements.followed_by.constraint_within`

Optional:

- `unit` (String) The unit for the link's time constraint.Valid values: Seconds, Minutes, Hours, Days, Weeks, Months.
- `value` (Number) The value for the link's time constraint.

