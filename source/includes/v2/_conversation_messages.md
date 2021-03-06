# Conversation messages

A conversation message is a message between one or more users participating in a
conversation.

> Conversation message object:

```json
{
   "id" : 514069,
   "content" : "Hi!",
   "creator" : 10073,
   "conversation_id" : 13037,
   "workspace_id" : 5517
   "obj_index" : 0,
   "attachments" : [],
   "actions" : [],
   "reactions" : {},
   "is_deleted" : false,
   "system_message" : null,
   "posted_ts" : 1497970956,
},
```

### Properties of conversation message object

| Name | Description |
| ---- | --- |
| id *Integer* | The id of the message |
| content *String* | The content of the message |
| creator *Integer* | The user that added the message |
| conversation_id *Integer* | The id of the conversation |
| workspace_id *Integer* | The id of the workspace |
| obj_index *Integer* | The index of the message in regards to all other messages in the conversation |
| attachments *List of Objects* | Files attached to the message |
| actions *List of Objects* | Actions define special messages that trigger actions, buttons to click to open URLs, etc. |
| reactions *Object* | Reactions to the thread, where keys are the reactions and values the users that had that reaction |
| is_deleted *Integer* | Whether the message is deleted |
| system_message *String* | A system message |
| posted_ts *Integer* | The Unix time when the message was created |


## Get message

> Example:

```shell
curl --get https://api.twistapp.com/api/v2/conversation_messages/getone \
  -H "Authorization: Bearer 9b1bf97783c1ad5593dee12f3019079dbd3042cf" \
  -d id=514069
```

`GET /api/v2/conversation_messages/getone`

Gets a single conversation message.

### Parameters

| Name | Required | Description |
| --- | --- | --- |
| id *Integer* | Yes | The id of the conversation message |

### Return value

A conversation message object is returned.


## Get all messages

> Example:

```shell
curl --get https://api.twistapp.com/api/v2/conversation_messages/get \
  -H "Authorization: Bearer 9b1bf97783c1ad5593dee12f3019079dbd3042cf" \
  -d conversation_id=13037
```

`GET /api/v2/conversation_messages/get`

Gets messages from a conversation.

### Parameters

| Name | Required | Description |
| --- | --- | --- |
| conversation_id *Integer* | Yes | The id of the conversation |
| limit *Integer* | No | Limits the number of messages returned |
| from_obj_index *Integer* | No | Limit messages starting at the specified object index |
| to_obj_index *String* | No | Limit messages ending at the specified object index |
| order_by *String* | No | The order of the conversations returned one of `DESC` or `ASC` |
| as_ids *Boolean* | No | If enabled, only the ids of the messages are returned |

### Return value

A list of conversation message objects is returned.


## Add message to conversation

> Example:

```shell
curl -X POST https://api.twistapp.com/api/v2/conversation_messages/add \
  -H "Authorization: Bearer 9b1bf97783c1ad5593dee12f3019079dbd3042cf" \
  -d conversation_id=13037 \
  -d content="Hello!"
```

`POST /api/v2/conversation_messages/add`

Adds a message to an existing conversation.

### Parameters

| Name | Required | Description |
| --- | --- | --- |
| conversation_id *Integer* | Yes | The id of the conversation |
| content *String* | Yes | The content of the new message |
| attachments *String* | No | Attachments to the new message |

### Return value

A conversation message object is returned.


## Update message in conversation

> Example:

```shell
curl -X POST https://api.twistapp.com/api/v2/conversation_messages/update \
  -H "Authorization: Bearer 9b1bf97783c1ad5593dee12f3019079dbd3042cf" \
  -d conversation_id=13037 \
  -d content="Hello!"
```

`POST /api/v2/conversation_messages/update`

Updates a message in conversation.

### Parameters

| Name | Required | Description |
| --- | --- | --- |
| id *Integer* | Yes | The id of the message |
| content *String* | No | The content of the new message |
| attachments *String* | No | Attachments to the new message |

### Return value

A conversation message object is returned.


## Remove message from conversation

> Example:

```shell
curl -X POST https://api.twistapp.com/api/v2/conversation_messages/remove \
  -H "Authorization: Bearer 9b1bf97783c1ad5593dee12f3019079dbd3042cf" \
  -d id=514069
```

`POST /api/v2/conversation_messages/remove`

Removes a message from conversation.

### Parameters

| Name | Required | Description |
| --- | --- | --- |
| id *Integer* | Yes | The id of the message |

> Return value:

```json
{
   "status": "ok"
}
```
