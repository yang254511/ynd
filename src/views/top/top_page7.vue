<template>
    <div class="top_page_a">
     <Topa></Topa>
     <!-- <br> -->
      <Topb :data="data"></Topb>
    </div>
</template>
<script>
import Topa from "../../components/common/top/topa7";
import Topb from "../../components/common/top/topb";
export default{
    name:"top_page",
    components:{
         Topa,
         Topb
       },
    //    props:["data"],
    data(){
        return {
            data:""
        }
    },
    methods:{
        getdata(){
            this.$axios.get(this.HOST+'/product/get_products/?start=1&end=40&f_c_id=7')
        .then((response)=>{
            //将response获得的数据进行处理
           // var data=response.data;
           // this.categoryInfo=data.data;
          console.log(response.data.data); 
         this.data=response.data.data;
         console.log(this.categoryInfo)
            //data可以是多种数据类型，通过全局变量tableData将数据传出。
        })
        .catch(function (error) {
            console.log(error);
        })
        }
    },
    created(){
       this. getdata();
    }
}
</script>
<style scoped>
 /* .top_page_a{
     background-color:whitesmoke;
 } */
</style>