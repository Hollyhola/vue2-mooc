<template>
  <div id="app">
    <!--不带冒号后面是字符串，带了冒号就是数据绑定-->
    <list :page="page"></list>
    <!--<a class="button" @click="next"> GO NEXT</a>-->
    <a class="button" @click="next"> GO NEXT<span>CURRENT:{{page}}</span></a>
    <!--<div id="loader" v-show:"!finish" :transition:"up"? 'up-start': 'down-start'>
        <span>Loading</span>
    </div>-->
  </div>
</template>

<script>
import List from './components/List'
export default {
  data() {
    return {
      page:  1
    }
  },
  components: { List },
  
  methods:{
    next() {
      this.page++
    }
  }
}
</script>

<style scoped>
 .button {
    display: block;
    width: 100%;
    background: #212121;
    color: #fff;
    font-weight: bold;
    text-align: center;
    padding: 1em;
    cursor: pointer;
    text-decoration: none;
  }
  .button span {
    margin-left: 2em;
    font-size: .5rem;
    color: white
  }
</style>
