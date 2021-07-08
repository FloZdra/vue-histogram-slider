<template>
  <div>
    <HistogramSlider
      style="margin: 200px auto"
      type="double"
      :width="900"
      :bar-height="110"
      :from="3"
      :to="7"
      :data="numberData"
      :clip="false"
      :drag-interval="true"
      :hideFromTo="true"
      @finish="finish"
      :force-edges="false"
      :colors="['#4facfe', '#00f2fe']"
    />

    <!--    <HistogramSlider-->
    <!--      style="margin: 200px auto"-->
    <!--      type="double"-->
    <!--      :width="900"-->
    <!--      :bar-height="110"-->
    <!--      :data="data"-->
    <!--      :prettify="prettify"-->
    <!--      :clip="true"-->
    <!--      :drag-interval="true"-->
    <!--      :hideFromTo="true"-->
    <!--      @finish="finish"-->
    <!--      :force-edges="false"-->
    <!--      :colors="['#4facfe', '#00f2fe']"-->
    <!--    />-->

    <!--    <HistogramSlider-->
    <!--      style="margin: 200px auto"-->
    <!--      ref="hist"-->
    <!--      type="double"-->
    <!--      :width="900"-->
    <!--      :bar-height="110"-->
    <!--      :data="data"-->
    <!--      :prettify="prettify"-->
    <!--      :clip="true"-->
    <!--      :drag-interval="true"-->
    <!--      :hideFromTo="true"-->
    <!--      @finish="finish"-->
    <!--      :force-edges="false"-->
    <!--      :colors="['#4facfe', '#00f2fe']"-->
    <!--    />-->
  </div>
</template>

<script>
import HistogramSlider from './lib//HistogramSlider'
export default {
  data() {
    return {
      // data: require('../resources/data.json').map(d => new Date(d).valueOf()),
      numberData: [0, 1, 1, 2, 2, 2, 3, 3, 4, 5, 6, 7, 7, 7, 7, 8, 9, 9],
      prettify: function (ts) {
        return new Date(ts).toLocaleDateString('en', {
          year: 'numeric',
          month: 'short',
          day: 'numeric'
        })
      }
    }
  },

  methods: {
    finish(val) {
      console.log(val)
    }
  },

  mounted() {
    setTimeout(() => {
      if (this.$refs.hist) {
        this.$refs.hist.update({ from: this.data[20], to: this.data[69] })
      }
    }, 2000)
  },

  components: {
    HistogramSlider
  }
}
</script>
