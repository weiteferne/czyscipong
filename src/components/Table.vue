<template>
  <div class="background">
    <div class="test">
      <div class="table">
        <div class="ball" :style="{ bottom: yv + '%', left: xv + '%' }"></div>
        <div
          class="ball"
          :style="{
            bottom: y_axis(0.25) * 90 + 5 + '%',
            left: 0.25 * 90 + 5 + '%',
          }"
        ></div>
        <div
          class="ball"
          :style="{
            bottom: y_axis(0.75) * 90 + 5 + '%',
            left: 0.75 * 90 + 5 + '%',
          }"
        ></div>
        <div class="first"></div>
        <div class="second"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function () {
    return {
      x: 0.25,
      xv: 0,
      yv: 0,
    };
  },
  methods: {
    steper: function () {
      var vm = this;
      setInterval(function () {
        vm.x += 0.01;
        vm.xv = 5 + vm.x * 90;
        vm.yv = vm.y_axis(vm.x) * 90 + 5;
      }, 500);
    },
    y_axis: function (x) {
      return -8 * x * x + 7 * x + -1 / 2;
    },
  },
  mounted() {
    this.steper();
  },
};
</script>

<style lang="scss">
.table {
  width: 80vw;
  height: 80vh;
  background-color: #fff;
  display: flex;
  //   transform: perspective(20px) rotateX(1deg);
}
.test {
  background-color: black;
}
.ball {
  position: absolute;
  bottom: 10%;
  left: 90px;
  width: 50px;
  background: #0d3c89;
  height: 40px;
  width: 40px;
  border-radius: 100%;
  //   transform: perspective(-20px) rotateX(10deg);
}
.background {
  width: 100vw;
  height: 100vh;
  background-color: #240115;

  display: flex;
  align-items: center;
  justify-content: center;
}
.first {
  border: 13px #fff solid;
  width: 49.5%;
  background-color: #35654d;
  //   border-right: 5px double black;
}

.second {
  border: 15px #fff solid;

  width: 49.5%;
  background-color: #35654d;
}
</style>
