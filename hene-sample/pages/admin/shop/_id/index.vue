<template>
  <div>


  <v-form>
    <v-card
      class="mx-auto"
      max-width="800"
      outlined
    >
      <v-card-title>パスワードの再設定</v-card-title>
      <v-card-text>
        <v-text-field
          :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
          :type="show1 ? 'password' : 'text'"
          name="input-10-1"
          label="新しいパスワードを入力してください"
          counter
          @click:append="show1 = !show1"
        ></v-text-field>
        <v-text-field
          :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
          :type="show1 ? 'password' : 'text'"
          name="input-10-1"
          label="確認用のパスワードを入力してください"
          counter
          @click:append="show1 = !show1"
        ></v-text-field>

        <v-card-actions>
          <v-btn
            color="primary"
            dark
            @click="snackbar = true"
          >パスワードを新しく設定する</v-btn>
        </v-card-actions>
      </v-card-text>
    </v-card>
    </v-form>

    <v-snackbar
      v-model="snackbar"
      :bottom="y === 'bottom'"
      :color="color"
      :left="x === 'left'"
      :multi-line="mode === 'multi-line'"
      :right="x === 'right'"
      :timeout="timeout"
      :top="y === 'top'"
      :vertical="mode === 'vertical'"
    >
      {{ text }}
      <template v-slot:action="{ attrs }">
        <v-btn
          dark
          text
          v-bind="attrs"
          @click="snackbar = false"
          to="/admin/login"
        >
          ログイン画面へ
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
    export default {
        data () {
            return {
                show1: true,
                color: '',
                mode: '',
                snackbar: false,
                text: 'パスワードの変更を完了しました',
                timeout: 6000,
                x: null,
                y: 'top',
            }
        }
    }
</script>
