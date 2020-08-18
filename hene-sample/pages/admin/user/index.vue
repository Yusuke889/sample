<template>
  <div>
      <v-card
        outlined
      >
        <v-card-title>
          ユーザー一覧
          <v-spacer />
          <v-text-field
            v-model="searchText"
            label="名前検索"
            sigle-line
          />
          <v-spacer />
          <v-text-field
            v-model="searchText"
            label="電話番号"
            sigle-line
          />
          <v-spacer />
          <v-btn
            color="success"
            class="mr-4"
          >
            検索
          </v-btn>
          <v-spacer />
          <v-btn
            color="secondary"
            class="mr-4"
          >
            CSVダウンロード
          </v-btn>
        </v-card-title>
      </v-card>
    <v-data-table
      :headers="headers"
      :items="items"
      item-key="name"
      class="elevation-1 row-pointer"
      @click:row="onClickEvent"
    >
      <template v-slot:item.face="{ item }">
        {{ item.face ? '済' :'未'}}
      </template>
      <template v-slot:item.credit="{ item }">
        {{ item.credit ? '済' :'未'}}
      </template>
      <template v-slot:item.status="{ item }">
        <span v-if="item.face && item.credit && !item.deleteAt">登録</span>
        <span v-else-if="!(item.face && item.credit)">仮登録</span>
        <span v-else="item.deleteAt">退会済み</span>
      </template>
    </v-data-table>
  </div>
</template>

<script>
    export default {
        data() {
            return {
                dialog: false,
                snackbar: false,
                show1: true,
                color: '',
                mode: '',
                text: 'パスワードの変更を完了しました',
                timeout: 6000,
                x: null,
                y: 'top',
                headers: [
                    {text: '名前', value: 'name',},
                    {text: '電話番号', value: 'tel'},
                    {text: '顔情報登録', value: 'face'},
                    {text: 'クレジットカード登録', value: 'credit'},
                    {text: 'ステータス', value: 'status'},
                ],
                items: [
                    {
                        name: '堀江 文之',
                        tel: '09089924708',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: '2020-01-01 21:30:00',
                    },
                    {
                        name: '長沢 譲介',
                        tel: '09048709933',
                        face: '2020-01-01 21:00:00',
                        credit: null,
                        deleteAt: null,
                    },
                    {
                        name: '根本 真由美',
                        tel: '08090712376',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '杉山 秀一',
                        tel: '09040959978',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '川野 光保',
                        tel: '09029050379',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '関根 敬吉',
                        tel: '07064009325',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '茂木 史男',
                        tel: '07071637608',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '岡野 満生',
                        tel: '09040376155',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '森山 謙三',
                        tel: '09083610749',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '向井 友恵',
                        tel: '07053006895',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '古田 征四郎',
                        tel: '09048478788',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '高松 歩',
                        tel: '09009635823',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '畠山 多美子',
                        tel: '09017477221',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '今野 慎治',
                        tel: '09047889520',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '中尾 護',
                        tel: '09005024684',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                    {
                        name: '福本 真由美',
                        tel: '09041942227',
                        face: '2020-01-01 21:00:00',
                        credit: '2020-01-01 21:30:00',
                        deleteAt: null,
                    },
                ],
            }
        },

        methods: {
            onClickEvent() {
                this.$router.push(`/admin/user/1`)
            },
            /**
             * 招待時の処理
             */
            invitaiton() {
                this.dialog = false
                this.snackbar = true
            }
        }
    }
</script>

<style lang="css" scoped>
  .row-pointer >>> tbody tr :hover {
    cursor: pointer;
  }
</style>