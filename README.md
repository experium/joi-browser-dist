# joi-browser

joi object schema validation bundled for the browser (babelified and bundled)

```bash
joi-browser.js
'use strict';

const Joi = require('joi');

module.exports = {Joi};


webpack.conf.js
module.exports = {
  entry: './src/joi-browser.js',
  output: {
    libary: 'Joi',
    libraryTarget: 'umd',
    umdNamedDefine: true,
    path: __dirname + '/dist',
    filename: 'joi-browser.js'
  },
  module: {
    loaders: [
      {
        // need to babelify joi, isemail, hoek, and topo's lib
        test: /\/node_modules\/(joi\/lib\/|isemail\/lib\/|hoek\/lib\/|topo\/lib\/)/,
        loader: 'babel'
      },
      {
        test: /\.jsx?$/,
        exclude: /node_modules/,
        loader: 'babel'
      }
    ]
  },
  node: {
    //buffer: 'empty',
    crypto: 'empty',
    net: 'empty',
    dns: 'empty',
    moment: 'empty',
    isemail: 'empty'
  },
  plugins: [
    // Since moment is now external, we can comment this out
    // but leaving it here in case we reverse that decision
    // english locale is included, exclude the rest
    new webpack.IgnorePlugin(/locale/, /moment$/)
  ],
  externals: {
    "moment": "moment"
  }
};
```