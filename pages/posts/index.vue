<template>
<div class="container">
    <h1>第一種方式，叫出文章列表 - blog</h1>
    <!-- 用 vue 的方法 button 新增文章 -->
    <button class="btn btn-primary" @click="$router.push('/admin')">新增文章1</button>
      <!-- 用 nuxt 的方法 新增文章 -->
    <nuxt-link to="/admin" class="btn btn-primary">新增文章2</nuxt-link>
    <br>

    <!-- 套用部落格文章版型，並抓取 資料夾_id 中的檔案內容產生文章列表 -->
    <div class="row">
        <!-- 使用迴圈方式重複顯示出近期文章，以 post. -->
         <div
            class="col-md-4"
            v-for="post in posts"
            v-bind:key="post.id"
        >
            <div class="card">
                <img src="https://picsum.photos/200/100" class="card-img-top">
               <div class="card-body">
                <h5 class="card-title">{{post.title}}</h5>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
                <!-- 字串中想要使用變數，需要使用 `` 包裹變數  -->
                <nuxt-link :to="`/posts/${post.id}`">點我啦</nuxt-link>
               </div>
            </div>
        </div>
    </div>
    <h1>第二種方式，用Components方式叫出文章列表</h1>
    <div class="container">
        <app-post-card
        :posts="posts"
        />
    </div>
</div>
</template>

<script>
import AppPostCard from '@/components/AppPostCard'
export default {
    components: {
        AppPostCard,
    },

    data() {
        return {
            posts:[]
        }
    },
    async mounted() {
      const {data} = await this.$axios.get('http://localhost:3003/posts')
      this.posts = data
    }
}
</script>

