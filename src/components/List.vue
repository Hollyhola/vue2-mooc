<template>  
    <ol>
        <li v-for="news of list">
            <p class="title">{{news.title}}</p>
            <p class="data">{{news.create_at}}</p>
            <p class="author">By: {{ news.author.loginname}}</p>
        </li>
    </ol>
</template>

<script>
    import news from '../api/news'

    export default {
        data: function() {
            return {
                list: [],
                limit: 10
            }
        },

        props: {
            page: {
                type:  Number,
                default: 1
            }
        },
        created() {
            this.get()
        },
        watch: {
            page(val) {
                this.get()
            }
        },
        methods: {
            get() {
                news.getList({
                    page: this.page,
                    limit: this.limit
                }, (err,list)=> {
                    if(err) {
                        console.log(err)
                    }else {
                        list.data.forEach((data)=> {
                            const d = new Date(data.create_at)
                            data.create_at = `${d.getFullYear()}-${d.getMonth() + 1}-${d.getDate()}`
                        })
                        //常规loadmore
                        // this.list = this.list.concat(list.data)
                        //分页数组
                        this.list = list.data
                        console.log(this.list)
                        //list是用于渲染的，第一种方法将数组拼接list里面存储的是加上前一次加载的内容，可以用console.log(this.list)感受
                    }
                })
            }
        }
    }
</script>

<style scoped>
      ol {
    margin-left: 2rem;
    list-style: outside decimal;
  }
  li {
    line-height: 1.5;
    padding: 1rem;
    border-bottom: 1px solid #b6b6b6;
  }
  .title {
    font-weight: bold;
    font-size: 1.3rem;
  }
  .date {
    font-size: .8rem;
    color: #d6d6d6;
  }
</style>