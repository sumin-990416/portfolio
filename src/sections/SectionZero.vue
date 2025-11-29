<template>
  <div class="zero-container">
    <div class="board">
      
      <div class="left-section">
        <div class="halo-circle"></div>
        <img src="/profile.png" alt="Profile" class="profile-image" />
      </div>

      <div class="right-section">
        
        <div class="title-container">
          <img 
            src="https://readme-typing-svg.herokuapp.com?font=Jua&pause=1000&size=40&color=ffffff&center=true&vCenter=true&width=600&lines=%EB%81%8A%EC%9E%84%EC%9D%B4+%EB%85%B8%EB%A0%A5%ED%95%98%EB%8A%94+%EA%B0%9C%EB%B0%9C%EC%9E%90+%EC%A0%95%EC%88%98%EB%AF%BC%EC%9E%85%EB%8B%88%EB%8B%A4." 
            alt="끊임없이 노력하는 개발자 정수민입니다" 
            class="typing-title"
          />
        </div>
        
        <div class="cards-container">
          <div class="content-card description-card">
            <p>
              통계학을 전공하면서, <span class="highlight">머신러닝</span>과 <span class="highlight">딥러닝</span>에<br />
              관심을 가지게 되었습니다. 실제 코딩으로<br />
              무언가를 <span class="highlight">예측하는 것</span>에 흥미를 느꼈습니다.
            </p>
            <p>
              이를 계기로 부트캠프를 통해 <span class="highlight-blue">Python</span>을 접하고<br />
              <span class="highlight-blue">데이터 분석</span>을 학습했으며, 현재는<br />
              사용자에게 가치를 주는 <b>개발자</b>로 성장 중입니다.
            </p>
          </div>

          <div class="content-card info-card">
            <h2 class="section-title">About Me</h2>
            
            <div class="info-grid">
              <div class="info-box">
                <div class="icon-circle">👤</div>
                <div class="info-text">
                  <span class="label">Name</span>
                  <span class="value">정수민</span>
                </div>
              </div>
              
              <div class="info-box">
                <div class="icon-circle">🎂</div>
                <div class="info-text">
                  <span class="label">Birth</span>
                  <span class="value">1999.04.16</span>
                </div>
              </div>

              <div class="info-box">
                <div class="icon-circle">🎓</div>
                <div class="info-text">
                  <span class="label">Major</span>
                  <span class="value">통계학</span>
                </div>
              </div>

              <div class="info-box">
                <div class="icon-circle">📧</div>
                <div class="info-text">
                  <span class="label">Email</span>
                  <span class="value email-text">dmdm0601@naver.com</span>
                </div>
              </div>
            </div>
          </div> </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// 특별한 로직이 없다면 비워둡니다.
</script>

<style scoped>
@import url("https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css");

.zero-container {
  width: 100%;
  height: 100%;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.board {
  width: 100%;
  height: 100%;
  max-width: none;
  border-radius: 50px;
  
  background-color: rgba(200, 200, 210, 0.3); 
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  
  display: flex;
  overflow: hidden;
  position: relative;
}


.left-section {
  flex: 0 0 40%; /* 영역 비율 */
  position: relative;
  display: flex;
  justify-content: center;
  align-items: flex-end; 
}


.halo-circle {
  position: absolute;
  width: 60vh;
  height: 60vh;
  background-color: rgba(255, 255, 255, 0.2); /* 은은한 흰색 */
  border-radius: 50%;
  bottom: -10vh;
  left: 50%;
  transform: translateX(-50%);
  z-index: 1;
}

.profile-image {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  height: 85%;
  object-fit: contain;
  z-index: 2;
  filter: drop-shadow(0 10px 20px rgba(0,0,0,0.3)); /* 그림자 */
}


.right-section {
  flex: 1;
  padding: 60px 10%; /* 상하 60px 여백으로 카드 잘림 방지 */
  display: flex;
  flex-direction: column;
  justify-content: center;
}


.title-container {
  margin-bottom: 30px;
  display: flex;
  justify-content: flex-end;
}

.typing-title {
  max-width: 100%;
  height: auto;
}

.cards-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  max-width: 800px;
  align-self: flex-end; /* 오른쪽 정렬 */
  width: 100%;
}

/* 📌 5. 카드 공통 디자인 */
.content-card {
  font-family: "Pretendard", sans-serif; /* 폰트 적용 */
  background-color: rgba(255, 255, 255, 0.6); 
  backdrop-filter: blur(10px); /* 이중 블러 효과 */
  border: 1px solid rgba(255, 255, 255, 0.4); 
  
  border-radius: 20px;
  padding: 35px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.05);
  transition: transform 0.3s ease;
}

.content-card:hover {
  transform: translateY(-3px); 
}


.description-card p {
  font-size: 1.2rem;
  line-height: 1.8;
  color: #333;
  margin-bottom: 15px;
  word-break: keep-all;
}
.description-card p:last-child {
  margin-bottom: 0;
}

/* 형광펜 밑줄 효과 (노랑) */
.highlight {
  background: linear-gradient(to top, #ffd700 20%, transparent 40%);
  font-weight: 700;
  padding: 0 2px;
}
/* 형광펜 밑줄 효과 (파랑) */
.highlight-blue {
  background: linear-gradient(to top, #87ceeb 20%, transparent 40%);
  font-weight: 700;
  padding: 0 2px;
}


/* 📌 7. About Me 그리드 스타일 */
.section-title {
  font-size: 1.8rem;
  font-weight: 800;
  color: #1a1a1a;
  margin: 0 0 25px 0;
  border-left: 5px solid #333; /* 제목 옆 포인트 */
  padding-left: 15px;
}

.info-grid {
  display: grid;
  grid-template-columns: 1fr 1fr; /* 2열 배치 */
  gap: 20px;
}


.info-box {
  display: flex;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.5);
  padding: 15px;
  border-radius: 15px;
  border: 1px solid rgba(255,255,255,0.6);
}

.icon-circle {
  width: 45px;
  height: 45px;
  background-color: #fff;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 1.4rem;
  margin-right: 15px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.05);
}

.info-text {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.info-text .label {
  font-size: 0.85rem;
  color: #666;
  font-weight: 600;
  text-transform: uppercase;
  margin-bottom: 3px;
}

.info-text .value {
  font-size: 1.1rem;
  color: #111;
  font-weight: 700;
}

/* 이메일 주소가 길 경우 글자 크기 조정 */
.email-text {
  font-size: 1rem;
}
</style>