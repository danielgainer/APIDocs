{{{
  "title": "Delete Shared Load Balancer",
  "date": "3-26-2015",
  "author": "Bryan Friedman",
  "attachments": []
}}}

Deletes a given shared load balancer by ID. Calls to this operation must include a token acquired from the authentication endpoint. See the [Login API](../Authentication/login.md) for information on acquiring this token.

### When to Use It

Use this API operation when you want to delete a specific load balancer within a given account and data center.

## URL

### Structure

    DELETE https://api.ctl.io/v2/sharedLoadBalancers/{accountAlias}/{dataCenter}/{loadBalancerId}

### Example

    DELETE https://api.ctl.io/v2/sharedLoadBalancers/ALIAS/WA1/ae3bbac5d9694c70ad7de062476ccb70

## Request

### URI Parameters

| Name | Type | Description | Req. |
| --- | --- | --- | --- |
| AccountAlias | string | Short code for a particular account | Yes |
| DataCenter | string | Short string representing the data center where the load balancer is located. Valid codes can be retrieved from the [Get Data Center List](../Data Centers/get-data-center.md) API operation. | Yes |
| LoadBalancerId | string | ID of the load balancer to delete. | Yes |

## Response

The response will not contain JSON content, but should return the HTTP `204 No Content` response upon deletion of the load balancer.
