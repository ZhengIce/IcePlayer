<script setup>
import { ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

const downloadSection = ref(null)

const scrollToDownload = () => {
  downloadSection.value?.scrollIntoView({ behavior: 'smooth', block: 'center' })
}
</script>

<template>
  <div class="app-container">
    <div class="header">
      <div>IcePlayer</div>
      <button @click="scrollToDownload">免费下载</button>
    </div>
    <div class="content">
      <div class="left">
        <span>全新v1.0.0现已发布</span>
        <span>极简主义</span>
        <span>云端播放器</span>
        <span>IcePlayer 专注于提供最纯粹的听歌体验。连接你的 WebDAV 私有云，让音乐回归本质，如冰雪般纯净。</span>
        <div>
          <div>无广告干扰</div>
          <div>隐私优先</div>
        </div>
      </div>
      <div class="download-buttons" ref="downloadSection">
        <button class="btn-download disabled" title="敬请期待">⬇ iOS 版 (敬请期待)</button>
        <a href="/downloads/IcePlayer-v1.0.0.apk" download class="btn-download">⬇ 立即下载 安卓版</a>
      </div>
      <div class="right">
        <img src="./assets/photo1.jpg" alt="IcePlayer 1" />
        <img src="./assets/photo2.jpg" alt="IcePlayer 2" />
        <img src="./assets/photo3.jpg" alt="IcePlayer 3" />
      </div>
    </div>
    <div class="footer"></div>
  </div>
</template>

<style scoped>
.app-container {
  min-height: 100vh;
  background: linear-gradient(135deg, #e0f2fe 0%, #f0f9ff 50%, #e0e7ff 100%);
  position: relative;
  overflow-x: hidden; /* 防止水平滚动 */
  width: 100%;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 2rem;
  font-size: 1.5rem;
  font-weight: 600;
  color: #1e293b;
  position: relative;
  z-index: 10; /* 确保 header 在最上层 */
}

button {
  padding: 0.75rem 1.5rem;
  background-color: #1e293b;
  color: white;
  border: none;
  border-radius: 2rem;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 300ms ease;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

button:hover {
  background-color: #0f172a;
  transform: translateY(-2px);
  box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15);
}

button:active {
  transform: translateY(0);
}

.content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto auto;
  align-items: center;
  padding: 4rem 4rem 2rem 4rem; /* 调整顶部 padding */
  gap: 2rem 4rem; /* row-gap 2rem, col-gap 4rem */
  position: relative;
  z-index: 1;
  max-width: 1400px;
  margin: 0 auto;
  min-height: calc(100vh - 80px); /* 确保内容区域撑满剩余高度 */
}

.left {
  grid-area: 1 / 1 / 2 / 2;
  display: flex;
  flex-direction: column;
  gap: 1.5rem; /* 增加间距 */
  animation: slideInLeft 0.8s ease-out;
  max-width: 600px; /* 限制文字区域最大宽度 */
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.left span:nth-child(1) {
  font-size: 0.875rem; /* 调整字体大小 */
  color: #0f172a;
  font-weight: 600;
  letter-spacing: 0.02em;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background-color: rgba(255, 255, 255, 0.6); /* 半透明背景 */
  backdrop-filter: blur(4px);
  padding: 0.5rem 1rem;
  border-radius: 2rem;
  width: fit-content;
  border: 1px solid rgba(255, 255, 255, 0.4);
}

.left span:nth-child(1)::before {
  content: '';
  width: 0.5rem;
  height: 0.5rem;
  border-radius: 50%;
  background-color: #0ea5e9;
  box-shadow: 0 0 8px #0ea5e9; /* 添加发光效果 */
}

.left span:nth-child(2) {
  font-size: 4.5rem; /* 调整标题大小 */
  font-weight: 800;
  color: #1e293b;
  line-height: 1.1;
  letter-spacing: -0.02em;
}

.left span:nth-child(3) {
  font-size: 4.5rem;
  font-weight: 800;
  background: linear-gradient(135deg, #0ea5e9 0%, #06b6d4 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1.1;
  letter-spacing: -0.02em;
  padding-bottom: 0.5rem; /* 防止下沉字符被切断 */
}

.left span:nth-child(4) {
  font-size: 1.125rem;
  color: #475569;
  line-height: 1.7;
  margin-top: 0.5rem;
  max-width: 90%;
}

.left > div {
  display: flex;
  gap: 2rem;
  margin-top: 1rem;
}

.left > div > div {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 1rem;
  color: #334155;
  font-weight: 500;
}

.left > div > div::before {
  content: '';
  width: 1.25rem;
  height: 1.25rem;
  border-radius: 50%;
  background: linear-gradient(135deg, #3b82f6 0%, #60a5fa 100%);
  box-shadow: 0 4px 6px rgba(59, 130, 246, 0.3);
  flex-shrink: 0;
}

.download-buttons {
  grid-area: 2 / 1 / 3 / 2;
  display: flex;
  gap: 1rem;
  flex-wrap: wrap; /* 允许换行 */
  align-self: start; /* 靠上对齐 */
}

.btn-download {
  padding: 0.875rem 2rem;
  border: none;
  border-radius: 2rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  background-color: white;
  color: #1e293b;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05), 0 10px 15px rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
  gap: 0.5rem;
  text-decoration: none; /* 确保 a 标签没有下划线 */
}

.btn-download:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
  background-color: #f8fafc;
}

.btn-download.disabled {
  background-color: #e2e8f0;
  color: #94a3b8;
  cursor: not-allowed;
  box-shadow: none;
}

.btn-download.disabled:hover {
  transform: none;
  box-shadow: none;
  background-color: #e2e8f0;
}

.right {
  grid-area: 1 / 2 / 3 / 3;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  height: 600px;
  animation: slideInRight 0.8s ease-out;
  width: 100%;
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.right img {
  position: absolute;
  width: 280px; /* 稍微调小一点默认宽度 */
  height: auto;
  border-radius: 1.5rem;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  border: 4px solid rgba(255, 255, 255, 0.8);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.right img:nth-child(1) {
  z-index: 3;
  transform: translateX(-80px) translateY(-40px) rotate(-6deg) scale(0.95);
}

.right img:nth-child(1):hover {
  z-index: 10;
  transform: translateX(-80px) translateY(-50px) rotate(-6deg) scale(1.05);
}

.right img:nth-child(2) {
  z-index: 2;
  transform: translateX(0) translateY(0) scale(1);
}

.right img:nth-child(2):hover {
  z-index: 10;
  transform: translateY(-10px) scale(1.1);
}

.right img:nth-child(3) {
  z-index: 1;
  transform: translateX(80px) translateY(40px) rotate(6deg) scale(0.95);
}

.right img:nth-child(3):hover {
  z-index: 10;
  transform: translateX(80px) translateY(30px) rotate(6deg) scale(1.05);
}

/* --- 响应式设计 --- */

/* 平板尺寸 */
@media (max-width: 1024px) {
  .content {
    display: flex;
    flex-direction: column;
    padding: 4rem 2rem;
    gap: 3rem;
    text-align: center;
  }

  .left {
    align-items: center;
    max-width: 100%;
    order: 1; /* 文字在最上 */
  }
  
  .download-buttons {
    order: 3; /* 下载按钮在最下 */
    justify-content: center;
    margin-top: 1rem;
  }
  
  .left span:nth-child(4) {
    max-width: 800px;
  }

  .left > div {
    justify-content: center;
  }

  .right {
    height: 500px;
    width: 100%;
    max-width: 600px;
    order: 2; /* 图片在中间 */
  }
}

/* 手机尺寸 */
@media (max-width: 768px) {
  .header {
    padding: 1rem 1.5rem;
  }
  
  .header > div {
    font-size: 1.25rem;
  }
  
  .header button {
    padding: 0.5rem 1rem;
    font-size: 0.875rem;
  }

  .content {
    padding: 2rem 1.5rem;
    gap: 3rem;
  }

  .left span:nth-child(1) {
    font-size: 0.75rem;
  }

  .left span:nth-child(2),
  .left span:nth-child(3) {
    font-size: 3rem;
  }

  .left span:nth-child(4) {
    font-size: 1rem;
  }

  .download-buttons {
    flex-direction: column;
    width: 100%;
    gap: 1rem;
    align-items: center; /* 确保子元素居中 */
  }

  .btn-download {
    width: 100%;
    justify-content: center;
    box-sizing: border-box; /* 确保 padding 不会撑大宽度 */
    max-width: 320px; /* 限制按钮最大宽度 */
  }

  .right {
    height: 400px;
    margin-top: 1rem;
  }

  .right img {
    width: 200px;
  }

  .right img:nth-child(1) {
    transform: translateX(-50px) translateY(-20px) rotate(-6deg) scale(0.95);
  }
  
  .right img:nth-child(1):hover {
    transform: translateX(-50px) translateY(-20px) rotate(-6deg) scale(1);
  }

  .right img:nth-child(3) {
    transform: translateX(50px) translateY(20px) rotate(6deg) scale(0.95);
  }
  
  .right img:nth-child(3):hover {
    transform: translateX(50px) translateY(20px) rotate(6deg) scale(1);
  }
}
</style>
