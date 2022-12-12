<template>
<div>
<div id="level-buttons" class="d-flex justify-content-between align-items-center mb-4">
  <div class="level-card" v-for="(level,idx) in levels[this.selectedPlan - 1]" :key="level" @click="changeLevel(idx+1)" :class="{ active: this.sliderValue===idx+1 }">
    {{ level.title }}
  </div>
</div>
  <Slider v-model="sliderValue" :min="1" :max="4" />
  <div class="buy-level mt-5">
    <p class="plan-description my-3"> {{getDescription}}</p>
    <h2>Price: 
      <a v-if="isNaN(getPrice)" class="btn secondary-button ml-3" href="/contact">Contact us</a>
      <span v-else>{{getPrice}}</span>
    </h2>
    <a  :href="url" class="btn primary-button mt-3">Buy plan</a>
  </div>
  </div>
</template>

<script>
import Slider from '@vueform/slider'

export default {
  name: 'PricingCalculator',
  components: {
    Slider
  },
  props: {
    selectedPlan: Number
  },
  data() {
    return {
      sliderValue: 1,
      prices: [
        [
            800,
            1500,
            2000,
            2400
        ],
        [
            1250,
            2350,
            3000,
            "Contact us"
        ]
      ],
      levels: require("../data/levels.json")
      
    }
  },
  methods: {
    changeLevel(value) {
      this.sliderValue =value;
    }
  },
  computed: {
    getPrice() {
        return this.prices[this.selectedPlan - 1][this.sliderValue - 1];
    },
    getDescription() {
      return this.levels[this.selectedPlan - 1][this.sliderValue - 1].description;
    },
    url() {
      return `/${this.selectedPlan}/${this.sliderValue}`;
    }
  }
}
</script>