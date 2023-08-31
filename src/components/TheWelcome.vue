<template>
  <div class="home">
    <div class="grid-goals">
      <h1 class="headerText">Define your goals</h1>
      <div class="div-choseyoursex">
        <p class="text-goals">I'm</p>
        <div>
          <button
            class="button-definesex"
            v-for="(button, index) in buttonsDefineYourSex"
            :key="index"
            :style="{ backgroundColor: button.selected ? '#00BD7E' : button.color }"
            @click="selectButtonSex(index)"
          >
            {{ button.label }}
          </button>
        </div>
      </div>
      <div class="div-weightgoal">
        <p class="text-goals">Weight goal</p>
        <div>
          <button
            class="button-weight"
            v-for="(button, index) in buttonsGoals"
            :key="index"
            :style="{ backgroundColor: button.selected ? '#00BD7E' : button.color }"
            @click="selectButton(index)"
          >
            {{ button.label }}
          </button>
        </div>
      </div>
      <div class="div-years">
        <p class="text-goals">I'm {{ years }} years old</p>
        <input type="range" v-model="years" min="0" max="90" step="1" class="rangeInput" />
      </div>
      <div class="div-height">
        <p class="text-goals">My height: {{ height }} cm</p>
        <input type="range" v-model="height" min="0" max="250" step="1" class="rangeInput" />
      </div>
      <div class="div-weight">
        <p class="text-goals">My weight: {{ weight }} kg</p>
        <input type="range" v-model="weight" min="0" max="200" step="1" class="rangeInput" />
      </div>
      <div class="div-button">
        <div class="button-wrapper">
          <router-link to="/goals" class="button">Define goals</router-link>
        </div>
      </div>
    </div>
    <div class="grid-macros">
      <h2 class="headerTextGoals">Your Daily Macros Goals</h2>
      <div class="container">
        <div class="circle">
          <div class="span-circle">
            <span class="total-text">Total</span>
            <span class="num-kcal">1920</span>
            <span class="kcal">KCal</span>
          </div>
        </div>
      </div>
      <div class="div-button">
        <button class="button">Progression</button>
      </div>
      <p class="macros-text">Daily macros</p>
      <div>
        <div class="carbs-container">
          <div class="protein">
            <p class="number-carbs">75g</p>
            <p>Protein</p>
          </div>
          <div class="carbs">
            <p class="number-carbs">75g</p>
            <p>Carbs</p>
          </div>
          <div class="fat">
            <p class="number-carbs">75g</p>
            <p>Fat</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Home',
  data() {
    return {
      years: 0,
      height: 0,
      weight: 0,
      buttonsDefineYourSex: [
        { label: 'Male', color: '#6A6A6A', selected: false },
        { label: 'Female', color: '#6A6A6A', selected: false }
      ],
      buttonsGoals: [
        { label: 'Lose', color: '#6A6A6A', selected: false },
        { label: 'Maintain', color: '#6A6A6A', selected: false },
        { label: 'Gain', color: '#818181', selected: false }
      ]
    }
  },
  methods: {
    selectButton(index: number) {
      this.buttonsGoals.forEach((button, i) => {
        button.selected = i === index
      })
    },
    selectButtonSex(index: number) {
      this.buttonsDefineYourSex.forEach((button, i) => {
        button.selected = i === index
      })
    }
  }
})
</script>

<style scoped>
* {
  --font-size: 24px;
}
.home {
  display: grid;
  grid-template-columns: 2fr 1fr;
  grid-template-rows: 1fr;
  grid-column-gap: 32px;
  grid-row-gap: 0px;
}

.grid-goals {
  margin-left: 64px;
  grid-area: 1 / 1 / 2 / 2;
}

