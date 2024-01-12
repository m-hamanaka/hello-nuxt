<script setup lang="ts">

  //Nuxt.jsのオートインポートが適用
  //import { watchEffect, ref } from 'vue';

  const cocktailNo = ref(1);
  const priceMsg = ref("");

  //watchEffect を使用して cocktailNo の変更を監視し、
  //その変更に応じて getCocktailInfo メソッドを呼び出して priceMsg を更新
  watchEffect(() => {
    priceMsg.value = getCocktailInfo(cocktailNo.value);
  });

  function getCocktailInfo(cocktailNo: number): string {
    // ここで実際のロジックを実装し、カクテル番号に基づいて価格情報を取得
    // 仮に、ダミーのロジックとして定義
    return `カクテル番号 ${cocktailNo} の価格情報です。`;
  }
</script>

<template>
  <div>
    <label for="cocktailNo">カクテル番号：</label>
    <input id="cocktailNo" v-model="cocktailNo" type="number" />

    <p>{{ priceMsg }}</p>
  </div>
</template>
