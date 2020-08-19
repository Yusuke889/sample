<template>
  <div>
        <v-card
          outlined
        >
          <v-card-title>店舗詳細
            <v-spacer/>
            <v-btn
              color="error"
              @click="deleteConfirm"
            >
              アカウントを停止する
            </v-btn>
          </v-card-title>
          <v-card-text>
              <v-text-field
                value="スキー場運営店舗"
                label="名前"
                readonly
              ></v-text-field>

              <v-text-field
                value="08011119999"
                label="電話番号"
                readonly
              ></v-text-field>

              <v-text-field
                value="akasaka@example.com"
                label="メールアドレス"
                readonly
              ></v-text-field>

              <v-text-field
                value="店舗担当者氏名"
                label="担当者"
                readonly
              ></v-text-field>

              <v-text-field
                value="09011112222"
                label="担当者担当者電話番号"
                readonly
              ></v-text-field>

              <v-text-field
                value="https://google.com"
                label="ホームページURL"
                readonly
              ></v-text-field>

              <v-text-field
                value="承認済み"
                label="ステータス"
                readonly
              ></v-text-field>

              <v-text-field
                value="2020年10月20日 13時59分"
                label="申請承認日時"
                readonly
              ></v-text-field>

              <v-text-field
                value=" "
                label="退会日時"
                readonly
              ></v-text-field>

              <v-text-field
                value=" "
                label="アカウント停止日時"
                readonly
              ></v-text-field>
          </v-card-text>
        </v-card>

    <!--  モーダル  -->
    <v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="600px">
        <v-card min-height="175px">
          <v-card-title>
            <h3>本当にこのアカウントを停止してよろしいですか？<br>このユーザーはサービスを利用できなくなります</h3>
          </v-card-title>
          <v-card-actions>
            <v-btn color="error" @click="deleted" class="mr-auto">停止</v-btn>
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
                headers: [
                    {
                        text: '利用店舗',
                        value: 'name',
                    },
                    {text: '利用日時', value: 'theDateOfUse'},
                    {text: 'お支払い金額', value: 'amount'},
                ],
                events: [
                    {
                        name: 'イベント会場',
                        theDateOfUse: '2020年12月3日 19時3分',
                        amount: '8,000円',
                    },
                    {
                        name: 'ホテル',
                        theDateOfUse: '2020年12月2日 17時10分',
                        amount: '35,000円',
                    },
                    {
                        name: 'ゴルフ場',
                        theDateOfUse: '2020年12月2日 9時5分',
                        amount: '10,000円',
                    },
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
                        name: 'プール',
                        theDateOfUse: '2020年9月2日 10時55分',
                        amount: '2,000円',
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