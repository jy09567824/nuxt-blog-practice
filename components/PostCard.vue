<template> 
            <div class="card col-md-4" style="float: right">
                <img :src="image" alt="">
                <div class="card-body">
                <h5 class="card-title">{{title}}</h5>
                <p class="card-text">{{content}}</p>
                <a href="#" class="btn btn-primary" @click="$emit('changeData', msg)">點我點我</a>
               </div>
            </div>
</template>
<script>
export default {
    data(){
        return{
            msg:'從子組件傳出去的資料'
        }
    },
    props: {
        title: {
            type: String,
            required: true
        },
        content: {
            type: String,
            required: true
        },
        image: {
            type: String,
            required: false
        },
        methods:{
            changeParentData(){
                this.title = '改變父組件的資料'
            }
        }                 
    }
}
</script>
