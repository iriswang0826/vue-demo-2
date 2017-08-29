<template>
  <div>
    <ul>
      <li v-for="item in list"> {{ item.name + '-' + item.price }} </li>
    </ul>
    <a :class="className">to baidu</a>
    <a class="link-href" :class="[classA, {'red-font': hasError}]" :style="linkCss">link 2</a>
    <a v-if="isIf">条件渲染v-if</a>
    <a v-else>no data</a>
    <!-- <a v-show="!isIf">条件渲染v-show</a> -->
    <button @click="toggle">toggle</button>
    <button v-on:click="addItem">addItem</button>
    <input @keydown.enter="onKeyDown">
    <componentA @my-event="onComaMyEvent"></componentA>
    <input v-model.trim="myValue" type="text">
    {{myValue}}
    <input type="checkbox" v-model="myBox" value="apple">
    <input type="checkbox" v-model="myBox" value="banana">
    <input type="checkbox" v-model="myBox" value="pinapple">
    {{myBox}}
    <!-- <select v-model="selection">
      <option value="1">1</option>
      <option value="2">2</option>
    </select> -->
    {{selection}}
    <select v-model="selection">
      <option v-for='item in selectOption' :value="item.value">{{ item.text }}</option>
    </select>

  </div>
</template>

<script>
import componentA from './components/a'
import Vue from 'vue'
export default {
  components: {
    componentA
  },
  data () {
    return {
      selectOption: [
        {
          text: 'apple',
          value: 0
        },
        {
          text: 'banana',
          value: 1
        }
      ],
      selection: null,
      myBox: [],
      myValue: '',
      hello: '<sapn>world</sapn>',
      link: 'http://www.baidu.com',
      dataA: 12,
      // className: {
      //   'red-font': true,
      //   'blue-font': true
      // },
      className: ['red-font', 'big-font'],
      classA: 'hello',
      classB: 'world',
      hasError: false,
      linkCss: {
        'color': 'red',
        'font-size': '20px'
      },
      isIf: true,
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
  },
  methods: {
    addItem () {
      // this.list.push({
      //   name: 'pinapple',
      //   price: 55
      // })
      Vue.set(this.list, 1, {
        name: 'pinapple',
        price: 55
      })
    },
    toggle () {
      this.isIf = !this.isIf
    },
    onKeyDown () {
      console.log('on key down')
    },
    onComaMyEvent (parmfromA) {
      console.log('onComaMyEvent' + parmfromA)
    }
  }
}
</script>

<style>
html {
  height: 100%;
}
</style>
