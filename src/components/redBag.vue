<template>
  <div class="ser_home" style="height: 10000000px">
    <ul class="red_packet" id="red_packet">
      <template v-for="(item, index) in liParams">
        <li :style="{ left: item.left, animationDuration: item.durTime, webkitAnimationDuration: item.durTime}" :class="item.cls" :data-index="index" @webkitAnimationEnd="removeDom">
          <a href="http://baidu.com">
            <!-- <i :style="{ transform: item.transforms, webkitTransform: item.transforms}"></i> -->
            <img src="../assets/rainingRedBag/hongbao.png" style="width: 100px; height: 100xp;" alt="" :style="{ transform: item.transforms, webkitTransform: item.transforms}">
          </a>
        </li>
      </template>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      liParams: [],
      timer: null,
      duration: 1000000 // 定义时间
    };
  },
  mounted() {
    this.startRedPacket();
  },
  methods: {
    /**
     * 开启动画
     */
    startRedPacket() {
      let win =
        document.documentElement.clientWidth || document.body.clientWidth;
      let left = parseInt(Math.random() * (win - 50) + 0);
      let rotate = parseInt(Math.random() * (45 - -45) - 45) + "deg"; 
      let scales = (Math.random() * (12 - 8 + 1) + 8) * 0.04; 
      let durTime = Math.random() * (15 - 1.2 + 1) + 1.2 + "s"; 
      this.liParams.push({
        left: left + "px",
        cls: "move_1",
        transforms: "rotate(" + rotate + ") scale(" + scales + ")",
        durTime: durTime
      });

      setTimeout(() => {
        // 多少时间结束
        clearTimeout(this.timer);
        return;
      }, this.duration);

      this.timer = setTimeout(() => {
        this.startRedPacket();
      }, 500);
    },
    /**
     * 回收dom节点
     */ removeDom(e) {
      let target = e.currentTarget;
      document.querySelector("#red_packet").removeChild(target);
    }
  }
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.ser_home {
  width: 100%;
  height: 100%;
  // background-color: #000;
}
.red_packet {
  display: block;
  position: relative;
  overflow: hidden;
  width: 100%;
  height: 100%;
  // i {
  //   width: 48px;
  //   height: 68px;
  //   display: block;
  //   background: 50px url("../assets/rainingRedBag/hongbao.png") no-repeat;
  //   // background-color: red;
  //   z-index: 10002;
  // }
  li {
    position: absolute;
    animation: all 3s linear;
    top: 100px;
    z-index: 1001;
    &.move_1 {
      -webkit-animation: aim_move 20s linear 1 forwards;
      animation: aim_move 20s linear 1 forwards;
    }
  }
  a {
    display: block;
  }
    @keyframes aim_move {
      0% {
        -webkit-transform: translateY();
        transform: translateY(0);
      }
      100% {
        -webkit-transform: translateY(120vh);
        transform: translateY(120vh);
      }
    }
}
</style>