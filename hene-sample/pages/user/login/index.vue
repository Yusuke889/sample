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
      <v-card>
        <v-card-title class="headline">
          ログイン
        </v-card-title>
        <v-card-actions>
        <v-text-field label="メールアドレス" />
        </v-card-actions>
        <v-card-actions>
        <v-text-field append-icon="mdi-eye-off" label="パスワード" />
        </v-card-actions>
        <v-card-actions>
          <v-btn>ログイン</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
    import Logo from '~/components/Logo.vue'
    import VuetifyLogo from '~/components/VuetifyLogo.vue'

    export default {
        layout: 'userDefault',
        name: 'userDefaultIndex',
        components: {
            Logo,
            VuetifyLogo
        }
    }
</script>
