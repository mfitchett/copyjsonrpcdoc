#Copy JSON-RPC API

#### ABOUT

#### API URL
      https://api.copy.com/jsonrpc/

#### AVAILABLE API METHODS
* User
  * [Create User](#create_user)
  * [Confirm User Email](#confirm_user_email)
  * [Update User](#update_user)
  * [Get Copy-User](#get_user)
  * [Reset Password](#reset_password)
* Authenticate
  * [Authenticate User](#authenticate_user)
* Shares
    * [Create Share](#create_share)
    * [Update Share](#update_share)
    * [List All Share](#list_shares)
	* [Add Share Member](#add_share_member)
* Object
	* [Check Version](#check_version)
	* [List Objects](#list_objects)
	* [List Removed Objects](#list_removed_objects)
	* [Undelete Object](#undelete_object)
	* [List Revisions](#list_revisions)
	* [Update Objects](#update_objects)
	* [Make Revision Latest](#make_revision_latest)
* Links
	* [Create Link](#create_link)
	* [Update Link](#update_link)
	* [Get Link](#get_link)
	* [List Links](#list_links)
	* [Send Link](#send_link)
	* [Sync Link](#sync_link)
	* [Update Link User](#update_link_user)
* Misc
	* [Get Thumbnail](#get_thumbnail)
	* [Get Thumbnails](#get_thumbnails)
	* [List Contacts](#list_contacts)

## <a name="create_user"></a>Create User

##### METHOD
      create_user

##### DESCRIPTION
Creates a user account.

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
email *  | An email address to associate with user
first_name *  | The first name for the user
last_name *  | The last name for the user
password *  | The password sent to authdb for storage
referral_code  | A token that will process a referral for the new user
redirect_url  | Passed to the welcome email for user direction
anon_auth_token | If provided anon user is melded into new account
source | Signup source
no_email_notification | If true, welcome email is suppressed
signup_ip | Originating IP address

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "create_user",
    "params": {
        "email": "johnh@domain.com",
        "password": "password",
        "first_name": "john",
        "last_name": "henry"
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "user_id": "hidden",
        "created_time": "1435579765",
        "email": "",
        "developer": "0",
        "emails": [
            {
                "email": "johnh@domain.com",
                "confirmed": "0",
                "primary": "1",
                "user_id": "hidden",
                "canonical_email": "johnh@domain.com"
            }
        ],
        "username": "johnh@domain.com",
        "first_name": "john",
        "last_name": "henry",
        "anonymous": "0",
        "confirmed": "0",
        "push_token": "hidden",
        "push_host": "push3.copy.com",
        "global_path_root": "/root/users/user-hidden",
        "ldap_status": false,
        "show_tour": "1",
        "auth_token": "hidden"
    }
}```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1010  | Email has already been used.
1003  | Mandatory Field Missing/ Invalid method



## <a name="confirm_user"></a>Confirm User Email

##### METHOD
      confirm_user_email

##### DESCRIPTION
Confirm User Email

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
confirm_token *  | 'auth_token' received from Authenticate User

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "confirm_user_email",
    "params": {
        "confirm_token": "hidden"
    }
}
```

##### RESPONSE
```
{

}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Mandatory Field Missing/ Invalid method
1039  | User does not contain invite email




## <a name="authenticate_user"></a>Authenticate User

##### METHOD
      auth_user

##### DESCRIPTION
Provide authentication tokens for the user.

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
username *  | Username to authenticate with
password *  | Password to authenticate with
anon_auth_token  | Anonymous user auth token

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "auth_user",
    "params": {
        "username": "johnh@domain.com",
        "password": "password"
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "user_id": "hidden",
        "created_time": "1435579765",
        "email": "johnh@domain.com",
        "developer": "0",
        "emails": [
            {
                "email": "johnh@domain.com",
                "confirmed": "1",
                "primary": "1"
            }
        ],
        "username": "johnh@domain.com",
        "first_name": "john",
        "last_name": "henry",
        "anonymous": "0",
        "confirmed": "1",
        "push_token": "hidden",
        "push_host": "push3.copy.com",
        "global_path_root": "/root/users/user-hidden",
        "ldap_status": false,
        "show_tour": "1",
        "auth_token": "hidden"
    }
}
}```

##### ERRORS
CODE  | DESCRIPTION
------------- | ------------
1003  | Mandatory Field Missing/ Invalid method
1008  | Authentication failed(Username or Password is incorrect)




## <a name="get_user"></a>Get Copy-User

##### METHOD
      get_user

##### DESCRIPTION
Get Copy user info from the copy-user table.

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "get_user",
    "params": [

    ]
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "user_id": "hidden",
        "created_time": "1435579765",
        "email": "johnh@domain.com",
        "developer": "0",
        "emails": [
            {
                "email": "johnh@domain.com",
                "confirmed": "1",
                "primary": "1"
            }
        ],
        "username": "johnh@domain.com",
        "first_name": "john",
        "last_name": "henry",
        "anonymous": "0",
        "confirmed": "1",
        "push_token": "hidden",
        "push_host": "push3.copy.com",
        "global_path_root": "/root/users/user-hidden",
        "ldap_companies": [],
        "ldap_status": false,
        "show_tour": "1",
        "client_id": 0,
        "usage": {
            "total_capacity": 16106127360,
            "shares": [
                {
                    "share_id": "0",
                    "share_member_count": 1,
                    "file_size": "0",
                    "file_count": "0",
                    "usage_size": 0
                }
            ],
            "total_file_size": "0",
            "total_file_count": "0",
            "raw_file_size": "0",
            "total_usage_size": "0"
        },
        "referrer": {
            "reasons": [],
            "qualified": "1",
            "referral_link": "https://copy.com?r=T1VOVs"
        },
        "storage_plan": "free",
        "billing_serial": null
    }
}
}```

##### ERRORS
CODE  | DESCRIPTION
------------- | ------------
1003  | Invalid method
1001  | Invalid authentication token



## <a name="update_user"></a>Update User

##### METHOD
      update_user

##### DESCRIPTION
Update the User Information.

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
update_fields *  | User Fields to be updated

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_user",
    "params": {
      "update_fields": {
        "first_name": "Mark",
        "last_name": "Weber"
      }
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "user_id": "hidden",
        "created_time": "1435579765",
        "email": "johnh@domain.com",
        "developer": "0",
        "emails": [
            {
                "email": "johnh@domain.com",
                "confirmed": "1",
                "primary": "1"
            }
        ],
        "username": "johnh@domain.com",
        "first_name": "Mark",
        "last_name": "Weber",
        "anonymous": "0",
        "confirmed": "1",
        "push_token": "hidden",
        "push_host": "push3.copy.com",
        "global_path_root": "/root/users/user-hidden",
        "ldap_status": false,
        "show_tour": "1"
    }
}
}```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1001  | Invalid authentication token
1003  | Invalid method



## <a name="reset_password"></a>Reset Password

##### METHOD
      reset_password

##### DESCRIPTION
Send reset password link to the registered email.

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
action *  | request
username *  | UserName of the account

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "reset_password",
  	"params": {
      "action": "request",
      "username": "johnh@domain.com"
  }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "user_id": "hidden",
        "auth_token": true
    }
}
}```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters



## <a name="create_share"></a>Create Share

##### METHOD
      create_share

##### DESCRIPTION
Create Folder and Share it to other users.

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
path *  | /Folder Name
invite  | Array of member Email id's

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "create_share",
    "params": {
        "path": "/New-Folder",
      	"invite":{
          "members":[
            "johnh@domain.com"
          ]
      }
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "share_id": "hidden",
        "created_time": "1435661174",
        "creator": "hidden",
        "meta_owner": {
            "user_id": "hidden",
            "email": "johnh@domain.com",
            "email_confirmed": true,
            "first_name": "john",
            "last_name": "henry"
        },
        "path": "/New-Folder",
        "last_change_time": null,
        "joined": "1",
        "sync_watermark": "5",
        "permission": null
    }
}
}```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters


## <a name="update_share"></a>Update Share

##### METHOD
      update_share

##### DESCRIPTION
Update Share invite or remove members.

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
share_id *  | Share ID received when create the share.
invite  | Array of member Email id's to be added or remove, Specify the string 'all' to remove the entire share.
keep_local_copy  | Whether to retain a local copy of the share for removed users.
hard_delete  | Whether to force a hard delete if the current user is removing themselves from a share. A user cannot re-add themselves to a share once they are hard deleted.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_share",
    "params":
      {
      "share_id": "hidden",
        "invite": {
          "members": [
            "name@domain.com"
            ]
        }
      }
}

{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_share",
    "params":
      {
      "share_id": "hidden",
        "remove": {
          "keep_local_copy": "false",
          "hard": "true",
          "members": [
            "name@domain.com"
            ]
        }
      }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "share_id": "hidden",
        "created_time": "1435657552",
        "creator": "hidden",
        "meta_owner": {
            "user_id": "hidden",
            "email": "johnh@domain.com",
            "email_confirmed": true,
            "first_name": "john",
            "last_name": "henry"
        },
        "path": "/Folder",
        "last_change_time": null,
        "joined": "1",
        "sync_watermark": 0,
        "permission": null
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters





## <a name="list_shares"></a>List All Share

##### METHOD
      list_shares

##### DESCRIPTION
List all the shares.

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
include_members  | 1 to include and 0 not to include member fields in the response
include_pending_invites  | 1 to include and 0 not to include pending_invites in the response
include_my_invites  | 1 to include and 0 not to include my_invites in the response
include_left_shares | 1 to include and 0 not to include left_shares in the response

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "list_shares",
    "params":
      {
      "include_members": "1",
        "include_pending_invites": "1",
        "include_my_invites": "1",
        "include_left_shares": "1"
      }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "shares": [
            {
                "share_id": "hidden",
                "created_time": "1435663455",
                "creator": "hidden",
                "meta_owner": {
                    "user_id": "hidden",
                    "email": "johnh@domain.com",
                    "email_confirmed": true,
                    "first_name": "john",
                    "last_name": "henry"
                },
                "path": "/New-Folder",
                "last_change_time": null,
                "joined": "1",
                "sync_watermark": 0,
                "permission": null,
                "members": [
                    {
                        "user_id": "hidden",
                        "email": "johnh@domain.com",
                        "first_name": "john",
                        "last_name": "henry"
                    }
                ],
                "pending_invites": [
                    {
                        "created_time": "1435663456",
                        "token": "hidden",
                        "creator": {
                            "user_id": "hidden",
                            "email": "name@domain.com",
                            "first_name": "john",
                            "last_name": "henry"
                        },
                        "recipient": {
                            "email": "name@domain.com"
                        }
                    }
                ]
            }
        ]
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method



## <a name="add_share_member"></a>Add Share Member

##### METHOD
      add_share_member

##### DESCRIPTION
Add Members to Share

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
share_id *  | Share ID received when create the share.
members  | Array of member Email id's to be added.
send_invite  | Whether to retain a local copy of the share for removed users.
invite_message  | Custom message to include in the invite email.
share_path  | Path of the share when created.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "add_share_member",
    "params": {
        "share_id": "hidden",
        "members": ["johncy@rediffmail.com","sheanw@gmail.com"],
        "send_invite": true,
        "invite_message": "Play Arena Welcomes You!!",
        "share_path": "/North-Park"
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "share_id": "hidden",
        "created_time": "1435671449",
        "creator": "hidden",
        "meta_owner": {
            "user_id": "hidden",
            "email": "johnh@domain.com",
            "email_confirmed": true,
            "first_name": "john",
            "last_name": "henry"
        },
        "path": "/North-Park",
        "last_change_time": null,
        "joined": "1",
        "sync_watermark": 0,
        "permission": null
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters
1031  | Mis-Match in Share Path provided in the request and the stored one.



## <a name="check_version"></a>Check Version

##### METHOD
      check_version

##### DESCRIPTION
Check Version

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
build_slot  |

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "check_version",
    "params": {
        "build_slot": null
    }
}
```

##### RESPONSE
```

```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters
1021  | Cannot find rollout slot api-ga.



## <a name="list_objects"></a>List Objects

##### METHOD
      list_objects

##### DESCRIPTION
List Objects

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
path *  | Name of the folder or Shared folder.
include_children  | 1 or 0 to include or not include the subfolders and files of the root folder.
include_companies  | 1 or 0 to include or not include the companies .
max_items  | Maximum number of items.
sort_field  | On which value want to sort, e.g(time).
sort_direction  | asc or desc.
filter_extension  | Array of extension e.g([doc, docx, txt]).
include_revisions  | Include file with revision.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "list_objects",
    "params": {
        "path": "/Movies",
        "include_children": "0"
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "share_id": "0",
        "share_owner": "hidden",
        "company_id": "",
        "more_items": "0",
        "object": {
            "path": "/Movies",
            "type": "dir",
            "subtype": "dir",
            "share_id": "0",
            "company_id": null,
            "size": "0",
            "created_time": "1435731802",
            "modified_time": "1435731802",
            "permission": null,
            "revision_id": null,
            "object_id": "5",
            "immutable": 0,
            "linkable": 1,
            "share_owner": "hidden",
            "date_last_synced": "1435731802",
            "removed_time": "",
            "mime_type": "",
            "revisions": [],
            "download_url": "http://d.qa.copy.com/web/users/user-hidden/copy/Movies"
        },
        "children": [],
        "list_watermark": "0",
        "sync_watermark": "0",
        "hash": "hidden"
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters



## <a name="list_removed_objects"></a>List Removed Objects

##### METHOD
      list_removed_objects

##### DESCRIPTION
List Objects

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
path *  | Name of the folder or Shared folder.
include_child_counts  | Include the number of children in the result.
include_parts  | Include the revision parts if we listed a single file.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "list_removed_objects",
    "params": {
        "path": "/",
        "include_child_counts": true,
        "include_parts": true
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "share_id": "0",
        "share_owner": "hidden",
        "company_id": "0",
        "children": [
            {
                "path": "/Rm_Folder",
                "type": "dir",
                "subtype": "dir",
                "share_id": "0",
                "company_id": null,
                "size": "0",
                "created_time": "1435738281",
                "modified_time": "1435738281",
                "permission": null,
                "revision_id": null,
                "object_id": "8",
                "immutable": 0,
                "linkable": 1,
                "share_owner": "hidden",
                "date_last_synced": "1435738281",
                "removed_time": "1435738327",
                "mime_type": "",
                "revisions": [],
                "children_count": "0"
            }
        ]
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters



## <a name="undelete_object"></a>Undelete Object

##### METHOD
      undelete_object

##### DESCRIPTION
List Objects

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
path  | Path of removed object to undelete.
object_id  | Object id to undelete.
share_id  | Share id to undelete.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "undelete_object",
    "params": {
        "path": "/Rm_Folder"
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "path": "/Rm_Folder",
        "type": "dir",
        "subtype": "dir",
        "share_id": "0",
        "company_id": null,
        "size": "0",
        "created_time": "1435738281",
        "modified_time": "1435738281",
        "permission": null,
        "revision_id": null,
        "object_id": "8",
        "immutable": 0,
        "linkable": 1,
        "share_owner": "hidden",
        "date_last_synced": "1435738281",
        "removed_time": "",
        "mime_type": ""
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters




## <a name="list_revisions"></a>List Revisions

##### METHOD
      list_revisions

##### DESCRIPTION
Return all revision to a given path

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
path  | Path of object.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "list_revisions",
    "params": {
        "path": "/pics",
        "use_global_paths":true
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "share_id": "0",
        "share_owner": "hidden",
        "revisions": []
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters



## <a name="update_objects"></a>Update Objects

##### METHOD
      update_objects

##### DESCRIPTION
Update an object

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
path  | Path of object.
meta  | Entities to update on a object.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_objects",
    "params": {
        "meta":[
            {"action":"create",
            "object_type":"dir",
            "path":"/foo"}
            ]

    }
}

{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_objects",
    "params": {
        "meta":[
            {"action":"rename",
            "object_type":"dir",
            "path":"/foo",
             "new_path":"MegaIT"}
            ]

    }
}

{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_objects",
    "params": {
        "meta":[
            {"action":"copy",
            "object_type":"dir",
            "path":"/MegaIT",
             "new_path":"/NewPath"}
            ]

    }
}

{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_objects",
    "params": {
        "meta":[
            {"action":"remove",
            "object_type":"dir",
            "path":"/Movies"}
            ]

    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
        {
            "share_id": "0",
            "share_owner": "hidden",
            "company_id": "",
            "more_items": "0",
            "object": {
                "path": "/foo",
                "type": "dir",
                "subtype": "dir",
                "share_id": "0",
                "company_id": null,
                "size": "0",
                "created_time": "1435744493",
                "modified_time": "1435744493",
                "permission": null,
                "revision_id": null,
                "object_id": "11",
                "immutable": 0,
                "linkable": 1,
                "share_owner": "hidden",
                "date_last_synced": "1435744493",
                "removed_time": "",
                "mime_type": "",
                "revisions": [],
                "download_url": "http://develop.d.dev.copy.com/web/users/user-hidden/copy/foo",
                "thumbnail_available": "0"
            },
            "children": [],
            "list_watermark": "0",
            "sync_watermark": "0",
            "hash": "hidden"
        }
    ]
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters




## <a name="make_revision_latest"></a>Make Revision Latest

##### METHOD
      make_revision_latest

##### DESCRIPTION
Given a path and revision time of meta object promote a meta revision to latest

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
path *  | Path of object to modify.
revision_time *  | Revision time to roll back to.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "make_revision_latest",
    "params": {
        "path": "/pics",
        "revision_time": 1436260685
    }
}
```

##### RESPONSE
```

```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters.
1092  | Cannot find revision with owner 677987979 object id 9 time '1970-01-02 10:17:36'





## <a name="create_link"></a>Create Link

##### METHOD
      create_link

##### DESCRIPTION
Create a link

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
request_links  | Array of links to be requested.
path  | Path of object.

##### REQUEST
```
	{
		"id": 1,
		"jsonrpc": 2,
		"method": "create_link",
		"params": {
			"request_links": {
				"action": "Create",
				"path": "/pics/Koala.jpg"
			}
		}
	}

{
    "id": 1,
    "jsonrpc": 2,
    "method": "create_link",
    "params": {
    "request_links": [
        {
            "public": "1",
            "expire": "never",
            "token_length": 10,
            "sender_name": "John",
            "sender_email": "johnh@domain.com",
            "email_recipients": false,
            "link_name": "New Link",
            "paths": [
                "/Movies"
            ],
            "recipients": [
                {
                    "email": "johnh@domain.com",
                    "permissions": "sync"
                }
            ]
        }
    ]
}
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": [
        {
            "token": "hidden",
            "link_token": "hidden",
            "link_name": "",
            "creator": "hidden",
            "company_id": null,
            "created_time": "1435749138",
            "expire": "",
            "public": "0",
            "reference_count": "1",
            "url": "https://copy.com/hidden",
            "download_url": "https://copy.com/hidden?download=1",
            "object_count": 0
        },
        {
            "token": "hidden",
            "link_token": "hidden",
            "link_name": "",
            "creator": "hidden",
            "company_id": null,
            "created_time": "1435749138",
            "expire": "",
            "public": "0",
            "reference_count": "1",
            "url": "https://copy.com/hidden",
            "download_url": "https://copy.com/hidden?download=1",
            "object_count": 0
        }
    ]
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters



## <a name="update_link"></a>Update Link

##### METHOD
      update_link

##### DESCRIPTION
Update a Link

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
token *  | Token in response from Create Token.
recipients  | Array of emails to share the document.
email_recipients  | boolean value to email the document link.
message  | String message to appear in the message.
link_name  | Name of the shared link.
public  | Integer value to indicate public link.
sender_name  | Sender Name.
sender_email  | Sender Email.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_link",
    "params": {
      "token": "hidden",
      "recipients": ["joshh@domain.com"],
      "email_recipients": true,
      "message": "Australian Koala Message",
      "link_name": "Australian Koala Link",
      "public": 1,
      "expire": "never",
      "sender_name": "john henry",
      "sender_email": "johnh@domain.com"
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "token": "hidden",
        "link_token": "hidden",
        "link_name": "Australian Koala Link",
        "creator": "hidden",
        "company_id": null,
        "created_time": "1435900014",
        "expire": "",
        "public": "1",
        "reference_count": "1",
        "url": "http://d.qa.copy.com/hidden",
        "download_url": "http://d.qa.copy.com/hidden?download=1",
        "object_count": 1,
        "attributes": {
            "sender_name": "john henry",
            "sender_email": "johnh@domain.com"
        },
        "status": "new",
        "permissions": "read",
        "invite_time": "1435902359",
        "syncing": "0",
        "copied": "0",
        "recipient_confirmed": 1,
        "invite_creator": {
            "user_id": "hidden",
            "created_time": "1432806022",
            "email": "johnh@domain.com",
            "developer": "1",
            "emails": [
                {
                    "email": "johnh@domain.com",
                    "confirmed": "1",
                    "primary": "1"
                }
            ],
            "username": "johnh@domain.com",
            "first_name": "john",
            "last_name": "henry",
            "anonymous": "0",
            "confirmed": "1",
            "show_tour": "1"
        },
        "recipients": [
            {
                "contact_type": "user",
                "contact_id": "user-hidden",
                "contact_source": "link-hidden",
                "match_position": false,
                "matches_exactly": false,
                "matched_field": null,
                "display_name": "John Henry",
                "user_id": "hidden",
                "email": "johnh@domain.com",
                "emails": [
                    {
                        "email": "johnh@domain.com",
                        "confirmed": "1",
                        "primary": "1"
                    }
                ],
                "first_name": "John",
                "last_name": "Henry",
                "permissions": "read"
            }
        ],
        "confirmation_required": false
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters




## <a name="get_link"></a>Get Link

##### METHOD
      get_link

##### DESCRIPTION
Get Link by Token

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
link_token *  | The token which identifies the link to get.
path  | (Default:'') The link relative path to retrieve objects for.
include_recipients  | (Default:false) Whether to include link recipient information.
offset  | (Default:0) When paging through the link, the offset to start listing from.
limit  | (Default:0) When paging through the link, how many children to return.
sortby  | (Default:'path') When paging through the link, which property to sort by.
order  | (Default:'asc') When paging through the link, the order to return results.
include_total_items  | (Default:false) Returns the total number of items inside the link.
include_parent_parts  | (Default:false) Includes binary part metadata for the latest revision of the parent object.
set_link_status_viewed  | (Default:true) Changes the link status to viewed prior to retrieving the link on this function call.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "get_link",
    "params": {
        "link_token": "hidden",
        "include_recipients": false,
        "offset": null,
        "limit": null,
        "sortby": null,
        "order": null,
        "include_total_items": true,
        "include_parent_parts": false,
        "set_link_status_viewed": false,
        "path": null
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "link": {
            "token": "hidden",
            "link_token": "hidden",
            "link_name": "Australian Koala Link",
            "creator": "hidden",
            "company_id": null,
            "created_time": "1435900014",
            "expire": "",
            "public": "1",
            "reference_count": "1",
            "url": "http://d.qa.copy.com/hidden",
            "download_url": "http://d.qa.copy.com/hidden?download=1",
            "object_count": 1,
            "attributes": {
                "sender_name": "john henry",
                "sender_email": "johnh@domain.com"
            },
            "status": "new",
            "permissions": "read",
            "invite_time": "1435902359",
            "syncing": "0",
            "copied": "0",
            "recipient_confirmed": 1,
            "invite_creator": {
                "user_id": "hidden",
                "created_time": "1432806022",
                "email": "johnh@domain.com",
                "developer": "1",
                "emails": [
                    {
                        "email": "johnh@domain.com",
                        "confirmed": "1",
                        "primary": "1"
                    }
                ],
                "username": "johnh@domain.com",
                "first_name": "john",
                "last_name": "henry",
                "anonymous": "0",
                "confirmed": "1",
                "show_tour": "1"
            },
            "objects": [
                {
                    "path": "/Koala.jpg",
                    "type": "file",
                    "subtype": "file",
                    "share_id": "0",
                    "company_id": null,
                    "size": "780831",
                    "created_time": "1435742846",
                    "modified_time": "1435742846",
                    "permission": null,
                    "revision_id": "4",
                    "object_id": "10",
                    "immutable": 0,
                    "linkable": 1,
                    "share_owner": "hidden",
                    "date_last_synced": "1435742846",
                    "removed_time": "",
                    "mime_type": "image/jpeg",
                    "name": "Koala.jpg",
                    "url": "http://d.qa.copy.com/hidden/Koala.jpg",
                    "download_url": "http://d.qa.copy.com/hidden/Koala.jpg?download=1",
                    "object_available": "1",
                    "syncable": true,
                    "thumbnail_available": "1",
                    "thumbnail_original_width": "1024",
                    "thumbnail_original_height": "768",
                    "thumbnail_url": "http://d.qa.copy.com/thumbs_public/hidden/Koala.jpg"
                }
            ],
            "syncable": false,
            "total_items": 1,
            "total_size": "0"
        }
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters



## <a name="list_links"></a>List links

##### METHOD
      list_links

##### DESCRIPTION
List links

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
include_created  | (Default:true).
include_expired  | (Default:false).
include_empty  | (Default:false).
include_inbox  | (Default:false).
fetch_only_new  | (Default:false).
include_hidden  | (Default:false).
include_recipients  | (Default:false).
limit  | (Default:null).
offset  | (Default:null).
sortby  | (Default:null).
order  | (Default:null).
include_total_items  | (Default:false)
include_syncable  | (Default:false)
include_company  | (Default:false).

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "list_links",
    "params": {
        "include_created": false,
        "include_expired": false,
        "include_empty": false,
        "include_inbox": true,
        "fetch_only_new": false,
        "include_hidden": false,
        "include_recipients": false,
        "limit": "100",
        "offset": "0",
        "sortby": null,
        "order": null,
        "include_total_items": "1",
        "include_syncable": "1",
        "include_company": false
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "links": [],
        "inbox": [
            {
                "token": "hidden",
                "link_token": "hidden",
                "link_name": "Jungle",
                "creator": "hidden",
                "company_id": null,
                "created_time": "1435671449",
                "expire": "",
                "public": "0",
                "reference_count": "1",
                "url": "http://d.qa.copy.com/hidden",
                "download_url": "http://d.qa.copy.com/hidden?download=1",
                "object_count": 1,
                "status": "viewed",
                "permissions": "sync",
                "invite_time": "1435671482",
                "syncing": "0",
                "copied": "0",
                "recipient_confirmed": 1,
                "invite_creator": {
                    "user_id": "hidden",
                    "created_time": "1435579765",
                    "email": "johnh@domain.com",
                    "developer": "0",
                    "emails": [
                        {
                            "email": "johnh@domain.com",
                            "confirmed": "1",
                            "primary": "1"
                        }
                    ],
                    "username": "johnh@domain.com",
                    "first_name": "john",
                    "last_name": "henry",
                    "anonymous": "0",
                    "confirmed": "1",
                    "show_tour": "1"
                },
                "single_object": {
                    "path": "/Jungle",
                    "type": "share",
                    "subtype": "share",
                    "share_id": "hidden",
                    "company_id": null,
                    "size": "0",
                    "created_time": "1435671449",
                    "modified_time": "1435671449",
                    "permission": null,
                    "revision_id": null,
                    "object_id": "8",
                    "immutable": 0,
                    "linkable": 1,
                    "share_owner": "677987979",
                    "date_last_synced": "1435671449",
                    "removed_time": "",
                    "mime_type": ""
                },
                "syncable": true
            }
        ],
        "inbox_count": 1,
        "inbox_count_new": 0
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters




## <a name="send_link"></a>Send Link

##### METHOD
      send_link

##### DESCRIPTION
Send link to recipients

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
link_token  | The token which identifies the link to share.
recipients  | Array of Emails.
redirect_url  | Redirect URL.
message  |  Message text.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "send_link",
    "params": {
        "link_token": "hidden",
        "recipients": ["johnh@domain.com", "johnh2@domain.com"],
        "redirect_url": null,
        "message": "Please follow this Link."
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": []
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters/ User does not have access to the Link.



## <a name="sync_link"></a>Sync Link

##### METHOD
      sync_link

##### DESCRIPTION
Modify the syncing state of a link

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
link_token  | Link Token to modify.
stop_syncing  | Stop syncing the link in question.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "sync_link",
    "params": {
        "link_token": "hidden",
        "stop_syncing": false
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "token": "hidden",
        "link_token": "hidden",
        "link_name": "New Link",
        "creator": "hidden",
        "company_id": null,
        "created_time": "1435750871",
        "expire": "",
        "public": "1",
        "reference_count": "1",
        "url": "http://d.qa.copy.com/hidden",
        "download_url": "http://d.qa.copy.com/hidden?download=1",
        "object_count": 1,
        "attributes": {
            "sender_name": "John",
            "sender_email": "johnh@domain.com"
        },
        "status": "new",
        "permissions": "sync",
        "invite_time": "1435911055",
        "syncing": "1",
        "copied": "0",
        "recipient_confirmed": 1,
        "invite_creator": {
            "user_id": "hidden",
            "created_time": "1432806022",
            "email": "johnh@domain.com",
            "developer": "1",
            "emails": [
                {
                    "email": "john@domain.com",
                    "confirmed": "1",
                    "primary": "1"
                }
            ],
            "username": "johnh@domain.com",
            "first_name": "john",
            "last_name": "henry",
            "anonymous": "0",
            "confirmed": "1",
            "show_tour": "1"
        },
        "share_id": "hidden"
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters/ User does not have access to the Link.
1047  | Link is not syncable.




## <a name="update_link_user"></a>Update Link User

##### METHOD
      update_link_user

##### DESCRIPTION
Update a user on a link

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
link_token  | Token of link to modify.
sync  | Start sycing the link.
path  | Path of link

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "update_link_user",
    "params": {
        "link_token": "hidden",
        "sync": true,
        "path": ""
    }
}
```

##### RESPONSE
```

```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters/ User does not have access to the Link.
1047  | Link is not syncable.



## <a name="get_thumbnail"></a>Get Thumbnail

##### METHOD
      get_thumbnail

##### DESCRIPTION
Get a thumbnail associated with a path

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
path  | Path of file to get thumbnail of.
size  | Size of thumbnail wanted.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "get_thumbnail",
    "params": {
        "path": "/Movies",
        "size": 32
    }
}
```

##### RESPONSE
```
Thumbnail
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters.
1092  | Cannot find latest revision with owner 'owner_id' 'object_id'.



## <a name="get_thumbnails"></a>Get Thumbnails

##### METHOD
      get_thumbnails

##### DESCRIPTION
Get the description of a thumbnail at a given path

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
paths  | Path of thumbnail in question.

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "get_thumbnails",
    "params": {
        "paths": "/South-Park"
    }
}
```

##### RESPONSE
```

```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters.



## <a name="list_contacts"></a>List Contacts

##### METHOD
      list_contacts

##### DESCRIPTION
Get the description of a thumbnail at a given path

##### HTTP HEADERS
HEADER  | VALUE
------------- | -------------
X-Client-Type  | API
X-Api-Version  | 1.0
X-Authorization  | 'auth_token' received from Authenticate User

##### PARAMETERS
PARAMETER  | DESCRIPTION
------------- | -------------
filters  | Array of ('company', 'group', 'shared_to', 'shared_from', 'share').
include_users  |
include_groups |
filter_name  |
limit  |

##### REQUEST
```
{
    "id": 1,
    "jsonrpc": 2,
    "method": "list_contacts",
    "params": {
      "filters": ["share"],
        "include_users": true,
        "include_groups": true,
        "filter_name": "\*",
        "limit": 100
    }
}
```

##### RESPONSE
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "contacts": [
            {
                "contact_type": "user",
                "contact_id": "user-hidden",
                "contact_source": [
                    "share-hidden",
                    "share-hidden",
                    "share-hidden"
                ],
                "match_position": false,
                "matches_exactly": false,
                "matched_field": null,
                "display_name": "Adam Perry",
                "user_id": "hidden",
                "email": "adam@domain.com",
                "emails": [
                    {
                        "email": "adam@domain.com",
                        "confirmed": "1",
                        "primary": "1"
                    }
                ],
                "first_name": "Adam",
                "last_name": "Perry"
            },
            {
                "contact_type": "user",
                "contact_id": "user-hidden",
                "contact_source": [
                    "share-hidden",
                    "share-hidden"
                ],
                "match_position": false,
                "matches_exactly": false,
                "matched_field": null,
                "display_name": "Adam Perry",
                "user_id": "hidden",
                "email": "adam@domain.com",
                "emails": [
                    {
                        "email": "adam@domain.com",
                        "confirmed": "1",
                        "primary": "1"
                    }
                ],
                "first_name": "Adam",
                "last_name": "Perry"
            },
            {
                "contact_type": "user",
                "contact_id": "user-hidden",
                "contact_source": [
                    "share-hidden"
                ],
                "match_position": false,
                "matches_exactly": false,
                "matched_field": null,
                "display_name": "Adam Perry",
                "user_id": "hidden",
                "email": null,
                "emails": [],
                "first_name": "Adam",
                "last_name": "Perry"
            }
        ]
    }
}
```

##### ERRORS
CODE  | DESCRIPTION
------------- | -------------
1003  | Invalid method/ Missing Parameters.
