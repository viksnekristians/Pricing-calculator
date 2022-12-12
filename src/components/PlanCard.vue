<template>
<div class="plan-card" :class="{ active: this.selectedPlan===this.plan.id }" @click="$emit('selectPlan' , this.plan.id)">
 {{getPlanName}}
  </div>
</template>

<script>

export default {
  name: 'PlanCard',
  props: {
    plan: Object,
    selectedPlan: Number
  },
  data() {
    return {
        plans: [{
            name: "Regular",
            description: "Ŗegular plan"
          },
          {
            name:"Premium",
            description: "Premium plan"
            }]
    }
  },
  computed: {
    getPlanName() {
        return this.plans[this.plan.id - 1].name;
    }
  }

}
</script>