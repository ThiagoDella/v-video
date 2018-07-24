# vue-video

> A video player wrapped as a Vue.js component

## How to use it on your project

### First of all, download it from [NPM](https://www.npmjs.com/package/@thiago.dlm/vue-video)
```bash
npm install -s @thiago.dlm/vue-video
```

### vue-video dependencies
>**vue-video** has **vue-fontawesome** as its dependency. Therefore it will be installed with this package. In order to use this component you will need to instanciate vue-fontawesome first.

### On your _main.js_ file
> **main.js**

```javascript
import { library } from '@fortawesome/fontawesome-svg-core';
import { faPlay, faPause, faExpand } from '@fortawesome/free-solid-svg-icons';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import App from './App';

library.add(faPlay, faPause, faExpand);

Vue.component('font-awesome-icon', FontAwesomeIcon);
```

### Importing into your component's code

> **Example.vue**
```html
  <template>
    <v_video :src="URL_TO_YOUR_VIDEO"/>
  </template>
```
```javascript
<script>
  import v_video from '@thiago.dlm/vue-video';

  export default {
    name: 'Portfolio',
    components: {
      v_video,
    },
  };
</script>

```

## If you want to run the code from [GitHub](https://github.com/ThiagoDella/v-video)

> This is pretty much the same for when you create a project using [vue-cli](https://vuejs.org/v2/guide/installation.html)

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
