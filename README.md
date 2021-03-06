# Webpack 2.1 beta slowness

Demo to highlight performance regression in Webpack 2.1.0-beta.28.

- OS: Max OS X 10.10.5
- Node: v7.0.0
- Yarn: 0.17.9

### Background

When trying out Webpack 2 on a larger project I saw a severe performance
regression for consecutive development builds. These were the timings from the
larger project

*Cold cache*
Webpack 1.13.3: 15-16 seconds
Webpack 2.1.0-beta.26: 28 seconds
Webpack 2.1.0-beta.27: 27 seconds

*Warm cache*
Webpack 1: 9 seconds
Webpack 2.1.0-beta.26: 19 seconds
Webpack 2.1.0-beta.27: 18 seconds

For production builds webpkack 2 showed a ~30% speedup compared to webpack 1.

This repo holds a simple test that should similar results as the big project mentioned above.


### Running the test

Start by running
    yarn


#### Webpack 1.14.0 test

    yarn add webpack@1.x.x
    time node_modules/.bin/webpack --config webpack-v1.config.js

I get 4.1 for first build, then 2.1 seconds for consecutive builds.


#### Webpack 2.1.0-beta.28 test

    yarn add webpack@2.1.0-beta.28
    time node_modules/.bin/webpack --config webpack-v2.config.js

I get 5.1 for first build, then 4.0 seconds for consecutive builds.
