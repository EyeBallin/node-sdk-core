[![Build Status](https://travis-ci.com/IBM/node-sdk-core.svg?branch=master)](https://travis-ci.com/IBM/node-sdk-core)
[![npm-version](https://img.shields.io/npm/v/ibm-cloud-sdk-core.svg)](https://www.npmjs.com/package/ibm-cloud-sdk-core)
[![codecov](https://codecov.io/gh/IBM/node-sdk-core/branch/master/graph/badge.svg)](https://codecov.io/gh/IBM/node-sdk-core)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)
[![CLA assistant](https://cla-assistant.io/readme/badge/ibm/node-sdk-core)](https://cla-assistant.io/ibm/node-sdk-core)

# node-sdk-core
This project contains the core functionality used by Node SDK's generated by the IBM OpenAPI 3 SDK Generator (`openapi-sdkgen`).
Code generated by `openapi-sdkgen` will depend on the functionality contained in this project.

## Installation
```bash
`npm install ibm-cloud-sdk-core`
```

## Usage
This package exports a single object containing a number of modules as top level properties.

Example:
```js
// this is TypeScript, since the `openapi-sdkgen` project generates TypeScript
import { BaseService } from 'ibm-cloud-sdk-core';

class YourSDK extends BaseService { ... }
```

## Authentication
This library provides a set of Authenticators used to authenticate requests from an SDK. There are authenticators for the following authentication schemes:
- No Auth
- Basic
- Bearer Token
- IAM
- CP4D

There are two ways to create an authenticator:
1. Creating an instance and providing credentials programmatically
2. Using the `getAuthenticatorFromEnvironment` function to create an authenticator from externally-provided configuration

For more information about the various authentication types and how to use them with your services, click [here](AUTHENTICATION.md).

### Examples

#### Programmatic
```js
import { IamAuthenticator } from 'ibm-cloud-sdk-core';

const authenticator = new IamAuthenticator({
  apikey: '{apikey}',
});
```

#### External configuration
```js
import { getAuthenticatorFromEnvironment } from 'ibm-cloud-sdk-core';

// env vars
// MY_SERVICE_AUTH_TYPE=iam
// MY_SERVICE_APIKEY=<apikey>
const iamAuthenticator = getAuthenticatorFromEnvironment('my-service');
```

## Logging
This package uses [debug](https://www.npmjs.com/package/debug) for logging.

- Logging is disabled by default.
- Logging has been configured to use log levels which are assumed to be numerically ascending from most important to least important.
- In order to see the log output, set the environment variable ``DEBUG`` including the desired log level.
  - ```DEBUG=ibm-cloud-sdk-core:error``` enables error logs
  - ```DEBUG=ibm-cloud-sdk-core:warning``` enables warning logs and below
  - ```DEBUG=ibm-cloud-sdk-core:info``` enables info logs and below
  - ```DEBUG=ibm-cloud-sdk-core:verbose``` enables verbose logs and below
  - ```DEBUG=ibm-cloud-sdk-core:debug``` enables debug logs and below

To see the output from all of the debugging levels you can use:

``DEBUG=ibm-cloud-sdk-core*``

The debug logger can be configured to be used for more than one library. In example, you can set a comma-separated string:

``DEBUG=ibm-cloud-sdk-core:debug,other-lib:debug``

## Issues
If you encounter an issue with this project, you are welcome to submit a [bug report](https://github.com/IBM/node-sdk-core/issues).
Before opening a new issue, please search for similar issues. It's possible that someone has already reported it.

## Tests
Run all test suites:
```bash
npm test
```

## Contributing
See [CONTRIBUTING](CONTRIBUTING.md).

## License
This library is licensed under Apache 2.0. Full license text is
available in [LICENSE](LICENSE.md).
