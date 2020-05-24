<template>
  <div>
    <!-- 方法2 -->
    <div class="form-group">
      <label name="name">first name</label>
      <input v-model="firstName" type="text" name="name" />
      <!-- 當fristError是ture的時候，會觸發，去抓return裡面的firstError/lastError，去判斷給出什麼回應-->
      <div v-show="firstError">this field is required</div>
    </div>
    <div class="form-group">
      <label name="name">last name</label>
      <input v-model="lastName" type="text" name="name" />
    </div>
    <!-- :disabled="!(firstName && lastName) 可以在這裡面寫一個邏輯，例如：是ture就可按送出，沒有資料是false，就無法按送出 -->
    <button :disabled="!(firstName && lastName)" @click="submit">Submit</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      firstError: false,
      lastError: false
    }
  },
  watch: {
    // 第一種寫法，這是簡寫方式
    // 新進來的值val，用watch判斷，判斷錯誤是成立的，就會顯現ture，不成立就會false
    // watch第三者觀察每個狀況，輸入值或沒有值，都會做一個觀察判斷，如果今天沒有輸入任何值，讓這個error是成立的，就會做出一些回應
    firstName(val) {
      // eslint-disable-next-line no-unneeded-ternary
      this.firstError = !val
    },
    lastName(val) {
      if (!val) {
        this.lastError = true
      } else {
        this.lastError = false
      }
    }
    // 第二種寫法
    //  firstName: function(val, oldval) {
    // if (!val) {
    //   this.firstError = true
    // } else {
    //   this.firstError = false
    // }
    // },
    // lastName: function(val, oldval) {
    //   if (!val) {
    //     this.lastError = true
    //   } else {
    //     this.lastError = false
    //   }
    // }
  },
  methods: {
    submit() {
      if (this.firstName && this.lastName) {
        // 繼續發送表單
        alert('success')
      }
    }
  }
}
</script>
