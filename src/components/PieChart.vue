<template>
<div class="wrapper">
  <div class="chart">
    <div @mouseover.stop="darkenColor"
         @mouseleave="resetColor"
         class="chart-green"
         id="green"
    >
    </div>

    <div
        @mouseover="darkenColor"
        @mouseleave="resetColor"
        class="chart-pink"
        id="pink"
    >
    </div>

    <div
        @mouseover="darkenColor"
        @mouseleave="resetColor"
        class="chart-grey"
        id="grey"
    >
    </div>
  </div>

  <div class="legend">
    <div class="legend__text-wrapper">
      <div class="legend__pink_color"></div>
      <p class="legend__pink"
         :class="{_activePink: activeSegment === 'pink'}"
      >РОЗОВЫЙ СЕГМЕНТ</p>
    </div>

    <div class="legend__text-wrapper">
      <div class="legend__green_color"></div>
      <p class="legend__green"
         :class="{_activeGreen: activeSegment === 'green'}"
      > ЗЕЛЕНЫЙ СЕГМЕНТ</p>
    </div>



    <div class="legend__text-wrapper">
      <div class="legend__grey_color"></div>
      <p class="legend__grey"
         :class="{_activeGrey: activeSegment === 'grey'}"
      >СЕРЫЙ СЕГМЕНТ</p>
    </div>
  </div>
</div>

</template>

<script>
export default {
  data() {
    return {
      activeSegment: ''
    }
  },
  methods: {
  darkenColor(event) {
    event.target.style.filter = "brightness(80%)"
    this.activeSegment = event.target.id
    console.log(event.target.id)
  },
  resetColor(event) {
    this.activeSegment = ''
    event.target.style.filter = "none"
  }
  }
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  color: #D9D9D9;
}

.wrapper {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 0 auto;
  width: 820px;
}

.chart{
  width: 516px;
  height: 516px;
  position: relative;
  border-radius: 50%;
  overflow: hidden;
}

.chart-green,
.chart-pink,
.chart-grey {
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
}

.chart-green{
  background-color: #97BB31;
  clip-path: polygon(48.75% 50%, 0% 17%, 0% 100%, 60% 100%);
}

.chart-pink{
  background-color: #FF69B4;
  clip-path: polygon(48.75% 50%, 0% 17%, 0% 0%, 100% 0%, 100% 50%);
}

.chart-grey{
  background-color: #D9D9D9;
  position: absolute;
  clip-path: polygon(48.75% 50%, 42% 100%, 100% 100%, 100% 50%);
}

._activeGreen,
._activePink,
._activeGrey {
  color: black;
  text-decoration: underline;
}

._activeGreen {
  text-decoration-color: #97BB31;
}

._activePink {
  text-decoration-color: #FF69B4;
}

._activeGrey {
  text-decoration-color: #D9D9D9;
}

.legend__text-wrapper {
  display: flex;
  align-items: center;
}

.legend__green_color,
.legend__pink_color,
.legend__grey_color {
  margin-right: 10px;
  width: 10px;
  height: 10px;
}

.legend__green_color {
  background: #97BB31;

}

.legend__pink_color {
  background: #FF69B4;
}

.legend__grey_color {
  background: #D9D9D9;
}
</style>