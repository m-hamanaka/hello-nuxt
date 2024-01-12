
<!-- ボタンをクリックすると、msg の値が "Hello" とボタンのテキストである
"こんにちは" と組み合わされて更新され、それが表示されるという動作 -->

<script setup lang="ts">

  //ref 関数を使用して、msg というリアクティブな変数を作成し、初期値を "まだ" に設定
  const msg = ref("まだ");

  //ボタンがクリックされたときに呼び出される関数 onButtonClick を定義
  //メソッドを定義 アロー関数を変数に代入 constメソッド名 = (引数): void => {
  //label と event という2つの引数を受け取り、
  //ボタンのテキストとして label を、
  //ボタン要素のテキストコンテンツとして event.target から取得したものを組み合わせて、
  //msg の値を更新
  const onButtonClick = (label: string, event: Event): void => {

    //TypeScript における型キャストの書き方
    //イベントオブジェクト (event) から target プロパティを取得し、
    //その値を HTMLButtonElement 型にキャスト
    const target = event.target as HTMLButtonElement;
    const text = target.innerText;
    msg.value = `${label}と${text}`;
  };
</script>

<template>
  <!-- ボタンがクリックされると更新 -->
  <p>{{ msg }}</p>

  <!-- メソッドをv-onディレクティブでイベントハンドラとする -->
  <!-- v-on:click ディレクティブは、クリックイベントが発生したときに指定されたメソッドを呼び出す -->
  <button v-on:click="onButtonClick('Hello', $event)">こんにちは</button>

  <!-- $event は、クリックイベント自体を引数として渡すための特殊な構文
  "Hello" という文字列を label として onButtonClick メソッドに渡す -->
</template>
