```shell script
boundary auth-methods create oidc \
  -issuer "https://login.microsoftonline.com/<tenant-id>/v2.0" \
  -client-id <client-id> \
  -client-secret <secret-id> \
  -signing-algorithm RS256 \
  -api-url-prefix "http://localhost:9200" \
  -name "azuread"

boundary auth-methods change-state oidc -id amoidc_s13ZsPNpoY -state active-public

boundary scopes update -primary-auth-method-id amoidc_s13ZsPNpoY -id global

boundary authenticate oidc -auth-method-id amoidc_s13ZsPNpoY
```