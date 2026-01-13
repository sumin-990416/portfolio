<template>
  <div>
    <div id="fullpage" class="fullpage-wrapper">
      <div class="section">
        <SectionZero />
      </div>
      <div class="section">
        <SectionOne />
      </div>
      <div class="section">
        <div class="slide">
          <SectionTwoBase />
        </div>
        <div class='slide'>
          <SectionTwo />
        </div>
        <div class='slide'>
          <SectionTwo2 />
        </div>
        <div class='slide'>
          <SectionTwo3 />
        </div>
        <div class='slide'>
          <SectionTwo4 />
        </div>
      </div>
      <div class="section">
        <SectionThree />
      </div>
      <div class="section">
        <SectionFour />
      </div>
      <div class="section">
        <SectionFive />
      </div>
    </div>
  </div>
</template>

<script setup>
// ... script 부분은 그대로 유지하세요 ...
import { onMounted, onBeforeUnmount } from 'vue';
import fullpage from 'fullpage.js';

import SectionOne from './sections/SectionOne.vue';
import SectionTwo from './sections/SectionTwo.vue';
import SectionTwo2 from './sections/SectionTwo2.vue';
import SectionTwo3 from './sections/SectionTwo3.vue';
import SectionTwo4 from './sections/SectionTwo4.vue';
import SectionThree from './sections/SectionThree.vue';
import SectionFour from './sections/SectionFour.vue';
import SectionZero from './sections/SectionZero.vue';
import SectionTwoBase from './sections/SectionTwoBase.vue';

let fpInstance;

onMounted(() => {
  fpInstance = new fullpage('#fullpage', {
    autoScrolling: true,
    scrollHorizontally: true,
    navigation: true,
    controlArrows: true, 
    anchors: ['home', 'about', 'portfolio', 'contact', 'section5'],
  });
});

onBeforeUnmount(() => {
  if (fpInstance) fpInstance.destroy('all');
});
</script>

<style>
/* Jua 폰트 불러오기 */
@import url('https://fonts.googleapis.com/css2?family=Jua&display=swap');
@import 'fullpage.js/dist/fullpage.min.css';

/* 전체 폰트 적용 */
body {
  font-family: "Jua", sans-serif;
  margin: 0;
  /* 전체 배경 이미지 설정 */
  background-image: url('/background.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
  color: #fff;
}

.fullpage-wrapper {
  box-sizing: border-box;
}

.section {
  text-align: center;
  font-size: 32px;
  background: transparent !important; /* 각 섹션 배경을 투명하게 해서 body 배경이 보이게 */
}


/* 화살표 커스텀 스타일 */
.fp-controlArrow {
  border: none !important;
  width: 30px !important;
  height: 30px !important;
  border-top: 8px solid #000 !important;
  border-right: 8px solid #000 !important;
  border-radius: 5px;
  transition: all 0.2s ease;
  opacity: 0.4;
  margin-top: -15px !important;
}

.fp-controlArrow:hover {
  opacity: 1;
  transform: scale(1.1);
}

.fp-controlArrow.fp-prev {
  left: 40px !important;
  transform: rotate(-135deg); 
}

.fp-controlArrow.fp-next {
  right: 40px !important;
  transform: rotate(45deg);
}
</style>