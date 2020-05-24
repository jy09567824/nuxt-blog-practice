<template>
  <section class="container">
    <div>
      <!-- 全域叫出 plugins\global-component.js 內定義的global-logo元素 -->
      <!-- 需要先從 nuxt.config.js 中啟用 global-component.js -->
      <!-- <global-logo /> -->
      <div :style="{ color : fromChildColor }"
        >
        我是父組件
        </div>
      <counter
       :fromParent="fromParent"
       @counterPlus="counterPlus"
      />
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import counter from '~/components/counter.vue'

export default {
  data(){
    return {
      fromParent: 'this is from parent',
      number: 0,
      fromChildColor: ''
    }
  },
  // 叫出logo的components --> components\logo.vue 
  components: {
    //Logo
    counter
  },
  methods: {
    counterPlus(color){
      this.fromChildColor = color
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
