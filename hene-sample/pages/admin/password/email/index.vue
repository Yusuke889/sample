<template>
  <v-card width="600px" class="mx-auto mt-5">
    <v-card-title>
      <h1 class="display-1">パスワード再設定リクエスト</h1>
    </v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field prepend-icon="mdi-email" label="メールアドレス"/>
      </v-form>
      <v-card-actions>
        <v-btn to="email/send">パスワード再設定メールを送信</v-btn>
      </v-card-actions>
    </v-card-text>
  </v-card>
</template>
