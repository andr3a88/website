+++
categories = ["code"]
comments = true
showpagemeta = true
draft = false
title = "SwiftLint"
description = "Enforce Swift style and conventions"
date = "2017-03-20T20:15:28+01:00"
showcomments = true
tags = ["swift", "swiftlint", "cleancode", "iosdev", "realm"]
slug = ""

+++

### Installation

```
brew install swiftlint
```

### Usage
Integrate SwiftLint into an Xcode scheme to get warnings and errors displayed in the IDE. Just add a new "Run Script Phase" with:

```
if which swiftlint >/dev/null; then
  swiftlint
else
  echo "warning: SwiftLint not installed, download from https://github.com/realm/SwiftLint"
fi
```

### Commands

```
$ swiftlint help
Available commands:

   autocorrect  Automatically correct warnings and errors
   help         Display general or command-specific help
   lint         Print lint warnings and errors for the Swift files in the current directory (default command)
   rules        Display the list of rules and their identifiers
   version      Display the current version of SwiftLint

```
### My configuration file (.swiftlint.yml)

```
disabled_rules: # rule identifiers to exclude from running
  - colon
  - conditional_binding_cascade
  - comma
  - control_statement
  - force_cast
  - legacy_constant
  - legacy_constructor
  - line_length
  - nesting
  - todo
  - trailing_whitespace
  - type_name
  - variable_name
  - cyclomatic_complexity

opt_in_rules: # some rules are only opt-in
  #- empty_count
  #- missing_docs

included: # paths to include during linting. `--path` is ignored if present.
  #- Folder
  #- ../Folder/Pod

excluded: # paths to ignore during linting. Takes precedence over `included`.
  - Carthage
  - Pods

# These properties are marked as error by default.
force_try: warning

file_length:
  warning: 550
  error: 1200
  
function_body_length:
  warning: 150
  error: 200
  
type_body_length:
  warning: 300
  error: 1000
  
function_parameter_count:
  warning: 10
  error: 15
```

### Repository
* [SwiftLint Github](https://github.com/realm/SwiftLint) 
