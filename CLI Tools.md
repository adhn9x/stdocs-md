# CLI Tools

So you've just built an awesome app, and you want to publish it for your SeaTalk users to try, using the SeaTalk Open Platform. To do so, you need to upload a**SeaTalkBundle file (.stb)**to the Open platform, which will contain all the necessary resources (js bundles, assets etc) of your RN app. Fortunately, there is a handy tool to help you do that, and it is an npm package called**'@seatalk-rn/cli'**.

# Prerequisites

1. Must have [Node.js](https://nodejs.org/en/)installed, version >= v14.x.x
2. Must have [yarn package manager](https://yarnpkg.com/)installed, version >= 1.22.x

# Usage Instructions

1. Install '@seatalk-rn/cli' as a dependency to your project

   ```javascript
   $ yarn add @seatalk-rn/cli --dev Copy
   ```
2. Run 'npx bundle-app'

   ```bash
   $ npx bundle-app Copy
   ```
3. Follow the prompts of the CLI tool。
4. Wait for bundling to finish... (Appropriate time to eat a few snacks)。
5. Done! If you have configured the setup properly, you should see your app's .stb file as a successful output in the*out*folder.

Once you have your App's .stb file, you may upload it to the SeaTalk Open Platform, and use it to release a new version of your app.

Was this document helpful?

No

Yes