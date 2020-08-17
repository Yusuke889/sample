<template>
  <div>
    <h1>管理者一覧</h1>
    <div class="my-2">
      <v-btn
        depressed
        color="primary"
        @click="dialog = true"
      >新規登録</v-btn>
    </div>
    <v-data-table
      :headers="headers"
      :items="items"
      item-key="name"
      class="elevation-1 row-pointer"
      hide-default-footer
      @click:row="onClickEvent"
    >
    </v-data-table>

    <!--  モーダル  -->
    <v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="600px">
        <v-card>
          <v-card-title>
            <span class="headline">管理者アカウント招待</span>
          </v-card-title>
          <v-card-text>
            <v-container>
              <v-row>
                <v-col cols="12">
                  <v-text-field label="登録メールアドレス" required></v-text-field>
                </v-col>
                <v-col cols="12" sm="6">
                  <v-select
                    :items="['閲覧', '管理者']"
                    label="権限選択"
                    required
                  ></v-select>
                </v-col>
                <v-col cols="12">
                  <v-btn
                    color="success"
                    required
                    @click="invitaiton">招待する</v-btn>
                </v-col>
              </v-row>
            </v-container>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialog = false">閉じる</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>

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
      招待完了しました
    </v-snackbar>
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
                    {text: 'アカウントネーム', value: 'name',},
                    {text: 'メールアドレス', value: 'email'},
                    {text: '権限', value: 'role'},
                ],
                items: [
                    {
                        name: '管理者ユーザー1',
                        email: 'admin+1@example.com',
                        role: '管理者',
                    },
                    {
                        name: '閲覧ユーザー1',
                        email: 'general+1@example.com',
                        role: '閲覧',
                    },
                    {
                        name: '閲覧ユーザー2',
                        email: 'general+2@example.com',
                        role: '閲覧',
                    },
                    {
                        name: '管理者ユーザー2',
                        email: 'admin+2@example.com',
                        role: '管理者',
                    },
                    {
                        name: '閲覧ユーザー3',
                        email: 'general+3@example.com',
                        role: '閲覧',
                    },
                    {
                        name: '管理者ユーザー3',
                        email: 'admin+3@example.com',
                        role: '管理者',
                    },
                    {
                        name: '閲覧ユーザー4',
                        email: 'general+4@example.com',
                        role: '閲覧',
                    },
                    {
                        name: '管理者ユーザー4',
                        email: 'admin+4@example.com',
                        role: '管理者',
                    },
                    {
                        name: '管理者ユーザー5',
                        email: 'admin+5@example.com',
                        role: '管理者',
                    },
                    {
                        name: '閲覧ユーザー5',
                        email: 'general+5@example.com',
                        role: '閲覧',
                    },
                ],
            }
        },

        methods: {
            // 第一引数にクリックした行のObjectが渡されるので処理を用意しておく
            onClickEvent(data) {
                console.log(data)
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