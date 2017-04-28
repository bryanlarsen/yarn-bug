# yarn-bug
https://github.com/yarnpkg/yarn/issues/3005

I would expect

    yarn cache clean && rm -rf */node_modules && cd a && yarn && cd ../b && yarn && cd ../c && yarn && cd .. && find . -name progress-bar.js

and

    yarn cache clean && rm -rf */node_modules && cd b && yarn && cd ../b && yarn && cd ../a && yarn && cd .. && find . -name progress-bar.js

to produce the same results.
