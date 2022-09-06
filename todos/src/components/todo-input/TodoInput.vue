<template>
   <form class="form-inline" @submit.prevent="onFormSubmit">
    
    <div class="input-group mb-2 mr-sm-2">
        <!--输入框前缀  -->
        <div class="input-group-prepend">
            <div class="input-group-text">任务</div>
        </div>
        <!-- 文本输入框 -->
        <input type="text" class="form-control" placeholder="请填写任务信息" style="width:356px" v-model.trim="taskname">
        <!-- 添加按钮 -->
        <button type="submit" class="btn btn-primary">添加新任务</button>
    </div>
    
   </form>

</template>
<script>
    export default{
        name:'TodoInput',
        emits:['add'],
        data(){
            return{
                taskname:''
            }
        },
        methods:{
            onFormSubmit(){
                if(!this.taskname) return alert('任务名称不能为空')
                this.$emit('add',this.taskname)
                this.taskname=''
            }
        }
    }
</script>
<style lang="less" scoped>

</style>