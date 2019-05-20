<template>
  <v-container>
    <v-layout wrap fill-height >
      <v-flex xs12 md12 xl12 id="top-title" class="mt-3 mb-3">
        <h1 id="hauserSind">Unsere Fertighäuser sind </h1>
        <h1 id="hausIst">{{hausIst}}.</h1>
        <v-carousel style="margin-top: 20px;">
          <v-carousel-item v-for="(item,i) in items" :key="i" :src="item.src"></v-carousel-item>
        </v-carousel>
      </v-flex>
      <v-flex xs12 md12 class="mt-3 mb-3">
        <v-layout row justify-center>
          <v-dialog v-model="dialog" max-width="600px">
            <template v-slot:activator="{ on }">
              <v-btn color="orange" dark v-on="on">Newsletter Abonnieren</v-btn>
            </template>
            <v-card>
              <v-card-title>
                <span class="headline">bauen wie wir Newsletter</span>
              </v-card-title>
              <v-card-text>
                <v-container grid-list-md>
                  <v-layout wrap>
                    <v-flex md12 xl12>
                      <v-img position="center" style="width:250px;" :src="require('../assets/HausInfo.jpg')"></v-img>
                    </v-flex>
                    <v-flex xs12 sm6 md4>
                      <v-text-field label="Vorname*" required></v-text-field>
                    </v-flex>
                    <v-flex xs12 sm6 md4>
                      <v-text-field label="Nachname"></v-text-field>
                    </v-flex>
                    <v-flex xs12 sm6 md4>
                      <v-text-field label="Email*" required></v-text-field>
                    </v-flex>
                    <v-flex xs12 sm12 xl12>
                      <v-autocomplete :items="['Fertighäuser', 'Smart Home', 'Finanzierung']"
                        label="Ich bin interessiert an" multiple></v-autocomplete>
                    </v-flex>
                    <v-flex xs12 sm12>
                      <v-checkbox color="blue" v-model="switch1" label="Mit AGB und Datenschutzpolitik einverstanden">
                      </v-checkbox>
                    </v-flex>
                  </v-layout>
                </v-container>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="blue darken-1" flat @click="dialog = false">Abbrechen</v-btn>
                <v-btn color="blue darken-1" flat @click="dialog = false">Abschicken</v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </v-layout>
      </v-flex>

    <v-flex xs12 md12 xl12 class="mt-3 mb-3">
      <v-layout row wrap>
      <v-flex xs12 md4 xl4 >
        <v-card height="300px">
          <v-card-title class="v-card-title">
            KFW-55
          </v-card-title>
          <v-card-text style="text-align: center;">
            <img
              src="https://d33wubrfki0l68.cloudfront.net/f9bab870908feeee421a4e8abb20af9d3977887a/ffb09/images/icons/windmill-f9bab870.svg"
              width="100"><br>
            ist bei uns Standard
            Bei unseren bauen.wiewir Fertighäusern erhalten Sie immer alle kfw 55 Anforderungen im Standard. Dies ist
            unser Geschenk an jeden Bauherrn und jede Bauherrin, damit Sie langfristig in einem energieeffizienten
            Zuhause leben können.

          </v-card-text>
        </v-card>
      </v-flex>
      <v-flex xs12 md4 xl4>
        <v-card height="300px">
          <v-card-title class="v-card-title">
            6 MONATE
          </v-card-title>
          <v-card-text style="text-align: center;">
            <img
              src="https://d33wubrfki0l68.cloudfront.net/21b75b377229f29a7bd3b267e018edf45e4d0985/66ed6/images/icons/truck-21b75b37.svg"
              width="100"><br>
            bis zum Einzug
            Mit bauen.wiewir können Sie sich bei Ihrem Fertighausbau auf eine fristgerechte Lieferung verlassen. Hier
            haben Sie die Garantie auf einen schnellen und reibungslosen Hausbau, denn wir liefern Ihnen Ihr Fertighaus
            in nur 6 Monaten.

          </v-card-text>
        </v-card>
      </v-flex>
      <v-flex xs12 md4 xl4>
        <v-card height="300px">
          <v-card-title class="v-card-title">
            FIX-PREIS
          </v-card-title>
          <v-card-text style="text-align: center;">
            <img
              src="https://d33wubrfki0l68.cloudfront.net/712f134a380149f66be5310bbe69243f2e6a61ef/7dff1/images/icons/euro-712f134a.svg"
              width="100"><br>
            auf alle Häuser
            Langfristig zufriedene und glückliche Kunden sind uns wichtig! Deshalb halten wir für Sie alle Kosten
            transparent und garantieren unseren Fix-Preis für jedes Fertighaus. Mit bauen.wiewir gibt es bei Ihrer
            Baufinanzierung keine versteckten Kosten.

          </v-card-text>
        </v-card>
      </v-flex>
      </v-layout>
    </v-flex>

    </v-layout>

  </v-container>
</template>

<script>
import { setTimeout, setInterval } from 'timers';
  export default {
    name: 'Main',
    data() {
      return {
        hausIst: '',
        hauserSind: ['smarter', 'besser', 'schneller', 'digitaler', 'preiswerter'],
        dialog: false,
        switch1: false,
        items: [
          {src: require('../assets/Haus1.jpg')},
          
          {src: require('../assets/Haus2.jpg')},
          
          {src: require('../assets/Haus3.jpg')}
        ]
    }
  },
  mounted() {
    setTimeout(() => {
      this.dialog = true;
    }, 3000)

    const max = this.hauserSind.length
    let newIndex = 0
    const interval = setInterval(() => {
      newIndex++
      if (newIndex >= max) {
        newIndex = 0
      }
      this.hausIst = this.hauserSind[newIndex]
    }, 1500)
  }
  }
</script>

<style>
#hauserSind {
  margin: 20px 0px 20px 20px;
  display: inline;
}

#hausIst {
  display: inline;
  margin: 20px 20px 20px 0px;
  color: rgb(12, 143, 0)
}

#top-title {
  text-align: center;
}

.v-card-title {
  font-size: 24px;
}
</style>
