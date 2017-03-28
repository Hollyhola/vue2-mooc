<template>
  <div id="app">
    <h1 v-text="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
        <li v-for="item in items" 
        v-bind:class="{finish: item.isFinished}"
        v-on:click="toggleFinish(item)">
        {{item.label}}</li>
    </ul>
    <component-a myMsg="我我往往我我"
                 v-on:childTold="listenTo"></component-a>
    <p>child word: {{childWords}}</p>
  </div>
</template>

<script>
  import Store from './store.js'
  import ComponentA from './components/componentA'
export default {
  data: function() {
    return {
      title: 'this is a todo list',
      items: Store.fetch(),
      newItem: ' ',     
      childWords: ' ' 
    }
  },
  components: { ComponentA },
  watch: {
    items: {
      handler: function(val,oldval) {
        Store.save(this.items)
      },
      deep: true//必要，触发handler
    }
  },
  methods:{
    toggleFinish: function(item) {
      item.isFinished = !(item.isFinished)
    },
    addNew: function() {
      this.items.push({
        label: this.newItem,
        isFinished: false
      });
      console.log(this.newItem);
      // this,newItem= ''
    },
    listenTo: function(msg) {
      this.childWords = msg
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.finish {
background: pink;





}
</style>
