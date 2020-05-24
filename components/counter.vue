<template>
    <div>
        <!-- v-on:click = @click 用哪個都可 -->
        <h2> {{ fromParent }} </h2>
        <button v-on:click="plus">點我點我 {{ number }} times</button>
    </div>
</template>

<script>
export default {
    props:{
    fromParent: {
      type: String,
      default: 'default',
      required: false
      }
    },
    data(){
        return{
            number:0,
            color: 'red'
        }
    },
    methods: {
        plus(){
            //plus 發動後數值 +1
            //this.number ++
            this.$emit('counterPlus',this.color)
        }
    }
}
</script>
