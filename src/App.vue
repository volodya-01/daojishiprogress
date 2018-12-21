<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
   <!--  {{stu}} -->
  </div>
</template>

<script>
export default {
  name: 'App',
   /*  created(){
       this.$axios
      .post("https://www.wwtliu.com/sxtstu/blueberrypai/getIndexBanner.php")
      .then(res => {
       var resdata=res.data;
       console.log(res);
        console.log(resdata.Data);
      })
      .catch(error => {
        console.log(error.data);
      });
  } */
  data(){
    return{
      stu:[]
    }
  },
    created(){
       var WaterNum = "21312323";
      var _this = this;
       this.$axios
      .post("http://121.40.242.176:8010/Service1.svc/MyPostTest1",
       JSON.stringify(WaterNum),
       /*  {headers: {'Content-Type':'application/json;'}} */
        )
      .then(res => {
     
         console.log(res);
    
     
      })
      .catch(error => {
        console.log(error.data);
      });
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
