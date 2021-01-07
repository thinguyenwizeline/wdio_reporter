# Running the project

1. Make sure you have Docker running.

2. In order to run Fusion, more CPUs and memory are needed. Go to Docker **Preferences** -> **Advanced** and set the following configuration:

   ```
   CPUs: 2
   Minimum Memory: 6.0 GiB
   Swap: 2.0 GiB
   ```

   After making the changes click **Apply & Restart** and wait for Docker to restart.

3. Install the Node modules :warning:

   In order to run the project you must have these versions of Node.js and NPM:

   ```
   Node.js: 10.16.3
   NPM: 6.9.0
   ```

   **Note:** The minimum versions documented in the `package.json` are the ones that Fusion containers use. For development, use the versions mentioned above.

   Once you have installed these Node and NPM versions, run the following command:

   ```
   $ npm install
   ```

4.  Create a `.env` file using as base the `.env.example` file. Ask the team for the keys and add them here.

5. Start Fusion

   ```
   $ npm run start
   ```

6. Go to [http://localhost/pf/admin](http://localhost/pf/admin)

# Project Structure

```
.
├── components
│  ├── chains
│  │  ├── {chain_name}
│  │  │  ├── __mocks__
│  │  │  │  ├── {chain_name}.mock.jsx
│  │  │  │  └── ...
│  │  │  ├── __test__
│  │  │  │  ├── {chain_name}.test.jsx
│  │  │  │  └── ...
│  │  │  └── {chain_name}-chain
│  │  │     ├── {chain_name}.jsx
│  │  │     ├── {chain_name}.proptypes.jsx
│  │  │     ├── {chain_name}.styled.jsx
│  │  │     └── ...
│  │  ├── {chain_name}.jsx
│  │  └── ...
│  ├── features
│  │  ├── {feature_name}
│  │  │  ├── __mocks__
│  │  │  │  ├── {feature_name}.mock.jsx
│  │  │  │  └── ...
│  │  │  ├── __test__
│  │  │  │  ├── {feature_name}.test.jsx
│  │  │  │  └── ...
│  │  │  ├── {feature_name}-component
│  │  │  │  ├── {feature_name}.jsx
│  │  │  │  ├── {feature_name}.proptypes.jsx
│  │  │  │  ├── {feature_name}.styled.jsx
│  │  │  │  └── ...
│  │  │  └── index.jsx
│  │  └── ...
│  ├── layouts
│  │  ├── __test__
│  │  │  ├── {layout_name}.mock.jsx
│  │  │  ├── {layout_name}.test.jsx
│  │  │  └── ...
│  │  ├── styles
│  │  │  ├── layout.scss
│  │  │  └── ...
│  │  ├── {layout_name}.jsx
│  │  └── ...
│  ├── shared-components
│  │  ├── {component_name}.jsx
│  │  └── ...
│  └── ...
└── resources
   └── fonts
   │  ├── {font_name}-{style}.otf
   │  ├── {font_name}.css
   │  └── ...
   └── svg
      └── {image_name}.svg
      └── ...
```

### Chains

- Chain components are meant to be simple wrapper elements surrounding a single group of Features.
- They can only have `features` as children.
- They are not completely necessary but it's a best practice and adds value to the PB user's experience.
- Every chain component has its own folder and shares the main index in the root folder `(components/chains/index.jsx)` where the labels are added and the chain components are exported.

### Features

- The purpose of a Feature is to be a configurable, composable markup block on your webpage that can display content fetched from your content sources (although it doesn't have to).
- Feature components, unlike other components, are stored in directories based on their "group". This is why every feature folder has a different index that adds the label and exports it.

### Layouts

- Layouts are a unique type of component within Fusion - they serve as wrappers for the body of the webpage you're building, and they can encompass all other components (except output types) that may exist on the page.
- The layout components are stored in their root folder `(components/layouts)`.

### Shared components

- Shared components are styled components that are used in multiple features.
- Shared components are not available for the PB user to use as building blocks (like features, chains or layouts)
- These are not a core functionality of Arc, this is something proposed and used by us particularly.
- The shared components are stored in their root folder `(components/shared-components)`.

# Testing

- Chains and features components have their tests in the `__test__` folder that is in the `{chain_name/feature_name}` folder.
- All the layouts components share the `__test__` folder because all the layouts must be in the root folder `(components/layouts)`.

## Unit tests

For unit tests, we use [Jest](https://jestjs.io/docs/en/getting-started). Run them with:

```
$ npm run test
```

## Code linting

To lint code, we use [ESLint](https://eslint.org/) and [Prettier](https://prettier.io/). Run them with:

```
$ npm run lint
```

# Arc Publishing Docs

Read more at [Arc Publishing Platform Docs](https://wizeline.arcpublishing.com/alc/arc-products/pagebuilder/fusion/documentation/recipes/creating-feature-pack.md#initializing-a-feature-pack)
