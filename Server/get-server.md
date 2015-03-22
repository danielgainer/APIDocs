{{{
  "title": "GetServer",
  "date": "10-29-2014",
  "author": "Peter Kowalczyk",
  "attachments": []
}}}

Gets the detail for one server.

## URL

    REST: https://api.ctl.io/REST/Server/GetServer/<format> (format = XML | JSON)
    SOAP: https://api.ctl.io/SOAP/Server.asmx?op=ServerResponseMsg

## Request

### Attributes

| Name | Type | Description | Req. |
| --- | --- | --- | --- |
| AccountAlias | String | The alias of the account that owns the server. If not provided it will assume the account to which the API user is mapped. Providing this value gives you the ability to access servers in your sub accounts. | No |
| Name | String | The name of the server. | Yes |

### Examples

#### JSON

    { "Name": "WA1T3NWEB01" }

#### XML

    <ServerRequest>
        <AccountAlias>ACCT</AccountAlias>
        <Name>SERVER1</Name>
    </ServerRequest>

## Response

### Attributes

| Name | Type | Description |
| --- | --- | --- |
| Success | Boolean | True if the request was successful, otherwise False. |
| Message | String | A description of the result. The contents of this field does not contain any actionable information, it is purely intended to provide a human readable description of the result. |
| StatusCode | Int | This value will help to identify any errors which were encountered while processing the request. The value of '0' indicates success, all non-zero StatusCodes indicate an error state. |
| Server | Complex | A [Server Object](server-object.md). |

### Examples

#### JSON

    {
      "Success":true,
      "Message":"Success",
      "StatusCode":0,
      "Server":
        {
          "ID":1001,
          "HardwareGroupID":1,
          "Name":"WA1T3NWEB01",
          "Description":"WA1T3NWEB01",
          "DnsName":"WA1T3NWEB01",
          "IsTemplate":false,
          "Cpu":2,
          "MemoryGB":4,
          "DiskCount":3,
          "TotalDiskSpaceGB":116,
          "Status":"Active",
          "ServerType":2,
          "ServiceLevel":1,
          "OperatingSystem":4,
          "PowerState":"Started",
          "Location":"WA1",
          "IPAddress":"172.0.0.1",
          "IPAddresses:[
            {"Address":"172.0.01", "AddressType":1}],
          "CustomFields":[
            { "CustomFieldID": 100,"Name": "My Field", "Type": "Text", "Value": "A test"},
            { "CustomFieldID": 101,"Name": "My Field 2","Type": "Option","Value": "2"},
            { "CustomFieldID": 102,"Name": "My Field 3","Type": "Checkbox","Value": "true"}
          ]
        }
    }

#### XML

    <ServerResponse Success="true" Message="Successfully retrieved servers" StatusCode="0">
        <Server ID="1001" HardwareGroupID="1" Name="WA1T3NWEB01" Description="WA1T3NWEB01"
          DnsName="WA1T3NWEB01" IsTemplate="false" Cpu="2" MemoryGB="4" DiskCount="3"
          TotalDiskSpaceGB="116" Status="Active" ServerType="1" ServiceLevel="2"
          OperatingSystem="2" PowerState="Started" Location="WA1" IPAddress="172.0.0.1">
            <IPAddresses>
                <IPAddress Address="172.0.0.1" AddressType="RIP" />
            </IPAddresses>
            <CustomFields CustomFieldID="100" Name="My Field" Type="Text" Value="Test Value" />
            <CustomFields CustomFieldID="101" Name="My 2nd Field" Type="Option" Value="Value 3" />
            <CustomFields CustomFieldID="102" Name="My 3rd Field" Type="Checkbox" Value="true" />
       </Server>
    </ServerResponse>

### Status Codes

| Status Code | Description |
| --- | --- |
| 0 | Request was successfully processed |
| 2 | Unknown Error.  An application error occurred processing your request, contact support to resolve the issue. |
| 3 | Invalid Request Format. This value indicates that the XML or JSON requests do not match the expected format. |
| 5 | Resource Not Found.  A Group with the specified ID cannot be found. |
| 100 | Authentication Failed.  You must logon to the API prior to calling this method. |