<script setup lang="ts">
  const widthInit = Math.round(Math.random() * 10);
  const heightInit = Math.round(Math.random() * 10);

  //Nuxtは、ref computedは オートインポート

  //リアクティブなテンプレート変数
  const width = ref(widthInit);
  const height = ref(heightInit);
  //計算結果をリアクティブ
  const area = computed(
    (): number => {
      return width.value * height.value;
    }
  );

//.valueプロパティへ代入、変数の値変更
setInterval(
  ():void => {
    width.value = Math.round(Math.random() * 10);
    height.value = Math.round(Math.random() * 10);
  },
  1000
);
</script>

<template>
  <p>縦が{{height}}で横が{{width}}の長方形の面積は{{area}}</p>

</template>
