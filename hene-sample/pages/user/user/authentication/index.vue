<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <v-card
        min-width="300px"
      >
        <v-card-title class="headline">
          SMS認証
        </v-card-title>
        <v-card-actions>
          <v-text-field label="認証番号6桁を記入してください" />
        </v-card-actions>
        <v-card-actions>
          <v-btn to="/user/user/create">SMS認証</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
    export default {
        layout: 'userDefault',
    }
</script>
