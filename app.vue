<script setup lang="ts">
  const widthInit = Math.round(Math.random() * 10);
  const heightInit = Math.round(Math.random() * 10);

  //縦横の長さをまとめたひとつのオブジェクトリレラルを用意
  //オブジェクトをまとめてリアクティブなテンプレート変数にする
  const rectangle = reactive({
    width: widthInit,
    height: heightInit
  });

  //計算結果をリアクティブ
  const area = computed(
    (): number => {
      return rectangle.width * rectangle.height;
    }
  );

//オブジェクト内のプロパティという形でアクセス
setInterval(
  ():void => {
    rectangle.width = Math.round(Math.random() * 10);
    rectangle.height = Math.round(Math.random() * 10);
  },
  1000
);
</script>

<template>
  <p>縦が{{rectangle.height}}で横が{{rectangle.width}}の長方形の面積は{{area}}</p>

</template>
