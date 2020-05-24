<template>
<div class="container col-md-6" style="margin-top:32px">
  <div class="form-group">
    <label for="formGroupExampleInput">文章標題</label>
    <input type="text" v-model="post.title" class="form-control" id="formGroupExampleInput" placeholder="Example input">
  </div>
  <div class="form-group">
    <label for="formGroupExampleInput2">作者</label>
    <input type="text" v-model="post.author" class="form-control" id="formGroupExampleInput2" placeholder="Another input">
  </div>
  <div class="form-group">
    <label for="exampleFormControlTextarea1">文章內容</label>
    <textarea v-model="post.content" class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
  </div>
  <button class="btn btn-primary" @click="updatePost">送出</button>
  <button class="btn btn-secondary" @click="$router.go(-1)">取消</button>

</div>
</template>
<script>
export default {
  data() {
    return{
      post: {}
    }
  },
  async mounted(){
    const {data} = await this.$axios.get(`http://localhost:3003/posts/${this.$route.params.id}`)
    this.post = data
  },
  methods: {
    async updatePost(){
      const { data } = await this.$axios.patch(
        `http://localhost:3003/posts/${this.$route.params.id}`,
        Object.assign({},this.post)
        )
        this.$route.push("/posts")
    }
  }
}
</script>
