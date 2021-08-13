<template>
  <v-card>
    <v-row align="center">
      <!-- Section-> image column -->
      <v-col cols="12" md="3">
        <v-img
          src="https://cdn.vuetifyjs.com/images/cards/house.jpg"
          alt="avatar"
          max-height="150"
          class="ma-5"
        ></v-img>
      </v-col>
      <!-- Section-> data column -->
      <v-col cols="12" md="9">
        <!-- Section-> first row -->
        <p class="text-h5 font-weight-bold">Repo name</p>
        <!-- Section-> second row -->

        <p class="text-body-1">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium
          magnam veniam assumenda consequuntur expedita, placeat iure explicabo
          deleniti libero reprehenderit facere nisi, sunt quasi. Dolor sequi
          modi repellat deserunt distinctio.
        </p>
        <!-- Section-> third row -->

        <div>
          <v-btn color="primary lighten-1" class="mr-2">
            <v-icon color="yellow darken-2" class="mr-2">mdi-star</v-icon>
            Stars: 118k
          </v-btn>
          <v-btn color="primary lighten-1" class="mr-2">
            <v-icon color="red darken-2" class="mr-2">mdi-alert</v-icon>
            Issues: 1.6k
          </v-btn>
          <span class="text-body-2 font-weight-bold">
            Submitted 30 days ago by test
          </span>
        </div>
      </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {}
</script>

<style></style>
