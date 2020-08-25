<template>
  <div>
    <h1 class="font-weight-bold display-3 basil--text align-center">マイページ</h1>
    <v-card>
      <v-tabs
        v-model="tab"
        background-color="transparent"
        color="basil"
        mobile-breakpoint
      >
        <v-tab
          v-for="item in items"
          :key="item"
        >
          {{ item }}
        </v-tab>
      </v-tabs>
      <v-tabs-items v-model="tab">
        <v-tab-item
          v-for="item in items"
          :key="item"
        >
          <v-card
            flat
          >
            <template v-if="item === '基本情報'">
                <v-card-text>
                  <v-text-field
                    value="田中太郎"
                    label="名前"
                    readonly
                  ></v-text-field>

                  <v-text-field
                    value="09011112222"
                    label="電話番号"
                    readonly
                  ></v-text-field>

                  <v-text-field
                    value="test@example.com"
                    label="メールアドレス"
                    readonly
                  ></v-text-field>

                  <v-select
                    :items="genders"
                    label="性別"
                  ></v-select>

              </v-card-text>
              <v-card-actions>
                <v-btn
                  class="info"
                >
                  アカウント情報を更新する
                </v-btn>
              </v-card-actions>
            </template>
            <template v-if="item === '顔情報登録'">
              <v-container>
                <v-row justify="space-between">
                  <v-col cols="auto">
                    <img
                      src="/ユーザー顔画像300x300.png"
                    >
                  </v-col>
                </v-row>
              </v-container>

              <v-card-actions>
                <v-btn
                  class="secondary"
                >
                  アップロード
                </v-btn>
                <v-btn
                  class="info"
                >
                  登録または更新
                </v-btn>
              </v-card-actions>
            </template>
            <template v-if="item === 'クレジットカード登録・更新'">
              <v-card-text>
                <v-text-field
                  value="1234567890123456"
                  label="カード番号"
                ></v-text-field>
                <v-text-field
                  value="月/年"
                  label="有効期限"
                ></v-text-field>
                <v-text-field
                  value="CVC"
                  label="CVC番号"
                ></v-text-field>
                <v-text-field
                  value="TARO YAMADA"
                  label="名前"
                ></v-text-field>
              </v-card-text>
              <v-card-acitons>
                <v-btn
                  class="info"
                >
                  登録
                </v-btn>
              </v-card-acitons>
            </template>
          </v-card>
        </v-tab-item>
      </v-tabs-items>
    </v-card>
  </div>
</template>

<script>
    export default {
        layout: 'userDefault',
        name: 'userDefaultIndex',
        data () {
            return {
                tab: null,
                items: [
                    '基本情報', '顔情報登録', 'クレジットカード登録・更新',
                ],
                genders:['男','女'],
            }
        },
    }
</script>