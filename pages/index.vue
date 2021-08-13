<template>
  <div>
    <v-container>
      <repo-card
        v-for="item in repos"
        :key="item.id"
        :name="item.name"
        :description="item.description"
        :image="item.image"
        :owner_url="item.owner_url"
        :repo_url="item.repo_url"
        :stars="item.stars"
        :issues="item.issues"
        :owner_name="item.owner_name"
        :created="item.created"
      ></repo-card>
    </v-container>
  </div>
</template>

<script>
import repo_card from '~/components/repo-card.vue'
export default {
  components: {
    'repo-card': repo_card,
  },
  data() {
    return {
      repos: [],
    }
  },
  head() {
    return {
      title: 'Most starred Github repos',
    }
  },
  mounted() {
    // Comment-> 1/ Call the api
    this.$axios
      .$get(
        'https://api.github.com/search/repositories?q=created:>2017-10-22&sort=stars&order=desc'
      )
      .then((res) => {
        // Comment-> 2/ Handle the response and map the arrays
        this.repos = res.items.map((item) => ({
          id: item.id,
          name: item.name,
          description: item.description,
          image: item.owner.avatar_url,
          owner_url: item.owner.html_url,
          repo_url: item.html_url,
          stars: item.stargazers_count,
          issues: item.open_issues_count,
          owner_name: item.owner.login,
          created: this.get_days_between_dates(
            Date.now(),
            new Date(item.created_at)
          ),
        }))
      })
    // Comment-> 3/ Dynamic the UI --->
    // Comment-> 3/ Pagination
  },
  methods: {
    get_days_between_dates(first_date, second_date) {
      // Comment-> get the difference and divide it by milliseconds in the day
      return Math.floor((first_date - second_date) / (1000 * 60 * 60 * 24))
    },
  },
}
</script>

<style></style>
