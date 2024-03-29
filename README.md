# RFY.JsonApi.Authenticator
[![Code Climate](https://codeclimate.com/github/rfyio/RFY.JsonApi.Authenticator/badges/gpa.svg)](https://codeclimate.com/github/rfyio/RFY.JsonApi.Authenticator)
[![Test Coverage](https://codeclimate.com/github/rfyio/RFY.JsonApi.Authenticator/badges/coverage.svg)](https://codeclimate.com/github/rfyio/RFY.JsonApi.Authenticator/coverage)
[![Build Status](https://travis-ci.org/rfyio/RFY.JsonApi.Authenticator.svg)](https://travis-ci.org/rfyio/RFY.JsonApi.Authenticator)

This package is meant to make a TOKEN authentication possible for any request authentication attempt.

The possible responses are:

- AuthenticationSuccessfull which returns the authentication JWT token
- AuthenticationFailure which returns a message with the corresponding error code


## Getting started

To start using this package you will need to do the following steps:

To incluse this package into your TYPO3 Flow application just run:

	composer require rfy/jsonapi-authenticator

Add the below YAML to the projects `Configuration/Routes.yaml`:

```yaml
-
  name: 'Token'
  uriPattern: '<TokenSubroutes>'
  defaults:
    '@format': 'json'
  subRoutes:
    TokenSubroutes:
      package: RFY.JsonApi.Authenticator
```

By default the security features are enabled in this package by these settings:

```yaml
TYPO3:
  Flow:
    security:
      authentication:
        providers:
          'BackendProvider':
            provider: 'RFY\JsonApi\Authenticator\Security\Authentication\Provider\PersistedApiTokenProvider'
            token: 'RFY\JsonApi\Authenticator\Security\Authentication\Token\ApiToken'
            entryPoint: 'HttpBasic'
```
You of course overwrite these settings based on your wishes.
 


### Intended Features:

- Optional security params checked, like creationDate, expirationDate & IP-Address.

### References:

This implementation is requires the [Firebase JWT package](https://github.com/firebase/php-jwt).

#### Authors:
Author: Sebastiaan van Parijs (<svparijs@refactory.it>)

#### Feedback & Reviews:

Reviewer: Bastian Waidelich

License:
--------
Copyright 2015 Sebastiaan van Parijs

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.