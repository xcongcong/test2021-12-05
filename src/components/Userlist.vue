<template>
    <div class='userlist'>
        <ul>
            <li v-for="(item,index) in users" :key='item.id' >
                姓名:{{item.name}}-----年龄:{{item.age}}
                <button @click="del(item.id, item.name,item.age)" style="background-color:#ff4d4f;border:none;color:#fff">删除该用户</button>&nbsp;
                <button @click="reviseName(item.name, item.age,index)" style="background-color:#1890ff;border:none;color:#fff">修改用户名</button>
            </li>
        </ul>
        <div v-show="isShow">
            <input type="text" placeholder="请输入修改后的名称" v-model="rname">&nbsp;
            <input type="text" placeholder="请输入修改后的性别" v-model="rage">
            <button @click="qer">确认修改</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Userlist",
    data() {
        return {
            users:[
                {name: "小明",age:18,id: "001",},
                {name: "小张",age:20,id: "002",},
                {name: "大白",age:25,id: "003",},
                {name: "小聪",age:24,id: "004",},
            ],
            isShow:false,
            rname:"ww",
            rage:'cc',
            gg:'oo1',
            ider:''
            }
        },

    mounted() {
        this.$bus.$emit('user',this.users)

        this.$bus.$on('searchuser',(data) => {
            this.users = data
        });

        
    },
    methods: {
        del(id,){
            console.log('web前端初级-王聪-15181765917-微信同号')
            const result = this.users.filter((item)=>{
                return item.id !== id
                })
            this.users = result
        },

        reviseName(a,b,c){
            this.isShow = true
            this.rname = a
            this.rage = b
            this.ider = c
        },
        qer(){
            
            this.newPrson = {name: this.rname,age:this.rage,id:this.ider ,}
            const p = this.newPrson
            this.$set(this.users,this.ider,p)
        }
    },
    
}
</script>

<style scoped >
    .userlist{
        transform: translateX(50%) translateY(10%);
        width: 50vw;
        height: 40vh;
        border: 1px solid #1890ff ;
        border-radius:1%;
        
    }
    .userlist li{
        list-style-type: none;
    }
    .userlist li:hover{
        background-color: #ddd;
    }
</style>