<template>
   <div>
    <div class="plan-cards mb-3">
      <PlanCard @selectPlan="changePlan" :plan="this.plans[0]" :selectedPlan="this.selectedPlan"/>
      <PlanCard @selectPlan="changePlan" :plan="this.plans[1]" :selectedPlan="this.selectedPlan"/>
    </div>
    <div class="plan-description mb-5">
      {{this.plans[this.selectedPlan-1].description}}
    </div>
    <PricingCalculator v-show="selectedPlan === 1" :selectedPlan="1"  />
    <PricingCalculator v-show="selectedPlan === 2" :selectedPlan="2"  />
  </div>
</template>

<script>
import PricingCalculator from './components/PricingCalculator.vue'
import PlanCard from './components/PlanCard.vue'

export default {
  name: 'App',
  components: {
    PricingCalculator,
    PlanCard
  },
  data() {
    return {
      selectedPlan: 1,
      plans: [{
            id: 1,
            name: "Regular",
            description: "With Regular plan you will get one of our developers to work with your website. Each plan's level determines how many hours your dedicated developer will work with your website and newest requests from you. More specialists like designers or DevOps specialists can be assigned for specific tasks when they are free."
          },
          {
            id: 2,
            name:"Premium",
            description: "With Premium plan we will assign you a team with atleast 1-2 dedicated web developers and other specialists like designers, DevOps,SEO specialists and others depending on your website's needs. You can select level that fits best for your needs and timelines. You can also get in touch with us and customize your team and project delivery."
            }]
    }
  },
  methods: {
    changePlan(plan) {
      this.selectedPlan = plan;
    }
  }
}
</script>
<style src="@vueform/slider/themes/default.css"></style>

