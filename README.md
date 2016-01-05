# Overview #

This repo is the result of an internal project to come up up with a generic testing structure for use across client projects. It is a work-in-progress.

A basic carousel component was used as the test subject. Applying testing to a pre-existing project enables focus to be placed solely on functional testing (as a proper unit testing implementation demands a TDD/BDD approach). As such, this example focusing on [Intern][intern] and [Nightwatch][nightwatch] since they are the most developed functional testing frameworks currently available. Also, using a "[Page Object][page-object]" pattern for both sets of tests enabled abstracting away the DOM tree structure from the tests themselves.



## Install ##

[TODO]



## Usage ##

The following commands initiate their respective test framework and are defined in the [`scripts` member of the package.json](package.json#L5-L8):

**Intern**

    $ npm run intern


**Nightwatch**

    $ npm run nightwatch


Each framework runs the following tests:

  1. Load page: dynamic DOM wrapper elements should init
  2. First set of two tiles should be visible within the carousel's viewport
  3. Click "next" button: carousel should advance to the next two tiles
  4. Click fourth pagination link: carousel should advance to the fourth set of two tiles
  5. Click "next" button: carousel should advance to the third set of two tiles
  6. Update carousel options to be 3-up
  7. Click first pagination link: first set of three tiles should be visible

The actual tests exist in the following folder: `tests/functional/[framework]/index.js` and the "Page Object" files are in `tests/support/pages/[framework]/IndexPage.js`.


## Framework Pros & Cons ##


### Intern ###
  
**Pros**:
  
  - Supports unit tests                     
  - Supports different assertion libraries  
  - Robust Promises interface               
  - Good documentation                      
  - AMD support                             

**Cons**:

  - [TODO]


### Nightwatch ###

**Pros**:
  
  - Manages starting/stopping of selenium server (a killer feature)
  - Cleaner console messaging during tests
  - Much simpler synchronous interface
  - Better Page Object model
  - Supports chaining of custom methods out-of-the-box

**Cons**:

  - [TODO]



## Automated Testing Layers ##

```text              
                                  Test Cases
                                      ↓
                    ┌────────────────────────────────────┐
                    │          Testing Harness           │
Testing Framework → │                 ↓                  │
                    │          Assertion Library         │
                    └────────────────────────────────────┘
                                      ↓
                    ┌────────────────────────────────────┐
                    │      WebDriver Server/Client       │
        Selenium →  │                 ↓                  │
                    │           WebDriver API            │
                    └────────────────────────────────────┘
                                      ↓
                             OS/Browser Platform
                                      ↓
                              Code to be Tested
```


## Glossary ##

**Test Case**: The test written by a developer or a QA engineer.

**Testing Harness**: The testing framework being used; in this case, Intern or Nightwatch.

**Assertion Library**: Responsible for the logical assertions which constitute a test.

**WebDriver Server/Client**: Provides a unified interface to interacting to the WebDriver API.

**[WebDriver API][webdriver]**: The low-level browser interaction automation API which enables the programmatic control of a modern browser.

**OS/Browser Platform**: The operating system/browser combination which the code above is being tested on.

**Code to be Tested**: The development code which is the subject of testing. In the case of this repo, the carousel's JavaScript in library folder.




[intern]: http://theintern.github.io/intern/
[nightwatch]: http://nightwatchjs.org/
[webdriver]: http://www.w3.org/TR/webdriver/
[page-object]: https://theintern.github.io/intern/#page-objects
