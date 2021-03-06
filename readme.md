# Intro

I found that there are lots of unfamiliar terms in Webpack configuration. When I first time encounter
those terms, I read the official doc, examples, Stackoverflow, etc. I still have
no idea what they are talking about, but I am able to find a better explanation in a Youtube video.
This repository hosts video (mostly) and text explanation of a particular term in Webpack. Contribution is welcome and sorry about my English.

I realise that it is very important to know a particular term in deeper level.

# Sample Webpack config file from [here](https://github.com/mschwarzmueller/yt-webpack2-basics/blob/06-webpack-babel-scss-img-html/webpack.config.js)

```
var path = require('path');
var ExtractTextPlugin = require('extract-text-webpack-plugin');
var HtmlWebpackPlugin = require('html-webpack-plugin');
var CleanWebpackPlugin = require('clean-webpack-plugin');

var extractPlugin = new ExtractTextPlugin({
   filename: 'main.css'
});

module.exports = {
    entry: './src/js/app.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js',
        // publicPath: '/dist'
    },
    module: {
        rules: [
            {
                test: /\.js$/,
                use: [
                    {
                        loader: 'babel-loader',
                        options: {
                            presets: ['es2015']
                        }
                    }
                ]
            },
            {
                test: /\.scss$/,
                use: extractPlugin.extract({
                    use: ['css-loader', 'sass-loader']
                })
            },
            {
                test: /\.html$/,
                use: ['html-loader']
            },
            {
                test: /\.(jpg|png)$/,
                use: [
                    {
                        loader: 'file-loader',
                        options: {
                            name: '[name].[ext]',
                            outputPath: 'img/',
                            publicPath: 'img/'
                        }
                    }
                ]
            }
        ]
    },
    plugins: [
        extractPlugin,
        new HtmlWebpackPlugin({
            template: 'src/index.html'
        }),
        new CleanWebpackPlugin(['dist'])
    ]
};
```

# What is Webpack?
* [WHAT IS WEBPACK, HOW DOES IT WORK? | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=GU-2T7k9NfI)
* [Front End Center — Webpack from First Principles](https://www.youtube.com/watch?v=WQue1AN93YU)
* [THE WEBPACK CORE CONCEPTS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=8DDVr6wjJzQ)

# What is single entry point in Webpack?
* Starting point of your app.
```
const config = {
  entry: './path/to/my/entry/file.js'
};

module.exports = config;
```


# Webpack multiple entry points
* [Webpack multiple entry points - ProgrammingTIL Webpack Video Tutorial Screencast 0004](https://www.youtube.com/watch?v=_yDHz5ESgrc)
* [Webpack Config Basics - 3. Multiple entry points](https://www.youtube.com/watch?v=dt_9ttDw6lA)

# Path
* [Absolute and Relative Paths](https://www.youtube.com/watch?v=ephId3mYu9o)

# What is output?
* [Output - Changing your bundle location!](https://webpack.academy/courses/the-core-concepts/lectures/2951148)

# What is output path?
* It require absolute path. Normally it uses path.join to resolve the absolute path.
* [Output - Changing your bundle location!](https://webpack.academy/courses/the-core-concepts/lectures/2951148)

# What is output filename?
* ```/path/to/your/project/dist/bundle.js```. It writes into disk.

# What is publicPath in output?
* From my understanding is that, webpack dev server serves javascript, css etc from the ```publicPath```. Like how you define a localhost in your machine.
* [THE WEBPACK CORE CONCEPTS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=8DDVr6wjJzQ&t=977s)
. At around 6:48

# What is module?
* [THE WEBPACK CORE CONCEPTS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=8DDVr6wjJzQ). At around 7:44

# What is rule in module?
* [THE WEBPACK CORE CONCEPTS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=8DDVr6wjJzQ). At around 10:51

# What is test in rule in module?
* [THE WEBPACK CORE CONCEPTS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=8DDVr6wjJzQ). At around 11:11

# What is use in rule in module?
* [THE WEBPACK CORE CONCEPTS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=8DDVr6wjJzQ). At round 12:10

# Style loader before css loader in module
* [THE WEBPACK CORE CONCEPTS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=8DDVr6wjJzQ). At round 14:23

# What is plugin?
* [THE WEBPACK CORE CONCEPTS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=8DDVr6wjJzQ). At round 15:28

# What is extract-text-webpack-plugin?
* [Export Your CSS with the extract-text-webpack-plugin - Ep. 4](https://www.youtube.com/watch?v=-j_90uQw-Iw)
* [Webpack & CSS - 7. Extract text plugin](https://www.youtube.com/watch?v=U9pYH5ESOb8)

# What is babel loader?
* [Webpack Tutorial for Beginners #4 - Babel Loaders](https://www.youtube.com/watch?v=H_QACBSqRBE)

# What is babel?
* [https://www.youtube.com/watch?v=8vnkM8JgjpU](https://www.youtube.com/watch?v=8vnkM8JgjpU)
* [Start Coding ES6 With Babel: Introduction](https://www.youtube.com/watch?v=t8HBL17uhBo)

# What is preset?
* [What are Babel "plugins" and "presets"? (And how to use them)](https://www.fullstackreact.com/articles/what-are-babel-plugins-and-presets/)

# What is stage-0, stage-1, etc?
* [What are Babel "plugins" and "presets"? (And how to use them)](https://www.fullstackreact.com/articles/what-are-babel-plugins-and-presets/)

# ES5, ES6, ES2015, etc, confused?
* [ES5, ES6, ES2016, ES.Next: What's going on with JavaScript versioning?](https://benmccormick.org/2015/09/14/es5-es6-es2016-es-next-whats-going-on-with-javascript-versioning/)

# HTML an Image loader
* [HTML + IMAGE LOADERS | Webpack 2 Basics Tutorial](https://www.youtube.com/watch?v=CzLiXgRUt4g&t=2s)


# What is html-webpack-plugin?
* [Webpack 2 - HTML Webpack Plugin](https://www.youtube.com/watch?v=cKTDYSK0ArI)
