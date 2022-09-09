# "Editor of thy Text"

## Table of Contents

- [Description](#description)
- [Installation](#installation)
- [Technologies](#technologies-used)
- [Deployed Link](#link)
- [Usage](#usage)
- [User Information](#user-information)
- [Credits](#credits)
- [Questions](#questions)
- [License](#license)

## Description

A basic text editor application that can be used even when offline.

## Installation

```ruby
npm install
```

## Technologies Used

- IndexedDB
- Node
- Express
- Babel
- Webpack

## Deployed Link

[alt text](https://king-editor.herokuapp.com/)

## Usage

### Code Snippets

Configuration for the webpack.

```javascript
module.exports = () => {
  return {
    mode: "development",
    entry: {
      main: "./src/js/index.js",
      install: "./src/js/install.js",
    },
    output: {
      filename: "[name].bundle.js",
      path: path.resolve(__dirname, "dist"),
    },
    plugins: [
      new HtmlWebpackPlugin({
        template: "./index.html",
        title: "Webpack Plugin",
      }),

      new InjectManifest({
        swSrc: "./src-sw.js",
        swDest: "src-sw.js",
      }),
      new WebpackPwaManifest({
        fingerprints: false,
        inject: true,
        name: "edit-thy-text",
        short_name: "ett",
        description: "a text editor",
        background_color: "#225ca3",
        theme_color: "#225ca3",
        start_url: "/",
        publicPath: "/",
        icons: [
          {
            src: path.resolve("src/images/logo.png"),
            sizes: [96, 128, 192, 256, 384, 512],
            destination: path.join("assets", "icons"),
          },
        ],
      }),
    ],

    module: {
      rules: [
        {
          test: /\.css$/i,
          use: ["style-loader", "css-loader"],
        },
        {
          test: /\.(png|svg|jpg|jpeg|gif)$/i,
          type: "asset/resource",
        },
        {
          test: /\.m?js$/,
          exclude: /(node_modules|bower_components)/,
          use: {
            loader: "babel-loader",
            options: {
              presets: ["@babel/preset-env"],
              plugins: [
                "@babel/plugin-proposal-object-rest-spread",
                "@babel/transform-runtime",
              ],
            },
          },
        },
      ],
    },
  };
};
```

## User Information

### **Michael Wence**

[LinkedIn](https://www.linkedin.com/in/michael-wence/) |
[GitHub](https://github.com/mtwence)

## Credits

UCB - Coding Bootcamp

## Questions

If you have any questions about this repository, you can contact me at mtwence@gmail.com.

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

© 2022 Michael Wence. All Rights Reserved.
