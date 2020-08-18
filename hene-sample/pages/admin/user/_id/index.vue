<template>
  <div>

  <v-form>
    <v-card
      class="mx-auto"
      max-width="1200"
      outlined
    >
      <v-card-title>ユーザー詳細</v-card-title>
      <v-card-text>
        <v-form
          ref="form"
        >
          <v-text-field
            v-model="name"
            :counter="100"
            label="名前"
            readonly="true"
          ></v-text-field>

          <v-text-field
            v-model="tel"
            label="電話番号"
            readonly="true"
          ></v-text-field>

          <v-text-field
            value="認証済み"
            label="顔認証情報"
            readonly="true"
            disabled="true"
          ></v-text-field>

          <v-text-field
            value="登録済み"
            label="クレジットカード情報"
            readonly="true"
            disabled="true"
          ></v-text-field>

          <v-text-field
            value="2020年9月15日 20時30分"
            label="登録日時"
            readonly="true"
            disabled="true"
          ></v-text-field>

          <v-text-field
            value="有効"
            label="ステータス"
            readonly="true"
            disabled="true"
          ></v-text-field>

          <v-btn
            color="error"
            class="mr-8"
            @click="deleteConfirm"
          >
            アカウントを停止する
          </v-btn>
        </v-form>
      </v-card-text>
    </v-card>
    </v-form>

    <!--  モーダル  -->
    <v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="600px">
        <v-card min-height="175px">
          <v-card-title>
            <h3>本当にこのアカウントを削除してよろしいですか？</h3>
          </v-card-title>
          <v-card-actions>
            <v-btn color="error"@click="deleted" class="mr-auto">削除する</v-btn>
          </v-card-actions>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialog = false">閉じる</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>

  </div>
</template>

<script>
    export default {
        data () {
            return {
                dialog: false,
                name:'管理者ユーザー1',
                tel:'09011112222',
            }
        },
        methods: {
            update() {
                this.updateSnackbar = true
            },
            deleteConfirm() {
                this.dialog = true
            },
            deleted(){
                this.dialog = false
                this.$router.push('/admin/admin')
            }
        }
    }
</script>

<style scoped>
  .mr-auto {
    margin: auto;
  }
</style>