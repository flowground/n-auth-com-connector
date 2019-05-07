# ![LOGO](logo.png) n-Auth **flow**ground Connector

## Description

A generated **flow**ground connector for the n-Auth API (version 0.0.3).

Generated from: https://api.apis.guru/v2/specs/n-auth.com/0.0.3/swagger.json<br/>
Generated at: 2019-05-07T17:43:06+03:00

## API Description

API for the server

## Authorization

Supported authorization schemes:
- API Key
## Actions

### n-Auth protocol

> Hook for the n-Auth protocol handler

*Tags:* `n-Auth Protocol`

### Create a new server

> Create a new server. Required permission 'createserver'

*Tags:* `Servers`

#### Input Parameters
* `servername` - _required_ - Name for the server
* `owner` - _required_ - Owner id
* `pinEnabled` - _optional_ - PIN protection enabled

### Configuration of specific server

> Returns the configuration of a specific server.<br/>
> Required permission: 'servers' or 'createserver'

*Tags:* `Servers`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id

### Update configuration of specific server

> Update the configuration of a specific server.<br/>
> Required permission: 'createserver'

*Tags:* `Servers`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `serverName` - _optional_ - server name
* `pinTimeout` - _optional_ - time (minutes) since the last time the user entered his PIN, that the user is not requested a PIN at login.
* `pinTransTimeout` - _optional_ - time (minutes) since the last time the user entered his PIN, that the user is not requested a PIN at transaction approval.
* `pingTime` - _optional_ - time (seconds) that the n-Auth app has to reply to a ping request from the n-Auth server (continious authentication).
* `serverFlags` - _optional_ - server flags

### Delete specific account

> Delete an account. Required permission 'accounts'

*Tags:* `Users`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `accountid` - _required_ - Accountid

### Get specific account. Required permission 'sessions' or 'accounts'

> Returns the account

*Tags:* `Users`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `accountid` - _required_ - Accountid

### Update specific account

> Update an account. The only available change is (un)blocking the account. Required permission 'accounts'

*Tags:* `Users`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `accountid` - _required_ - Accountid
* `blocked` - _required_ - True if the account is blocked

### Provoke a login

> Provoke a login in the n-Auth app on the given session. Required permission 'sessions' or 'accounts'

*Tags:* `Basic Login/logout`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `nonce` - _required_ - Base64 encoded nonce to identify the browser/webserver session
* `accountid` - _required_ - Accountid

### Check if the user is logged in

> Based on the browser/webserver session identifier, check if the user is logged in and return the associated username. The n-Auth server can handle multiple realms in which a user can separately be registrated. This also returns additional information: the data for a login visual (qr/nauth) code and whether or not a loggin can be provoked directly from the server. <br/>
> Required permission: 'sessions'

*Tags:* `Basic Login/logout`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `nonce` - _required_ - Base64 encoded nonce to identify the browser/webserver session
* `realm` - _optional_ - Realm for the user registeration.

### Force a logout on the given session

> Force a logout on the given session<br/>
> <br/>
> Required permission: 'sessions'

*Tags:* `Basic Login/logout`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `nonce` - _required_ - Base64 encoded nonce to identify the browser/webserver session

### Provoke a login

> Provoke a login in the n-Auth app on the given session. Required permission: 'sessions'

*Tags:* `Basic Login/logout`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `nonce` - _required_ - Base64 encoded nonce to identify the browser/webserver session

### Generate data for a qr code

> Returns the data for a n-auth or qr code.<br/>
> Required permission: 'sessions'

*Tags:* `Basic Login/logout`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `type` - _required_ - ENROL or LOGIN
* `nonce` - _required_ - Base64 encoded nonce to identify the browser/webserver session
* `img` - _optional_ - Type of image to show (currently 'nauth' and 'qr' are supported, format is PNG). If not set, the raw data encoded in the image will be returned.
* `name` - _optional_ - Only for ENROL, name to forward to the n-Auth app for this account.
* `userid` - _optional_ - Only for ENROL, userid to register this user under.
* `realm` - _optional_ - Only for ENROL (and if userid is set), realm of the userid

### Register a userid for the given realm.

> Register a user (under a certain realm) for the currently logged in user. You can also directly pass a userid when generating an ENROL qr code. Required permission 'users'

*Tags:* `Users`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `nonce` - _required_ - Base64 encoded nonce to identify the browser/webserver session
* `userid` - _required_ - Userid to register
* `realm` - _optional_ - Realm for the user registeration.

### Get all users

> Returns an array of arrays containing all accounts corresponding to all users<br/>
> Required permission: 'users'

*Tags:* `Users`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `realm` - _optional_ - Only for ENROL (and if userid is set), realm of the userid

### Get specific user

> Returns an array containing all accounts corresponding to this user<br/>
> Required permission: 'sessions' or 'users'

*Tags:* `Users`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `realm` - _optional_ - realm of the userid
* `userid` - _required_ - Userid

### Provoke a login

> Provoke a login in the n-Auth app on the given session. Required permission 'users' or 'sessions'

*Tags:* `Basic Login/logout`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id
* `nonce` - _required_ - Base64 encoded nonce to identify the browser/webserver session
* `realm` - _optional_ - realm of the userid
* `userid` - _required_ - Userid

### Visual hash of this server

> Returns a PNG of the visual hash corresponding to this server. Required permission 'sessions' or 'servers'

*Tags:* `Servers`

#### Input Parameters
* `server` - _required_ - Base64 encoded server id

## License

**flow**ground :- Telekom iPaaS / n-auth-com-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
