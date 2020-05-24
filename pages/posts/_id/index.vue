<!-- 部落格文章範例，輸入id更改路由器網址，改變頁面顯示內容 -->
<template>
<div class=container>
  <nuxt-link :to="`${$route.params.id}/edit`" class="btn btn-primary">編輯文章</nuxt-link>
  <button class="btn btn-danger" @click="deletePost">刪除</button>
  <h1>{{ post.title }}</h1>
  <p>{{ post.author }}</p>
  <p>{{ post.content }}</p>
</div>
</template>


<script>
export default {
    data(){
        return{
            post:{}
        }
    },
    methods:{
        async getPost() {
            const post_id = this.$route.params.id
            const {data} = await this.$axios.get(`http://localhost:3003/posts/${post_id}`)
            this.post = data
        },
        async deletePost(){
          await this.$axios.delete(`http://localhost:3003/posts/${this.$route.params.id}`)
          this.$router.push('/posts')
          }
      },
      mounted(){
        this.getPost()
      }
    }
</script>

