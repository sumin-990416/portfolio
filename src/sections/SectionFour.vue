<template>
  <div class="section-container">
    <div class="glass-board">
      <div class="container-fluid">
        
        <div class="row mb-5 justify-content-center">
          <div class="col-12 text-center">
            <h2 class="section-title">Thank You!</h2>
            <p class="section-subtitle">
              끝까지 봐주셔서 감사합니다.<br>
              새로운 배움과 협업의 기회는 언제나 환영합니다.
            </p>
          </div>
        </div>

        <div class="row justify-content-center">
          <div class="col-auto">
            
            <div 
              class="contact-card" 
              @click="copyToClipboard" 
              :class="{ 'copied': isCopied }"
            >
              
              <div class="email-text">dmdm0601@naver.com</div>
              
              <div class="action-box">
                <span v-if="!isCopied" class="copy-label">Click to Copy 📋</span>
                <span v-else class="copy-label success">Copied! ✅</span>
              </div>
            </div>

          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const isCopied = ref(false);
const email = "dmdm0601@naver.com";

const copyToClipboard = async () => {
  try {
    await navigator.clipboard.writeText(email);
    isCopied.value = true;
    
    // 2초 뒤에 다시 원래 상태로 복귀
    setTimeout(() => {
      isCopied.value = false;
    }, 2000);
  } catch (err) {
    console.error('Failed to copy: ', err);
  }
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
  height: 800px;
  background-color: rgba(20, 20, 30, 0.4);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: relative; /* 푸터 위치 잡기 위함 */
  border-radius: 30px;
}

/* 제목 스타일 */
.section-title {
  font-family: "Pretendard", sans-serif;
  font-size: 4rem;
  font-weight: 900;
  color: #fff;
  margin-bottom: 20px;
  text-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

.section-subtitle {
  font-family: "Pretendard", sans-serif;
  font-size: 1.3rem;
  line-height: 1.6;
  color: #fff;
  margin-bottom: 50px;
  font-weight: 500;
  text-shadow: 0 2px 5px rgba(0,0,0,0.3);
}

/* ⭐ 이메일 카드 스타일 ⭐ */
.contact-card {
  display: flex;
  align-items: center;
  gap: 20px;
  
  background-color: rgba(255, 255, 255, 0.9);
  padding: 25px 50px;
  border-radius: 50px; /* 알약 모양 */
  cursor: pointer;
  
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
  border: 4px solid rgba(255, 255, 255, 0.5);
  transition: all 0.3s ease;
  
  min-width: 400px;
  justify-content: center;
}

.contact-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 40px rgba(0,0,0,0.2);
  background-color: #fff;
}

/* 클릭(복사)되었을 때 스타일 변화 */
.contact-card.copied {
  background-color: #e3f9e5; /* 연한 초록색 */
  border-color: #42b883;
  transform: scale(0.98);
}

.icon-box {
  font-size: 2rem;
}

.email-text {
  font-family: "Pretendard", sans-serif;
  font-size: 1.5rem;
  font-weight: 700;
  color: #333;
}

.action-box {
  background-color: #f1f3f5;
  padding: 8px 15px;
  border-radius: 20px;
  margin-left: 20px;
  font-size: 0.9rem;
  font-weight: 600;
  color: #666;
  transition: all 0.3s;
}

.copy-label.success {
  color: #2b8a3e; /* 성공 시 초록 글씨 */
}

/* 푸터 (화면 맨 아래 고정) */
.footer {
  position: absolute;
  bottom: 30px;
  width: 100%;
  text-align: center;
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.9rem;
  font-family: "Pretendard", sans-serif;
}

/* 모바일 대응 */
@media (max-width: 768px) {
  .section-title { font-size: 2.5rem; }
  .section-subtitle { font-size: 1rem; br { display: none; } }
  .contact-card { 
    flex-direction: column; 
    gap: 10px; 
    padding: 30px; 
    border-radius: 30px; 
    min-width: auto;
    width: 90vw;
  }
  .action-box { margin-left: 0; margin-top: 10px; }
}
</style>