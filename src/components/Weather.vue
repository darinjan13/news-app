<template>
  <div>
    <v-container>
      <v-row>
        <v-col>
          <v-carousel
            height="300"
            max="4"
            hide-delimiters
            show-arrows
            show-arrows-on-hover
          >
            <v-carousel-item v-for="d in details" :key="d.id">
              <v-card>
                <v-sheet color="primary">
                  <v-card-text>{{ d.Date }}</v-card-text>
                  <v-avatar size="68"><v-img :src="icon+d.Day.Icon+'-s.png'"></v-img></v-avatar>
                </v-sheet>
              </v-card>
            </v-carousel-item>
          </v-carousel>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      details: [],
      icon: `https://developer.accuweather.com/sites/default/files/`,
    };
  },
  mounted() {
    axios
      .get(
        "http://dataservice.accuweather.com/forecasts/v1/daily/5day/262736?apikey=p8NirceXo8WtobGtRONzNhaAxIbAY5CO&metric=true"
      )
      .then((res) => {
        console.log(res.data.DailyForecasts);
        this.details = res.data.DailyForecasts;
      });
  },
};
</script>