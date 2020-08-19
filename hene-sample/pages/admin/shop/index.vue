<template>
  <div>
    <v-card
      outlined
    >
      <v-card-title>
        店舗一覧
        <v-spacer />
        <v-text-field
          v-model="searchText"
          label="店舗名検索"
          sigle-line
        />
        <v-spacer />
        <v-text-field
          v-model="searchText"
          label="電話番号"
          sigle-line
        />
        <v-spacer />
        <v-select
          v-model="value"
          :items="selectItems"
          attach
          chips
          label="承認ステータス"
          multiple
          class="mw-100"
        ></v-select>
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
      :page.sync="page"
      :items-per-page="itemsPerPage"
      @page-count="pageCount = $event"
      item-key="name"
      hide-default-footer
      class="elevation-1 row-pointer"
      @click:row="onClickEvent"
    >
      <template v-slot:item.credit="{ item }">
        {{ item.credit ? '済' :'未'}}
      </template>
      <template v-slot:item.detail="{ item }">
        <v-btn
          color="primary"
          to="/admin/shop/1"
        >
          詳細
        </v-btn>
      </template>
    </v-data-table>
    <div class="text-center pt-2">
      <v-pagination v-model="page" :length="pageCount"></v-pagination>
    </div>
  </div>
</template>

<script>
    export default {
        data() {
            return {
                selectItems: ['未承認', '承認済み'],
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
                    {text: '店舗名', value: 'name',},
                    {text: '店舗電話番号', value: 'tel'},
                    {text: '担当者様氏名', value: 'person'},
                    {text: '承認ステータス', value: 'status'},
                    {text: '詳細', value: 'detail'},
                ],
                items: [
                    {
                        name: 'イベント会場',
                        tel: '09089924708',
                        person: '鈴木理恵',
                        status: '未申請',
                    },
                    {
                        name: 'ホテル',
                        tel: '09048709933',
                        person: '多田 秀次郎',
                        status: '申請中',
                    },
                    {
                        name: 'ゴルフ場',
                        tel: '09048709933',
                        person: '中田 孝彦',
                        status: '否認',
                    },
                    {
                        name: 'スキー会場',
                        tel: '09048709933',
                        person: '中田 義経',
                        status: '承認済み',
                    },
                    {
                        name: '旅館',
                        tel: '09048709933',
                        person: '細川 徳彦',
                        status: 'アカウント停止',
                    },
                    {
                        name: 'プール',
                        tel: '09048709933',
                        person: '川島 あさ美',
                        status: '承認済み',
                    },
                ],
                page: 1,
                pageCount: 1,
                itemsPerPage: 10,
            }
        },
        methods: {
            onClickEvent() {
                this.$router.push(`/admin/shop/1`)
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
  .mw-100 {
    max-width: 300px;
  }
</style>