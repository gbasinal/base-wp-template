Transpiling JavaScript Code
In this guide, we will be using webpack to transpile our JavaScript code. Webpack is a powerful tool for bundling and transforming different types of assets, such as JavaScript, CSS, and images. We will be using webpack to take our modern JavaScript code, and transpile it to a version of JavaScript that is compatible with older browsers.

Prerequisites
Before we begin, make sure that you have the following installed:

Node.js
npm (Node Package Manager)
Installation
1. Install webpack and webpack-cli in your project by running npm install webpack webpack-cli --save-dev
2. Create a configuration file, named webpack.config.js at the root of your project.

///////////////////////////////////////////
webpack.config.js


const path = require('path');

module.exports = {
  entry: './wp-content/themes/base/assets/js/script.js',
  output: {
    path: path.resolve(__dirname, 'wp-content/themes/base/dist/'),
    filename: 'script.js'
  },
  module: {
    rules: [
      {
        test: /\.m?js$/,
        exclude: /(node_modules|bower_components)/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env']
          }
        }
      }
    ]
  }
};

//////////////////////////////////////////
3. In your package.json, add a new script for webpack:

//////////////////////////////////////////
package.json

"scripts": {
  "build": "webpack --watch"
}

//////////////////////////////////////////

Usage
Run the script by running the command npm run build

This configuration file tells webpack to start from the main.js file, and to output the transpiled code to a script.js file in the wp-content/themes/base/dist/ directory. The --watch flag tells webpack to watch for changes in the entry file and rebuild when changes are detected.



/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////