<template>
  <main class="carousel" @click="init">
    <ul class="carousel-list">
      <button class="carousel-prev" @click="carouselPrev">prev</button>
      <button class="carousel-next" @click="carouselNext">next</button>

      <li
        v-for="(itemData, index) in itemsData"
        :key="index"
        class="carousel-item"
        :data-pos="itemData.pos"
        ref="items"
      >
        <div class="carousel-content">
          <div class="carousel-title">{{ "title" + index }}</div>
          <div class="carousel-pic"></div>
          <div class="carousel-btn"></div>
        </div>
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  data() {
    return {
      itemsData: [
        { pos: -2, imgSrc: "https://picsum.photos/id/100/700/500" },
        { pos: -1, imgSrc: "https://picsum.photos/id/154/700/500" },
        { pos: 0, imgSrc: "https://picsum.photos/id/38/700/500" },
        { pos: 1, imgSrc: "https://picsum.photos/id/173/700/500" },
        { pos: 2, imgSrc: "https://picsum.photos/id/44/700/500" },
      ],
    };
  },

  methods: {
    carouselPrev() {
      for (const item of this.$refs.items) {
        const itemPos = Number(item.dataset.pos);

        itemPos === -2
          ? (item.dataset.pos = 2)
          : (item.dataset.pos = itemPos - 1);
      }
    },

    carouselNext() {
      for (const item of this.$refs.items) {
        const itemPos = Number(item.dataset.pos);

        itemPos === 2
          ? (item.dataset.pos = -2)
          : (item.dataset.pos = itemPos + 1);
      }
    },
  },
};
</script>

<style scoped lang="scss">
// 這裡開始是carousel的功能與版型，並不是carousel中的內容，修改要注意
.carousel {
  margin-top: 200px; // 可改
}

.carousel-list {
  position: relative;
  list-style-type: none;
  display: flex;
  justify-content: center;

  width: 500px; // 寬度影響左右方向鍵位置，更改時要注意
  margin: 0 auto;
}

.carousel-prev,
.carousel-next {
  width: 50px; // 測試
  height: 50px; // 測試
  position: absolute;
  z-index: 10;
}

.carousel-prev {
  left: 0;
}

.carousel-next {
  right: 0;
}

.carousel-item {
  position: absolute;
  transition: transform 500ms;
  background-color: #fff;

  width: 400px; // 可改
  min-height: 500px; // 可改 注意標題長度

  border: 1px solid #000; // 測試
}

li[data-pos="0"] {
  z-index: 9;
}
li[data-pos="-1"],
li[data-pos="1"] {
  z-index: 6;
}
li[data-pos="-2"],
li[data-pos="2"] {
  z-index: 3;
}

li[data-pos="-1"] {
  transform: translateX(-50%) scale(0.9);
}
li[data-pos="1"] {
  transform: translateX(50%) scale(0.9);
}
li[data-pos="-2"] {
  transform: translateX(-90%) scale(0.8);
}
li[data-pos="2"] {
  transform: translateX(90%) scale(0.8);
}

li[data-pos="-1"]::after,
li[data-pos="1"]::after {
  background-color: rgba(0, 0, 0, 0.25);
}
li[data-pos="-2"]::after,
li[data-pos="2"]::after {
  background-color: rgba(0, 0, 0, 0.5);
}

// 這裡開始可以放carousel中的內容

.carousel-pic {
  width: 100%; // 測試
  height: 300px; // 測試
  background-color: #fa0; // 測試
}
</style>
