<template>
<div class="container col-md-6" style="margin-top:32px">
  <div class="form-group">
    <label for="formGroupExampleInput">文章標題</label>
    <input type="text" v-model="title" class="form-control" id="formGroupExampleInput" placeholder="Example input">
  </div>
  <div class="form-group">
    <label for="formGroupExampleInput2">作者</label>
    <input type="text" v-model="author" class="form-control" id="formGroupExampleInput2" placeholder="Another input">
  </div>
  <div class="form-group">
    <label for="exampleFormControlTextarea1">文章內容</label>
    <textarea v-model="content" class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
  </div>
  <button class="btn btn-primary" @click="createPost">按我啊幹</button>
</div>
</template>

<script>
export default {
    data() {
    return {
        title: '',
        author: '',
        content: ''
        }
    },
    methods: {
        async createPost(){
            const data = await this.$axios.post('http://localhost:3008/posts/',{
                title: this.title,
                author: this.author,
                content: this.content
            })
            console.log(data);
            this.$router.push("/posts");
        }
    }
}
</script>
