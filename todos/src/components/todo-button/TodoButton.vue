<template>
    <div class="button-container mt-3">
        
        <div class="btn-group">
            <button type="button" class="btn" :class="active===0?'btn-primary':'btn-secondary'" @click="onBtnClick(0)">全部</button>
            <button type="button" class="btn" :class="active===1?'btn-primary':'btn-secondary'" @click="onBtnClick(1)">已完成</button>
            <button type="button" class="btn" :class="active===2?'btn-primary':'btn-secondary'" @click="onBtnClick(2)">未完成</button>


        </div>
        
    </div>
 
 </template>
 <script>
     export default{
         name:'TodoButton',
        //  声明和v-model相关的自定义事件
        emits:['update:active'],
         props:{
            // 激活项的索引值
            active:{
                type:Number,
                required:true,
                // 默认激活索引值为0的按钮（全部：0，已完成：1，未完成：2）
                default:0,
            }
         },
         methods:{
            onBtnClick(index){
                if(index===this.active) return
                // 不一致
                this.$emit('update:active',index)
            }
         }
     }
 </script>
 <style lang="less" scoped>
 .button-container{
    width: 400px;
    text-align: center;
 }
 </style>