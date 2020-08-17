<template>
  <div>

  <v-form>
    <v-card
      class="mx-auto"
      max-width="800"
      outlined
    >
      <v-card-title>アカウント編集</v-card-title>
      <v-card-text>
        <v-form
          ref="form"
          lazy-validation
        >
          <v-text-field
            v-model="name"
            :counter="100"
            label="名前"
            required
          ></v-text-field>

          <v-text-field
            v-model="email"
            label="メールアドレス"
            required
          ></v-text-field>

          <v-select
            v-model="select"
            :items="['閲覧', '管理者']"
            label="権限"
            required
          ></v-select>

          <v-btn
            color="success"
            class="mr-4"
            @click="update"
          >
            アカウント情報を更新する
          </v-btn>
          <v-btn
            color="error"
            class="mr-8"
            @click="deleteConfirm"
          >
            アカウントを削除する
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

    <v-snackbar
      v-model="updateSnackbar"
      :bottom="y === 'bottom'"
      :left="x === 'left'"
      :right="x === 'right'"
      :timeout="timeout"
      :top="y === 'top'"
    >
      アカウント情報を変更しました。
    </v-snackbar>

    <v-snackbar
      v-model="deleteSnackbar"
      :bottom="y === 'bottom'"
      :left="x === 'left'"
      :right="x === 'right'"
      :timeout="timeout"
      :top="y === 'top'"
    >
      アカウントを削除しました。
    </v-snackbar>
  </div>
</template>

<script>
    export default {
        data () {
            return {
                dialog: false,
                name:'管理者ユーザー1',
                email:'admin+1@example.com',
                select:'管理者',
                show1: true,
                snackbar: false,
                timeout: 3000,
                x: null,
                y: 'top',
                updateSnackbar: false,
                deleteSnackbar: false
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