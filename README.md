# Privacy Holder Vue.js component

Vue component for [privacy-holder.js](https://github.com/ihavecoke/privacy-holder) 

## Install

Install via yarn 

```bash
yarn add vprivacy-holder
```

Import to your project

```javascript
// page.vue
<template>
  <VPrivacyHolder raw-value='ihavecoke'/>
</template>

<script>
    import VPrivacyHolder from "./VPrivacyHolder";
    export default{
      components:{VPrivacyHolder}
    }
</script>
```

## Component options

* **raw-value** the raw value should toggle privacy 
* **privacy-strategy** privacy strategy eg: `email`,`phone`,`name`,`all` etc. 
