<template>
  <div></div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({
  components: {
    List: () => import('~/components/List.vue'),
  },
})
export default class MainPage extends Vue {}
</script>
