<template>
  <br /><br />
  <div
    class="block"
    v-if="showBlock"
    :style="{ background: dyColor }"
    @click="stopTime"
  ></div>
</template>

<script>
export default {
  props: ["p_delay"],
  data() {
    return {
      showBlock: false,
      time: null,
      fire: null,
      dyColor: "#f4845f",
      cngColor:null,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.starTimer();
    }, this.p_delay);
  },

  components: {},
  methods: {
    setColor() {
      this.cngColor = setInterval(
        () => {
          let schema = "0123456789ABCDEF";
          let res = "#";
          for (let i = 0; i < 6; i++) {
            res = res + schema[Math.floor(Math.random() * 15)];
          }
          this.dyColor = res;
        }, 100)
      },
    
    starTimer() {
      this.setColor();
      this.fire = setInterval(() => {
        this.time = this.time + 10;
      }, 10);
    },
    stopTime() {
      clearInterval(this.fire);
      clearInterval(this.cngColor);
      this.$emit("ended", this.time);
    },
  },
};
</script>

<style scoped>
.block {
  height: 300px;
  width: 400px;
  margin: auto;
  color: white;
  border-radius: 10px;
  box-shadow: 0px 0px 4px 0px;
  font-weight: bold;
}
h2 {
  background: #f4845f;
}
</style>
