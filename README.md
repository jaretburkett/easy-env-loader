## easy-env-loader

#### Easily get variables from a .env file in Node Js

This module requires Node JS >v6.4

### Install

NPM

```bash
npm install easy-env-loader --save
```

Yarn

```bash
yarn add easy-env-loader
```

### Usage

Basic usage

```javascript
const path = require('path');
const EasyEnv = require('easy-env-loader');

const defaults = {
    ENV_CONTENT:'This is coming from defaultValues option'
};

const options = {
    envPath:path.resolve(__dirname, './.env'),
    defaultEnvPath:path.resolve(__dirname, './default.env'), // optional
    defaultValues:defaults // optional
};

const env = new EasyEnv(options);

const envConfig = env.parsed;

console.log(envConfig);

// output

// { ENV_CONTENT: 'Value from .env file}'

```

### Options

There are 3 main options that can be passed when instantiating the class.

#### defaultValues: [object] - optional

All values in `defaultValues` will be present in the `.parsed` output. They will be overwritten
if they also exist in the `defaultEnvPath` file or the `envPath` file. 

#### defaultEnvPath: [absolute path] - optional

All values in `defaultEnvPath` file will be present in the `.parsed` output. They will be overwritten
if they also exist in the `envPath` file. This file must exist if this parameter is passed.

#### envPath: [absolute path] - required

All values will be present in the `.parsed` output. The only values required to be in this
file are ones where the values have changed from the `defaultValues` or `defaultEnvPath`.
You do not need to check if this file exists, as the library will do that for you. If the file
does not exist, the default values will be used instead.

### An example

You can see more in the `example.js` file included.

Example .env file

```
# Comments that start with the # symbol are ignored

# ^ Blank Spaces are ignored

ENV_CONTENT=This is a string variable for ENV_CONTENT

# Numbers will be parsed as strings. use parseInt(VAR NAME) or parseFloat(VAR NAME) to get number as a number
NUMBER=3
```

