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
          新規会員会員登録
        </v-card-title>
        <v-card-actions>
          <v-text-field label="名前" />
        </v-card-actions>
        <v-card-actions>
          <v-text-field label="電話番号" />
        </v-card-actions>
        <v-card-actions>
          <v-text-field label="メールアドレス" />
        </v-card-actions>
        <v-card-actions>
          <v-text-field label="性別" />
        </v-card-actions>
        <v-card-actions>
          <v-text-field label="パスワード" />
        </v-card-actions>
        <v-card-actions>
          <v-text-field label="確認用パスワード" />
        </v-card-actions>
        <v-card-actions>
          <v-btn to="/user/mypage">アカウント登録</v-btn>
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
