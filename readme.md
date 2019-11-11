
====================================================================================
Creating simple Boilerplate:

1. npm init 
2. git init
3. Create folder public and src
4. Add .gitignore to ignore node_modules and dist
5. Add index.html in public folder
6. npm install --save-dev @babel/core@7.1.0 @babel/cli@7.1.0 @babel/preset-env@7.1.0 @babel/preset-react@7.0.0
7. create .babelrc with following contents
    {
    "presets": ["@babel/env", "@babel/preset-react"]
    }
8. npm install --save-dev webpack@4.19.1 webpack-cli@3.1.1 webpack-dev-server@3.1.8 style-loader@0.23.0 css-loader@1.0.0 babel-loader@8.0.2
9. Create webpack.config.js and paste contents
10. Add react code to index.js/ App.js
11. Run using webpack-dev-server --mode development
12. npm install react-hot-loader@4.3.11

index.html file contents:
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>React Starter</title>
</head>

<body>
    <div id="root"></div>
    <noscript>
        You need to enable JavaScript to run this app.
    </noscript>
    <script src="../dist/bundle.js"></script>
</body>

</html>

webpack.config.js file contents:

const path = require("path");
const webpack = require("webpack");

module.exports = {
    entry: "./src/index.js",
    mode: "development",
    module: {
        rules: [
            {
                test: /\.(js|jsx)$/,
                exclude: /(node_modules|bower_components)/,
                loader: "babel-loader",
                options: { presets: ["@babel/env"] }
            },
            {
                test: /\.css$/,
                use: ["style-loader", "css-loader"]
            }
        ]
    },
    resolve: { extensions: ["*", ".js", ".jsx"] },
    output: {
        path: path.resolve(__dirname, "dist/"),
        publicPath: "/dist/",
        filename: "bundle.js"
    },
    devServer: {
        contentBase: path.join(__dirname, "public/"),
        port: 3000,
        publicPath: "http://localhost:3000/dist/",
        hotOnly: true
    },
    plugins: [new webpack.HotModuleReplacementPlugin()]
};

Reference: https://blog.usejournal.com/creating-a-react-app-from-scratch-f3c693b84658

====================================================================================