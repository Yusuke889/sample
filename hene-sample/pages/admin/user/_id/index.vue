<template>
  <div>
    <v-row>
      <v-col cols="6">
        <v-card
          max-width="600"
          class="ma-3 pa-6"
          outlined
        >
          <v-card-title>ユーザー詳細
            <v-spacer/>
            <v-btn
              color="error"
              @click="deleteConfirm"
            >
              アカウントを停止する
            </v-btn>
          </v-card-title>
          <v-card-text>
            <v-form
            >
              <v-text-field
                v-model="name"
                :counter="100"
                label="名前"
                readonly
              ></v-text-field>

              <v-text-field
                v-model="tel"
                label="電話番号"
                readonly
              ></v-text-field>

              <v-text-field
                v-model="email"
                label="メールアドレス"
                readonly
              ></v-text-field>

              <v-text-field
                v-model="gender"
                label="性別"
                readonly
              ></v-text-field>

              <v-text-field
                v-model="face"
                label="顔情報認証時刻"
                readonly
              ></v-text-field>

              <v-text-field
                value="2020年10月20日 13時59分"
                label="クレジットカード認証時刻"
                readonly
              ></v-text-field>

              <v-text-field
                value="2020年9月15日 20時30分"
                label="登録日時"
                readonly
              ></v-text-field>

              <v-text-field
                value=" "
                label="退会日時"
                readonly
              ></v-text-field>

              <v-text-field
                value="登録済み"
                label="ステータス"
                readonly
              ></v-text-field>
            </v-form>
          </v-card-text>
        </v-card>

      </v-col>

      <v-col cols="6">
        <v-card
          max-width="600"
          class="ma-3 pa-6"
          outlined
        >
          <v-card-title>利用状況
          </v-card-title>
          <v-data-table
            :headers="headers"
            :items="events"
            hide-default-footer
            class="elevation-1"
          ></v-data-table>
        </v-card>
      </v-col>
    </v-row>
    <!--  モーダル  -->
    <v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="600px">
        <v-card min-height="175px">
          <v-card-title>
            <h3>本当にこのアカウントを削除してよろしいですか？</h3>
          </v-card-title>
          <v-card-actions>
            <v-btn color="error" @click="deleted" class="mr-auto">削除する</v-btn>
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
        data() {
            return {
                dialog: false,
                name: '管理者ユーザー1',
                email: 'dev-test@@example.com',
                gender: '男',
                tel: '09011112222',
                face: '2020年11月1日 10時22分',
                headers: [
                    {
                        text: '利用店舗',
                        value: 'name',
                    },
                    {text: '利用日時', value: 'theDateOfUse'},
                    {text: '発生金額', value: 'amount'},
                ],
                events: [
                    {
                        name: 'スキー会場',
                        theDateOfUse: '2020年11月2日 13時16分',
                        amount: '10,000円',
                    },
                    {
                        name: '旅館',
                        theDateOfUse: '2020年11月12日 11時22分',
                        amount: '20,000円',
                    },
                    {
                        name: 'ホテル',
                        theDateOfUse: '2020年12月2日 17時10分',
                        amount: '35,000円',
                    },
                    {
                        name: 'ゴルフ場',
                        theDateOfUse: '2020年13月2日 9時5分',
                        amount: '10,000円',
                    },
                    {
                        name: 'プール',
                        theDateOfUse: '2020年9月2日 10時55分',
                        amount: '2,000円',
                    },
                    {
                        name: 'イベント会場',
                        theDateOfUse: '2020年12月3日 19時3分',
                        amount: '8,000円',
                    },
                ]
            }
        },
        methods: {
            update() {
                this.updateSnackbar = true
            },
            deleteConfirm() {
                this.dialog = true
            },
            deleted() {
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