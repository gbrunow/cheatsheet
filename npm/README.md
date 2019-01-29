# NPM

## Create alias to NPM registry
See this [stack overflow questions](https://stackoverflow.com/questions/32633678/is-there-any-way-to-configure-multiple-registries-in-a-single-npmrc-file).

Creating an alias:
```shell
npm config set @custom_registry:registry http://reg.example.com
```
To install a package:
```shell
npm install @custom_registry/some-package
```
