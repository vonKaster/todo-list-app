<template>
    <div>
      <v-card :loading="loading" class="mx-auto my-12" max-width="374">
        <template slot="progress">
          <v-progress-linear
            color="deep-purple"
            height="10"
            indeterminate
          ></v-progress-linear>
        </template>
  
        <v-img
          height="250"
          src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
        ></v-img>
  
        <v-card-title>Cafe Badilico</v-card-title>
  
        <v-card-text>
          <v-row class="mx-0">
            <v-rating
              :value="4.5"
              color="amber"
              dense
              half-increments
              readonly
              size="14"
            ></v-rating>
  
            <div class="grey--text ms-4">4.5 (413)</div>
          </v-row>
  
          <div class="my-4 text-subtitle-1">$ • Italian, Cafe</div>
  
          <div>
            Small plates, salads & sandwiches - an intimate setting with 12 indoor
            seats plus patio seating.
          </div>
        </v-card-text>
  
        <v-divider class="mx-4"></v-divider>
  
        <v-card-title>Tonight's availability</v-card-title>
  
        <v-card-text>
          <v-chip-group
            v-model="selection"
            active-class="deep-purple accent-4 white--text"
            column
          >
            <v-chip>5:30PM</v-chip>
  
            <v-chip>7:30PM</v-chip>
  
            <v-chip>8:00PM</v-chip>
  
            <v-chip>9:00PM</v-chip>
          </v-chip-group>
        </v-card-text>
  
        <v-card-actions>
          <v-btn color="deep-purple lighten-2" text> Reserve </v-btn>
        </v-card-actions>
      </v-card>
  
        <v-card class="mx-auto mb-10" max-width="400">
          <v-list-item two-line>
            <v-list-item-content>
              <v-list-item-title class="text-h5">
                San Francisco
              </v-list-item-title>
              <v-list-item-subtitle
                >Mon, 12:30 PM, Mostly sunny</v-list-item-subtitle
              >
            </v-list-item-content>
          </v-list-item>
  
          <v-card-text>
            <v-row>
              <v-col class="text-h2" cols="6"> 23&deg;C </v-col>
              <v-col cols="6">
                <v-img
                  src="https://cdn.vuetifyjs.com/images/cards/sun.png"
                  alt="Sunny image"
                  width="92"
                ></v-img>
              </v-col>
            </v-row>
          </v-card-text>
  
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-send</v-icon>
            </v-list-item-icon>
            <v-list-item-subtitle>23 km/h</v-list-item-subtitle>
          </v-list-item>
  
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-cloud-download</v-icon>
            </v-list-item-icon>
            <v-list-item-subtitle>48%</v-list-item-subtitle>
          </v-list-item>
  
          <v-slider
            :max="6"
            :tick-labels="labels"
            class="mx-4"
            ticks
          ></v-slider>
  
          <v-list class="transparent">
            <v-list-item v-for="item in forecast" :key="item.day">
              <v-list-item-title>{{ item.day }}</v-list-item-title>
  
              <v-list-item-icon>
                <v-icon>{{ item.icon }}</v-icon>
              </v-list-item-icon>
  
              <v-list-item-subtitle class="text-right">
                {{ item.temp }}
              </v-list-item-subtitle>
            </v-list-item>
          </v-list>
  
          <v-divider></v-divider>
  
          <v-card-actions>
            <v-btn text> Full Report </v-btn>
          </v-card-actions>
        </v-card>
    </div>
  </template>

<script>
export default {
  name: "Cards",

  data: () => ({
    loading: false,
    selection: 1,
    labels: ["SU", "MO", "TU", "WED", "TH", "FR", "SA"],
    time: 0,
    forecast: [
      {
        day: "Tuesday",
        icon: "mdi-white-balance-sunny",
        temp: "24\xB0/12\xB0",
      },
      {
        day: "Wednesday",
        icon: "mdi-white-balance-sunny",
        temp: "22\xB0/14\xB0",
      },
      { day: "Thursday", icon: "mdi-cloud", temp: "25\xB0/15\xB0" },
    ],
  }),
};
</script>