<script setup>
let message = 'Hello World!!!';

const test = '<h2>Hello World!!!</h2>';

const upperCase = () => {
  message = message.toUpperCase();
  upperCase();
};

const link = 'https://google.com';

const isActive = false;

import { ref } from 'vue';
const count = ref(0);

const addCount = () => {
  count.value++;
};

import { reactive, computed } from 'vue';

const state = reactive({
  count: 0,
});

const addCounter = () => {
  state.count++;
};

// 10.入力フォーム
const clickButton = () => {
  console.log(message);
};

// 11.Computedプロパティ
const user = reactive({
  firstName: 'John',
  lastName: 'Doe',
});
const fullName = computed(() => `${user.firstName} ${user.lastName}`);

// usersのadminがtrueのレコードだけ取り出す処理
const users = [
  { id: 1, name: 'John Doe', email: 'john@test.com', admin: true },
  { id: 2, name: 'Jane Doe', email: 'jane@example.com', admin: false },
  { id: 3, name: 'Kevin MacDonald', email: 'kevin@test.com', admin: false },
];
const adminUsers = computed(() => users.filter((user) => user.admin === true));


</script>

<template>
  <h1>Vue 3 入門</h1>

  <!-- マスタッシュで変数を表示できる -->
  <p>{{ message }}</p>

  <!-- JavaScriptコードを実行できる -->
  <div>{{ message.length * 10 }}</div>

  <!-- 三項演算子も使用できる -->
  <div>{{ message.length > 10 ? 'Long' : 'Short' }}</div>

  <!-- v-textディレクティブで変数をブラウザ上に表示させることができる -->
  <p v-text="message"></p>

  <!-- v-htmlディレクティブ 変数をタグとして扱い、表示させることができる -->
  <div v-text="test"></div>
  <div v-html="test"></div>

  <!-- v-bindディレクティブでhtmlタグの属性の設定を行うことができる -->
  <div>
    <a v-bind:href="link">Google</a>
  </div>
  <!-- hrefに変数が設定できるということはユーザの行う行動によって変数の値を変更することでユーザの行動に応じたリンク先を設定できるようになることを意味します。ボタンをクリックするとGoogleのリンクからYahooへのリンクへと変更することもできます。 -->
  <!-- imgタグのsrc属性やbuttonタグのdisabled属性でもよく利用される -->


  <p class="active">test</p>
  <p :class="{ active: isActive }">v-bindで&lt;style&gt;.activeクラスを呼び出す</p>

  <!-- ref関数を利用してreactiveな変数を設定する -->
  <button type="button" @click="addCount">ref関数 count is: {{ count }}</button>

  <!-- reactive関数を利用してreactiveな変数を設定する -->
  <button type="button" @click="addCounter">
    reactive関数 count is: {{ state.count }}
  </button>

  <h2>10.入力フォーム</h2>
  <input v-model="message" />
  <div><button @click="clickButton">Click</button></div>


  <h2>11.Computedプロパティ</h2>
  <h3>Computedを使用しない fullName: {{ user.firstName }} {{ user.lastName }}</h3>
  <h3>Computedを使用 fullName: {{ fullName }}</h3>

  <div v-for="user in adminUsers" :key="user.id">
    <div>{{ user.id }} {{ user.name }} {{ user.email }}</div>
  </div>

</template>

<style>
.active {
  color: red;
  font-weight: 900;
}
</style>
