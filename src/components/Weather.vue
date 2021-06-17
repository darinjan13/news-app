<template>
  <div>
    <v-container>
      <v-row>
        <v-col>
            <v-alert dense prominent text color="danger">
              <h2 class="caption text-uppercase">Today's Weather Forecast</h2>
              <h2 class="caption text-uppercase">{{ HL.Text }}</h2>
            </v-alert>
            <v-alert dense prominent text color="info">
              <h2 class="caption text-uppercase">5 Day's Daily Forecast</h2>
            </v-alert>
          <v-carousel
            height="200"
            max="4"
            hide-delimiters
            show-arrows
            show-arrows-on-hover
          >
            <v-carousel-item v-for="d in DF" :key="d.id">
              <v-card>
                <v-sheet height="200" color="dark">
                  <v-card-text>Date: {{ d.Date }}</v-card-text>
                  <v-avatar tile class="mt-n6" size="100" v-if="parseInt(d.Day.Icon) < 10">
                    <v-img contain :src="`${icon}0${d.Day.Icon}-s.png`" alt="img"></v-img>
                  </v-avatar>
                  <v-avatar tile class="mt-n6" size="100" v-else>
                    <v-img contain :src="`${icon}${d.Day.Icon}-s.png`" alt="img">
                    </v-img>
                  </v-avatar>
                  <v-card-subtitle class="mt-n6">{{ d.Day.IconPhrase }}</v-card-subtitle>
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
      DF: [],
      HL: [],
      icon: null,
    };
  },
  mounted() {
    axios
      .get(
        "https://dataservice.accuweather.com/forecasts/v1/daily/5day/262736?apikey=p8NirceXo8WtobGtRONzNhaAxIbAY5CO&metric=true"
      )
      .then((res) => {
        console.log(res.data.DailyForecasts);
        this.DF = res.data.DailyForecasts;
        this.HL = res.data.Headline;
        this.icon = "https://developer.accuweather.com/sites/default/files/";
      });
  },
};
</script>

