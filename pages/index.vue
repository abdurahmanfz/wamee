<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <!-- <div class="text-center">
        <logo />
        <vuetify-logo />
      </div> -->
      <v-card class="rounded-lg">
        <v-card-title class="headline">
          Text any one seamlessly.
        </v-card-title>
        <v-card-text>
          <p>WaMe is a simple project create using Vue.js. It was designed to text to any one without saving their phone number.</p>
          <p>Thank you for using WaMe.</p>
          <div class="text-xs-right">
            <em><small>&mdash; Fauzan Abdurrahman</small></em>
          </div>
        </v-card-text>

        <v-card-text>
          <!-- <v-row class="ma-2" align="top"> -->
            <span class="caption">Whatsapp numbers</span>
            <v-text-field
              v-model="number"
              background-color="grey lighten-4"
              class="white"
              solo
              placeholder="e.g (62 8812 3456 789)"
              clearable
            ></v-text-field>

            <span class="caption">short text</span>
            <v-text-field
              v-model="text"
              background-color="grey lighten-4"
              class="white"
              solo
              :placeholder="randText"
              clearable
            ></v-text-field>
            <v-row justify="end" class="ma-1">
              <v-btn @click="sendMessage" class="primary" large align="end">
                Send
                <v-icon right>mdi-send</v-icon>
              </v-btn>
            </v-row>
          <!-- </v-row> -->
        </v-card-text>
          
        <v-card-text>
          <hr class="my-3">
          <a
            href="https://www.buymeacoffee.com/abdurahmanfz"
            target="_blank"
            rel="noopener noreferrer"
          >
            Buy me a coffee
          </a>
          <br>
          <a
            href="https://github.com/abdurahmanfz"
            target="_blank"
            rel="noopener noreferrer"
          >
            GitHub Profile
          </a>
        </v-card-text>
      </v-card>

      <v-hover v-slot="{hover}">
        <v-btn
          color="secondary"
          fixed bottom
          right fab
          x-large
          :class="hover ? 'elevation-8' : 'elevation-2'"
          href="https://www.buymeacoffee.com/abdurahmanfz"
          target="_blank"
        >
          <v-img width="40" height="40" contain src="bmc.png"></v-img>
          <!-- <v-icon>mdi-plus</v-icon> -->
        </v-btn>
      </v-hover>
    </v-col>
  </v-row>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  },

  head: {
    title: 'Home',
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { hid: 'description', name: 'description', content: '' }
    ],
  },

  data() {
    return {
      number: '',
      text: '',

      randText: '',

      texts: [
        'Met me at the office at 8',
        'I see your listing on Marketplace, is it available?',
        'Hey, nice to see you...',
        'Hi this is Deon your Uber Driver, im in the Hotel Lobby',
        'Thank you for your purchase! We have received your payment for order #555321. - Outdoor Retail Shop',
        'Jim, your rent payment for May 23 has been received.',
        'Happy Holidays! Thank you for being a valued team member. Show this text at Midtown Restaurant and get 30% off your meal.',
        'This is Emma from EMs Barber shop, can you please call us to confirm your booking at Feb 21?',
        'Enter your message'
      ]
    }
  }, 

  mounted() {
    this.getRandomText(0, this.texts.length)
  },

  methods: {
    sendMessage() {
      window.open('https://wa.me/'+this.number+'?text='+this.text)
    },

    getRandomText(min, max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      this.randText = this.texts[Math.floor(Math.random() * (max - min) + min)]
    }
  },
}
</script>
