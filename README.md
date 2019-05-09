Lost my now-tv remote and had had enough of the adverts on the mobile apps so had a quick look to find the now-tv boxes IP, found the roku docs (https://sdkdocs.roku.com/display/sdkdoc/External+Control+API#ExternalControlAPI-KeypressKeyValues) and quickly knocked up a working remote.

You will need to know the IP of the now-tv box, which you can find with nmap or by logging into your router's admin page.

# now-tv-remote

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# Change box's IP
# sed -i 's/192.168.0.2/<YOUR_BOX_IP>/' ./src/config/index.json 
sed -i '' 's/192.168.0.2/<YOUR_BOX_IP>/' ./src/config/index.json

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
