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
  <button type="button" @click="addCount">count is: {{ count }}</button>


</template>

<style>
.active {
  color: red;
  font-weight: 900;
}
</style>