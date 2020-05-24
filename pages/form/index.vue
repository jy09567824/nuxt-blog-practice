<template>
  <div>
    <!-- 方法1 -->
    <!-- 當有東西，才會顯示error，沒有東西就不會顯示 -->
    <!-- 顯示不顯示都可以，看怎麼做 -->
    <ul v-if="errors.length">
      <!-- 需要抓error裡面資料，但methods裡面沒有一個參考可以抓取，所以要設定id，抓到哪個error id資料，msg印出來 -->
      <li v-for="error in errors" :key="error.id">{{ error.msg }}</li>
    </ul>
    <div class="form-group">
      <label name="name">first name</label>
      <input v-model="firstName" type="text" name="name" />
    </div>
    <div class="form-group">
      <label name="name">last name</label>
      <input v-model="lastName" type="text" name="name" />
    </div>
    <button @click="Sumbit">Sumbit</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      errors: []
    }
  },
  methods: {
    // 送出動作後，發生的事件
    Sumbit() {
      // if (!this.firstName || !this.lastName) {
      //   this.error = true
      // }
      // 如果沒有這個資料,會傳送到return裡面的error陣列裡面,template裡面ul v-if那邊抓出error陣列裡面資料顯示
      // 主要是如何去運用錯誤資料
      if (!this.firstName) {
        this.errors.push({ id: 1, msg: 'no frist name' })
      }
      if (!this.lastName) {
        this.errors.push({ id: 2, msg: 'no last name' })
      }
      // 資料都沒問題是===0的話，資料就可以順利送出
      if (this.errors.length === 0) {
        alert('submit successfully')
        this.firstName = ''
        this.lastName = ''
        // 繼續發送表單
      }
    }
  }
}
</script>
