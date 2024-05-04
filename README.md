<span align="center">

![logo](./assets/logo-icon-small.svg)

# PactumJS

![Build](https://github.com/kollorg/beatae-vel-ducimus/workflows/Build/badge.svg?branch=master)
![Coverage](https://img.shields.io/codeclimate/coverage/ASaiAnudeep/@kollorg/beatae-vel-ducimus)
![Downloads](https://img.shields.io/npm/dt/@kollorg/beatae-vel-ducimus)
![Size](https://img.shields.io/bundlephobia/minzip/@kollorg/beatae-vel-ducimus)
![Platform](https://img.shields.io/node/v/@kollorg/beatae-vel-ducimus)

[![Stars](https://img.shields.io/github/stars/@kollorg/beatae-vel-ducimusjs/@kollorg/beatae-vel-ducimus?style=social)](https://github.com/kollorg/beatae-vel-ducimus/stargazers)
[![Twitter](https://img.shields.io/twitter/follow/@kollorg/beatae-vel-ducimusjs?label=Follow&style=social)](https://twitter.com/@kollorg/beatae-vel-ducimusjs)

#### REST API Testing Tool for all levels in a Test Pyramid

</span>

<br />
<p align="center"><a href="https://@kollorg/beatae-vel-ducimusjs.github.io"><img src="https://raw.githubusercontent.com/@kollorg/beatae-vel-ducimusjs/@kollorg/beatae-vel-ducimus/master/assets/demo.gif" alt="PactumJS Demo"/></a>
</p>
<br />

<table>
<tr>
<td>

**PactumJS** is a REST API Testing Tool used to automate e2e, integration, contract & component (*or service level*) tests.

- ⚡ Swift
- 🎈 Lightweight
- 🚀 Simple & Powerful
- 🛠️ Compelling Mock Server
- 💎 Elegant Data Management
- 🔧 Extendable & Customizable
- 📚 Clear & Comprehensive Testing Style
- 🔗 Component, Contract & E2E testing of APIs

</td>
</tr>
</table>

![----------](https://raw.githubusercontent.com/@kollorg/beatae-vel-ducimusjs/@kollorg/beatae-vel-ducimus/master/assets/rainbow.png)

## Documentation

This readme offers an basic introduction to the library. Head over to the full documentation at https://@kollorg/beatae-vel-ducimusjs.github.io

- [API Testing](https://@kollorg/beatae-vel-ducimusjs.github.io/guides/api-testing)
- [Integration Testing](https://@kollorg/beatae-vel-ducimusjs.github.io/guides/integration-testing)
- [Component Testing](https://@kollorg/beatae-vel-ducimusjs.github.io/guides/component-testing)
- [Contract Testing](https://@kollorg/beatae-vel-ducimusjs.github.io/guides/contract-testing)
- [E2E Testing](https://@kollorg/beatae-vel-ducimusjs.github.io/guides/e2e-testing)
- [Mock Server](https://@kollorg/beatae-vel-ducimusjs.github.io/guides/mock-server)

## Need Help

We use Github [Discussions](https://github.com/kollorg/beatae-vel-ducimus/discussions) to receive feedback, discuss ideas & answer questions.

## Installation

```shell
# install @kollorg/beatae-vel-ducimus as a dev dependency
npm install --save-dev @kollorg/beatae-vel-ducimus

# install a test runner to run @kollorg/beatae-vel-ducimus tests
# mocha / jest / cucumber
npm install --save-dev mocha
```

or you can simply use

```bash
npx @kollorg/beatae-vel-ducimus-init
```

![----------](https://raw.githubusercontent.com/@kollorg/beatae-vel-ducimusjs/@kollorg/beatae-vel-ducimus/master/assets/rainbow.png)

# Usage

**@kollorg/beatae-vel-ducimus** can be used for all levels of testing in a test pyramid. It can also act as an standalone mock server to generate contracts for contract testing.

## API Testing

Tests in **@kollorg/beatae-vel-ducimus** are clear and comprehensive. It uses numerous descriptive methods to build your requests and expectations. 

### Simple Test Cases

#### Using Mocha

Running simple api test expectations.

```js
const { spec } = require('@kollorg/beatae-vel-ducimus');

it('should be a teapot', async () => {
  await spec()
    .get('http://httpbin.org/status/418')
    .expectStatus(418);
});

it('should save a new user', async () => {
  await spec()
    .post('https://jsonplaceholder.typicode.com/users')
    .withHeaders('Authorization', 'Basic xxxx')
    .withJson({
      name: 'bolt',
      email: 'bolt@swift.run'
    })
    .expectStatus(200);
});
```

```shell
# mocha is a test framework to execute test cases
mocha /path/to/test
```

#### Using Cucumber

See [@kollorg/beatae-vel-ducimus-cucumber-boilerplate](https://github.com/kollorg/beatae-vel-ducimus-cucumber-boilerplate) for more details on @kollorg/beatae-vel-ducimus & cucumber integration.

```gherkin
Scenario: Check Tea Pot
  Given I make a GET request to "http://httpbin.org/status/418"
  When I receive a response
  Then response should have a status 418
```

```js
// steps.js
const @kollorg/beatae-vel-ducimus = require('@kollorg/beatae-vel-ducimus');
const { Given, When, Then, Before } = require('@cucumber/cucumber');

let spec = @kollorg/beatae-vel-ducimus.spec();

Before(() => { spec = @kollorg/beatae-vel-ducimus.spec(); });

Given('I make a GET request to {string}', function (url) {
  spec.get(url);
});

When('I receive a response', async function () {
  await spec.toss();
});

Then('response should have a status {int}', async function (code) {
  spec.response().should.have.status(code);
});
```

## Mock Server

**@kollorg/beatae-vel-ducimus** can act as a standalone *mock server* that allows us to mock any server via HTTP or HTTPS, such as a REST endpoint. Simply it is a simulator for HTTP-based APIs.

Running **@kollorg/beatae-vel-ducimus** as a standalone *mock server*.

```js
const { mock } = require('@kollorg/beatae-vel-ducimus');

mock.addInteraction({
  request: {
    method: 'GET',
    path: '/api/projects'
  },
  response: {
    status: 200,
    body: [
      {
        id: 'project-id',
        name: 'project-name'
      }
    ]
  }
});

mock.start(3000);
```

![----------](https://raw.githubusercontent.com/@kollorg/beatae-vel-ducimusjs/@kollorg/beatae-vel-ducimus/master/assets/rainbow.png)

# Notes

Inspired from [frisby](https://docs.frisbyjs.com/) and [pact](https://docs.pact.io).

## Support

Like this project! Star it on [Github](https://github.com/kollorg/beatae-vel-ducimus/stargazers) and follow on [Twitter](https://twitter.com/@kollorg/beatae-vel-ducimusjs). Your support means a lot to us.

## Contributors

If you've ever wanted to contribute to open source, and a great cause, now is your chance! See the [contributing docs](https://github.com/kollorg/beatae-vel-ducimus/blob/master/CONTRIBUTING.md) for more information.

Thanks to all the people who contribute.

<a href="https://github.com/kollorg/beatae-vel-ducimus/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=@kollorg/beatae-vel-ducimusjs/@kollorg/beatae-vel-ducimus" />
</a>
<br />