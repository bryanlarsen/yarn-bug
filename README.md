# yarn-bug

https://github.com/yarnpkg/yarn/issues/3005

Problem:

A yarn install in a package is messing with the node_modules in another
directory that has been yarn linked.

How to reproduce:

Using yarn 0.23.2, node 4 or 7.

A:

    rm -rf */node_modules
    yarn cache clean
    cd con
    yarn
    yarn link
    cd ../th
    yarn link con
    yarn
    yarn link
    cd ..
    jq .version th/node_modules/gauge/package.json

Yields "2.7.2"

B:

    cd c
    yarn link con
    yarn link th
    yarn
    cd ..
    jq .version th/node_modules/gauge/package.json

Yields "1.2.7"
