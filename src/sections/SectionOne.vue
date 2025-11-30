<template>
  <div class="section-container">
    <div class="glass-board">
      <div class="container-fluid">
        
        <div class="row mb-5 justify-content-center">
          <div class="col-12 text-center">
            <h2 class="section-title">My Stacks</h2>
            <p class="section-subtitle">(통계학 + 데이터 사이언스 + 개발자)</p>
          </div>
        </div>

        <div class="row justify-content-center">
          <div class="col-11 col-xl-10">
            
            <div v-for="(category, index) in skillData" :key="index" class="skill-card">
              
              <div class="card-title">
                <h3>{{ category.title }}</h3>
              </div>

              <div class="circles-container">
                <div v-for="(skill, sIndex) in category.skills" :key="sIndex" class="circle-item">
                  
                  <div 
                    class="circle-wrapper" 
                    @mouseenter="replayAnimation(skill)"
                  >
                    <svg class="progress-ring" width="90" height="90" viewBox="0 0 90 90">
                      <circle
                        class="progress-ring__circle-bg"
                        stroke="#e6e6e6"
                        stroke-width="7"
                        fill="transparent"
                        r="40"
                        cx="45"
                        cy="45"
                      />
                      <circle
                        class="progress-ring__circle"
                        :stroke="skill.color"
                        stroke-width="7"
                        fill="transparent"
                        r="40"
                        cx="45"
                        cy="45"
                        :style="{ 
                          strokeDashoffset: skill.currentOffset,
                          transition: skill.transitionState
                        }"
                      />
                    </svg>
                    
                    <div class="circle-content">
                      <img 
                        :src="skill.icon" 
                        :alt="skill.name" 
                        class="skill-icon-img"
                      />
                      <span class="skill-percent">{{ skill.percent }}%</span>
                    </div>
                  </div>
                  
                  <span class="skill-label">{{ skill.name }}</span>
                  
                </div>
              </div>
              
            </div>

          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

// ⭐ 사이즈를 다시 90px(반지름 40) 기준으로 조정 ⭐
const RADIUS = 40;
const CIRCUMFERENCE = 2 * Math.PI * RADIUS; // 약 251.32

const skillData = ref([
  {
    title: "Algorithm",
    skills: [
      { name: "Python", percent: 60, color: "#3776AB", icon: "/python.png" },
      { name: "C++", percent: 40, color: "#00599C", icon: "/cplusplus.png" },
    ]
  },
  {
    title: "Front-end",
    skills: [
      { name: "Vue.js", percent: 60, color: "#42b883", icon: "/vuedotjs.png" },
      { name: "React", percent: 40, color: "#61DAFB", icon: "/react.png" },
    ]
  },
  {
    title: "AI",
    skills: [
      { name: "Sklearn", percent: 70, color: "#F7931E", icon: "/scikitlearn.png" },
      { name: "PyTorch", percent: 50, color: "#EE4C2C", icon: "/pytorch.png" },
      { name: "TensorFlow", percent: 30, color: "#FF6F00", icon: "/tensorflow.png" },
    ]
  }
]);

const calculateTargetOffset = (percent) => {
  return CIRCUMFERENCE - (percent / 100) * CIRCUMFERENCE;
};

// 초기값 설정
onMounted(() => {
  skillData.value.forEach(category => {
    category.skills.forEach(skill => {
      skill.currentOffset = calculateTargetOffset(skill.percent);
      skill.transitionState = 'stroke-dashoffset 1s ease-in-out';
    });
  });
});

// 호버 시 리플레이 함수
const replayAnimation = (skill) => {
  skill.transitionState = 'none'; 
  skill.currentOffset = CIRCUMFERENCE;

  setTimeout(() => {
    skill.transitionState = 'stroke-dashoffset 1s ease-in-out';
    skill.currentOffset = calculateTargetOffset(skill.percent);
  }, 50);
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

/* 제목 크기 조정 (적당히 줄임) */
.section-title {
  font-family: "Pretendard", sans-serif;
  font-size: 3rem; /* 3.5rem -> 3rem */
  font-weight: 900;
  color: #ffffff !important;
  margin-bottom: 5px;
  text-shadow: 0 2px 10px rgba(255,255,255,0.5);
}

.section-subtitle {
  font-family: "Pretendard", sans-serif;
  font-size: 1.4rem; /* 1.4rem -> 1.2rem */
  color: #ffffff !important;
  margin-bottom: 40px;
  font-weight: 600;
}

/* 카드 스타일 (패딩 줄임) */
.skill-card {
  font-family: "Pretendard", sans-serif;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.95);
  border-radius: 25px;
  
  /* 패딩 최적화: 40px 80px -> 25px 50px */
  padding: 25px 50px; 
  margin-bottom: 25px;
  box-shadow: 0 5px 20px rgba(0,0,0,0.05);
  transition: transform 0.3s ease;
  width: 100%;
  color: #000 !important;
}

.skill-card:hover {
  transform: translateY(-5px);
  background-color: #ffffff;
}

/* 카테고리 제목 크기 조정 */
.card-title h3 {
  font-size: 1.6rem; /* 2.2rem -> 1.6rem */
  font-weight: 800;
  color: #000 !important;
  margin: 0;
  min-width: 200px;
  text-align: left;
}

/* 그래프 영역 */
.circles-container {
  display: flex;
  gap: 40px; /* 간격 조정 */
  justify-content: flex-end;
  flex: 1;
}

.circle-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  flex-shrink: 0;
  width: 90px; /* 120px -> 90px */
}

/* 원형 그래프 래퍼 */
.circle-wrapper {
  position: relative;
  width: 90px; /* 120px -> 90px */
  height: 90px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.circle-wrapper:hover {
  transform: scale(1.05);
  transition: transform 0.2s ease;
}

/* SVG 스타일 */
.progress-ring__circle-bg,
.progress-ring__circle {
  fill: transparent;
  stroke-dasharray: 251.32; /* 2 * PI * 40 */
  transform: rotate(-90deg);
  transform-origin: 50% 50%;
}

/* 원 안의 내용 */
.circle-content {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

/* 아이콘 크기 조정 */
.skill-icon-img {
  width: 30px; /* 45px -> 30px */
  height: 30px;
  margin-bottom: 4px;
  object-fit: contain;
}

.skill-percent {
  font-size: 0.9rem; /* 1.1rem -> 0.9rem */
  font-weight: 900;
  color: #333 !important;
}

/* 라벨 크기 조정 */
.skill-label {
  margin-top: 10px;
  font-size: 1rem; /* 1.2rem -> 1rem */
  font-weight: 700;
  color: #444 !important;
  text-align: center;
  white-space: nowrap;
}

/* 모바일 대응 */
@media (max-width: 991px) {
  .skill-card {
    flex-direction: column;
    padding: 30px;
    gap: 30px;
    align-items: center;
  }
  .card-title h3 {
    text-align: center;
    margin-bottom: 10px;
  }
  .circles-container {
    justify-content: center;
    flex-wrap: wrap;
    gap: 30px;
    width: 100%;
  }
}
</style>