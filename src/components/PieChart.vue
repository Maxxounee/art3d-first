<template>
<div class="wrapper">
  <div class="chart">
    <div
        @mouseover.stop="darkenColor('green')"
        @mouseleave="resetColor"
        class="chart-green"
        :class="{_chartActive: activeSegment === 'green'}"
    >
    </div>
    <div
        @mouseover="darkenColor('pink')"
        @mouseleave="resetColor"
        class="chart-pink"
        :class="{_chartActive: activeSegment === 'pink'}"
    >
    </div>
    <div
        @mouseover="darkenColor('grey')"
        @mouseleave="resetColor"
        class="chart-grey"
        :class="{_chartActive: activeSegment === 'grey'}"
    >
    </div>
  </div>
  <div class="legend">
    <div
        class="legend__text-wrapper"
        @mouseover="darkenColor('pink')"
        @mouseleave="resetColor"
    >
      <div class="legend__pink_color" :class="{_activeSquare: activeSegment === 'pink'}"></div>
      <p class="legend__pink" :class="{_activeLegendPink: activeSegment === 'pink'}">РОЗОВЫЙ СЕГМЕНТ</p>
    </div>
    <div
        class="legend__text-wrapper"
        @mouseover="darkenColor('green')"
        @mouseleave="resetColor"
    >
      <div class="legend__green_color" :class="{_activeSquare: activeSegment === 'green'}"></div>
      <p class="legend__green" :class="{_activeLegendGreen: activeSegment === 'green'}">ЗЕЛЕНЫЙ СЕГМЕНТ</p>
    </div>
    <div
        class="legend__text-wrapper"
        @mouseover="darkenColor('grey')"
        @mouseleave="resetColor"
    >
      <div class="legend__grey_color" :class="{_activeSquare: activeSegment === 'grey'}"></div>
      <p class="legend__grey" :class="{_activeLegendGrey: activeSegment === 'grey'}">СЕРЫЙ СЕГМЕНТ</p>
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
    darkenColor(color) {
      this.activeSegment = color
      },
    resetColor() {
      this.activeSegment = ''
    }
  }
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
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
  z-index: 100;
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
  filter: brightness(100%);
  transition-property: filter;
  transition-duration: 0.6s;
}

.chart-green{
  background-color: #97BB31;
  clip-path: polygon(48.75% 50%, 0% -25%, 0% 100%, 60% 100%);
}

.chart-pink{
  background-color: #FF69B4;
  clip-path: polygon(48.75% 50%, 0% -25%, 0% 0%, 100% 0%, 100% 50%);
}

.chart-grey{
  background-color: #D9D9D9;
  clip-path: polygon(48.75% 50%, 42% 100%, 100% 100%, 100% 50%);
}

._chartActive {
  filter: brightness(75%);
}

.legend__pink,
.legend__green,
.legend__grey {
  color: #D9D9D9;
  text-decoration: underline;
  text-underline-offset: 3px;
  text-decoration-color: transparent;
  user-select: none;
  transition: 0.7s;
}

._activeLegendGreen,
._activeLegendPink,
._activeLegendGrey {
  color: black;
}

._activeLegendGreen {
  text-decoration-color: #97BB31;
}

._activeLegendPink {
  text-decoration-color: #FF69B4;
}

._activeLegendGrey {
  text-decoration-color: #D9D9D9;
}

.legend__text-wrapper {
  display: flex;
  align-items: center;
  margin-bottom: 8px;
}

.legend__green_color,
.legend__pink_color,
.legend__grey_color {
  margin-right: 10px;
  width: 10px;
  height: 10px;
  transform: rotate(0deg);
  transition: 0.6s;
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

._activeSquare {
  transform: rotate(180deg);
}
</style>