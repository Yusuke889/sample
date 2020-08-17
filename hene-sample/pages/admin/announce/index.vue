<template>
  <div>
    <h1>お知らせ一覧</h1>
    <div class="my-2">
      <v-btn
        depressed
        color="primary"
        to="/admin/announce/create"
      >新規登録
      </v-btn>
    </div>
    <template v-for="item in items">
      <div style="margin-top: 30px;margin-bottom: 30px">
        <v-card
          max-width="1200"
          elevation="10"
          link="true"
          to="/admin/announce/1"
        >
          <v-card-text>
            <div>タイトル</div>
            <p class="display-1 text--primary">
              {{item.title}}
            </p>
            <p>状態</p>
            <p class="text--primary">
              {{item.status === 'editing'? '下書き':'公開'}}
            </p>
            <div>公開範囲</div>
            <div class="text-left">
              <v-chip
                class="ma-2"
              >
                ユーザーweb
              </v-chip>
              <v-chip
                class="ma-2"
                color="primary"
              >
                店舗Web
              </v-chip>
              <v-chip
                class="ma-2"
                color="secondary"
              >
                店舗iOS
              </v-chip>
            </div>
            <div>公開期限</div>
            <p class="text--primary">
              {{item.releaseData}} 〜 {{item.lastReleaseDate}}
            </p>
          </v-card-text>
        </v-card>
      </div>
    </template>
  </div>
</template>

<script>
    export default {
        data() {
            return {
                items: [
                    {
                        title: '新規機能リリースのお知らせ',
                        releaseData: '2020-09-01',
                        lastReleaseDate: '2020-09-31',
                        status: 'editing',
                        announceScope: ['userWeb']
                    },
                    {
                        title: 'システムメンテナンスのお知らせ',
                        releaseData: '2020-10-01',
                        lastReleaseDate: '2020-10-31',
                        status: 'fixed',
                        announceScope: ['shopWeb', 'shopiOS']
                    },
                    {
                        title: 'システムメンテナンスのお知らせ',
                        releaseData: '2020-10-01',
                        lastReleaseDate: '2020-10-31',
                        status: 'fixed',
                        announceScope: ['userWeb', 'shopWeb', 'shopiOS']
                    },
                ]
            }
        },
    }
</script>