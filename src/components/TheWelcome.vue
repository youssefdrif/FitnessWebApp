<template>
  <div class="home">
    <h1 class="headerText">Define your goals</h1>
    <div>
      <p>I'm</p>
      <button class="buttonSelected">Female</button>
      <button>Male</button>
    </div>
    <div>
      <p>Weight goal</p>
      <button class="buttonSelected">Lose</button>
      <button>Maintain</button>
      <button>Gain</button>
    </div>
    <div>
      <p>I'm {{ years }} years old</p>
      <input type="range" v-model="years" min="0" max="90" step="1" class="rangeInput">
    </div>
    <div>
      <p>My height : {{ height }} cm</p>
      <input type="range" v-model="height" min="0" max="250" step="1" class="rangeInput">
    </div>
    <div>
      <p>My weight : {{ weight }} kg</p>
      <input type="range" v-model="weight" min="0" max="200" step="1" class="rangeInput">
    </div>
    <div class="button-wrapper">
      <router-link to="/goals" class="button">Define goals</router-link>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Home',
  data() {
    return {
      years: 0,
      height: 0,
      weight: 0,
    };
  },
});
</script>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
}

.rangeInput {
  width: 100%;
  height: 6px;
  appearance: none;
  background-color: #00BD7E;
  outline: none;
  border-radius: 3px;
  margin-top: 8px;
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
  background-color: #00BD7E;
  color: #fff;
  border-radius: 8px;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
}

.button:hover {
  background-color: #008559;
}

.headerText{
  color: #fff;
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 48px;
}

input[type="range"] {
	font-size: 1.5rem;
	width: 12.5em;
}

input[type="range"] {
	color: #00BD7E;
	--thumb-height: 1.125em;
	--track-height: 0.125em;
	--track-color: #fff;
	--brightness-hover: 180%;
	--brightness-down: 80%;
	--clip-edges: 0.125em;
}


/* === range commons === */
input[type="range"] {
	position: relative;
	background: #fff0;
	overflow: hidden;
}

input[type="range"]:active {
	cursor: grabbing;
}

input[type="range"]:disabled {
	filter: grayscale(1);
	opacity: 0.3;
	cursor: not-allowed;
}

/* === WebKit specific styles === */
input[type="range"],
input[type="range"]::-webkit-slider-runnable-track,
input[type="range"]::-webkit-slider-thumb {
	-webkit-appearance: none;
	transition: all ease 100ms;
	height: var(--thumb-height);
}

input[type="range"]::-webkit-slider-runnable-track,
input[type="range"]::-webkit-slider-thumb {
	position: relative;
}

input[type="range"]::-webkit-slider-thumb {
	--thumb-radius: calc((var(--thumb-height) * 0.5) - 1px);
	--clip-top: calc((var(--thumb-height) - var(--track-height)) * 0.5 - 0.5px);
	--clip-bottom: calc(var(--thumb-height) - var(--clip-top));
	--clip-further: calc(100% + 1px);
	--box-fill: calc(-100vmax - var(--thumb-width, var(--thumb-height))) 0 0
		100vmax currentColor;

	width: var(--thumb-width, var(--thumb-height));
	background: linear-gradient(currentColor 0 0) scroll no-repeat left center /
		50% calc(var(--track-height) + 1px);
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

input[type="range"]:hover::-webkit-slider-thumb {
	filter: brightness(var(--brightness-hover));
	cursor: grab;
}

input[type="range"]:active::-webkit-slider-thumb {
	filter: brightness(var(--brightness-down));
	cursor: grabbing;
}

input[type="range"]::-webkit-slider-runnable-track {
	background: linear-gradient(var(--track-color) 0 0) scroll no-repeat center /
		100% calc(var(--track-height) + 1px);
}

input[type="range"]:disabled::-webkit-slider-thumb {
	cursor: not-allowed;
}

/* === Firefox specific styles === */
input[type="range"],
input[type="range"]::-moz-range-track,
input[type="range"]::-moz-range-thumb {
	appearance: none;
	transition: all ease 100ms;
	height: var(--thumb-height);
}

input[type="range"]::-moz-range-track,
input[type="range"]::-moz-range-thumb,
input[type="range"]::-moz-range-progress {
	background: #fff0;
}

input[type="range"]::-moz-range-thumb {
	background: currentColor;
	border: 0;
	width: var(--thumb-width, var(--thumb-height));
	border-radius: var(--thumb-width, var(--thumb-height));
	cursor: grab;
}

input[type="range"]:active::-moz-range-thumb {
	cursor: grabbing;
}

input[type="range"]::-moz-range-track {
	width: 100%;
	background: var(--track-color);
}

input[type="range"]::-moz-range-progress {
	appearance: none;
	background: currentColor;
	transition-delay: 30ms;
}

input[type="range"]::-moz-range-track,
input[type="range"]::-moz-range-progress {
	height: calc(var(--track-height) + 1px);
	border-radius: var(--track-height);
}

input[type="range"]::-moz-range-thumb,
input[type="range"]::-moz-range-progress {
	filter: brightness(100%);
}

input[type="range"]:hover::-moz-range-thumb,
input[type="range"]:hover::-moz-range-progress {
	filter: brightness(var(--brightness-hover));
}

input[type="range"]:active::-moz-range-thumb,
input[type="range"]:active::-moz-range-progress {
	filter: brightness(var(--brightness-down));
}

input[type="range"]:disabled::-moz-range-thumb {
	cursor: not-allowed;
}

</style>
