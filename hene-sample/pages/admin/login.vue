<template>
  <v-card width="400px" class="mx-auto mt-5">
    <v-card-title>
      <h1 class="display-1">ログイン</h1>
    </v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field prepend-icon="mdi-account-circle" label="メールアドレス" />
        <v-text-field prepend-icon="mdi-lock" append-icon="mdi-eye-off" label="パスワード" />
      </v-form>
      <v-card-actions>
        <v-btn>ログイン</v-btn>
      </v-card-actions>
    </v-card-text>
    <v-card-text class="text--primary">
      <div> <a href="password/email">パスワードをお忘れのかたはこちら</a></div>
    </v-card-text>
  </v-card>
</template>
