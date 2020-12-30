# Learnings about React-Native-Web

## Difference between React and React Native Web

- This project uses react.js. With the React Native Web integration it allows us to use the React Native API and render HTML elements.
- React Native web uses different components like `<View><Text>Hello<Text/><View/>` and then converts them into jsx/html elements like div.
- For rendering the elements we use a different injection/entry point into the html which is further explained [here](http://necolas.github.io/react-native-web/docs/?path=/docs/guides-client-side--page).

## Installation/Setup

### CRA project with TypeScript support and react native dependencies for client side rendering

```
yarn create react-app workout-scheduler --template typescript
yarn add react-native@0.55.4 react-native-web@0.10.0 react-art@16.8.2
yarn add -D @types/react-native@0.55.4
```

### Instead of Expo for working with hooks we will use React Native cli

```
npm i -g react-native-cli
```

### Install a separate new React Native project and use specific react version for compatibility

```
npx react-native init MyApp --template react-native-template-typescript
npm i react@16.8.2 react-native@0.59.0-rc.1
```

### Converting React Native Web and React Native into a shared monorepo

- Just paste both projects into one repository under the folder packages and rename react native web to `web` and react native to `app` to make distinction easier.

## Handy TypeScript React Snippets support

- [More here](https://gist.github.com/benawad/1e9dd01994f78489306fbfd6f7b01cd3)
- Add them with SHIFT + CMD + P
- Use `rnss` snippet for creating React Style Sheets quickly above a functional react component
- Use `rh` snippet for creating React Hook Components quickly

```
{
  // Place your snippets for typescriptreact here. Each snippet is defined under a snippet name and has a prefix, body and
  // description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
  // $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the
  // same ids are connected.
  // Example:
  "Typescript React PureComponent": {
    "prefix": "rpc",
    "body": [
      "import * as React from 'react'",
      "",
      "export class $1 extends React.PureComponent {",
      "\trender() {",
      "\t\treturn ($2);",
      "}}"
    ],
    "description": "Typescript React PureComponent"
  },

  "Typescript React Function Component": {
    "prefix": "rh",
    "body": [
      "import React from 'react'",
      "",
      "interface ${TM_FILENAME_BASE}Props {",
      "$1",
      "}",
      "",
      "export const $TM_FILENAME_BASE: React.FC<${TM_FILENAME_BASE}Props> = ({$2}) => {",
      "\t\treturn ($3);",
      "}"
    ],
    "description": "Typescript React Function Component"
  },
  "React Native StyleSheet": {
    "prefix": "rnss",
    "body": [
      "import {StyleSheet} from 'react-native'",
      "const styles = StyleSheet.create({",
      "",
      "});"
    ],
    "description": "React Native StyleSheet"
  },
  "Toggle State": {
    "prefix": "tog",
    "body": ["this.setState(state => ({", "\topen: !state.open", "}));"],
    "description": "toggle state"
  },
  "console.log": {
    "prefix": "cl",
    "body": ["console.log($1)"],
    "description": "console.log"
  },
  "className={classnames()}": {
    "prefix": "cc",
    "body": ["className={classnames('$1')}"],
    "description": "tailwind react stuff"
  },
  "Apollo Query Component": {
    "prefix": "apq",
    "body": [
      "interface Props {",
      "  children: (data: QueryResult<$1, OperationVariables>) => JSX.Element;",
      "}",
      "",
      "export class $2 extends React.PureComponent<Props> {",
      "  render() {",
      "    return (",
      "     <Query<$1> query={$3}>{x => this.props.children(x)}</Query>",
      "    );",
      "  }",
      "}"
    ],
    "description": "Apollo Query Component"
  }
}
```

## Handy Shortcuts

- Import all missimg imports

```
Cursor on file
CMD/CTRL + .
Chose import all missing imports
```