.grid-macros {
  grid-area: 1 / 2 / 2 / 3;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.div-button {
  margin-top: 64px;
  display: flex;
  justify-content: center;
}

.carbs-container {
  display: flex;
  justify-content: space-evenly;
  margin-top: 24px;
}

.circle {
  width: 275px;
  height: 285px;
  border: 30px solid #00bd7e;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.span-circle {
  display: grid;
}

.total-text {
  color: #fff;
  font-size: var(--font-size);
  text-align: center;
}

.num-kcal {
  color: #00bd7e;
  font-size: 48px;
  font-weight: bold;
  text-align: center;
}

.kcal {
  color: #00bd7e;
  font-size: var(--font-size);
  text-align: center;
}

.macros-text {
  font-size: var(--font-size);
  margin-left: 50px;
  margin-top: 64px;
  color: #00bd7e;
}

.text-goals {
  font-size: var(--font-size);
}

.number-carbs {
  font-size: var(--font-size);
  font-weight: bold;
  color: #00bd7e;
  text-align: center;
}

.protein,
.carbs,
.fat {
  font-size: var(--font-size);
  background-color: #363636;
  padding: 16px;
  border-radius: 8px;
  text-align: center;
}

.div-choseyoursex,
.div-weightgoal,
.div-years,
.div-weight,
.div-height {
  margin-bottom: 32px; /* changed the size compared to the figma on desktop */
}

.rangeInput {
  width: 100%;
  height: 6px;
  appearance: none;
  background-color: #00bd7e;
  outline: none;
  border-radius: 3px;
  margin-top: 8px;
}

.selected {
  background-color: #00bd7e;
  color: #fff;
}

.button-weight,
.button-definesex {
  width: 210px;
  height: 49px;
  color: #fff;
  border-radius: 8px;
  text-align: center;
  font-size: var(--font-size);
  border: none;
}

.button-define {
  color: #fff;
  background-color: #6a6a6a;
  text-align: center;
  border-radius: 8px;
  border: none;
  height: 55px;
  width: 250px;
}

p {
  font-size: 18px;
  color: #fff;
}

.button-wrapper {
  display: flex;
}

.button {
  width: 210px;
  height: 49px;
  background-color: #00bd7e;
  color: #fff;
  border: none;
  border-radius: 8px;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: var(--font-size);
}

.button:hover {
  background-color: #008559;
}

.headerText {
  color: #fff;
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 48px;
  margin-top: 64px;
}

.headerTextGoals {
  color: #fff;
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 48px;
  margin-top: 64px;
  text-align: center;
}

input[type='range'] {
  font-size: 1.5rem;
  width: 26em;
}

input[type='range'] {
  color: #00bd7e;
  --thumb-height: 1.125em;
  --track-height: 0.125em;
  --track-color: #fff;
  --brightness-hover: 180%;
  --brightness-down: 80%;
  --clip-edges: 0.125em;
}

/* === range commons === */
input[type='range'] {
  position: relative;
  background: #fff0;
  overflow: hidden;
}

input[type='range']:active {
  cursor: grabbing;
}

input[type='range']:disabled {
  filter: grayscale(1);
  opacity: 0.3;
  cursor: not-allowed;
}

/* === WebKit specific styles === */
input[type='range'],
input[type='range']::-webkit-slider-runnable-track,
input[type='range']::-webkit-slider-thumb {
  -webkit-appearance: none;
  transition: all ease 100ms;
  height: var(--thumb-height);
}

input[type='range']::-webkit-slider-runnable-track,
input[type='range']::-webkit-slider-thumb {
  position: relative;
}

input[type='range']::-webkit-slider-thumb {
  --thumb-radius: calc((var(--thumb-height) * 0.5) - 1px);
  --clip-top: calc((var(--thumb-height) - var(--track-height)) * 0.5 - 0.5px);
  --clip-bottom: calc(var(--thumb-height) - var(--clip-top));
  --clip-further: calc(100% + 1px);
  --box-fill: calc(-100vmax - var(--thumb-width, var(--thumb-height))) 0 0 100vmax currentColor;

  width: var(--thumb-width, var(--thumb-height));
  background: linear-gradient(currentColor 0 0) scroll no-repeat left center / 50%
    calc(var(--track-height) + 1px);
  background-color: currentColor;
  box-shadow: var(--box-fill);
  border-radius: var(--thumb-width, var(--thumb-height));

  filter: brightness(100%);
  clip-path: polygon(
    100% -1px,
    var(--clip-edges) -1px,
    0 var(--clip-top),
    -100vmax var(--clip-top),
    -100vmax var(--clip-bottom),
    0 var(--clip-bottom),
    var(--clip-edges) 100%,
    var(--clip-further) var(--clip-further)
  );
}

input[type='range']:hover::-webkit-slider-thumb {
  filter: brightness(var(--brightness-hover));
  cursor: grab;
}

input[type='range']:active::-webkit-slider-thumb {
  filter: brightness(var(--brightness-down));
  cursor: grabbing;
}

input[type='range']::-webkit-slider-runnable-track {
  background: linear-gradient(var(--track-color) 0 0) scroll no-repeat center / 100%
    calc(var(--track-height) + 1px);
}

input[type='range']:disabled::-webkit-slider-thumb {
  cursor: not-allowed;
}

/* === Firefox specific styles === */
input[type='range'],
input[type='range']::-moz-range-track,
input[type='range']::-moz-range-thumb {
  appearance: none;
  transition: all ease 100ms;
  height: var(--thumb-height);
}

input[type='range']::-moz-range-track,
input[type='range']::-moz-range-thumb,
input[type='range']::-moz-range-progress {
  background: #fff0;
}

input[type='range']::-moz-range-thumb {
  background: currentColor;
  border: 0;
  width: var(--thumb-width, var(--thumb-height));
  border-radius: var(--thumb-width, var(--thumb-height));
  cursor: grab;
}

input[type='range']:active::-moz-range-thumb {
  cursor: grabbing;
}

input[type='range']::-moz-range-track {
  width: 100%;
  background: var(--track-color);
}

input[type='range']::-moz-range-progress {
  appearance: none;
  background: currentColor;
  transition-delay: 30ms;
}

input[type='range']::-moz-range-track,
input[type='range']::-moz-range-progress {
  height: calc(var(--track-height) + 1px);
  border-radius: var(--track-height);
}

input[type='range']::-moz-range-thumb,
input[type='range']::-moz-range-progress {
  filter: brightness(100%);
}

input[type='range']:hover::-moz-range-thumb,
input[type='range']:hover::-moz-range-progress {
  filter: brightness(var(--brightness-hover));
}

input[type='range']:active::-moz-range-thumb,
input[type='range']:active::-moz-range-progress {
  filter: brightness(var(--brightness-down));
}

input[type='range']:disabled::-moz-range-thumb {
  cursor: not-allowed;
}
</style>
