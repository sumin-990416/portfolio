<template>
  <div class="section-container">
    <div class="glass-board">
      <div class="container-fluid h-100 d-flex flex-column justify-content-center align-items-center">
        
        <div class="card-stack">
          <div class="bg-card card-1"></div>
          <div class="bg-card card-2"></div>
          
          <div class="main-card">
            <span class="sub-badge">PORTFOLIO</span>
            <h1 class="cover-title">MY PROJECTS</h1>
            <p class="cover-desc">
              데이터 분석부터 AI 모델링, 개발 그리고 기획까지.<br>
              치열하게 고민하고 해결한 결과물들을 소개합니다.
            </p>
            
            <div class="stats-row">
              <div class="stat-item">
                <span class="number">05</span>
                <span class="label">Projects</span>
              </div>
              <div class="divider"></div>
              <div class="stat-item">
                <span class="number">100%</span>
                <span class="label">Passion</span>
              </div>
            </div>
          </div>
        </div>

        <div class="slide-hint">
          <span>SLIDE TO VIEW</span>
          <div class="arrow-anim">👉</div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
// 로직 없음
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

.glass-board {
  width: 100%;
  height: 800px;
  /* 배경을 좀 더 어둡게 해서 타이틀 강조 */
  background-color: rgba(20, 20, 30, 0.4); 
  backdrop-filter: blur(10px);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 30px;
}

/* ⭐ 카드 스택 레이아웃 ⭐ */
.card-stack {
  position: relative;
  width: 600px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 뒤에 깔리는 장식용 카드들 */
.bg-card {
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 30px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 15px 35px rgba(0,0,0,0.2);
}

/* 왼쪽으로 살짝 기운 카드 */
.card-1 {
  transform: rotate(-5deg) scale(0.95);
  z-index: 1;
  background: linear-gradient(135deg, rgba(255,255,255,0.1), rgba(255,255,255,0.05));
}

/* 오른쪽으로 살짝 기운 카드 */
.card-2 {
  transform: rotate(5deg) scale(0.95);
  z-index: 2;
  background: linear-gradient(135deg, rgba(255,255,255,0.15), rgba(255,255,255,0.05));
}

/* ⭐ 메인 카드 ⭐ */
.main-card {
  position: relative;
  width: 100%;
  height: 100%;
  z-index: 3;
  
  background: rgba(255, 255, 255, 0.95); /* 흰색 배경 */
  border-radius: 30px;
  padding: 50px;
  
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  
  box-shadow: 0 20px 50px rgba(0,0,0,0.3);
  transform: translateY(0);
  transition: transform 0.3s ease;
}

.main-card:hover {
  transform: translateY(-10px); /* 호버 시 둥실 */
}

/* 작은 뱃지 */
.sub-badge {
  font-family: "Pretendard", sans-serif;
  font-size: 0.9rem;
  font-weight: 800;
  color: #666;
  letter-spacing: 4px;
  margin-bottom: 10px;
  border: 2px solid #ddd;
  padding: 5px 15px;
  border-radius: 20px;
}

/* 타이틀 (그라데이션 효과) */
.cover-title {
  font-family: "Pretendard", sans-serif;
  font-size: 4rem;
  font-weight: 900;
  margin-bottom: 20px;
  
  /* 텍스트 그라데이션 (우주 색감) */
  background: linear-gradient(45deg, #2b5876, #4e4376, #F08EFC);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  
  filter: drop-shadow(0 2px 5px rgba(0,0,0,0.1));
}

.cover-desc {
  font-family: "Pretendard", sans-serif;
  font-size: 1.1rem;
  color: #555;
  line-height: 1.6;
  margin-bottom: 40px;
  font-weight: 500;
  word-break: keep-all;
}

/* 하단 통계 */
.stats-row {
  display: flex;
  align-items: center;
  gap: 30px;
}

.stat-item {
  display: flex;
  flex-direction: column;
}

.stat-item .number {
  font-size: 1.5rem;
  font-weight: 900;
  color: #333;
}

.stat-item .label {
  font-size: 0.8rem;
  color: #888;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
}

.divider {
  width: 1px;
  height: 40px;
  background-color: #ddd;
}

/* ⭐ 오른쪽 넘기기 힌트 ⭐ */
.slide-hint {
  margin-top: 50px;
  display: flex;
  align-items: center;
  gap: 15px;
  color: #fff;
  font-family: "Pretendard", sans-serif;
  font-weight: 700;
  font-size: 1.2rem;
  opacity: 0.8;
}

.arrow-anim {
  font-size: 2rem;
  animation: moveRight 1.5s infinite ease-in-out;
}

@keyframes moveRight {
  0%, 100% { transform: translateX(0); }
  50% { transform: translateX(10px); }
}

/* 모바일 대응 */
@media (max-width: 768px) {
  .card-stack { width: 90vw; height: 60vh; }
  .cover-title { font-size: 2.5rem; }
  .cover-desc { font-size: 1rem; br { display: none; } }
}
</style>