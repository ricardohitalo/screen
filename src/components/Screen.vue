<template>
  <v-app>
    <v-app-bar
      app>
    <v-toolbar-title>Track your order</v-toolbar-title>
      </v-app-bar>
    <v-main>
      <v-container>
        <v-row>
          <v-col
              class="center"
              cols="12">
            <h4>Estimate Delivery Time</h4>
            <h1>00:00</h1>
          </v-col>

        </v-row>
        <v-row>
          <v-col
          cols="12">
            <v-list two-line>
              <v-list-item
              v-for="item in items"
              :key="item.title">
              <v-list-item-avatar size="56">
                <v-img :src="item.avatar"></v-img>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-subtitle>Your Rider</v-list-item-subtitle>
                <v-list-item-title v-text="item.name"></v-list-item-title>
              </v-list-item-content>

              </v-list-item>
            </v-list>
          </v-col>
        </v-row>
        <v-stepper
        v-model="e6"
        vertical>
          <v-stepper-step
          :complete="e6 > 1"
          step="1">Order confirmed</v-stepper-step>
          <v-stepper-step
          :complete="e6 > 2"
          step="2">Preparing your order</v-stepper-step>
          <v-stepper-step
          :complete="e6 > 3"
          step="3">Order is ready at the restaurant</v-stepper-step>
          <v-stepper-step
          :complete="e6 > 4"
          step="4">Rider is picking your order</v-stepper-step>
          <v-stepper-step
          :complete="e6 > 5"
          step="5">Rider is nearby your place</v-stepper-step>
        </v-stepper>
      </v-container>
    </v-main>
    <v-footer
    fixed>
      <v-btn
        dark
        color="red"
        rounded
        block
        @click="sheet = !sheet">
        Cancel your order
      </v-btn>
      <v-bottom-sheet v-model="sheet">
        <v-sheet
        class="text-center"
        height="200px">
          <v-btn
          class="mt-6"
          text
          color="red"
          @click="sheet = !sheet">
            Close
          </v-btn>
          <div class="py-3">
            Order canceled sucessfully
          </div>
        </v-sheet>
      </v-bottom-sheet>
    </v-footer>
  </v-app>
</template>
<script>
export default {
  data: () => {
    return ({
      e6: 3,
      items: [
        {
          avatar: 'https://i.pinimg.com/564x/df/e4/de/dfe4def88ebb596e614837bca4193410.jpg',
          name: 'Yuuta Togashi',
        }
      ],
      sheet: false,
      tiles: [
        {img: 'keep.png', title: 'Keep'},
        {img: 'inbox.png', title: 'Inbox'},
        {img: 'hangouts.png', title: 'Hangouts'},
        {img: 'messenger.png', title: 'Messenger'},
        {img: 'google.png', title: 'Google+'},
      ],

    });
  },
}
</script>
<style>
.center {
  text-align: center;
}
h4 {
  color: #FF0000;
}
</style>