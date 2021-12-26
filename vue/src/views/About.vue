<template>
  <div class="about">
    <ViewTxs/>
  </div>
</template>

<script>
// @ is an alias to /src
import ViewTxs from '@/components/viewTxHistories.vue'

export default {
  name: 'App',
  components: {
    ViewTxs
  }
}
</script>
