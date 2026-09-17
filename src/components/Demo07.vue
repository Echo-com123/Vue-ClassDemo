<template>
    <h2>用户注册</h2>
    <form action="#" method="post">
        <!-- 文本框 -->
        <fieldset>
            <legend>基本信息</legend>
            <p>
                <label for="username">用户名：</label>
                <input v-model="user.username" type="text" id="username" name="username" placeholder="请输入用户名" required>
            </p>
            <p>
                <label for="password">密码：</label>
                <input v-model="user.password" type="password" id="password" name="password" placeholder="请输入密码" required>
            </p>
            <p>
                <label for="confirmPassword">确认密码：</label>
                <input v-model="user.confirmPassword" type="password" id="confirmPassword" name="confirmPassword" placeholder="请再次输入密码" required>
            </p>
            <p>
                <label for="email">邮箱：</label>
                <input v-model="user.email" type="email" id="email" name="email" placeholder="请输入邮箱地址">
            </p>
            <p>
                <label for="phone">手机号：</label>
                <input v-model="user.phone" type="tel" id="phone" name="phone" placeholder="请输入手机号">
            </p>
        </fieldset>
        <!-- 单选框 -->
        <fieldset>
            <legend>个人信息</legend>
            <p>性别：</p>
            <p>
                <input v-model="user.gender" type="radio" id="male" name="gender" value="male">
                <label for="male">男</label>
                <input v-model="user.gender" type="radio" id="female" name="gender" value="female">
                <label for="female">女</label>
                <input v-model="user.gender" type="radio" id="secret" name="gender" value="secret">
                <label for="secret">保密</label>
            </p>
            <!-- 下拉列表 -->
            <p>
                <label for="province">所在省份：</label>
                <select v-model="province" id="province" name="province">
                    <option value="">--请选择省份--</option>
                    <option value="beijing">北京市</option>
                    <option value="shanghai">上海市</option>
                    <option value="guangdong">广东省</option>
                    <option value="zhejiang">浙江省</option>
                    <option value="jiangsu">江苏省</option>
                    <option value="sichuan">四川省</option>
                    <option value="other">其他</option>
                </select>
            </p>
            <p>
                <label for="city">所在城市：</label>
                <select v-model="user.city" id="city" name="city">
                    <option value="">--请选择城市--</option>
                    <option value="city1">城市1</option>
                    <option value="city2">城市2</option>
                    <option value="city3">城市3</option>
                    <option value="city4">城市4</option>
                </select>
            </p>
            <!-- 多选框 -->
            <p>兴趣爱好：</p>
            <p>
                <input v-model="user.hobby" type="checkbox" id="reading" name="hobby" value="reading">
                <label for="reading">阅读</label>
                <input v-model="user.hobby" type="checkbox" id="sports" name="hobby" value="sports">
                <label for="sports">运动</label>
                <input v-model="user.hobby" type="checkbox" id="music" name="hobby" value="music">
                <label for="music">音乐</label>
                <input v-model="user.hobby" type="checkbox" id="travel" name="hobby" value="travel">
                <label for="travel">旅行</label>
                <input v-model="user.hobby" type="checkbox" id="game" name="hobby" value="game">
                <label for="game">游戏</label>
                <input v-model="user.hobby" type="checkbox" id="movie" name="hobby" value="movie">
                <label for="movie">电影</label>
            </p>
        </fieldset>
        <!-- 文本域 -->
        <fieldset>
            <legend>补充信息</legend>
            <p>
                <label for="bio">个人简介：</label><br>
                <textarea v-model="user.bio" id="bio" name="bio" rows="5" cols="40" placeholder="请简单介绍一下自己..."></textarea>
            </p>
        </fieldset>
        <!-- 提交与重置按钮 -->
        <p>
            <input type="submit" value="注册">
            <input  @click="clean" type="reset" value="重置">
        </p>    
    </form>
    <div>
        {{ user }}
    </div>
</template>
<script setup>
// import { ref } from 'vue';
// const username = ref("admin")
// const password = ref("***********")
// const confirmPassword = ref("")
// const email = ref("123@qq.com")
// const phone = ref("")
// const gender = ref("male")
// const province = ref("")
// const city = ref("")
// const hobby = ref([])
// const bio = ref("")

const user = reactive({
  username: "",
  password: "",
  confirmPassword: "",
  email: "",
  phone: "",
  gender: "male",
  province: "",
  city: "",
  hobby: [],
  bio: ""
})

const clean = () => {
  user.username = ""
  user.password = ""
  user.confirmPassword = ""
  user.email = ""
  user.phone = ""
  user.gender = "male"
  user.province = ""
  user.city = ""
}

//城市选项集合，二级联动核心数据
const cityOptions = ref([])


//省份‑城市映射表
const mapData = {
  beijing: [
    {value:"bj1",label:"东城区"},
    {value:"bj2",label:"西城区"}
  ],
  shanghai: [
    {value:"sh1",label:"黄浦区"},
    {value:"sh2",label:"徐汇区"}
  ],
  guangdong: [
    {value:"gd1",label:"广州市"},
    {value:"gd2",label:"深圳市"}
  ],
  zhejiang: [
    {value:"zj1",label:"杭州市"},
    {value:"zj2",label:"宁波市"}
  ],
  jiangsu: [
    {value:"js1",label:"南京市"},
    {value:"js2",label:"苏州市"}
  ],
  sichuan: [
    {value:"sc1",label:"成都市"},
    {value:"sc2",label:"绵阳市"}
  ],
  other: [
    {value:"ot1",label:"其他城市"}
  ]
}

//省份切换触发函数
const provinceChange = ()=>{
  //切换省份之后清空已经选好的城市
  city.value = ""
  if(province.value){
    //取出对应省份的城市列表
    cityOptions.value = mapData[province.value]
  }else{
    //选择"--请选择省份--"清空城市下拉
    cityOptions.value = []
  }
}
</script>
<style scoped>


</style>
