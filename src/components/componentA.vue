<template>
    <div>
        <h1>{{msg}}</h1>
        <h2>{{myMsg}}</h2>
        <button v-on:click="onClickMe">open Mouse</button>
    </div>  
    
</template>

<script>
    export default ({
        data: function() {
           return { msg: 'hello from Component A'}
        },
        props: ['myMsg'],
        methods: {
            onClickMe: function() {
                console.log(this.myMsg)
                this.$emit('childTold',this.msg)
        }
        }
    })
</script>
<style>
    h1 {
        font-size: 30px;
        color: green;
    }
</style>