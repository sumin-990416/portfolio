<template>
  <div class="section-container">
    <div class="glass-board">
      <div class="container-fluid">
        
        <div class="row mb-5 justify-content-center">
          <div class="col-12 text-center">
            <h2 class="section-title">My Channels</h2>
            <p class="section-subtitle">저의 개발자의 여정과 제 작업들을 확인해보세요!</p>
          </div>
        </div>

        <div class="row justify-content-center">
          <div class="col-12 col-xl-10">
            
            <div class="link-grid">
              <a 
                v-for="(link, index) in links" 
                :key="index" 
                :href="link.url" 
                target="_blank" 
                class="link-card"
                :class="link.id"
              >
                <div class="icon-box" v-html="link.icon"></div>
                
                <div class="text-box">
                  <h3>{{ link.title }}</h3>
                  <p>{{ link.desc }}</p>
                </div>

                <div class="arrow-icon">↗</div>
              </a>
            </div>

          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// ⭐ 아이콘 SVG 데이터 ⭐
const icons = {
  // GitHub (고양이 로고)
  github: `<svg viewBox="0 0 98 96" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" clip-rule="evenodd" d="M48.854 0C21.839 0 0 22 0 49.217c0 21.756 13.993 40.172 33.405 46.69 2.427.49 3.316-1.059 3.316-2.362 0-1.141-.08-5.052-.08-9.127-13.59 2.934-16.42-5.867-16.42-5.867-2.184-5.704-5.42-7.17-5.42-7.17-4.448-3.015.324-3.015.324-3.015 4.934.326 7.523 5.052 7.523 5.052 4.367 7.496 11.404 5.378 14.235 4.074.404-3.178 1.699-5.378 3.074-6.6-10.839-1.141-22.243-5.378-22.243-24.283 0-5.378 1.94-9.778 5.014-13.2-.485-1.222-2.184-6.275.486-13.038 0 0 4.125-1.304 13.426 5.052a46.97 46.97 0 0 1 12.214-1.63c4.125 0 8.33.571 12.213 1.63 9.302-6.356 13.427-5.052 13.427-5.052 2.67 6.763.97 11.816.485 13.038 3.155 3.422 5.015 7.822 5.015 13.2 0 18.905-11.404 23.06-22.324 24.283 1.78 1.548 3.316 4.481 3.316 9.126 0 6.6-.08 11.897-.08 13.526 0 1.304.89 2.853 3.316 2.364 19.412-6.52 33.405-24.935 33.405-46.691C97.707 22 75.788 0 48.854 0z" fill="currentColor"/></svg>`,
  
  // Tistory (T 로고)
  tistory: `<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><circle cx="12" cy="12" r="12" fill="currentColor"/><path d="M7 8h10v2.5H7zM10.75 11h2.5v6h-2.5z" fill="#fff"/></svg>`,
  
  // Team Blog (책/문서 아이콘)
  team: `<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/><path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/></svg>`
};

// ⭐ 여기에 실제 링크 주소를 넣어주세요! ⭐
const links = ref([
  { 
    id: 'github',
    title: 'GitHub', 
    desc: '소스코드 저장소', 
    url: 'https://github.com/sumin-990416', // 👈 수정
    icon: icons.github 
  },
  { 
    id: 'tistory',
    title: 'Tistory', 
    desc: '기술 블로그', 
    url: 'https://ss-coding-99.tistory.com/', // 👈 수정
    icon: icons.tistory 
  },
  { 
    id: 'team',
    title: 'Team Blog', 
    desc: '팀 프로젝트 기록', 
    url: 'https://team-bob-blog.github.io/bob_blog.github.io/', // 👈 수정
    icon: icons.team 
  }
]);
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
  height: 800px;
  background-color: rgba(20, 20, 30, 0.4); 
  backdrop-filter: blur(10px);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 30px;
}

/* 제목 */
.section-title {
  font-family: "Pretendard", sans-serif;
  font-size: 3rem;
  font-weight: 900;
  color: #fff;
  margin-bottom: 5px;
  text-shadow: 0 2px 10px rgba(255,255,255,0.5);
}

.section-subtitle {
  font-family: "Pretendard", sans-serif;
  font-size: 1.2rem;
  color: #fff;
  margin-bottom: 50px;
  font-weight: 600;
}

/* ⭐ 링크 카드 그리드 (3개 가로 배치) ⭐ */
.link-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 1:1:1 비율 */
  gap: 30px;
  width: 100%;
}

/* 개별 카드 스타일 */
.link-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  
  background-color: rgba(255, 255, 255, 0.9);
  padding: 50px 20px;
  border-radius: 25px;
  text-decoration: none; /* 밑줄 제거 */
  
  box-shadow: 0 10px 30px rgba(0,0,0,0.05);
  border: 1px solid rgba(255,255,255,0.5);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

/* 호버 효과 */
.link-card:hover {
  transform: translateY(-10px); /* 위로 붕 뜸 */
  box-shadow: 0 20px 40px rgba(0,0,0,0.15);
}

/* 아이콘 박스 */
.icon-box {
  width: 80px;
  height: 80px;
  margin-bottom: 20px;
  transition: transform 0.3s ease;
}

.link-card:hover .icon-box {
  transform: scale(1.1); /* 아이콘 커짐 */
}

:deep(.icon-box svg) {
  width: 100%;
  height: 100%;
}

/* 텍스트 스타일 */
.text-box {
  text-align: center;
}

.text-box h3 {
  font-family: "Pretendard", sans-serif;
  font-size: 1.5rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0 0 5px 0;
}

.text-box p {
  font-family: "Pretendard", sans-serif;
  font-size: 1rem;
  color: #666;
  margin: 0;
  font-weight: 500;
}

/* 화살표 아이콘 (우측 상단) */
.arrow-icon {
  position: absolute;
  top: 20px;
  right: 25px;
  font-size: 1.5rem;
  color: #ccc;
  transition: all 0.3s ease;
}

.link-card:hover .arrow-icon {
  color: #1a1a1a;
  transform: translate(5px, -5px); /* 대각선 이동 */
}

/* --- 브랜드별 컬러 설정 --- */

/* 1. GitHub (검정) */
.link-card.github .icon-box { color: #181717; }

/* 2. Tistory (주황) */
.link-card.tistory .icon-box { color: #FF5500; }

/* 3. Team Blog (파랑 - 예시) */
.link-card.team .icon-box { color: #3776AB; }

/* 모바일 대응 */
@media (max-width: 991px) {
  .link-grid {
    grid-template-columns: 1fr; /* 세로로 쌓임 */
    gap: 20px;
  }
  .link-card {
    flex-direction: row; /* 모바일에선 가로 배치 */
    justify-content: flex-start;
    padding: 20px 30px;
    text-align: left;
  }
  .icon-box {
    width: 50px;
    height: 50px;
    margin-bottom: 0;
    margin-right: 20px;
  }
  .text-box {
    text-align: left;
  }
}
</style>