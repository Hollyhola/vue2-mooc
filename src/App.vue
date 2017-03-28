<template>
  <div id="app">
    <!--<list></list>-->
    <a class="button" @click="next"> GO NEXT</a>
  </div>
</template>

<script>
// import List from './components/List'
export default {
  
  components: {  },
  
  methods:{
    next() {

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
    color: #d6
  }
</style>
