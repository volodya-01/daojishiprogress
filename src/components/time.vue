<template>
  <div class="outbox">
        <div id="timer"></div>
      <!--   <label for="myProgress">进度条</label> -->
        <div>
          <progress id="myProgress" value="0" max="900"></progress>
          <span id="mySpan"></span>
        </div>
  </div>
</template>
<script>
export default {
  name: "Time",
  data() {
    return {
      date: ""
    };
  },

  //实例创建完成后调用，此阶段完成了数据的观测等，但尚未挂载，$el 还不可用。需要初始化处理一些数据时会比较有用
  created: function() {},
  //el挂载到实例上后调用，一般我们的第一个业务逻辑会在这里开始
  mounted: function() {
    var _this = this; //声明一个变量指向Vue实例this，保证作用域一致
    this.djs = setInterval(function() {
       var seconds = new Date().getMinutes() * 60 + new Date().getSeconds();
            var nowmin = new Date().getMinutes()
            var cycle = 15;
            var ts = ((parseInt(nowmin / 15) + 1) * 15) * 60 - seconds;
            var hh = parseInt(ts / 60 / 60 % 24, 10); //计算剩余的小时数
            var mm = parseInt(ts / 60 % 60, 10); //计算剩余的分钟数
            var ss = parseInt(ts % 60, 10); //计算剩余的秒数
            hh = checkTime(hh);
            mm = checkTime(mm);
            ss = checkTime(ss);
            document.getElementById("timer").innerHTML = hh + ":" + mm + ":" + ss;
            var myProgress = document.getElementById("myProgress");
            var mySpan = document.getElementById("mySpan");
            myProgress.value = 900 - ts;
            var value = myProgress.value;
            mySpan.innerText = value;
            value = myProgress.value;
            value += 1
            if (value == 900) {
                value = 0
            }
            function checkTime(i) {
                if (i < 10) {
                    i = "0" + i;
                }
                return i;
            }
    }, 1000);
  },
  //实例销毁之前调用。主要解绑一些使用addEventListener监听的事件等
  beforeDestroy: function() {
    if (this.djs) {
      clearInterval(this.djs); //在Vue实例销毁前，清除我们的定时器
    }
  }
};
</script>
<style  scoped>
.outbox {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 206px;
  overflow: hidden;
}


</style>




