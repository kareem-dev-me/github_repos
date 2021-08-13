<template>
  <div>
    <v-container>
      <repo-card></repo-card>
    </v-container>
  </div>
</template>

<script>
import repo_card from '~/components/repo-card.vue'
export default {
  components: {
    'repo-card': repo_card,
  },
  head() {
    return {
      title: 'Most starred Github repos',
    }
  },
}
</script>

<style></style>
