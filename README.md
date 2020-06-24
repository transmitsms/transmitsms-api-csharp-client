# Getting started

Fast, secure, and easy integrations

API authentication will require your API Key and Secret.
Obtain these by logging into your BurstSMS account and visiting the settings page.

## How to Build

The generated code uses the Newtonsoft Json.NET NuGet Package. If the automatic NuGet package restore
is enabled, these dependencies will be installed automatically. Therefore,
you will need internet access for build.

"This library requires Visual Studio 2017 for compilation."
1. Open the solution (TransmitSMS.sln) file.
2. Invoke the build process using `Ctrl+Shift+B` shortcut key or using the `Build` menu as shown below.

![Building SDK using Visual Studio](https://apidocs.io/illustration/cs?step=buildSDK&workspaceFolder=TransmitSMS-CSharp&workspaceName=TransmitSMS&projectName=TransmitSMS.Standard)

## How to Use

The build process generates a portable class library, which can be used like a normal class library. The generated library is compatible with Windows Forms, Windows RT, Windows Phone 8,
Silverlight 5, Xamarin iOS, Xamarin Android and Mono. More information on how to use can be found at the [MSDN Portable Class Libraries documentation](http://msdn.microsoft.com/en-us/library/vstudio/gg597391%28v=vs.100%29.aspx).

The following section explains how to use the TransmitSMS library in a new console project.

### 1. Starting a new project

For starting a new project, right click on the current solution from the *solution explorer* and choose  ``` Add -> New Project ```.

![Add a new project in the existing solution using Visual Studio](https://apidocs.io/illustration/cs?step=addProject&workspaceFolder=TransmitSMS-CSharp&workspaceName=TransmitSMS&projectName=TransmitSMS.Standard)

Next, choose "Console Application", provide a ``` TestConsoleProject ``` as the project name and click ``` OK ```.

![Create a new console project using Visual Studio](https://apidocs.io/illustration/cs?step=createProject&workspaceFolder=TransmitSMS-CSharp&workspaceName=TransmitSMS&projectName=TransmitSMS.Standard)

### 2. Set as startup project

The new console project is the entry point for the eventual execution. This requires us to set the ``` TestConsoleProject ``` as the start-up project. To do this, right-click on the  ``` TestConsoleProject ``` and choose  ``` Set as StartUp Project ``` form the context menu.

![Set the new cosole project as the start up project](https://apidocs.io/illustration/cs?step=setStartup&workspaceFolder=TransmitSMS-CSharp&workspaceName=TransmitSMS&projectName=TransmitSMS.Standard)

### 3. Add reference of the library project

In order to use the TransmitSMS library in the new project, first we must add a projet reference to the ``` TestConsoleProject ```. First, right click on the ``` References ``` node in the *solution explorer* and click ``` Add Reference... ```.

![Open references of the TestConsoleProject](https://apidocs.io/illustration/cs?step=addReference&workspaceFolder=TransmitSMS-CSharp&workspaceName=TransmitSMS&projectName=TransmitSMS.Standard)

Next, a window will be displayed where we must set the ``` checkbox ``` on ``` TransmitSMS.Standard ``` and click ``` OK ```. By doing this, we have added a reference of the ```TransmitSMS.Standard``` project into the new ``` TestConsoleProject ```.

![Add a reference to the TestConsoleProject](https://apidocs.io/illustration/cs?step=createReference&workspaceFolder=TransmitSMS-CSharp&workspaceName=TransmitSMS&projectName=TransmitSMS.Standard)

### 4. Write sample code

Once the ``` TestConsoleProject ``` is created, a file named ``` Program.cs ``` will be visible in the *solution explorer* with an empty ``` Main ``` method. This is the entry point for the execution of the entire solution.
Here, you can add code to initialize the client library and acquire the instance of a *Controller* class. Sample code to initialize the client library and using controller methods is given in the subsequent sections.

![Add a reference to the TestConsoleProject](https://apidocs.io/illustration/cs?step=addCode&workspaceFolder=TransmitSMS-CSharp&workspaceName=TransmitSMS&projectName=TransmitSMS.Standard)

## How to Test

The generated SDK also contain one or more Tests, which are contained in the Tests project.
In order to invoke these test cases, you will need *NUnit 3.0 Test Adapter Extension for Visual Studio*.
Once the SDK is complied, the test cases should appear in the Test Explorer window.
Here, you can click *Run All* to execute these test cases.

## Initialization

### Authentication
In order to setup authentication and initialization of the API client, you need the following information.

| Parameter | Description |
|-----------|-------------|
| apikey | Obtain your API Key by logging into BurstSMS and visiting the settings page |
| apisecret | Obtain your API Secret by logging into BurstSMS and visiting the settings page |



API client can be initialized as following.

```csharp
// Configuration parameters and credentials
string apikey = "APIKEY"; // Obtain your API Key by logging into BurstSMS and visiting the settings page
string apisecret = "APISECRET"; // Obtain your API Secret by logging into BurstSMS and visiting the settings page

TransmitSMSClient client = new TransmitSMSClient(apikey, apisecret);
```



# Class Reference

## <a name="list_of_controllers"></a>List of Controllers

* [SMSController](#sms_controller)
* [NumbersController](#numbers_controller)
* [ListsController](#lists_controller)
* [EmailSMSController](#email_sms_controller)
* [KeywordsController](#keywords_controller)
* [ResellersController](#resellers_controller)
* [AccountController](#account_controller)

## <a name="sms_controller"></a>![Class: ](https://apidocs.io/img/class.png "TransmitSMS.Standard.Controllers.SMSController") SMSController

### Get singleton instance

The singleton instance of the ``` SMSController ``` class can be accessed from the API Client.

```csharp
SMSController sMS = client.SMS;
```

### <a name="send_sms"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.SendSMS") SendSMS

> The Send-SMS call is the primary method of sending SMS.
> 
> You can elect to pass us the recipient numbers from your database each time you make a call, or you can elect to store recipient data in a contact list and submit only the list_id to trigger the send. This is best for large databases. To add a list please refer to the add-list call.
> 
> You must provide either `to` or `list_id`.
> 
> Cost data is returned in the major unit of your account currency, e.g. dollars or pounds
> 
> **NOTE:** If you do not pass the 'from' parameter the messages will be sent from the shared number pool, unless you have a leased number on your account in which case it will be set as the Caller ID


```csharp
Task<dynamic> SendSMS(
        string format,
        string message,
        string to = null,
        int? listId = null,
        string mfrom = null,
        string sendAt = null,
        string dlrCallback = null,
        string replyCallback = null,
        int? validity = null,
        string repliesToEmail = null,
        bool? fromShared = null,
        string countrycode = null,
        string trackedLinkUrl = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format, either `json` or `xml`. Appended to the URL path. |
| message |  ``` Required ```  ``` DefaultValue ```  | Message text. Include `[tracked-link]` if you are using the tracked link feature where you want the link to appear. |
| to |  ``` Optional ```  | **Required if `list_id` is not provided**.   Mobile number or set of up to 1000 comma separated mobile numbers to send the SMS to. If your number set has some invalid numbers, they won’t cause a validation error and will be simply ignored. Number must be defined in international format.  Some examples by destination:  AU `61491570156`, NZ `64212670129`, SG `6598654321`, UK `44750017696`, US `1213811413` |
| listId |  ``` Optional ```  | **Required if `to` is not provided**.   This is a reference to one of your stored lists.  **Note:** List ID's are made up of digits and will be returned by the add-list call, or can be found at any time by logging into your account and visiting your contacts page. |
| mfrom |  ``` Optional ```  | Set the sender ID for the message. Mobile numbers should be in international format, max 15 digits. Alphanumeric sender IDs up to 11 characters, no spaces, are available in some regions. If not set message will use the shared number option. |
| sendAt |  ``` Optional ```  | A time in the future to send the message.  **Note:** All returned timestamps are in ISO8601 format e.g. `YYYY-MM-DD HH:MM:SS`. The timezone is always UTC. |
| dlrCallback |  ``` Optional ```  | A URL which we can call to notify you of Delivery Receipts. If required, this Parameter can be different for each message sent and will take precedence over the DLR Callback URL supplied by you in the API Settings. |
| replyCallback |  ``` Optional ```  | A URL which we can call to notify you of incoming messages. If required, this parameter can be different and will take precedence over the Reply Callback URL supplied by you on the API Settings. |
| validity |  ``` Optional ```  | Specify the maximum time to attempt to deliver. In minutes, 0 (zero) implies no limit. |
| repliesToEmail |  ``` Optional ```  | Specify an email address to send responses to this message to. NOTE: specified email must be authorised to send messages via add-email or in your account under the 'Email SMS' section. |
| fromShared |  ``` Optional ```  | Forces sending via the shared number when you have virtual numbers |
| countrycode |  ``` Optional ```  | Formats numbers given to international format for this 2 letter country code. i.e. `0422222222` will become `6142222222` when `countrycode` is `AU`. Codes available `AU` Australia, `NZ` New Zealand, `SG` Singapore, `GB` United Kingdom, `US` United States |
| trackedLinkUrl |  ``` Optional ```  | Converts this URL to unique tapth.is/xxxxxx tracking link for each contact. Inserted into message with variable [tracked-link]. Clicks on this URL will be passed as notifications via 'Link hits callback URL' defined in account settings. |


#### Example Usage

```csharp
string format = "json";
string message = "[Enter your message here]";
string to = "to";
int? listId = 27;
string mfrom = "from";
string sendAt = "send_at";
string dlrCallback = "dlr_callback";
string replyCallback = "reply_callback";
int? validity = 27;
string repliesToEmail = "replies_to_email";
bool? fromShared = false;
string countrycode = "countrycode";
string trackedLinkUrl = "tracked_link_url";

dynamic result = await sMS.SendSMS(format, message, to, listId, mfrom, sendAt, dlrCallback, replyCallback, validity, repliesToEmail, fromShared, countrycode, trackedLinkUrl);

```


### <a name="format_number"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.FormatNumber") FormatNumber

> Format and validate a given number.


```csharp
Task<dynamic> FormatNumber(string msisdn, string countrycode, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| msisdn |  ``` Required ```  | The number to check |
| countrycode |  ``` Required ```  | 2 Letter countrycode to validate number against |
| format |  ``` Required ```  ``` DefaultValue ```  | Response Format |


#### Example Usage

```csharp
string msisdn = "msisdn";
string countrycode = "countrycode";
string format = "json";

dynamic result = await sMS.FormatNumber(msisdn, countrycode, format);

```


### <a name="get_sms"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.GetSMS") GetSMS

> Get information about a message you have sent.


```csharp
Task<dynamic> GetSMS(string messageId, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| messageId |  ``` Required ```  | Message ID |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format either json or xml |


#### Example Usage

```csharp
string messageId = "message_id";
string format = "json";

dynamic result = await sMS.GetSMS(messageId, format);

```


### <a name="get_sms_stats"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.GetSMSStats") GetSMSStats

> Get the status about a message you have sent.


```csharp
Task<dynamic> GetSMSStats(string messageId, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| messageId |  ``` Required ```  | Message ID |
| format |  ``` Required ```  ``` DefaultValue ```  | Response Format e.g. json or xml |


#### Example Usage

```csharp
string messageId = "message_id";
string format = "json";

dynamic result = await sMS.GetSMSStats(messageId, format);

```


### <a name="get_sms_responses"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.GetSMSResponses") GetSMSResponses

> Pick up responses to messages you have sent. Filter by keyword or for just one phone number.


```csharp
Task<dynamic> GetSMSResponses(
        string format,
        string messageId = null,
        string keywordId = null,
        string keyword = null,
        string number = null,
        string msisdn = null,
        string page = null,
        string max = null,
        string includeOriginal = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| messageId |  ``` Optional ```  | Message ID |
| keywordId |  ``` Optional ```  | Keyword ID |
| keyword |  ``` Optional ```  | Keyword |
| number |  ``` Optional ```  | Filter results by response number, If keyword is set |
| msisdn |  ``` Optional ```  | Filter results by a particular mobile number |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |
| includeOriginal |  ``` Optional ```  | include text of original message |


#### Example Usage

```csharp
string format = "json";
string messageId = "message_id";
string keywordId = "keyword_id";
string keyword = "keyword";
string number = "number";
string msisdn = "msisdn";
string page = "page";
string max = "max";
string includeOriginal = "include_original";

dynamic result = await sMS.GetSMSResponses(format, messageId, keywordId, keyword, number, msisdn, page, max, includeOriginal);

```


### <a name="get_user_sms_responses"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.GetUserSMSResponses") GetUserSMSResponses

> Pick up responses to messages you have sent. Instead of setting message ID, you should provide a time frame.


```csharp
Task<dynamic> GetUserSMSResponses(
        string format,
        string start = null,
        string end = null,
        string page = null,
        string max = null,
        string keywords = null,
        string includeOriginal = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| start |  ``` Optional ```  | A timestamp to start the report from (Format yyyy-mm-dd, Timezone UTC) |
| end |  ``` Optional ```  | A timestamp to end the report at (Format yyyy-mm-dd, Timezone UTC) |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |
| keywords |  ``` Optional ```  | Filter if keyword responses should be included. Can be: ‘only’ - only keyword responses will be included‘omit’ - only regular campaign responses will be included  ‘both’ - both keyword and campaign responses will be included (default) |
| includeOriginal |  ``` Optional ```  | include text of original message |


#### Example Usage

```csharp
string format = "json";
string start = "start";
string end = "end";
string page = "page";
string max = "max";
string keywords = "keywords";
string includeOriginal = "include_original";

dynamic result = await sMS.GetUserSMSResponses(format, start, end, page, max, keywords, includeOriginal);

```


### <a name="get_link_hits"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.GetLinkHits") GetLinkHits

> Get the list of recipients who have clicked on your tracked link.


```csharp
Task<dynamic> GetLinkHits(string messageId, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| messageId |  ``` Required ```  | Message ID |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string messageId = "message_id";
string format = "json";

dynamic result = await sMS.GetLinkHits(messageId, format);

```


### <a name="get_sms_sent"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.GetSMSSent") GetSMSSent

> Get a list of recipients from a message send. Get up to date information such as opt-out status and delivery status.


```csharp
Task<dynamic> GetSMSSent(
        string messageId,
        string format,
        string optouts = null,
        string page = null,
        string max = null,
        string delivery = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| messageId |  ``` Required ```  | Message ID's are made up of digits |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g json or xml |
| optouts |  ``` Optional ```  | Whether to include optouts. Valid options are:    only - only get optouts   omit - do not get optouts   include - get all recipients including optouts (default) |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |
| delivery |  ``` Optional ```  | Only show messages with requested delivery status. Valid options are:   delivered - only show delivered messages   failed - only show failed messages   pending - only show pending messages |


#### Example Usage

```csharp
string messageId = "message_id";
string format = "json";
string optouts = "optouts";
string page = "page";
string max = "max";
string delivery = "delivery";

dynamic result = await sMS.GetSMSSent(messageId, format, optouts, page, max, delivery);

```


### <a name="get_sms_delivery_status"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.GetSMSDeliveryStatus") GetSMSDeliveryStatus

> Get the delivery time of a delivered message.


```csharp
Task<dynamic> GetSMSDeliveryStatus(string messageId, string msisdn, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| messageId |  ``` Required ```  | Message ID |
| msisdn |  ``` Required ```  | Mobile number |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string messageId = "message_id";
string msisdn = "msisdn";
string format = "json";

dynamic result = await sMS.GetSMSDeliveryStatus(messageId, msisdn, format);

```


### <a name="cancel_sms"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.CancelSMS") CancelSMS

> Cancel a message you have scheduled to be sent in the future.


```csharp
Task<dynamic> CancelSMS(string id, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| id |  ``` Required ```  | Message ID |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string id = "id";
string format = "json";

dynamic result = await sMS.CancelSMS(id, format);

```


### <a name="get_contact_sms_stats"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.SMSController.GetContactSMSStats") GetContactSMSStats

> Get Contact SMS stats


```csharp
Task<dynamic> GetContactSMSStats(
        string format,
        string mobile,
        string countrycode,
        string start = null,
        string end = null,
        string sortField = null,
        string order = null,
        string page = null,
        string max = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| mobile |  ``` Required ```  | valid phone number in international format |
| countrycode |  ``` Required ```  | required if mobile is not in international format , will default to account country code setting |
| start |  ``` Optional ```  | default to account registration date |
| end |  ``` Optional ```  | default to current date |
| sortField |  ``` Optional ```  | possible values our  "delivery_status" - possible values our hard-bounce, "soft-bounce", "delivered", "pending" "message_id" - the unique number identifying the message "datetime_send" the date and time the message was sent |
| order |  ``` Optional ```  | possible values our "asc" and "desc" default to "asc" |
| page |  ``` Optional ```  | page number for pagination |
| max |  ``` Optional ```  | maximum result returned per page |


#### Example Usage

```csharp
string format = "json";
string mobile = "mobile";
string countrycode = "countrycode";
string start = "start";
string end = "end";
string sortField = "sort_field";
string order = "order";
string page = "page";
string max = "max";

dynamic result = await sMS.GetContactSMSStats(format, mobile, countrycode, start, end, sortField, order, page, max);

```


[Back to List of Controllers](#list_of_controllers)

## <a name="numbers_controller"></a>![Class: ](https://apidocs.io/img/class.png "TransmitSMS.Standard.Controllers.NumbersController") NumbersController

### Get singleton instance

The singleton instance of the ``` NumbersController ``` class can be accessed from the API Client.

```csharp
NumbersController numbers = client.Numbers;
```

### <a name="lease_number"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.NumbersController.LeaseNumber") LeaseNumber

> Lease a dedicated virtual number.


```csharp
Task<dynamic> LeaseNumber(string number, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| number |  ``` Required ```  | The virtual number to lease. Omit this field to be given a random number. Use get-numbers to find out which numbers are currently available. |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string number = "number";
string format = "json";

dynamic result = await numbers.LeaseNumber(number, format);

```


### <a name="edit_number_options"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.NumbersController.EditNumberOptions") EditNumberOptions

> Edit your dedicated virtual number options.


```csharp
Task<dynamic> EditNumberOptions(
        string number,
        string format,
        string forwardEmail = null,
        string forwardSms = null,
        string forwardUrl = null,
        string listId = null,
        string welcomeMessage = null,
        string membersMessage = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| number |  ``` Required ```  | The dedicated virtual number. |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| forwardEmail |  ``` Optional ```  | Forward incoming messages to a set of email addresses. |
| forwardSms |  ``` Optional ```  | Forward incoming messages to a set of mobile numbers. |
| forwardUrl |  ``` Optional ```  | Forward incoming messages to a URL. |
| listId |  ``` Optional ```  | Add new numbers that message in to this list. |
| welcomeMessage |  ``` Optional ```  | Auto-response for all messages received. |
| membersMessage |  ``` Optional ```  | Auto-response if the number is already on the list. (must be adding the number to a list) |


#### Example Usage

```csharp
string number = "number";
string format = "json";
string forwardEmail = "forward_email";
string forwardSms = "forward_sms";
string forwardUrl = "forward_url";
string listId = "list_id";
string welcomeMessage = "welcome_message";
string membersMessage = "members_message";

dynamic result = await numbers.EditNumberOptions(number, format, forwardEmail, forwardSms, forwardUrl, listId, welcomeMessage, membersMessage);

```


### <a name="get_numbers"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.NumbersController.GetNumbers") GetNumbers

> Get a list of numbers either leased by you or available to be leased.


```csharp
Task<dynamic> GetNumbers(
        string filter,
        string format,
        string page = null,
        string max = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| filter |  ``` Required ```  ``` DefaultValue ```  | Possible values are owned - retrieve your own response numbers (default) available - retrieve response numbers available for purchase |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |


#### Example Usage

```csharp
string filter = "owned";
string format = "json";
string page = "page";
string max = "max";

dynamic result = await numbers.GetNumbers(filter, format, page, max);

```


### <a name="get_number"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.NumbersController.GetNumber") GetNumber

> Get detailed information about a response number you have leased.


```csharp
Task<dynamic> GetNumber(string number, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| number |  ``` Required ```  | The virtual number to retrieve |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string number = "number";
string format = "json";

dynamic result = await numbers.GetNumber(number, format);

```


### <a name="get_sender_ids"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.NumbersController.GetSenderIds") GetSenderIds

> Get Sender ID's


```csharp
Task<dynamic> GetSenderIds(string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string format = "json";

dynamic result = await numbers.GetSenderIds(format);

```


[Back to List of Controllers](#list_of_controllers)

## <a name="lists_controller"></a>![Class: ](https://apidocs.io/img/class.png "TransmitSMS.Standard.Controllers.ListsController") ListsController

### Get singleton instance

The singleton instance of the ``` ListsController ``` class can be accessed from the API Client.

```csharp
ListsController lists = client.Lists;
```

### <a name="add_to_list"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.AddToList") AddToList

> Add a member to a list.


```csharp
Task<dynamic> AddToList(
        string listId,
        string msisdn,
        string format,
        string firstName = null,
        string lastName = null,
        string countrycode = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| listId |  ``` Required ```  | ID of the list to add to |
| msisdn |  ``` Required ```  | Mobile number of the member |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| firstName |  ``` Optional ```  | First name of the member |
| lastName |  ``` Optional ```  | Last name of the member |
| countrycode |  ``` Optional ```  | Formats msisdn for the given countrycode |


#### Example Usage

```csharp
string listId = "list_id";
string msisdn = "msisdn";
string format = "json";
string firstName = "first_name";
string lastName = "last_name";
string countrycode = "countrycode";

dynamic result = await lists.AddToList(listId, msisdn, format, firstName, lastName, countrycode);

```


### <a name="add_field_to_list"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.AddFieldToList") AddFieldToList

> Update or add custom fields to a list


```csharp
Task<dynamic> AddFieldToList(
        string listId,
        string field1,
        string format,
        string field2 = null,
        Dictionary<string, object> queryParameters = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| listId |  ``` Required ```  | ID of the list to add to |
| field1 |  ``` Required ```  | Custom field value where n is an integer between 1 and 10. You can also use the names of the custom fields you have chosen for your list, e.g. field.birthday. |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| field2 |  ``` Optional ```  | Custom field value where n is an integer between 1 and 10. You can also use the names of the custom fields you have chosen for your list, e.g. field.birthday. |
| queryParameters | ``` Optional ``` | Additional optional query parameters are supported by this method |


#### Example Usage

```csharp
string listId = "list_id";
string field1 = "field_1";
string format = "json";
string field2 = "field_2";
// key-value map for optional query parameters
var queryParams = new Dictionary<string, object>();


dynamic result = await lists.AddFieldToList(listId, field1, format, field2, queryParams);

```


### <a name="add_list"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.AddList") AddList

> Create a new list including the ability to add custom fields.


```csharp
Task<dynamic> AddList(
        string name,
        string format,
        string field1 = null,
        Dictionary<string, object> queryParameters = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| name |  ``` Required ```  | name |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| field1 |  ``` Optional ```  | A custom field name where n is an integer between 1 and 10. Once field names have been set they cannot be changed. |
| queryParameters | ``` Optional ``` | Additional optional query parameters are supported by this method |


#### Example Usage

```csharp
string name = "name";
string format = "json";
string field1 = "field_1";
// key-value map for optional query parameters
var queryParams = new Dictionary<string, object>();


dynamic result = await lists.AddList(name, format, field1, queryParams);

```


### <a name="optout_list_member"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.OptoutListMember") OptoutListMember

> Opt a user out of one list or all lists.


```csharp
Task<dynamic> OptoutListMember(string listId, string msisdn, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| listId |  ``` Required ```  | ID of the list to opt the user out of. Set this to 0 (zero) to opt out of all of your lists. |
| msisdn |  ``` Required ```  | Mobile number of the member to opt out |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g json or xml |


#### Example Usage

```csharp
string listId = "list_id";
string msisdn = "msisdn";
string format = "json";

dynamic result = await lists.OptoutListMember(listId, msisdn, format);

```


### <a name="delete_from_list"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.DeleteFromList") DeleteFromList

> Remove a member from one list or all lists.


```csharp
Task<dynamic> DeleteFromList(int listId, string msisdn, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| listId |  ``` Required ```  | ID of the list to remove from. If set to 0 (zero) the member will be removed from all lists. |
| msisdn |  ``` Required ```  | Mobile number of the member |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
int listId = 27;
string msisdn = "msisdn";
string format = "json";

dynamic result = await lists.DeleteFromList(listId, msisdn, format);

```


### <a name="get_list"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.GetList") GetList

> Get information about a list and its members.


```csharp
Task<dynamic> GetList(
        string listId,
        string format,
        string members = null,
        string page = null,
        string max = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| listId |  ``` Required ```  | List ID |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| members |  ``` Optional ```  | Which types of members to return. Possible values: active - only get active members (default) inactive - only get inactive members all - get active and inactive members none - do not get any members, just metadata |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |


#### Example Usage

```csharp
string listId = "list_id";
string format = "json";
string members = "members";
string page = "page";
string max = "max";

dynamic result = await lists.GetList(listId, format, members, page, max);

```


### <a name="get_lists"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.GetLists") GetLists

> Get the metadata of all your lists.


```csharp
Task<dynamic> GetLists(string format, string page = null, string max = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |


#### Example Usage

```csharp
string format = "json";
string page = "page";
string max = "max";

dynamic result = await lists.GetLists(format, page, max);

```


### <a name="edit_list_member"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.EditListMember") EditListMember

> Edit a member of a list.


```csharp
Task<dynamic> EditListMember(
        string listId,
        string msisdn,
        string format,
        string firstName = null,
        string lastName = null,
        string field1 = null,
        Dictionary<string, object> queryParameters = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| listId |  ``` Required ```  | ID of the list the member belongs to |
| msisdn |  ``` Required ```  | Mobile number of the member to edit |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| firstName |  ``` Optional ```  | First name of the member |
| lastName |  ``` Optional ```  | Last name of the member |
| field1 |  ``` Optional ```  | Custom field value where n is an integer between 1 and 10. You can also use the names of the custom fields you have chosen for your list, e.g. field.birthday. To remove a value set it to an empty string. |
| queryParameters | ``` Optional ``` | Additional optional query parameters are supported by this method |


#### Example Usage

```csharp
string listId = "list_id";
string msisdn = "msisdn";
string format = "json";
string firstName = "first_name";
string lastName = "last_name";
string field1 = "field.1";
// key-value map for optional query parameters
var queryParams = new Dictionary<string, object>();


dynamic result = await lists.EditListMember(listId, msisdn, format, firstName, lastName, field1, queryParams);

```


### <a name="get_contact"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.GetContact") GetContact

> Get contact information from a list.


```csharp
Task<dynamic> GetContact(string listId, string msisdn, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| listId |  ``` Required ```  | ID of the list the contact is on. |
| msisdn |  ``` Required ```  | Mobile number of the contact. |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string listId = "list_id";
string msisdn = "msisdn";
string format = "json";

dynamic result = await lists.GetContact(listId, msisdn, format);

```


### <a name="add_contacts_bulk"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.AddContactsBulk") AddContactsBulk

> Upload a list of contacts to Burst SMS


```csharp
Task<dynamic> AddContactsBulk(
        string name,
        string fileUrl,
        string format,
        string countrycode = null,
        string field1 = null,
        Dictionary<string, object> queryParameters = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| name |  ``` Required ```  | Name of the list |
| fileUrl |  ``` Required ```  | URL location of the contact list (NB: The list you are uploading requires a column labelled mobile) |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| countrycode |  ``` Optional ```  | Specifies which country the numbers are to be formatted in (e.g AU). If uploading numbers for multiple countries, do not define this, you will need to ensure that all the numbers are in correct international format before upload. |
| field1 |  ``` Optional ```  | Adds custom fields to the list. |
| queryParameters | ``` Optional ``` | Additional optional query parameters are supported by this method |


#### Example Usage

```csharp
string name = "name";
string fileUrl = "file_url";
string format = "json";
string countrycode = "countrycode";
string field1 = "field_1";
// key-value map for optional query parameters
var queryParams = new Dictionary<string, object>();


dynamic result = await lists.AddContactsBulk(name, fileUrl, format, countrycode, field1, queryParams);

```


### <a name="remove_list"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ListsController.RemoveList") RemoveList

> Delete a list and its members.


```csharp
Task<dynamic> RemoveList(string listId, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| listId |  ``` Required ```  | List ID |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string listId = "list_id";
string format = "json";

dynamic result = await lists.RemoveList(listId, format);

```


[Back to List of Controllers](#list_of_controllers)

## <a name="email_sms_controller"></a>![Class: ](https://apidocs.io/img/class.png "TransmitSMS.Standard.Controllers.EmailSMSController") EmailSMSController

### Get singleton instance

The singleton instance of the ``` EmailSMSController ``` class can be accessed from the API Client.

```csharp
EmailSMSController emailSMS = client.EmailSMS;
```

### <a name="add_email"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.EmailSMSController.AddEmail") AddEmail

> Authorise an email address for sending Email to SMS


```csharp
Task<dynamic> AddEmail(
        string email,
        string number,
        string format,
        string maxSms = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| email |  ``` Required ```  | Email address to register. You may also register a wild-card email which allows any user on the same domain to use Email to SMS.  Wild-card format: *@example.com |
| number |  ``` Required ```  | Optional dedicated virtual number virtual number |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| maxSms |  ``` Optional ```  | The maximum number of SMS messages to send from one email message sent from this email address.  Possible values: 1 - up to 160 characters (default) 2 - up to 306 characters 3 - up to 459 characters 4 - up to 612 characters |


#### Example Usage

```csharp
string email = "email";
string number = "number";
string format = "json";
string maxSms = "max_sms";

dynamic result = await emailSMS.AddEmail(email, number, format, maxSms);

```


### <a name="delete_email"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.EmailSMSController.DeleteEmail") DeleteEmail

> Remove an email address from the Email to SMS authorised list.


```csharp
Task<dynamic> DeleteEmail(string email, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| email |  ``` Required ```  | Email address to remove. You may also use a wild-card email which removes all emails on that domain.  Wild-card format: *@example.com |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string email = "email";
string format = "json";

dynamic result = await emailSMS.DeleteEmail(email, format);

```


[Back to List of Controllers](#list_of_controllers)

## <a name="keywords_controller"></a>![Class: ](https://apidocs.io/img/class.png "TransmitSMS.Standard.Controllers.KeywordsController") KeywordsController

### Get singleton instance

The singleton instance of the ``` KeywordsController ``` class can be accessed from the API Client.

```csharp
KeywordsController keywords = client.Keywords;
```

### <a name="get_keywords"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.KeywordsController.GetKeywords") GetKeywords

> Get a list of existing keywords.


```csharp
Task<dynamic> GetKeywords(
        string format,
        string number = null,
        string page = null,
        string max = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| number |  ``` Optional ```  | Filter the list by virtual number |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |


#### Example Usage

```csharp
string format = "json";
string number = "number";
string page = "page";
string max = "max";

dynamic result = await keywords.GetKeywords(format, number, page, max);

```


### <a name="add_keyword"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.KeywordsController.AddKeyword") AddKeyword

> Add a keyword to an existing virtual number.


```csharp
Task<dynamic> AddKeyword(
        string keyword,
        string number,
        string format,
        string reference = null,
        string listId = null,
        string welcomeMessage = null,
        string membersMessage = null,
        string activate = null,
        string forwardUrl = null,
        string forwardEmail = null,
        string forwardSms = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| keyword |  ``` Required ```  | The first word of a text message |
| number |  ``` Required ```  | The dedicated virtual number that the keyword belongs to |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| reference |  ``` Optional ```  | Your own reference (up to 100 characters) |
| listId |  ``` Optional ```  | ID of a list to add respondents to, list ID's can be found in the title of a list or in the list page URL |
| welcomeMessage |  ``` Optional ```  | SMS message to send to new members |
| membersMessage |  ``` Optional ```  | SMS message to existing members |
| activate |  ``` Optional ```  | Whether to make the keyword active immediately.  Possible values: true - activate immediately (default) false - create the keyword but do not activate |
| forwardUrl |  ``` Optional ```  | Forward messages to a URL |
| forwardEmail |  ``` Optional ```  | Forward messages to a set of email addresses |
| forwardSms |  ``` Optional ```  | Forward messages to a set of msisdns |


#### Example Usage

```csharp
string keyword = "keyword";
string number = "number";
string format = "json";
string reference = "reference";
string listId = "list_id";
string welcomeMessage = "welcome_message";
string membersMessage = "members_message";
string activate = "activate";
string forwardUrl = "forward_url";
string forwardEmail = "forward_email";
string forwardSms = "forward_sms";

dynamic result = await keywords.AddKeyword(keyword, number, format, reference, listId, welcomeMessage, membersMessage, activate, forwardUrl, forwardEmail, forwardSms);

```


### <a name="edit_keyword"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.KeywordsController.EditKeyword") EditKeyword

> Edit an existing keyword.


```csharp
Task<dynamic> EditKeyword(
        string keyword,
        string number,
        string format,
        string reference = null,
        string status = null,
        string listId = null,
        string welcomeMessage = null,
        string membersMessage = null,
        string activate = null,
        string forwardUrl = null,
        string forwardEmail = null,
        string forwardSms = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| keyword |  ``` Required ```  | The first word of a text message |
| number |  ``` Required ```  | The dedicated virtual number that the keyword belongs to |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| reference |  ``` Optional ```  | Your own reference (up to 100 characters) |
| status |  ``` Optional ```  | Your own reference (up to 100 characters) |
| listId |  ``` Optional ```  | ID of a list to add respondents to, list ID's can be found in the title of a list or in the list page URL |
| welcomeMessage |  ``` Optional ```  | SMS message to send to new members |
| membersMessage |  ``` Optional ```  | SMS message to existing members |
| activate |  ``` Optional ```  | Whether to make the keyword active immediately.  Possible values: true - activate immediately (default) false - create the keyword but do not activate |
| forwardUrl |  ``` Optional ```  | Forward messages to a URL |
| forwardEmail |  ``` Optional ```  | Forward messages to a set of email addresses |
| forwardSms |  ``` Optional ```  | Forward messages to a set of msisdns |


#### Example Usage

```csharp
string keyword = "keyword";
string number = "number";
string format = "json";
string reference = "reference";
string status = "status";
string listId = "list_id";
string welcomeMessage = "welcome_message";
string membersMessage = "members_message";
string activate = "activate";
string forwardUrl = "forward_url";
string forwardEmail = "forward_email";
string forwardSms = "forward_sms";

dynamic result = await keywords.EditKeyword(keyword, number, format, reference, status, listId, welcomeMessage, membersMessage, activate, forwardUrl, forwardEmail, forwardSms);

```


[Back to List of Controllers](#list_of_controllers)

## <a name="resellers_controller"></a>![Class: ](https://apidocs.io/img/class.png "TransmitSMS.Standard.Controllers.ResellersController") ResellersController

### Get singleton instance

The singleton instance of the ``` ResellersController ``` class can be accessed from the API Client.

```csharp
ResellersController resellers = client.Resellers;
```

### <a name="get_transaction"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ResellersController.GetTransaction") GetTransaction

> Get a list of transactions for an account.


```csharp
Task<dynamic> GetTransaction(string id, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| id |  ``` Required ```  | Transaction ID |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string id = "id";
string format = "json";

dynamic result = await resellers.GetTransaction(id, format);

```


### <a name="edit_client"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ResellersController.EditClient") EditClient

> Edit an existing client


```csharp
Task<dynamic> EditClient(
        string clientId,
        string format,
        string name = null,
        string contact = null,
        string password = null,
        string msisdn = null,
        string timezone = null,
        string clientPays = null,
        string smsMargin = null,
        int? fixedTopUpAmount = null,
        string paymentMethod = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| clientId |  ``` Required ```  | The ID of the client |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| name |  ``` Optional ```  | Client company name. Must be unique |
| contact |  ``` Optional ```  | Contact name |
| password |  ``` Optional ```  | Client password |
| msisdn |  ``` Optional ```  | Client phone number |
| timezone |  ``` Optional ```  | A valid timezone, Australia/Sydney. Defaults to your own |
| clientPays |  ``` Optional ```  | Set to true if the client will pay (the default) or false if you will pay |
| smsMargin |  ``` Optional ```  | The number of cents to add to the base SMS price. A decimal value. |
| fixedTopUpAmount |  ``` Optional ```  | Fixed top up amount |
| paymentMethod |  ``` Optional ```  | Payment Method e.g. variable or fixed |


#### Example Usage

```csharp
string clientId = "client_id";
string format = "json";
string name = "name";
string contact = "contact";
string password = "password";
string msisdn = "msisdn";
string timezone = "timezone";
string clientPays = "client_pays";
string smsMargin = "sms_margin";
int? fixedTopUpAmount = 27;
string paymentMethod = "payment_method";

dynamic result = await resellers.EditClient(clientId, format, name, contact, password, msisdn, timezone, clientPays, smsMargin, fixedTopUpAmount, paymentMethod);

```


### <a name="get_transactions"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ResellersController.GetTransactions") GetTransactions

> Get a list of transactions for a client.


```csharp
Task<dynamic> GetTransactions(
        string clientId,
        string format,
        string start = null,
        string end = null,
        string page = null,
        string max = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| clientId |  ``` Required ```  | Only retrieve records for a particular client |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| start |  ``` Optional ```  | A timestamp to start the report from |
| end |  ``` Optional ```  | A timestamp to end the report at |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |


#### Example Usage

```csharp
string clientId = "client_id";
string format = "json";
string start = "start";
string end = "end";
string page = "page";
string max = "max";

dynamic result = await resellers.GetTransactions(clientId, format, start, end, page, max);

```


### <a name="get_client"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ResellersController.GetClient") GetClient

> Get detailed information about a client.


```csharp
Task<dynamic> GetClient(string clientId, string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| clientId |  ``` Required ```  | The ID of the client |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |


#### Example Usage

```csharp
string clientId = "client_id";
string format = "json";

dynamic result = await resellers.GetClient(clientId, format);

```


### <a name="get_clients"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ResellersController.GetClients") GetClients

> Get a list of all clients.


```csharp
Task<dynamic> GetClients(string format, string page = null, string max = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json or xml |
| page |  ``` Optional ```  | Page number, for pagination |
| max |  ``` Optional ```  | Maximum results returned per page |


#### Example Usage

```csharp
string format = "json";
string page = "page";
string max = "max";

dynamic result = await resellers.GetClients(format, page, max);

```


### <a name="add_client"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.ResellersController.AddClient") AddClient

> Add a new client.


```csharp
Task<dynamic> AddClient(
        string name,
        string email,
        string password,
        string msisdn,
        string format,
        string contact = null,
        string timezone = null,
        string clientPays = null,
        string smsMargin = null,
        string numberMargin = null,
        int? fixedTopUpAmount = null,
        string paymentMethod = null,
        string apiSecret = null)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| name |  ``` Required ```  | Client company name |
| email |  ``` Required ```  | Client email address |
| password |  ``` Required ```  | Client password |
| msisdn |  ``` Required ```  | Client phone number |
| format |  ``` Required ```  ``` DefaultValue ```  | Response format e.g. json |
| contact |  ``` Optional ```  | Contact name |
| timezone |  ``` Optional ```  | A valid timezone, Australia/Sydney. Defaults to your own |
| clientPays |  ``` Optional ```  | Set to true if the client will pay (the default) or false if you will pay |
| smsMargin |  ``` Optional ```  | The number of cents to add to the base SMS price. A decimal value |
| numberMargin |  ``` Optional ```  | The number of cents to add to the base number price. A decimal value |
| fixedTopUpAmount |  ``` Optional ```  | Fixed top up amount |
| paymentMethod |  ``` Optional ```  | Payment Method e.g. variable or fixed |
| apiSecret |  ``` Optional ```  | API Secret. Note: if omitted it will be auto generated |


#### Example Usage

```csharp
string name = "name";
string email = "email";
string password = "password";
string msisdn = "msisdn";
string format = "json";
string contact = "contact";
string timezone = "timezone";
string clientPays = "client_pays";
string smsMargin = "sms_margin";
string numberMargin = "number_margin";
int? fixedTopUpAmount = 27;
string paymentMethod = "payment_method";
string apiSecret = "api_secret";

dynamic result = await resellers.AddClient(name, email, password, msisdn, format, contact, timezone, clientPays, smsMargin, numberMargin, fixedTopUpAmount, paymentMethod, apiSecret);

```


[Back to List of Controllers](#list_of_controllers)

## <a name="account_controller"></a>![Class: ](https://apidocs.io/img/class.png "TransmitSMS.Standard.Controllers.AccountController") AccountController

### Get singleton instance

The singleton instance of the ``` AccountController ``` class can be accessed from the API Client.

```csharp
AccountController account = client.Account;
```

### <a name="get_balance"></a>![Method: ](https://apidocs.io/img/method.png "TransmitSMS.Standard.Controllers.AccountController.GetBalance") GetBalance

> Get a summary of your account balance.


```csharp
Task<dynamic> GetBalance(string format)
```

#### Parameters

| Parameter | Tags | Description |
|-----------|------|-------------|
| format |  ``` Required ```  ``` DefaultValue ```  | Response format |


#### Example Usage

```csharp
string format = "json";

dynamic result = await account.GetBalance(format);

```


[Back to List of Controllers](#list_of_controllers)



