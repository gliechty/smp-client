<template>
  <div class="block">
    <div class="title">{{title}}</div>

    <div class="slidecontainer">
      <input
        class="slider"
        type="range"
        :min="min"
        :max="max"
        :step="step"
        @input="setValueByPath({ path, value: $event.target.value})"
      />
      <label>
        <span v-if="unitSymbol !== '%'">
          {{unitSymbol}}
        </span>
        {{value}}
        <span v-if="unitSymbol === '%'">
          {{unitSymbol}}
        </span>
      </label>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  props: ['title', 'path', 'min', 'max', 'step', 'value', 'unitSymbol'],
  methods: {
    ...mapActions(['setValueByPath'])
  }
}
</script>

<style scoped>
.slidecontainer {
  width: 100%; /* Width of the outside container */
}

.slidecontainer label {
  float: left;
  position: relative;
  top: -2em;
  left: 1em;
  font-size: 1.33em;
  font-weight: 300;
}

.slidecontainer label span {
  font-size: .6em;
  vertical-align: text-bottom;
}

/* The slider itself */
.slider {
    -webkit-appearance: none;  /* Override default CSS styles */
    appearance: none;
    width: 100%; /* Full-width */
    height: 4em; /* Specified height */
    border-bottom: 1px solid white;
    background: transparent;
    outline: none; /* Remove outline */
    -webkit-transition: .2s; /* 0.2 seconds transition on hover */
    transition: opacity .2s;
    border-radius: 0;
}

.slider:hover {
    opacity: 1; /* Fully shown on mouse-over */
}

.slider::-webkit-slider-thumb {
    -webkit-appearance: none; /* Override default look */
    appearance: none;
    width: 30px; /* Set a specific slider handle width */
    height: 30px; /* Slider handle height */
    background: white;
    border-radius: 100%;
    cursor: pointer; /* Cursor on hover */
    position: relative;
    top: 2em;
}

.slider::-moz-range-thumb {
    width: 30px; /* Set a specific slider handle width */
    height: 30px; /* Slider handle height */
    background: white;
    border-radius: 100%;
    cursor: pointer; /* Cursor on hover */
    position: relative;
    top: 2em;
}
</style>
