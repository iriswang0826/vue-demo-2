<template>
  <div>
    <p v-text='hello'></p>
    <p v-html='hello'></p>
    {{ num + 1 }}
    {{ status ? 'success' : 'fail' }}
    <ul>
      <li v-for='(item, index) in list' :class="{odd:index % 2}">{{ item.name }} - {{ item.price }} - {{ index }}</li>
    </ul>
    <ul>
      <li v-for='value in objList'>{{value}}</li>
    </ul>
    <ul>
      <li v-for='(value, key) in objList'>{{key + value}}</li>
    </ul>
    <componentA v-for='(value, key) in objList'></componentA>
  </div>
</template>

<script>
import componentA from './components/a'
export default {
  components: {
    componentA
  },
  data () {
    return {
      hello: '<sapn>world</sapn>',
      num: 1,
      status: true,
      list: [
        {
          name: 'apple',
          price: 34
        },
        {
          name: 'banana',
          price: 56
        }
      ],
      objList: {
        name: 'apple',
        price: 34,
        color: 'red',
        weight: 14
      }
    }
  }
}
</script>

<style>
html {
  height: 100%;
}
</style>
