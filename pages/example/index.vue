<template>
    <div class="container" style="">
        文章標題： <input type="text" v-model="title"><br><br>
        文章內容：<textarea v-model="content" name="" id="" cols="30" rows="10"></textarea><br><br>
        文章圖片：<img src="https://picsum.photos/200/100">

        <post-card 
        :title="title"
        :content="content"
        :image="image"
        @changeData="changeData"
        />
    </div>
</template>

<script>
import PostCard from '@/components/PostCard'

export default {

    components: {
        PostCard,      
    },

    data(){
        return{
            title:'',
            content:'',
            image:'https://picsum.photos/200/100'
        }
    },
    methods: {
        changeData(msg){
            this.title = msg
        }
    }
}
</script>
