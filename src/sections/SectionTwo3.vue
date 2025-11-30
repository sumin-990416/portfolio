<template>
  <div class="section-container">
    
    <div class="glass-board">
      <div class="container-fluid">
        
        <div class="row mb-4 justify-content-center">
          <div class="col-12 text-center">
            <h2 class="section-title"> AI Agent를 활용한 공공업무 인수인계 지원 서비스</h2>
            <p class="section-subtitle">카드를 클릭하면 뒷면(결과)을 볼 수 있습니다.</p>
          </div>
        </div>

        <div class="flip-card" @click="toggleFlip">
          <div class="flip-card-inner" :class="{ 'is-flipped': isFlipped }">
            
            <div class="flip-card-front">
              <img src="/sec2_3.jpg" alt="앞면" />
            </div>

            <div class="flip-card-back">
              <img src="/sec2_3_2.jpg" alt="뒷면" />
            </div>

          </div>
        </div>

      </div>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue';

const isFlipped = ref(false);

const toggleFlip = () => {
  isFlipped.value = !isFlipped.value;
};
</script>

<style scoped>
@import url("https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css");

/* 컨테이너 */
.section-container {
  width: 100%;
  height: 100%;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 유리 질감 배경 */
.glass-board {
  width: 100%;
  height: 900px;
  /* 배경을 좀 더 어둡게 해서 타이틀 강조 */
  background-color: rgba(20, 20, 30, 0.4); 
  backdrop-filter: blur(10px);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 30px;
}

/* 제목 스타일 */
.section-title {
  font-family: "Pretendard", sans-serif;
  font-size: 3rem;
  font-weight: 900;
  color: #ffffff;
  margin-bottom: 5px;
  text-shadow: 0 2px 10px rgba(255,255,255,0.5);
}

.section-subtitle {
  font-family: "Pretendard", sans-serif;
  font-size: 1.2rem;
  color: #fff;
  margin-bottom: 30px;
  font-weight: 600;
  animation: bounce 2s infinite;
}

/* ⭐ 플립 카드 (반응형) ⭐ */
.flip-card {
  width: 80vw;
  max-width: 1100px;
  aspect-ratio: 16 / 9; /* 16:9 비율 고정 */
  
  perspective: 1000px;
  cursor: pointer;
  margin: 0 auto;
  
  /* 카드 배경 투명화 (잔상 방지) */
  background-color: transparent;
}

/* 내부 회전체 */
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  transform-style: preserve-3d;
  
  /* 🛑 [핵심 1] 렌더링 최적화 힌트 */
  will-change: transform; 
}

/* 뒤집힘 상태 */
.flip-card-inner.is-flipped {
  transform: rotateY(180deg);
}

/* 앞면, 뒷면 공통 설정 */
.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 97%;
  height: 97%;
  
  /* 🛑 [핵심 2] 뒷면 숨김 처리 */
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  
  /* 🛑 [핵심 3] 검은 선 방지용 흰색 그림자 추가 */
  /* 카드 테두리(1px)를 흰색 그림자로 덮어서 틈새를 메움 */
  box-shadow: 0 0 0 1px #fff, 0 15px 40px rgba(0,0,0,0.3);
  
  /* 🛑 [핵심 4] 안티앨리어싱 강제 적용 */
  outline: 1px solid transparent;
  
  /* 🛑 [핵심 5] 3D 가속 활성화 */
  transform: translate3d(0, 0, 0);

  border-radius: 20px;
  overflow: hidden;
  

}

/* 앞면 */
.flip-card-front {
  z-index: 2;
}

/* 뒷면 (180도 회전) */
.flip-card-back {
  transform: rotateY(180deg);
}

/* 이미지 스타일 */
.flip-card-front img,
.flip-card-back img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block; /* 하단 공백 제거 */
  
  /* 이미지에도 뒷면 숨김 적용 */
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

/* 바운스 애니메이션 */
@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
  40% { transform: translateY(-5px); }
  60% { transform: translateY(-3px); }
}

/* 모바일 대응 */
@media (max-width: 768px) {
  .flip-card {
    width: 95vw;
  }
}
</style>