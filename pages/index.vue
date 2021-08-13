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
      >
      </repo-card>
    </v-container>
    <observer v-if="observe" @intersect="get_repos(page)"></observer>
    <overlay :show="!observe"></overlay>
  </div>
</template>

<script>
import repo_card from '~/components/repo-card.vue'
import observer from '~/components/helper/observer.vue'
import overlay from '~/components/helper/overlay.vue'
export default {
  components: {
    'repo-card': repo_card,
    observer,
    overlay,
  },
  data() {
    return {
      repos: [],
      page: 1,
      observe: false,
    }
  },
  head() {
    return {
      title: 'Most starred Github repos',
    }
  },

  async mounted() {
    // Comment-> 1/ Call the api
    await this.get_repos(this.page)
    // Comment-> 2/ Handle the response and map the array ----> Done
    // Comment-> 3/ Dynamic the UI ----> Done
    // Comment-> 3/ Pagination ----> Done
  },
  methods: {
    async get_repos(page) {
      // Comment-> Should stop observe
      this.observe = false
      // Comment-> check not the first page
      const page_number = !!page & (page !== 1) ? `&page=${page}` : null

      await this.$axios
        .$get(
          `https://api.github.com/search/repositories?q=created:>2017-10-22&sort=stars&order=desc${page_number}`
        )
        .then((res) => {
          // Comment-> Handle the response and map the array
          this.repos.push(
            ...res.items.map((item) => {
              return {
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
              }
            })
          )
          // Comment-> increase the count of page
          this.page++
          // Comment-> retturn observe to run
          this.observe = true
        })
    },
    get_days_between_dates(first_date, second_date) {
      // Comment-> get the difference and divide it by milliseconds in the day
      return Math.floor((first_date - second_date) / (1000 * 60 * 60 * 24))
    },
  },
}
</script>

<style></style>
