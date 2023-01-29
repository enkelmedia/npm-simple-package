# NpmSimplePackage

## Gotchas about GitHub Packages
* Package name and repository needs to match.
* The .npmrc-file needs to be populated with the GITHUB-TOKEN (see hack below)
* Scope need to be github username (or organization I guess)
* Private Package publish is not avalible on free plan
* package.json must contain the "publishConfig"
* consuming libraries must have the `.npmrc`-file

Create .npmrc-file during Github Action-run
```
- run: echo "//npm.pkg.github.com:_authToken=${{ secrets.GITHUB_TOKEN }}" > ~/.npmrc
```

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

