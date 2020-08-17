<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="items"
      item-key="name"
      class="elevation-1 row-pointer"
      hide-default-footer
      @click:row="onClickEvent"
    >
    </v-data-table>
  </div>
</template>

<script>
    export default {
        data() {
            return {
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
        }
    }
</script>

<style lang="css" scoped>
  .row-pointer >>> tbody tr :hover {
    cursor: pointer;
  }
</style>