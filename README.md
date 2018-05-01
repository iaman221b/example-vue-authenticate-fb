# test-project

> An example of using vue-authenticate plugin for Facebook login on Nuxt.js

## configuration:

1. Facebook App

    1. Go to [Facebook's Apps Page](https://developers.facebook.com/apps)
    2. Add a new App
    3. Adding product "Facebook Login", but no need to follow the quickstart guide
    4. On the left panel of the screen, go to "Settings" (the top one), then select "Basic", you will get "App Id" here.
    5. On the left panel again, go to "Products" -> "Facebook Login" -> "Settings"
    6. Set "Valid OAuth Redirect URIs" to your redirected URL e.g. `https://localhost:3443`, then click save

2. Configure the code

The configuration for "vue-authenticate" is inside `plugins/vue-authenticate.js`.

    ``` javascript
    Vue.use(VueAuthenticate, {
      baseUrl: 'https://localhost:8080', // Your backend API domain
      providers: {
        facebook: {
          clientId: '', //your Facebook App ID e.g. 12345667890
          redirectUri: 'https://localhost:3443/', // Your client app URL
          responseType: 'token',
          authorizationEndpoint: 'https://www.facebook.com/v3.0/dialog/oauth',
        }
      }
    })
    ```

    - "clientId": Change its value to Facebook App Id from step 1.4.
    - "redirectdUri": Change its value to be the same as step 1.6.
    - "responseType": set value to "token" so that Facebook will return back access toen immediately. Otherwise, Facebook will return access code, which needs another step to get access token (by sending access code with app secret).
    - "authorizationEndpoint": set to version 3.0 (default is 2.5)

## Build Setup

``` bash
# install dependencies
$ npm install # Or yarn install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, checkout the [Nuxt.js docs](https://github.com/nuxt/nuxt.js).
