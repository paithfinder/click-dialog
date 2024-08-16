<template>
  <div id="app">
    <div id="mask" v-if="showBox">
    </div>
    <div class="box">
      <ul class="car">
        <li v-for="(item,index) in carList" :key="index" @click="openBox(item.id)">
          <carItem :name="item.name" :title="item.title"
          :content="item.content" :money="item.money" :ref="'carItem'+'id'"></carItem>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

import carItem from '@/components/car.vue'
export default {
  name: 'App',
  components:{
    carItem
  },
  data(){
    return{
      carList:[
        {id:1,name:'住宿一',title:'海滨风情别墅',content:'尽享海风轻拂，风情别墅等你来体验',money:599},
        {id:2,name:'住宿二',title:'私人海滩小屋',content:'专属海滩，私密小屋，享受独一无二的假期',money:699},
        {id:3,name:'住宿三',title:'海景露台套房',content:'露台上的海景，套房中的奢华，尽在此处',money:578},
        {id:4,name:'住宿四',title:'顶级海景豪宅',content:' 奢华至极，顶级海景豪宅，定义高端度假新标准',money:888}
      ],
      showBox:false,
      showId:null
    }
  },
  methods:{
    openBox(id){
      console.log(id)
      console.log(this.$refs)
      if(!this.showBox){
        this.showId=id
        this.$refs.carItemid[id-1].isShow = true
        this.showBox = true
        this.$nextTick(()=>{
          const mask=document.getElementById('mask')
          mask.addEventListener('click',()=>{
          this.showBox = false
          this.$refs.carItemid[this.showId-1].isShow = false
        })
        })
      }
    }
  },
  mounted(){
    // document.addEventListener('click',()=>{
    //       if(this.showBox){
    //         this.$refs.carItemid[this.showId-1].isShow = false
    //         this.showBox = false
            
    //       }else{
    //         console.log('hah')
    //         this.showBox = true
    //       }
    //     })
  },
 
}
</script>

<style>
*{
  padding:0;
  margin:0;
  list-style-type:none;

}
#app{
  width:100%;
  height:100vh;
  margin:0 auto;
  display:flex;
  justify-content: center;
  align-items: center;
  background-color: #081c1d;
}

.box{
  width:90%;
  height:90%;
  margin:0 auto;
  background-color: #053b31;
  box-shadow: 0 0 30px #0e9861;

  position:relative;
  border-radius: 1rem;
  border:2px solid #0e9861;


}
#mask{
  width:100%;
  height:100%;
  background-color: transparent;
  position:absolute;
  z-index:999;
}
.car{
  display:flex;
  flex-wrap: wrap;
  justify-content: space-between;
  width:50rem;
  height:30rem;
  background-color: rgba(18, 77, 60, 0.5);
  margin:0 auto;
  position:absolute;
  top:50%;
  left:50%;
  transform: translate(-50%,-50%);
}
.car li{
  width:25rem;
  height:15rem;
  display:flex;
  justify-content: center;
  align-items: center;
}
</style>
