<template>
  <div class="body">
    <div class="title">
      Financial info
    </div>

    <Progress />

    <smpNumber
      title="Monthly Household Income (after taxes - combined)"
      subtitle="Include all automatic deductions ex: 401K, Health Insurance, etc. We will enter those expenses in other sections"
      path="financial.monthlyHouseholdIncome"
      :value="financial.monthlyHouseholdIncome"
      unitSymbol="$"
    />

    <smpRadios
      title="Dependents (including yourself)"
      path="financial.dependents"
      :options="dependentsOptions"
      :value="financial.dependents"
    />

    <smpRadios
      title="Credit score"
      path="financial.creditScore"
      :options="creditScoreOptions"
      :value="financial.creditScore"
      :allowSkip="true"
    />
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
import smpNumber from '@/components/smpNumber'
import smpRadios from '@/components/smpRadios'
import Progress from '@/components/Progress'

export default {
  methods: {
    ...mapActions(['setValueByPath'])
  },
  computed: {
    ...mapGetters(['financial'])
  },
  components: { smpNumber, smpRadios, Progress },
  data () {
    return {
      creditScoreOptions: ['Poor', 'Fair', 'Good', 'Excellent'],
      dependentsOptions: ['1', '2', '3+']
    }
  }
}
</script>
