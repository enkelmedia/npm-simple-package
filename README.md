# NpmSimplePackage

## Gotchas about GitHub Packages
* Package name and repository needs to match.
* Scope need to be github username (or organization I guess)
* Private Package publish is not avalible on free plan
* Package.json must contain the "publishConfig"
* Consuming libraries must have the `.npmrc`-file



Publish confing for package.json
```
"publishConfig": {
"registry": "https://npm.pkg.github.com/"
}, 
```

Example-content of .npmrc-file
```
@REPLACE_WITH_USERNAME:registry=https://npm.pkg.github.com/
//npm.pkg.github.com/:_authToken=***Personal auth-token WITH READ package:read permissions***
```

**Create .npmrc-file during Github Action-run**
This was one way to "hack around" issues with the auth. But it seems to work without this.
```
- run: echo "//npm.pkg.github.com:_authToken=${{ secrets.GITHUB_TOKEN }}" > ~/.npmrc
```

## Links
* Video on how to create package https://www.youtube.com/watch?app=desktop&v=ZINPuzq62lE
* Video create project for package https://www.youtube.com/watch?v=V_5ImTOmMh0
* Video create Github Package: https://www.youtube.com/watch?v=7CNC0QBCY-Y

### Issues
https://github.com/actions/setup-node/issues/130
