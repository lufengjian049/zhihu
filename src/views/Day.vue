<template>
<section class="date-container">
    <History :day="oneDay"></History>
    <router-link :to="{path: '/'}" style="display:block;margin-top:10px">返回首页</router-link>
</div>
</template>

<script>
import Vue from 'vue';
import History from '../components/History.vue'
import DateCalc from '../../common/util/date';

const fetchHistory = store => {
  return store.dispatch('FETCH_ONEDAY', store.state.route.query.dtime);
}

export default {
  name: 'oneday',
  components: {
    History
  },
  preFetch: fetchHistory,
  computed: {
    oneDay() {
      return this.$store.state.oneday
    }
  },
  beforeMount () {
    fetchHistory(this.$store);
  }
};
</script>
