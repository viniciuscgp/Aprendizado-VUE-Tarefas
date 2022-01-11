<template>
   <div :style="style" class="bar">
      <div :style="stylebar" class="barmeter"></div>
      <span class="">{{ percent }}%</span>
   </div>
</template>

<script>
   export default {
      props: {
         value: { type: Number, required: true },
         max: { type: Number, requied: true }
      },
      computed: {
         style() {
            return {
               width: "300px",
            }
         },
         ratio() {
            return (this.value / Math.max(1, this.max))
         },
         stylebar() {
            let val = 300 * this.ratio;
            if (val >= 300) val = 298;
            return {
               width: val + "px"
            }
         },
         percent() {
            return (this.ratio * 100).toFixed(0)
         }

      }
   }
</script>

<style scoped>
   .bar {
      border: 1px solid white;
      height: 30px;
      margin: 10px;
      outline: none;
      position: relative;
   }
   .bar > span {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
   }

   .barmeter {
      border: none;
      height: 100%;
      outline: none;
      background-color: blueviolet;
   }
</style>