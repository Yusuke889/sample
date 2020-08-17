<template>
  <div>
    <v-form>
      <v-card
        class="mx-auto"
        max-width="1200"
        outlined
      >
        <v-card-title>お知らせ編集</v-card-title>
        <v-card-text>
          <v-form
            ref="form"
            lazy-validation
          >
            <v-text-field
              v-model="title"
              :counter="100"
              label="タイトル"
              required
            ></v-text-field>

            <v-select
              v-model="value"
              :items="items"
              attach
              chips
              label="公開範囲"
              multiple
            ></v-select>

            <v-col cols="12">
              <v-row justify="center">
                <v-col
                  cols="6"
                  md="5"
                >
                  <Datetime
                    v-model="requestStartDate"
                    label="公開開始時刻"
                    :minute-interval="30"
                    :format="'YYYY-MM-DD HH:mm'"
                    :disabled-hours="['00', '01', '02', '03', '04', '05', '06', '07', '08', '17', '18', '19', '20', '21', '22', '23']"
                    :overlay="true"
                    :min-date="start"
                    :max-date="end"
                  ></Datetime>
                </v-col>
                ~
                <v-col
                  cols="6"
                  md="5"
                ><Datetime
                  v-model="requestEndDate"
                  label="公開終了時刻"
                  :minute-interval="30"
                  :format="'YYYY-MM-DD HH:mm'"
                  :disabled-hours="['00', '01', '02', '03', '04', '05', '06', '07', '08', '17', '18', '19', '20', '21', '22', '23']"
                  :overlay="true"
                  :min-date="start"
                  :max-date="end"
                ></Datetime>
                </v-col>
              </v-row>
            </v-col>

            <v-textarea
              color="cyan"
              label="お知らせ内容"
            ></v-textarea>
            <p>公開設定</p>
            <v-radio-group v-model="radios" :mandatory="false">
              <v-radio label="下書き" value="radio-1"></v-radio>
              <v-radio label="公開" value="radio-2"></v-radio>
            </v-radio-group>
            <v-btn
              color="success"
              class="mr-4"
              @click="update"
            >
              更新する
            </v-btn>
            <v-btn
              color="error"
              class="mr-8"
              @click="deleteConfirm"
            >
              削除する
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
            <h3>本当にこのお知らせを削除してもよろしいですか？</h3>
          </v-card-title>
          <v-card-actions>
            <v-btn color="error" @click="deleted" class="mr-auto">削除</v-btn>
          </v-card-actions>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialog = false">キャンセル</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
    import moment from 'moment'
    import Datetime from 'vue-ctk-date-time-picker';
    import '@/node_modules/vue-ctk-date-time-picker/dist/vue-ctk-date-time-picker.css';

    export default {
        components: {
            Datetime
        },
        data() {
            return {
                dialog: false,
                title: '新規機能リリースのお知らせ',
                releaseData: '2020-09-01',
                lastReleaseDate: '2020-09-31',
                status: 'editing',
                announceScope: ['userWeb'],
                items: ['ユーザーWeb', '店舗web', '店舗IOS'],
                value: ['userWeb', 'shopWeb', 'shopiOS'],
                requestStartDate: '',
                requestEndDate: '',
                radios: 'radio-1'
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
        },
        computed: {
            start() {
                // min-date に明日の9時を指定
                const start = moment().add(1, 'days').hour(8)
                return start.format('YYYY-MM-DDTHH:mm:ss')
            },
            end() {
                // max-date に min-date から3ヶ月後を指定
                const start = moment(this.start)
                const end = start.add(3, 'months').endOf('day')
                return end.format('YYYY-MM-DDTHH:mm:ss')
            }
        }
    }
</script>

<style scoped>
  .mr-auto{
    margin: auto;
  }
</style>