<template>
  <v-card class="mx-auto my-5">
    <v-row align="center">
      <!-- Section-> image column -->
      <v-col cols="12" md="3">
        <a :href="owner_url" class="text-decoration-none ma-5" target="_blank">
          <v-img :src="image" alt="avatar" max-height="150" contain></v-img>
        </a>
      </v-col>
      <!-- Section-> data column -->
      <v-col cols="12" md="9">
        <!-- Section-> first row -->
        <p class="text-h5 font-weight-bold">
          <a :href="repo_url" class="text-decoration-none" target="_blank">
            {{ name }}
          </a>
        </p>
        <!-- Section-> second row -->

        <p class="text-body-1">
          {{ description }}
        </p>
        <!-- Section-> third row -->

        <div>
          <v-btn color="primary lighten-1" class="mr-2">
            <v-icon color="yellow darken-2" class="mr-2">mdi-star</v-icon>
            Stars: {{ stars }}
          </v-btn>
          <v-btn color="primary lighten-1" class="mr-2">
            <v-icon color="red darken-2" class="mr-2">mdi-alert</v-icon>
            Issues: {{ issues }}
          </v-btn>
          <span class="text-body-2 font-weight-bold">
            Submitted {{ created }} days ago by {{ owner_name }}
          </span>
        </div>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
  props: {
    image: {
      type: String,
      default: '',
    },
    name: {
      type: String,
      default: '',
    },
    description: {
      type: String,
      default: '',
    },
    stars: {
      type: Number,
      default: 0,
    },
    issues: {
      type: Number,
      default: 0,
    },
    owner_url: {
      type: String,
      default: '',
    },
    owner_name: {
      type: String,
      default: '',
    },
    repo_url: {
      type: String,
      default: '',
    },
    created: {
      type: Number,
      default: 0,
    },
  },
}
</script>

<style></style>
