# cloudformation-circleci-npm-lambda [![Build Status](https://travis-ci.org/bendrucker/cloudformation-circleci-npm-lambda.svg?branch=master)](https://travis-ci.org/bendrucker/cloudformation-circleci-npm-lambda)

> AWS Lambda handler for managing CircleCI AWS credentials


## Install

```
$ npm install --save cloudformation-circleci-npm-lambda
```


## Usage

```js
var CircleHandler = require('cloudformation-circleci-npm-lambda')

const credentialsHandler = CircleHandler(function getToken () {
  return Promise.resolve('my-npm-token')
})

exports.handler = function handler (event, context, callback) {
  npmHandler(event, context)
    .then(() => callback(null))
    .catch((err) => callback(err))
}
```

The returned handler receives event data from CloudFormation and installs an `NPM_TOKEN` environment variable on CircleCI. You are responsible for calling the handler's callback and triggering the completion of the Lambda execution. This allows you to chain other handlers into the same run.


## License

MIT © [Ben Drucker](http://bendrucker.me)
