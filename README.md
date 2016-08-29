# joi-browser

joi object schema validation bundled for the browser (babelified and bundled)

```bash
node: {
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
```