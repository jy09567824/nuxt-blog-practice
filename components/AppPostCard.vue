<template>
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
</template>

<script>
export default {
    props: {
        posts:{
            type: Array,
            required: true
            }
        }
}
</script>
