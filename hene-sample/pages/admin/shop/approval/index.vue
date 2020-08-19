<template>
  <div>
    <h1>承認依頼一覧</h1>
    <v-data-table
      :headers="headers"
      :items="items"
      :page.sync="page"
      :items-per-page="itemsPerPage"
      @page-count="pageCount = $event"
      item-key="name"
      hide-default-footer
      class="elevation-1 row-pointer"
    >
      <template v-slot:item.detail="{ item }">
        <v-btn
          color="info"
          class="black--text"
          @click="snackbar = true"
        >
          詳細へ
        </v-btn>
      </template>
      <template v-slot:item.operation="{ item }">
        <v-btn
          color="primary"
          class="black--text"
          @click="approvalDialog = true"
        >
          承認
        </v-btn>
        <v-btn
          color="warning"
          class="black--text"
          @click="nonApprovalDialog = true"
        >
          否認
        </v-btn>
      </template>
    </v-data-table>
    <div class="text-center pt-2">
      <v-pagination v-model="page" :length="pageCount"></v-pagination>
    </div>

    <!--  承認モーダル  -->
    <v-row justify="center">
      <v-dialog v-model="approvalDialog" persistent max-width="600px">
        <v-card min-height="175px">
          <v-card-title>
            <h3>この店舗を承認します<br>よろしいですか？</h3>
          </v-card-title>
          <v-card-actions>
            <v-btn color="success" @click="approval" class="mr-auto">承認する</v-btn>
          </v-card-actions>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="approvalDialog = false">閉じる</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>


    <!--  承認モーダル  -->
    <v-row justify="center">
      <v-dialog v-model="nonApprovalDialog" persistent max-width="600px">
        <v-card min-height="175px">
          <v-card-title>
            <h3>この店舗を否認します<br>よろしいですか？</h3>
          </v-card-title>
          <v-card-actions>
            <v-btn color="error" @click="approval" class="mr-auto">否認する</v-btn>
          </v-card-actions>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="nonApprovalDialog = false">閉じる</v-btn>
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
                approvalDialog: false,
                nonApprovalDialog: false,
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
                    {text: '電話番号', value: 'tel'},
                    {text: '承認依頼申請時刻', value: 'approvalTime'},
                    {text: '詳細', value: 'detail'},
                    {text: '操作', value: 'operation'},
                ],
                items: [
                    {
                        name: 'テスト店舗',
                        tel: '09041942227',
                        approvalTime: '2020-01-01 21:00:00',
                        operation: '2020-01-01 21:30:00',
                    },
                ],
                page: 1,
                pageCount: 1,
                itemsPerPage: 10,
            }
        },
        methods: {
            /**
             * 招待時の処理
             */
            invitaiton() {
                this.approvalDialog = false
                this.snackbar = true
            }
        }
    }
</script>

<style scoped>
  .mr-auto {
    margin: auto;
  }
</style>