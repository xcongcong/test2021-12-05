<template>
    <div class="search">
        <input type="text" placeholder="请输入姓名" v-model="searchName">
        <button @click='searcha' style="background-color:#1890ff;border:none;color:#fff">点击搜索用户名</button>&nbsp;
        <input type="text" placeholder="请输入要添加的用户名" v-model="username" v-show="isShow">&nbsp;
        <input type="text" placeholder="请输入用户年龄" v-model="userage" v-show="isShow">
        <button @click="addUser">添加用户</button>
    </div>
</template>

<script>
export default {
    name:'Search',
    data() {
        return {
            searchName:'',
            username:'',
            userage:'',
            isShow:true
        }
    },
    methods: {
        addUser(){
            console.log('web前端初级-王聪-15181765917-微信同号')
            // this.isShow =!this.isShow 
            const person = this.person
            const name = this.username
            const age = this.userage

            if(name===''||age===''){
                alert('添加不能为空')
                return 
            }
            person.unshift({name,age,id:Date.now(),})
            alert('添加成功')
        },
        searcha(){
            console.log('web前端初级-王聪-15181765917-微信同号')
            if(this.searchName===''){
                alert('姓名不能为空')
                return false
            }
            const p = this.person.filter((item)=>{
                return item.name.indexOf(this.searchName) !== -1
            })
            
            this.person = p
            this.$bus.$emit('searchuser',p)
            alert('搜索成功')
        }
    },
    mounted(){
        this.$bus.$on('user',(data) => {
            this.person = data
        })
    }
}
</script>

<style scoped>

</style>