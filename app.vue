<script setup lang="ts">
  const cocktailNo = ref(1);
  const priceMsg = ref("");

  //watch の第一引数には監視対象のリアクティブデータや式、
  //第二引数には変更があったときに実行されるコールバック関数が指定
  watch(() => cocktailNo.value, (newValue, oldValue) => {
    // cocktailNo が変更されたときに実行されるコード
    priceMsg.value = getCocktailInfo(newValue);
  });

  function getCocktailInfo(cocktailNo: number): string {
    // 実際のロジックを実装し、カクテル番号に基づいて価格情報を取得する
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
