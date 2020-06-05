# Privacy Holder Vue.js component

Integration [privacy-holder.js](https://github.com/ihavecoke/privacy-holder) to `Vue.js`

## Usage

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

## Options

| Name             | Example                     | Comments                                                     |
| ---------------- | --------------------------- | ------------------------------------------------------------ |
| raw-value        | 13800000000                 | The raw value you  toggle privacy will be 138****0000        |
| privacy-strategy | all,phone,email,idCard,name | This option set component how to privacy value (emial=>'ih*******@163.com') |
| show-trigger     | true,false                  | This option set componet if show privacy toggle, default trigger is eye icon you can clicked |