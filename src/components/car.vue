<template>
    <div class="wrap">
        <img src="../assets/帐篷.png" alt="" style="width:4rem;height:4rem">
        <div style="color:white">{{ name }}</div>
        <div class="dialog" v-show="isShow">
            <div class="text">
                <div style="font-weight:bold">{{name}}:{{title}}</div>
                <div>亲情价：{{ money }}元/晚</div>
                <div class="content">
                    {{ content }}
                </div>
            </div>
            <div class="move">
                <img src="../assets/旋转1.png" alt="" class="img1">
                <img src="../assets/旋转2.png" alt="" class="img2">
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'carItem',
    props: {
        name: {
            type: String,
            required: true,
            default: () => {

            }
        },
        title: {
            type: String,
            required: true,
            default: () => {

            }
        },
        content: {
            type: String,
            required: true,
            default: () => {

            }
        },
        money: {
            type: Number,
            required: true,
            default: () => {

            }
        }
    },
    data(){
        return{
            isShow:false,
        }
    },
    methods:{
     
    },
 
}
</script>

<style>
.wrap {
    text-align: center;
    position:relative;
}
.dialog{
    position:absolute;
    width:15rem;
    height:10rem;
    bottom:4rem;
    right:8rem;
    background:linear-gradient(to right,rgb(16,100,84),transparent);
    border:1px solid #1dcebe;
    border-right:none;
    border-radius:5px;
    display:flex;
    align-items: center;

}
.dialog::before{
    content: "";
    position: absolute;
    top: 40%;
    right: -20px;
    width: 20px;
    height: 2px;
    background: #26f730;
}
.dialog::after{
    content: "";
    position: absolute;
    top: 40%;
    right: -100px;
    width: 80px;
    height: 2px;
    background: repeating-linear-gradient(to right, #26F730, #26F730 2px, transparent 10px, transparent 2px);
    transform: rotate(60deg);
    transform-origin: left top;
}
.text{
    font-size:10px;
    text-align: left;
    color:white;
    padding:10px;
    box-sizing: border-box;
}

.text div{
    margin-top:1rem;
}
.content{
    background-color: #23c778;
    height:4rem;
    line-height: 1rem;
    padding:5px;
    box-sizing: border-box;
    border-radius: 5px;
}
.move{
    width:45%;
    height:5rem;
    position:relative;
}
.img2{
    width:5rem;
    height:5rem;
    position:absolute;
    top:0;
    left:0;
    animation:rotate 2s linear infinite;
}
.img1{
    width:2rem;
    height:2rem;
    line-height: 3rem;
    position:absolute;
    top:30%;
    left:32.5%;
    animation:rotate 5s reverse linear infinite;
}
@keyframes rotate{
    0%{
        transform: rotate(0)
    }
    100%{
        transform:rotate(360deg)
    }
}
</style>