---
layout: default
title: E-Link Home
---

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<style>
/* 1. 外层静态阴影容器 */
.header-sync-pulse {
  margin: 0;
  display: inline-block;
  border-radius: 4px;
  margin-bottom: 5px;
  filter: drop-shadow(0 0 8px rgba(96, 165, 250, 0.3)); 
}

/* 2. 【英文版专属】图片遮罩与光束扫过 */
.logo-mask-container {
  position: relative; 
  /* 加上 max-content 锁死宽度 */
  display: inline-block; 
  width: max-content; 
  max-width: 100%;
}

.logo-mask-container::after {
  content: "";
  position: absolute;
  inset: 0; /* 覆盖底层图片 */
  
  /* 把遮罩仅应用于光束层！底图绝对安全 */
  -webkit-mask-image: var(--logo-url); 
  mask-image: var(--logo-url);
  -webkit-mask-size: contain;
  -webkit-mask-position: center;
  -webkit-mask-repeat: no-repeat;
  
  /* 使用带角度的渐变代替 transform skewX，手机端硬件加速更流畅 */
  background: linear-gradient(
    105deg, 
    transparent 0%, 
    transparent 20%,
    rgba(96, 165, 250, 0.4) 35%,   
    rgba(167, 139, 250, 0.95) 50%, 
    rgba(167, 139, 250, 0.95) 60%, 
    rgba(96, 165, 250, 0.4) 75%,   
    transparent 90%,
    transparent 100%
  );
  background-size: 250% 100%;
  background-repeat: no-repeat;
  mix-blend-mode: screen;
  pointer-events: none;
  animation: safe-sweep-anim 3s linear infinite;
}

@keyframes searchlight-sweep {
  0% { transform: translateX(-100%) skewX(-20deg); }
  75% { transform: translateX(100%) skewX(-20deg); }
  100% { transform: translateX(100%) skewX(-20deg); }
}

/* 3. SVG 图标与纯文本双层背景扫光 */
.bi-color-title-sweep {
  background: 
    linear-gradient(105deg, transparent 0%, rgba(255, 255, 255, 0.5) 25%, rgba(255, 255, 255, 1) 50%, rgba(255, 255, 255, 0.5) 75%, transparent 100%),
    linear-gradient(90deg, #60a5fa 0%, #a78bfa 55%, #f472b6 100%);
  background-size: 250% auto, 100% auto; 
  background-repeat: no-repeat;
  -webkit-background-clip: text; 
  background-clip: text;
  -webkit-text-fill-color: transparent; 
  color: transparent;
  animation: text-searchlight 3s linear infinite;
}

@keyframes text-searchlight {
  0%  { background-position: -50% center, 0 center; }
  70% { background-position: 150% center, 0 center; }
  100% { background-position: 150% center, 0 center; }
}

/* 4. 通用副标题样式 */
.sub-title {
  background: linear-gradient(90deg, #60a5fa 0%, #818cf8 50%, #a78bfa 100%);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  font-family: 'Inter', system-ui, sans-serif; font-weight: 700;
  font-size: 1.5em; letter-spacing: -0.5px; text-align: center;
  margin-top: 0; line-height: 1.4; max-width: 90%; margin-left: auto; margin-right: auto;
}

/* 5. 新增：专门控制中文“易链”两个字的大小，使其与右侧图片高度协调 */
.zh-text-logo {
  font-size: 70px;
  font-weight: 800;
  letter-spacing: 4px;
  font-family: 'Inter', 'Noto Sans SC', sans-serif;
  line-height: 1;
}

/* 🚀 新增：英文版 Logo 电脑端基础大小控制 */
.main-logo {
  display: block;
  height: 120px !important;        
  width: auto !important;      
  max-width: 100% !important;     
  object-fit: contain;
  margin-left: auto;
  margin-right: auto;
} 

/* 👇 手机端优化适配 👇 */
@media (max-width: 768px) {
  .main-logo { height: 66px !important; } 
  .sub-title { font-size: 1.2em !important; padding: 0 10px !important; white-space: normal !important; }
  .mobile-br::before { content: "\A"; white-space: pre; }
} 
</style>

<div class="lang-en" markdown="1">

<div class="github-only">
  <p align="center">
    <a href="https://tianyu-bai.github.io/E-Link">
      🌐 Click here to view the interactive website
    </a>
  </p>
</div>

<div align="center" class="nav-badges">
  <a href="#en-overview"><img src="https://img.shields.io/badge/📖_Overview-3b82f6?style=flat-square&logoColor=white" alt="Overview"></a>
  <a href="#en-features"><img src="https://img.shields.io/badge/✨_Features-3b82f6?style=flat-square&logoColor=white" alt="Features"></a>
  <a href="#en-specs"><img src="https://img.shields.io/badge/📊_Specs-3b82f6?style=flat-square&logoColor=white" alt="Specs"></a>
  <a href="#en-components"><img src="https://img.shields.io/badge/🧩_Components-3b82f6?style=flat-square&logoColor=white" alt="Components"></a>
  <a href="#en-bom"><img src="https://img.shields.io/badge/🛠_BOM-3b82f6?style=flat-square&logoColor=white" alt="BOM"></a>
  <a href="#en-downloads"><img src="https://img.shields.io/badge/🔗_Downloads-3b82f6?style=flat-square&logoColor=white" alt="Downloads"></a>
</div>

<div align="center" style="margin-bottom: 5px;" data-aos="fade-up">
  <h1 class="header-sync-pulse">
    <span class="logo-mask-container" style="--logo-url: url('{{ "/Images/ELink Logo color.png" | relative_url }}')">
      <img src="{{ '/Images/ELink Logo color.png' | relative_url }}" alt="E-Link Logo color" class="main-logo">
    </span>
  </h1>
</div>

<h2 class="sub-title" data-aos="fade-up" data-aos-delay="200">
  An Open-Source, Elastomer Interconnection-based <br class="mobile-only-br"> Connector for Flexible Neural Interfaces
</h2>

<div align="center" style="margin-top: 15px;">
   <a href="https://sites.dartmouth.edu/fang-group/"><img src="https://img.shields.io/badge/Dartmouth-MINE--Lab-00693E?style=flat-square" alt="MINE Lab"></a>
    <img src="https://img.shields.io/badge/Verified-256ch-FFA500?style=flat-square" alt="Verified" />
    <a href="https://tianyu-bai.github.io/"><img src="https://img.shields.io/badge/Website-Tianyu%20Bai-0077B5?style=flat-square&logo=github&logoColor=white" alt="Website"></a>
    <a href="https://www.linkedin.com/in/tianyubai/"><img src="https://img.shields.io/badge/LinkedIn-Profile-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
     <a href="https://github.com/tianyu-bai/E-Link/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-A31F34?style=flat-square&logo=opensourceinitiative&logoColor=white" alt="License"></a>
 </div>
  
<div align="center">
 <br>
 <img src="Images/001.PNG" alt="E-Link(256) Exploded View" width="750" loading="lazy" decoding="async">
 <p style="margin-top: 5px; font-size: 0.95em; color: #3b82f6;">
   <b>Mating Dynamics (left) and Structural Breakdown (right) of the E-Link(256) </b>
 </p>
</div>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&family=JetBrains+Mono:wght@400;700&display=swap');

/* 🚀 终极防溢出护盾：彻底锁死横向滚动条 */
html { overflow-x: hidden; width: 100%; -webkit-text-size-adjust: 100%; }
body { overflow-x: hidden; width: 100%; position: relative; margin: 0; padding: 0; font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif; }
*, *::before, *::after { box-sizing: border-box; }

/* 占位由父容器负责 */
.gif-placeholder { width: 100%; max-width: 500px; min-height: 280px; margin: 0 auto; display: flex; align-items: center; justify-content: center; background: rgba(15, 23, 42, 0.15); border-radius: 8px; overflow: hidden; }
.gif-placeholder.narrow { max-width: 460px; }
.lazy-gif { width: 100%; height: auto; display: block; opacity: 0; transition: opacity 0.4s ease; border-radius: 6px; }
.lazy-gif.is-loaded { opacity: 1; }
  
/* ===================== 1. 核心设备感知与显隐逻辑 ===================== */
.pc-tip, .mobile-tip, .pc-only, .mobile-only { display: none !important; }
@media (pointer: fine) { .pc-tip, .pc-only { display: inline !important; } }
@media (pointer: coarse) { .mobile-tip, .mobile-only { display: inline !important; } }

/* ========================================= 2. 复杂时间轴与动作动画 ========================================= */
@keyframes timeline-drag-container {
  0%             { opacity: 0; z-index: 10; }
  0.5%, 5.75%    { opacity: 1; z-index: 10; }
  6.25%, 12%     { opacity: 0; z-index: -1; }
  12.5%, 18.25%  { opacity: 1; z-index: 10; }
  18.75%, 55.75% { opacity: 0; z-index: -1; }
  56.25%, 62%    { opacity: 1; z-index: 10; }
  62.5%, 100%    { opacity: 0; z-index: -1; }
}

@keyframes timeline-zoom-container {
  0%, 5.75%      { opacity: 0; z-index: -1; }
  6.25%, 12%     { opacity: 1; z-index: 10; }
  12.5%, 18.25%  { opacity: 0; z-index: -1; }
  18.75%, 24.5%  { opacity: 1; z-index: 10; }
  25%, 62%       { opacity: 0; z-index: -1; }
  62.5%, 68.25%  { opacity: 1; z-index: 10; }
  68.75%, 100%   { opacity: 0; z-index: -1; }
}

@keyframes move-drag-hand {
  0% { transform: translateX(-40px) rotate(-15deg); opacity: 0; }
  20% { opacity: 1; }
  80% { opacity: 1; }
  100% { transform: translateX(40px) rotate(5deg); opacity: 0; }
}

@keyframes move-zoom-left-diagonal {
  0% { transform: translate(-30px, 15px); opacity: 0; } 
  20% { opacity: 1; }
  80% { opacity: 1; }
  100% { transform: translate(-90px, 65px); opacity: 0; } 
}

@keyframes move-zoom-right-diagonal {
  0% { transform: translate(30px, -15px); opacity: 0; } 
  20% { opacity: 1; }
  80% { opacity: 1; }
  100% { transform: translate(90px, -65px); opacity: 0; } 
}

/* ========================================= 3. 容器与图标样式 ========================================= */
.gesture-overlay { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); pointer-events: none; text-align: center; width: 220px; height: 150px; display: flex; flex-direction: column; justify-content: center; align-items: center; }
.mode-drag { animation: timeline-drag-container 48s infinite; }
.mode-zoom { animation: timeline-zoom-container 48s infinite; }
.icon-box { position: relative; height: 80px; width: 100%; margin-bottom: 5px; }

.hand-icon { font-size: 50px; position: absolute; top: 20px; left: 50%; text-shadow: 2px 4px 0px rgba(0,0,0,0.8), 0 0 10px rgba(0,0,0,0.5); will-change: transform, opacity; }
.mode-drag .hand-icon { margin-left: -25px; animation: move-drag-hand 1.5s infinite ease-in-out; }
.mode-zoom .hand-icon { margin-left: -25px; top: 15px; }
.mode-zoom .hand-left { animation: move-zoom-left-diagonal 1.5s infinite ease-in-out; }
.mode-zoom .hand-right { animation: move-zoom-right-diagonal 1.5s infinite ease-in-out; }

.gesture-text { color: white; font-family: sans-serif; font-weight: bold; font-size: 16px; text-shadow: 0 2px 4px black; background: rgba(0,0,0,0.4); padding: 4px 12px; border-radius: 12px; white-space: nowrap; }

/* ===================== 4. HUD 与交互反馈 ===================== */
.gesture-hud { position: absolute; top: 12px; left: 50%; transform: translateX(-50%); display: flex; align-items: center; gap: 25px; font-size: 13px; font-family: system-ui, sans-serif; color: rgba(255, 255, 255, 0.65); background: rgba(15, 23, 42, 0.45); border: 1px solid rgba(59,130,246,0.25); padding: 6px 10px; border-radius: 20px; white-space: nowrap; backdrop-filter: blur(6px); -webkit-backdrop-filter: blur(6px); pointer-events: none; transition: opacity 0.4s ease; z-index: 5; }
.gesture-hidden { opacity: 0 !important; visibility: hidden !important; pointer-events: none !important; animation: none !important; }
.gesture-hidden * { animation: none !important; }
.gesture-overlay, .gesture-overlay * { animation-play-state: paused !important; }
.gesture-overlay.gesture-active, .gesture-overlay.gesture-active * { animation-play-state: running !important; }

.reset-btn { position: absolute; bottom: 16px; left: 16px; z-index: 10; background: rgba(15, 23, 42, 0.6); border: 1px solid rgba(59, 130, 246, 0.3); color: rgba(255, 255, 255, 0.8); border-radius: 8px; padding: 6px 12px; font-family: system-ui, sans-serif; font-size: 12px; cursor: pointer; backdrop-filter: blur(4px); -webkit-backdrop-filter: blur(4px); transition: all 0.3s ease; display: flex; align-items: center; gap: 6px; }
.reset-btn:hover { background: rgba(59, 130, 246, 0.4); color: #fff; transform: scale(1.05); }

kbd { background-color: rgba(255, 255, 255, 0.1); border-radius: 4px; border: 1px solid rgba(255, 255, 255, 0.3); box-shadow: 0 1px 1px rgba(0,0,0,0.2); font-family: inherit; font-size: 0.9em; font-weight: 600; padding: 1px 4px; margin: 0 2px; color: #60a5fa; }

/* ===================== 5. 模型全局基础样式 ===================== */
.custom-model-viewer { width: 100%; max-width: 100%; box-sizing: border-box; height: 460px; background: rgba(15, 23, 42, 0.45); backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px); border-radius: 16px; border: 1px solid rgba(59,130,246,0.3); box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5), inset 0 0 15px rgba(255,255,255,0.05); outline: none; overflow: hidden; transform: translateZ(0); backface-visibility: hidden; touch-action: none; will-change: transform; isolation: isolate; }
.custom-model-viewer:focus, .custom-model-viewer:active, .custom-model-viewer:focus-visible { outline: none !important; box-shadow: none !important; border: 1px solid rgba(59,130,246,0.3) !important; }
model-viewer, model-viewer:focus-within, model-viewer:focus-visible { outline: none !important; -webkit-tap-highlight-color: transparent; }
.model-block { max-width: 100% !important; margin-top: 5px !important;  margin-bottom: 15px !important; }
model-viewer::part(interaction-prompt), model-viewer::part(default-progress-bar) { display: none !important; }
model-viewer > [slot="poster"] { width: 100%; height: 100%; position: absolute; top: 0; left: 0; }

.model-watermark-text { position: absolute; bottom: 12px; right: 16px; font-family: 'JetBrains Mono', monospace; font-size: 10px; color: rgba(255, 255, 255, 0.25); pointer-events: none; z-index: 5; font-weight: 400; }
@keyframes text-blink { 0%, 100% { opacity: 1; } 50% { opacity: 0.3; } }
.gesture-hud span + span { position: relative; padding-left: 5px; }
.gesture-hud span + span::before { content: ""; position: absolute; left: -12px; top: 20%; height: 60%; width: 1px; background: rgba(255, 255, 255, 0.2); }

/* ===================== 🚀 浅色模式专属：3D 模型 UI 界面适配 ===================== */
body.light-mode .gesture-hud { color: #1e293b !important; background: rgba(255, 255, 255, 0.7) !important; border-color: rgba(59, 130, 246, 0.3) !important; box-shadow: 0 4px 12px rgba(148, 163, 184, 0.2) !important; }
body.light-mode .gesture-hud span + span::before { background: rgba(0, 0, 0, 0.15) !important; }
body.light-mode .gesture-text { color: #1e293b !important; text-shadow: none !important; background: rgba(255, 255, 255, 0.85) !important; border: 1px solid rgba(59, 130, 246, 0.2) !important; box-shadow: 0 4px 15px rgba(148, 163, 184, 0.2) !important; }
body.light-mode .reset-btn { background: rgba(255, 255, 255, 0.8) !important; color: #334155 !important; border-color: rgba(148, 163, 184, 0.4) !important; box-shadow: 0 2px 8px rgba(148, 163, 184, 0.15) !important; }
body.light-mode .reset-btn:hover { background: #ffffff !important; color: #2563eb !important; border-color: #60a5fa !important; }
body.light-mode .model-block [slot="poster"] { background: radial-gradient(circle at center, #f8fafc 0%, #e2e8f0 100%) !important; }
body.light-mode .model-block [slot="poster"] > div:nth-child(1) { background-image: linear-gradient(rgba(59, 130, 246, 0.15) 1px, transparent 1px), linear-gradient(90deg, rgba(59, 130, 246, 0.15) 1px, transparent 1px) !important; }
body.light-mode .model-block [slot="poster"] p:first-of-type { color: #1e40af !important; text-shadow: 0 0 10px rgba(59, 130, 246, 0.3) !important; }
body.light-mode .model-block [slot="poster"] .click-to-load-glow { color: #64748b !important; }
body.light-mode .model-block [slot="poster"] .click-to-load-glow:hover { text-shadow: 0 0 10px rgba(59, 130, 246, 0.5) !important; }
body.light-mode .model-watermark-text { color: rgba(71, 85, 105, 0.6) !important; }
  
/* ===================== E-Link 动态仪表盘样式 ===================== */
.nav-badges img, .github-only img, a img { transform: translateZ(0); backface-visibility: hidden; -webkit-font-smoothing: antialiased; }
.elink-dynamic-dashboard { width: 100%;  max-width: 760px;  margin: 20px auto;  padding: 0 5px; box-sizing: border-box; }
.metrics-grid { display: flex;  justify-content: space-between;  align-items: center;  flex-wrap: nowrap; gap: 12px;  width: 100%; box-sizing: border-box; }
.metric-card.glass-panel { flex: 1 1 0; min-width: 0; background: rgba(15, 23, 42, 0.6); border: 1px solid rgba(59, 130, 246, 0.3); border-radius: 12px; padding: 15px 5px; box-sizing: border-box; box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3); backdrop-filter: blur(8px); -webkit-backdrop-filter: blur(8px); transition: transform 0.3s ease; text-align: center; }
.chart-box { position: relative; width: 145px; height: 145px; margin: 0 auto; }
.chart-box svg { width: 100%; height: 100%; transform: rotate(-90deg); }
.bg-ring { fill: none; stroke: rgba(255, 255, 255, 0.1); stroke-width: 6; }
.fg-ring { fill: none; stroke-width: 6; stroke-linecap: round; stroke-dasharray: 283; stroke-dashoffset: 283; }
.weight-color { stroke: #10b981; filter: drop-shadow(0 0 6px rgba(16, 185, 129, 0.6)); } 
.channel-color { stroke: #3b82f6; filter: drop-shadow(0 0 6px rgba(59, 130, 246, 0.6)); } 
.pcb-color { stroke: #f59e0b; filter: drop-shadow(0 0 6px rgba(245, 158, 11, 0.6)); }    
.inner-content { position: absolute; top: 0; left: 0; right: 0; bottom: 0; display: flex; flex-direction: column; justify-content: center; align-items: center; }
.inner-content .label { font-size: 10px; font-weight: 700; color: #94a3b8; margin-bottom: 2px; }
.inner-content .number-container { display: flex; align-items: baseline; justify-content: center; }
.inner-content .number { font-family: 'JetBrains Mono', monospace; font-size: 32px; font-weight: 800; color: #ffffff; text-shadow: 0 2px 4px rgba(0,0,0,0.5); }
.inner-content .unit { font-size: 16px; font-weight: bold; color: #cbd5e1; margin-left: 2px; }
.inner-content .sub { font-size: 10px; color: rgba(148, 163, 184, 0.8); margin-top: 2px; }

@media (max-width: 600px) {
  .metrics-grid { gap: 6px; } 
  .metric-card.glass-panel { padding: 10px 2px; background: rgba(15, 23, 42, 0.92); backdrop-filter: none; -webkit-backdrop-filter: none; }
  .chart-box { width: 70px; height: 70px; }
  .inner-content .number { font-size: 18px; }
  .inner-content .unit { font-size: 11px; }
  .inner-content .label { font-size: 8px; font-family: sans-serif !important; letter-spacing: 0 !important; }
  .inner-content .sub { display: none; }
  .gesture-hud { backdrop-filter: none; -webkit-backdrop-filter: none; background: rgba(15, 23, 42, 0.75); }
}
    
/* ===================== 高级 3D 封面特效 (HUD) ===================== */
.cyber-loader { position: relative; width: 50px; height: 50px; }
.cyber-loader::before, .cyber-loader::after { content: ''; position: absolute; border-radius: 50%; }
.cyber-loader::before { top: 0; left: 0; right: 0; bottom: 0; border: 2.5px solid transparent; border-top-color: #60a5fa; border-bottom-color: #60a5fa; animation: spin 1.5s cubic-bezier(0.68, -0.55, 0.265, 1.55) infinite; box-shadow: 0 0 10px rgba(96, 165, 250, 0.5); }
.cyber-loader::after { top: 8px; left: 8px; right: 8px; bottom: 8px; border: 2px solid transparent; border-left-color: #3b82f6; border-right-color: #3b82f6; animation: spin-reverse 1s linear infinite; }
@keyframes spin-reverse { to { transform: rotate(-360deg); } }

.hud-corner { position: absolute; width: 25px; height: 25px; border: 2px solid rgba(96, 165, 250, 0.6); box-shadow: 0 0 8px rgba(59, 130, 246, 0.4); }
.hud-tl { top: 20px; left: 20px; border-right: none; border-bottom: none; }
.hud-tr { top: 20px; right: 20px; border-left: none; border-bottom: none; }
.hud-bl { bottom: 20px; left: 20px; border-right: none; border-top: none; }
.hud-br { bottom: 20px; right: 20px; border-left: none; border-top: none; }

.scanline { position: absolute; top: 0; left: 0; width: 100%; height: 3px; background: linear-gradient(90deg, transparent, rgba(96, 165, 250, 0.8), transparent); box-shadow: 0 0 15px rgba(59, 130, 246, 0.8); animation: scan-sweep 3s linear infinite; opacity: 0.6; }
@keyframes scan-sweep { 0% { top: 0; opacity: 0; } 10% { opacity: 0.6; } 90% { opacity: 0.6; } 100% { top: 100%; opacity: 0; } }

.nav-badges a { display: inline-block; transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1); margin: 0 2px; }
.nav-badges a:hover { transform: translateY(-3px) scale(1.05); filter: drop-shadow(0 5px 8px rgba(59, 130, 246, 0.4)); }
.nav-badges a:active { transform: translateY(0) scale(0.98); }
.click-to-load-glow { cursor: pointer; transition: all 0.3s ease; }
.click-to-load-glow:hover { transform: scale(1.05); text-shadow: 0 0 15px rgba(96, 165, 250, 1); }
</style>

## 🔬 Interactive 3D Model: E-Link Headstage Integration
 
<div class="model-block" data-lenis-prevent align="center" style="position: relative; max-width: 760px; margin: 0 auto; min-height: 460px;">
  <model-viewer
    class="custom-model-viewer"
    src="{{ '/Videos/On skull_3.16MB.glb' | relative_url }}"
    alt="E Link on Skull 3D Model"
    loading="eager"   reveal="manual"
    poster="{{ '/Images/poster.webp' | relative_url }}"
    camera-controls interpolation-decay="200" bounds="tight" field-of-view="30deg" auto-rotate  rotation-per-second="15deg"
    interaction-prompt="none" environment-image="neutral" exposure="0.75" shadow-intensity="0" tone-mapping="commerce">

<div slot="poster" style="position: relative; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; width: 100%; background: radial-gradient(circle at center, #111827 0%, #020617 100%); font-family: 'JetBrains Mono', monospace; overflow: hidden; border-radius: 16px; cursor: pointer;">
      <div style="position: absolute; inset: 0; background-image: linear-gradient(rgba(59, 130, 246, 0.08) 1px, transparent 1px), linear-gradient(90deg, rgba(59, 130, 246, 0.08) 1px, transparent 1px); background-size: 25px 25px; z-index: 0;"></div>
      <div class="scanline" style="z-index: 1;"></div>
      <div class="hud-corner hud-tl" style="z-index: 1;"></div>
      <div class="hud-corner hud-tr" style="z-index: 1;"></div>
      <div class="hud-corner hud-bl" style="z-index: 1;"></div>
      <div class="hud-corner hud-br" style="z-index: 1;"></div>
      <div style="z-index: 2; display: flex; flex-direction: column; align-items: center;">
        <div class="cyber-loader"></div>
        <p style="margin-top: 25px; margin-bottom: 5px; font-size: 0.95rem; font-weight: 600; letter-spacing: 3px; color: #93c5fd; text-shadow: 0 0 10px rgba(96, 165, 250, 0.8); animation: text-blink 1.5s ease-in-out infinite;">INITIALIZING 3D SIGNAL...</p>
        <p class="click-to-load-glow" style="margin: 0; font-size: 0.65rem; color: #a78bfa; letter-spacing: 1px; font-weight: bold;">[ SCROLL OR CLICK TO REVEAL ]</p>
      </div>
    </div>
    
<div class="model-watermark-text">Copyright © 2026 Tianyu Bai</div>

<div class="gesture-hud">
  <span>↺ Rotate: Drag</span>
  <span class="pc-only">Zoom: Ctrl + 🖱 Wheel/Trackpad Pinch</span>
  <span class="mobile-only">Zoom: Pinch</span>
</div>

<div class="gesture-overlay mode-zoom">
  <div class="icon-box">
    <div class="hand-icon hand-left">👉</div>
    <div class="hand-icon hand-right">👈</div>
  </div>
  <div class="gesture-text">
    <span class="pc-tip">Ctrl + 🖱️Wheel to Zoom</span>
    <span class="mobile-tip">Pinch with two fingers to Zoom</span>
  </div>
</div>

<div class="gesture-overlay mode-drag">
      <div class="icon-box"><div class="hand-icon">👆</div></div>
      <div class="gesture-text">Drag to Rotate</div>
    </div>
    
    <button class="reset-btn"
  onclick="
    const mv = this.closest('model-viewer');
    mv.setAttribute('camera-orbit','45deg 55deg auto');
    mv.setAttribute('field-of-view','30deg');
  ">
      ⟲ Reset View
    </button>
  </model-viewer>
</div>

## 🔬 E-Link – 3D Interactive View
 
<div class="model-block" data-lenis-prevent align="center" style="position: relative; max-width: 760px; margin: 0 auto; min-height: 460px;">
  <model-viewer
    class="custom-model-viewer"
    src="{{ '/Videos/Whole_2.34MB.glb' | relative_url }}"
    alt="E Link 3D Model"
    loading="lazy"       reveal="manual"
    poster="{{ '/Images/poster.webp' | relative_url }}"
    camera-controls interpolation-decay="200" bounds="tight" field-of-view="30deg" auto-rotate  rotation-per-second="15deg"
    interaction-prompt="none" environment-image="neutral" exposure="0.75" shadow-intensity="0" tone-mapping="commerce">

<div slot="poster" style="position: relative; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; width: 100%; background: radial-gradient(circle at center, #111827 0%, #020617 100%); font-family: 'JetBrains Mono', monospace; overflow: hidden; border-radius: 16px; cursor: pointer;">
   <div style="position: absolute; inset: 0; background-image: linear-gradient(rgba(59, 130, 246, 0.08) 1px, transparent 1px), linear-gradient(90deg, rgba(59, 130, 246, 0.08) 1px, transparent 1px); background-size: 25px 25px; z-index: 0;"></div>
      <div class="scanline" style="z-index: 1;"></div>
      <div class="hud-corner hud-tl" style="z-index: 1;"></div>
      <div class="hud-corner hud-tr" style="z-index: 1;"></div>
      <div class="hud-corner hud-bl" style="z-index: 1;"></div>
      <div class="hud-corner hud-br" style="z-index: 1;"></div>
      <div style="z-index: 2; display: flex; flex-direction: column; align-items: center;">
        <div class="cyber-loader"></div>
        <p style="margin-top: 25px; margin-bottom: 5px; font-size: 0.95rem; font-weight: 600; letter-spacing: 3px; color: #93c5fd; text-shadow: 0 0 10px rgba(96, 165, 250, 0.8); animation: text-blink 1.5s ease-in-out infinite;">INITIALIZING 3D SIGNAL...</p>
        <p class="click-to-load-glow" style="margin: 0; font-size: 0.65rem; color: #a78bfa; letter-spacing: 1px; font-weight: bold;">[ SCROLL OR CLICK TO REVEAL ]</p>
      </div>
    </div>
    
    <div class="model-watermark-text">Copyright © 2026 Tianyu Bai</div>
    
<div class="gesture-hud">
  <span>↺ Rotate: Drag</span>
  <span class="pc-only">Zoom: Ctrl + 🖱 Wheel/Trackpad Pinch</span>
  <span class="mobile-only">Zoom: Pinch</span>
</div>

<div class="gesture-overlay mode-zoom">
  <div class="icon-box">
    <div class="hand-icon hand-left">👉</div>
    <div class="hand-icon hand-right">👈</div>
  </div>
  <div class="gesture-text">
    <span class="pc-tip">Ctrl + 🖱️Wheel to Zoom</span>
    <span class="mobile-tip">Pinch with two fingers to Zoom</span>
  </div>
</div>
    <div class="gesture-overlay mode-drag">
      <div class="icon-box"><div class="hand-icon">👆</div></div>
      <div class="gesture-text">Drag to Rotate</div>
    </div>
    
   <button class="reset-btn"
  onclick="
    const mv = this.closest('model-viewer');
    mv.setAttribute('camera-orbit','45deg 55deg auto');
    mv.setAttribute('field-of-view','30deg');
  ">
      ⟲ Reset View
    </button>
  </model-viewer>
</div>

## 🔬 256Ch Customized Headstage – 3D Interactive View

<div class="model-block" data-lenis-prevent align="center" style="position: relative; max-width: 760px; margin: 0 auto; min-height: 460px;">
  <model-viewer
    class="custom-model-viewer"
    src="{{ '/Videos/3D_1.85MB.glb' | relative_url }}"
    alt="E-Link 256-Channel Custom Headstage 3D Model" 
    loading="lazy"       reveal="manual"
    poster="{{ '/Images/poster.webp' | relative_url }}"
    camera-controls interpolation-decay="200" bounds="tight" field-of-view="30deg" auto-rotate  rotation-per-second="15deg"
    interaction-prompt="none" environment-image="neutral" exposure="0.75" shadow-intensity="0" tone-mapping="commerce">

<div slot="poster" style="position: relative; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; width: 100%; background: radial-gradient(circle at center, #111827 0%, #020617 100%); font-family: 'JetBrains Mono', monospace; overflow: hidden; border-radius: 16px; cursor: pointer;">
      <div style="position: absolute; inset: 0; background-image: linear-gradient(rgba(59, 130, 246, 0.08) 1px, transparent 1px), linear-gradient(90deg, rgba(59, 130, 246, 0.08) 1px, transparent 1px); background-size: 25px 25px; z-index: 0;"></div>
      <div class="scanline" style="z-index: 1;"></div>
      <div class="hud-corner hud-tl" style="z-index: 1;"></div>
      <div class="hud-corner hud-tr" style="z-index: 1;"></div>
      <div class="hud-corner hud-bl" style="z-index: 1;"></div>
      <div class="hud-corner hud-br" style="z-index: 1;"></div>
      <div style="z-index: 2; display: flex; flex-direction: column; align-items: center;">
        <div class="cyber-loader"></div>
        <p style="margin-top: 25px; margin-bottom: 5px; font-size: 0.95rem; font-weight: 600; letter-spacing: 3px; color: #93c5fd; text-shadow: 0 0 10px rgba(96, 165, 250, 0.8); animation: text-blink 1.5s ease-in-out infinite;">INITIALIZING 3D SIGNAL...</p>
        <p class="click-to-load-glow" style="margin: 0; font-size: 0.65rem; color: #a78bfa; letter-spacing: 1px; font-weight: bold;">[ SCROLL OR CLICK TO REVEAL ]</p>
      </div>
    </div>
    
    <div class="model-watermark-text">Copyright © 2026 Tianyu Bai</div>
    
<div class="gesture-hud">
  <span>↺ Rotate: Drag</span>
  <span class="pc-only">Zoom: Ctrl + 🖱 Wheel/Trackpad Pinch</span>
  <span class="mobile-only">Zoom: Pinch</span>
</div>

<div class="gesture-overlay mode-zoom">
  <div class="icon-box">
    <div class="hand-icon hand-left">👉</div>
    <div class="hand-icon hand-right">👈</div>
  </div>
  <div class="gesture-text">
    <span class="pc-tip">Ctrl + 🖱️Wheel to Zoom</span>
    <span class="mobile-tip">Pinch with two fingers to Zoom</span>
  </div>
</div>
    <div class="gesture-overlay mode-drag">
      <div class="icon-box"><div class="hand-icon">👆</div></div>
      <div class="gesture-text">Drag to Rotate</div>
 </div>
   <button class="reset-btn"
  onclick="
    const mv = this.closest('model-viewer');
    mv.setAttribute('camera-orbit','45deg 55deg auto');
    mv.setAttribute('field-of-view','30deg');
  ">
      ⟲ Reset View
    </button>
  </model-viewer>
</div> 

<style>
/* ====== V2 仪表盘新增样式 ====== */
.metrics-grid-v2 { display: grid; grid-template-columns: repeat(3, 1fr); gap: 14px; width: 100%; max-width: 760px; margin: 25px auto; padding: 0 5px; box-sizing: border-box; }
.metric-card-v2 { background: rgba(15, 23, 42, 0.6); border: 1px solid rgba(59, 130, 246, 0.25); border-radius: 14px; padding: 18px 12px; box-sizing: border-box; backdrop-filter: blur(8px); -webkit-backdrop-filter: blur(8px); text-align: center; transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease; position: relative; overflow: hidden; }
.metric-card-v2:hover { transform: translateY(-4px); border-color: rgba(96, 165, 250, 0.5); box-shadow: 0 12px 40px rgba(59, 130, 246, 0.15); }
.metric-card-v2::before { content: ''; position: absolute; top: 0; left: 10%; right: 10%; height: 2px; background: var(--card-accent, #3b82f6); border-radius: 0 0 4px 4px; opacity: 0.6; filter: blur(1px); }
.metric-card-v2 .card-label { font-size: 13px; font-weight: 700; color: #94a3b8; letter-spacing: 2px; margin-bottom: 8px; text-transform: uppercase; }
.metric-card-v2 .card-value { font-family: 'JetBrains Mono', monospace; font-size: 34px; font-weight: 800; color: #fff; text-shadow: 0 2px 8px rgba(0,0,0,0.4); line-height: 1.1; display: inline-block; vertical-align: baseline; }
.metric-card-v2 .card-unit { font-size: 15px; font-weight: 600; color: #cbd5e1; margin-left: 2px; }
.metric-card-v2 .card-sub { font-size: 10px; color: rgba(148, 163, 184, 0.75); margin-top: 4px; }

.v2-chart-box { position: relative; width: 130px; height: 130px; margin: 0 auto 6px; }
.v2-chart-box svg { width: 100%; height: 100%; transform: rotate(-90deg); }
.v2-chart-box .bg-ring { fill: none; stroke: rgba(255, 255, 255, 0.08); stroke-width: 6; }
.v2-chart-box .fg-ring { fill: none; stroke-width: 6; stroke-linecap: round; stroke-dasharray: 283; stroke-dashoffset: 283; transition: filter 0.3s; }
.v2-chart-box .ring-inner { position: absolute; top: 0; left: 0; right: 0; bottom: 0; display: flex; flex-direction: column; justify-content: center; align-items: center; }

.thermo-wrapper { display: flex; flex-direction: column; align-items: center; margin: 5px auto 6px; position: relative; height: 100px; width: 40px; }
.thermo-track { width: 16px; height: 80px; background: rgba(255,255,255,0.08); border-radius: 8px 8px 0 0; position: relative; overflow: hidden; border: 1px solid rgba(255,255,255,0.1); }
.thermo-fill { position: absolute; bottom: 0; left: 0; right: 0; height: 0%; background: linear-gradient(to top, #ef4444, #f97316, #fbbf24); border-radius: 6px 6px 0 0; transition: height 0.1s; box-shadow: 0 0 12px rgba(239, 68, 68, 0.4); }
.thermo-bulb { width: 26px; height: 26px; border-radius: 50%; background: radial-gradient(circle at 40% 40%, #fca5a5, #ef4444); border: 1px solid rgba(255,255,255,0.15); box-shadow: 0 0 15px rgba(239, 68, 68, 0.5); margin-top: -4px; position: relative; z-index: 2; }
.thermo-safe-line { position: absolute; right: -28px; top: 22%; width: 20px; border-top: 1px dashed rgba(16, 185, 129, 0.6); }
.thermo-safe-label { position: absolute; right: -52px; top: 18%; font-size: 7px; color: #10b981; font-family: 'JetBrains Mono', monospace; white-space: nowrap; }

.waveform-box { height: 60px; margin: 8px auto 6px; position: relative; max-width: 140px; }
.waveform-box canvas { width: 100%; height: 100%; border-radius: 6px; }

.cycles-viz { position: relative; width: 130px; height: 90px; margin: 5px auto 6px; display: flex; align-items: center; justify-content: center; }
.press-icon { font-size: 36px; animation: press-bounce 1.2s ease-in-out infinite; filter: drop-shadow(0 0 8px rgba(16, 185, 129, 0.5)); }
@keyframes press-bounce { 0%, 100% { transform: translateY(0) scale(1); filter: drop-shadow(0 0 8px rgba(16, 185, 129, 0.3)); } 15% { transform: translateY(8px) scale(1.05, 0.9); filter: drop-shadow(0 0 15px rgba(16, 185, 129, 0.8)); } 30% { transform: translateY(-4px) scale(0.98, 1.04); } 45% { transform: translateY(0) scale(1); } }
.press-ripple { position: absolute; bottom: 8px; left: 50%; transform: translateX(-50%); width: 40px; height: 8px; background: radial-gradient(ellipse, rgba(16, 185, 129, 0.4) 0%, transparent 70%); border-radius: 50%; animation: ripple-squash 1.2s ease-in-out infinite; }
@keyframes ripple-squash { 0%, 100% { transform: translateX(-50%) scaleX(1); opacity: 0.3; } 15% { transform: translateX(-50%) scaleX(1.8); opacity: 0.8; } 45% { transform: translateX(-50%) scaleX(1); opacity: 0.3; } }
.cycles-counter-flash { position: absolute; top: 2px; right: 10px; font-family: 'JetBrains Mono', monospace; font-size: 9px; color: #10b981; opacity: 0; animation: counter-tick 1.2s ease-in-out infinite; }
@keyframes counter-tick { 0%, 10% { opacity: 0; transform: translateY(0); } 15%, 25% { opacity: 1; transform: translateY(-2px); } 40%, 100% { opacity: 0; transform: translateY(-8px); } }

.yield-bar-wrapper { margin: 15px auto 8px; max-width: 140px; }
.yield-bar-track { height: 10px; background: rgba(255,255,255,0.08); border-radius: 5px; overflow: hidden; position: relative; border: 1px solid rgba(255,255,255,0.06); }
.yield-bar-fill { height: 100%; width: 0%; background: linear-gradient(90deg, #3b82f6, #10b981); border-radius: 5px; position: relative; transition: width 0.1s; box-shadow: 0 0 10px rgba(16, 185, 129, 0.4); }
.yield-bar-fill::after { content: ''; position: absolute; right: 0; top: -3px; width: 6px; height: 16px; background: #fff; border-radius: 3px; box-shadow: 0 0 8px rgba(255,255,255,0.8); }
.yield-particles { position: relative; height: 20px; overflow: hidden; }
.yield-particle { position: absolute; width: 3px; height: 3px; background: #10b981; border-radius: 50%; opacity: 0; box-shadow: 0 0 4px #10b981; }

@media (max-width: 600px) {
  .metrics-grid-v2 { grid-template-columns: repeat(3, 1fr); gap: 6px; }
  .metric-card-v2 { padding: 12px 4px; backdrop-filter: none; -webkit-backdrop-filter: none; background: rgba(15, 23, 42, 0.92); }
  .metric-card-v2 .card-value { font-size: 20px; }
  .metric-card-v2 .card-unit { font-size: 11px; }
  .metric-card-v2 .card-label { font-size: 11px; letter-spacing: 1px; }
  .metric-card-v2 .card-sub { display: none; }
  .v2-chart-box { width: 68px; height: 68px; }
  .v2-chart-box .fg-ring, .v2-chart-box .bg-ring { stroke-width: 5; }
  .thermo-wrapper { height: 65px; width: 28px; }
  .thermo-track { width: 12px; height: 50px; }
  .thermo-bulb { width: 20px; height: 20px; }
  .thermo-safe-line, .thermo-safe-label { display: none; }
  .waveform-box { height: 40px; max-width: 90px; }
  .yield-bar-wrapper { max-width: 90px; }
  .cycles-viz { width: 70px; height: 55px; }
  .press-icon { font-size: 24px; }
  .cycles-counter-flash { display: none; }
}

body.light-mode .metric-card-v2 { background: rgba(241, 245, 249, 0.85); border-color: rgba(148, 163, 184, 0.3); }
body.light-mode .metric-card-v2:hover { box-shadow: 0 12px 40px rgba(148, 163, 184, 0.15); }
body.light-mode .metric-card-v2 .card-value { color: #1e293b; text-shadow: none; }
body.light-mode .metric-card-v2 .card-unit { color: #475569; }
body.light-mode .metric-card-v2 .card-label { color: #64748b; }
body.light-mode .v2-chart-box .bg-ring { stroke: rgba(0,0,0,0.08); }
body.light-mode .thermo-track { background: rgba(0,0,0,0.06); border-color: rgba(0,0,0,0.08); }
body.light-mode .yield-bar-track { background: rgba(0,0,0,0.06); border-color: rgba(0,0,0,0.06); }
</style>

<div class="metrics-grid-v2" data-aos="fade-up">
  <div class="metric-card-v2" style="--card-accent: #10b981;" data-type="ring" data-percent="100" data-value="2.8" data-is-float="true">
    <div class="card-label">WEIGHT</div>
    <div class="v2-chart-box">
      <svg viewBox="0 0 100 100"><circle class="bg-ring" cx="50" cy="50" r="45"></circle><circle class="fg-ring weight-color" cx="50" cy="50" r="45"></circle></svg>
      <div class="ring-inner">
        <div class="v2-val-wrap">
          <span class="card-value v2-count v2-val-sm">0</span><span class="card-unit">g</span>
        </div>
      </div>
    </div>
    <div class="card-sub">Lightweight</div>
  </div>

  <div class="metric-card-v2" style="--card-accent: #3b82f6;" data-type="ring" data-percent="100" data-value="256" data-is-float="false">
    <div class="card-label">CHANNELS</div>
    <div class="v2-chart-box">
      <svg viewBox="0 0 100 100"><circle class="bg-ring" cx="50" cy="50" r="45"></circle><circle class="fg-ring channel-color" cx="50" cy="50" r="45"></circle></svg>
      <div class="ring-inner">
        <div class="v2-val-wrap">
          <span class="card-value v2-count v2-val-sm">0</span>
        </div>
      </div>
    </div>
    <div class="card-sub">High-Density</div>
  </div>

  <div class="metric-card-v2" style="--card-accent: #f59e0b;" data-type="ring" data-percent="100" data-value="4" data-is-float="false">
    <div class="card-label">PCB LAYERS</div>
    <div class="v2-chart-box">
      <svg viewBox="0 0 100 100"><circle class="bg-ring" cx="50" cy="50" r="45"></circle><circle class="fg-ring pcb-color" cx="50" cy="50" r="45"></circle></svg>
      <div class="ring-inner">
        <div class="v2-val-wrap">
          <span class="card-value v2-count v2-val-sm">0</span>
        </div>
      </div>
    </div>
    <div class="card-sub">Custom Routing</div>
  </div>
  
  <div class="metric-card-v2" style="--card-accent: #ef4444;" data-type="thermo" data-value="30.5" data-max="50">
    <div class="card-label">TEMPERATURE</div>
    <div class="thermo-wrapper">
      <div class="thermo-track">
        <div class="thermo-fill"></div>
        <div class="thermo-safe-line"></div>
        <div class="thermo-safe-label">37°C</div>
      </div>
      <div class="thermo-bulb"></div>
    </div>
    <div class="card-value v2-count" style="font-size: 28px;">0</div><span class="card-unit">°C</span>
    <div class="card-sub">Below Bio Threshold</div>
  </div>

  <div class="metric-card-v2" style="--card-accent: #a78bfa;" data-type="waveform" data-value="2.68" data-is-float="true" data-decimals="2">
    <div class="card-label">NOISE FLOOR</div>
    <div class="waveform-box"><canvas class="waveform-canvas"></canvas></div>
    <div class="card-value v2-count" style="font-size: 28px;">0</div><span class="card-unit">µV (RMS)</span>
    <div class="card-sub">Near Chip Limit</div>
  </div>

  <div class="metric-card-v2" style="--card-accent: #10b981;" data-type="cycles" data-value="300">
    <div class="card-label">STRESS TESTED</div>
    <div class="cycles-viz">
      <div class="press-icon">
        <span class="icon-desktop">🫸</span>
        <span class="icon-mobile">
          <svg width="1em" height="1em" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
            <path d="M12 3v14"></path>
            <path d="m7 12 5 5 5-5"></path>
            <path d="M4 21h16"></path>
          </svg>
        </span>
      </div>
      <div class="press-ripple"></div>
      <div class="cycles-counter-flash">+1</div>
    </div>
    <div class="card-value v2-count" style="font-size: 28px;">0</div><span class="card-unit">+</span>
    <div class="card-sub">97%+ Yield Maintained</div>
  </div>
</div>

<span id="en-overview"></span>

## 📖 Overview

**E-Link** (Elastomer Interconnection-based connector) is an open-source, miniature pedestal connector system based on elastomer interconnection. It provides a robust, scalable interface for High-Density Soft Neural Interfaces, specifically engineered for chronic applications in freely moving animals.

<div align="center" data-aos="zoom-in-up" data-aos-duration="1000">
 <br>
 <div class="gif-placeholder">
   <img data-src="Videos/Demo%20new%20new.gif" 
         src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7"
         alt="ELINK-256 Assembly Demo GIF"
         class="lazy-gif white-bg-gif" 
         decoding="async">
 </div>
</div>

---

> [!NOTE]
> **Key Innovation:** The system integrates two high-density PCBs, an anisotropic elastomeric contact interface, and a lightweight pedestal housing into a fully integrated, headstage-ready solution.

---

<span id="en-specs"></span>
### 📊 Quick Specifications

<div style="width: 100%; max-width: 100%; overflow-x: auto; -webkit-overflow-scrolling: touch; padding-bottom: 10px;">
  <table style="margin-left: auto; margin-right: auto; width: 90%; min-width: 600px; text-align: center; border-collapse: collapse; border: 1px solid #e1e4e8;">
   <thead>
     <tr style="background-color: #f6f8fa; border-bottom: 2px solid #e1e4e8;">
       <th style="padding: 10px; border: 1px solid #e1e4e8;">Specification</th>
       <th style="padding: 10px; border: 1px solid #e1e4e8;">E-Link(256)_V1.0</th>
     </tr>
   </thead>
   <tbody>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>Channel Count</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">128 or 256 Channels (Single/Dual SPI Port support)</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>Total Mass</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">6.6 g (with housing)<br>2.8 g (without housing)</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>Interconnect Type</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">Solderless Anisotropic Elastomer</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>Compatible Acquisition System</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">Intan Recording Controller (512ch/1024ch)<br>Open-Ephys DAQ box<br>NeuroNexus Smartbox<br>OmniPlex DAQ box</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>Housing Material</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">3D-Printed PEEK / Surgical Grade Resin</td>
     </tr>
   </tbody>
 </table>
</div>

<style>
/* ── Assembly Pipeline Styles ── */
.pipeline-section { max-width: 760px; margin: 40px auto; }
 
.pipeline-card {
  background: rgba(11, 17, 33, 0.95);
  border: 1px solid rgba(59, 130, 246, 0.25);
  border-radius: 20px;
  padding: 30px 35px 35px;
  box-shadow: inset 0 0 20px rgba(0,0,0,0.4), 0 15px 40px rgba(0,0,0,0.2);
}
 
.pipeline-card-title {
  margin: 0 0 6px 0;
  color: #93c5fd;
  font-family: 'JetBrains Mono', monospace;
  font-size: 20px;
  font-weight: 700;
  border-bottom: 1px solid rgba(59, 130, 246, 0.25);
  padding-bottom: 14px;
  letter-spacing: 0.5px;
}
 
.pipeline-card-desc {
  font-size: 14px;
  color: #94a3b8;
  margin-bottom: 30px;
  line-height: 1.7;
}
 
/* ── Horizontal Pipeline (Desktop) ── */
.pipe-track-wrapper {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  padding: 0 10px;
  margin-bottom: 10px;
}
 
/* Connecting track line */
.pipe-track-line {
  position: absolute;
  top: 20px;
  left: 40px;
  right: 40px;
  height: 2px;
  background: rgba(59, 130, 246, 0.15);
  z-index: 1;
  overflow: hidden;
  border-radius: 1px;
}
 
/* Animated flowing light pulse */
.pipe-flow-light {
  position: absolute;
  top: 0;
  left: -60px;
  width: 60px;
  height: 100%;
  background: linear-gradient(90deg, transparent, #3b82f6, transparent);
  animation: pipeFlowH 3.5s linear infinite;
}
 
@keyframes pipeFlowH {
  0%   { left: -60px; opacity: 0; }
  8%   { opacity: 1; }
  92%  { opacity: 1; }
  100% { left: 100%; opacity: 0; }
}
 
/* Each step node */
.pipe-node {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 16.66%;
  text-align: center;
}
 
.pipe-circle {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: #0f172a;
  border: 2px solid #3b82f6;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'JetBrains Mono', monospace;
  font-size: 14px;
  font-weight: 700;
  color: #93c5fd;
  margin-bottom: 14px;
  box-shadow: 0 0 12px rgba(59, 130, 246, 0.3);
  transition: all 0.35s cubic-bezier(0.25, 0.8, 0.25, 1);
  cursor: default;
  flex-shrink: 0;
}
 
.pipe-node:hover .pipe-circle {
  background: #3b82f6;
  color: #ffffff;
  box-shadow: 0 0 24px rgba(59, 130, 246, 0.7);
  transform: scale(1.15);
}
 
.pipe-label {
  font-size: 13px;
  font-weight: 600;
  color: #cbd5e1;
  line-height: 1.35;
  transition: color 0.3s;
}
 
.pipe-node:hover .pipe-label {
  color: #ffffff;
}
 
.pipe-icon {
  font-size: 16px;
  margin-bottom: 4px;
  display: block;
  opacity: 0.8;
}
 
/* ── Validation stats row ── */
.pipe-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin-top: 28px;
}
 
.pipe-stat-card {
  background: rgba(15, 23, 42, 0.4);
  border-radius: 10px;
  padding: 14px 16px;
  border-left: 3px solid;
  transition: transform 0.25s, box-shadow 0.25s;
}
 
.pipe-stat-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(0,0,0,0.2);
}
 
.pipe-stat-card:nth-child(1) { border-left-color: #10b981; border-color: rgba(16, 185, 129, 0.2); }
.pipe-stat-card:nth-child(2) { border-left-color: #3b82f6; border-color: rgba(59, 130, 246, 0.2); }
.pipe-stat-card:nth-child(3) { border-left-color: #f59e0b; border-color: rgba(245, 158, 11, 0.2); }
 
.pipe-stat-card { border: 1px solid; }
.pipe-stat-card:nth-child(1) { border-color: rgba(16, 185, 129, 0.2); border-left: 3px solid #10b981; }
.pipe-stat-card:nth-child(2) { border-color: rgba(59, 130, 246, 0.2); border-left: 3px solid #3b82f6; }
.pipe-stat-card:nth-child(3) { border-color: rgba(245, 158, 11, 0.2); border-left: 3px solid #f59e0b; }
 
.pipe-stat-title {
  font-family: 'JetBrains Mono', monospace;
  font-size: 14px;
  font-weight: 700;
  margin-bottom: 4px;
}
 
.pipe-stat-card:nth-child(1) .pipe-stat-title { color: #10b981; }
.pipe-stat-card:nth-child(2) .pipe-stat-title { color: #3b82f6; }
.pipe-stat-card:nth-child(3) .pipe-stat-title { color: #f59e0b; }
 
.pipe-stat-desc {
  font-size: 12px;
  color: #94a3b8;
  line-height: 1.45;
}
 
/* ── Light Mode ── */
body.light-mode .pipeline-card {
  background: #ffffff;
  border-color: #cbd5e1;
  box-shadow: 0 15px 40px rgba(0,0,0,0.05);
}
body.light-mode .pipeline-card-title { color: #2563eb; border-bottom-color: #e2e8f0; }
body.light-mode .pipeline-card-desc { color: #475569; }
body.light-mode .pipe-circle { background: #ffffff; border-color: #2563eb; color: #2563eb; box-shadow: 0 0 10px rgba(37, 99, 235, 0.15); }
body.light-mode .pipe-node:hover .pipe-circle { background: #2563eb; color: #fff; }
body.light-mode .pipe-label { color: #475569; }
body.light-mode .pipe-node:hover .pipe-label { color: #0f172a; }
body.light-mode .pipe-track-line { background: rgba(37, 99, 235, 0.12); }
body.light-mode .pipe-stat-card { background: #f8fafc; }
body.light-mode .pipe-stat-desc { color: #64748b; }
 
/* ── Mobile: Switch to vertical layout ── */
@media (max-width: 768px) {
  .pipeline-card { padding: 25px 18px; }
 
  .pipe-track-wrapper {
    flex-direction: column;
    align-items: flex-start;
    gap: 0;
    padding-left: 28px;
  }
 
  /* Vertical track line */
  .pipe-track-line {
    top: 0;
    bottom: 0;
    left: 47px;
    right: auto;
    width: 2px;
    height: auto;
  }
 
  .pipe-flow-light {
    width: 100%;
    height: 50px;
    left: auto;
    top: -50px;
    background: linear-gradient(180deg, transparent, #3b82f6, transparent);
    animation: pipeFlowV 3.5s linear infinite;
  }
 
  @keyframes pipeFlowV {
    0%   { top: -50px; opacity: 0; }
    8%   { opacity: 1; }
    92%  { opacity: 1; }
    100% { top: 100%; opacity: 0; }
  }
 
  .pipe-node {
    flex-direction: row;
    width: 100%;
    text-align: left;
    gap: 16px;
    padding: 10px 0;
  }
 
  .pipe-circle { margin-bottom: 0; width: 38px; height: 38px; }
  .pipe-label { font-size: 14px; }
  .pipe-icon { display: inline; margin-right: 4px; margin-bottom: 0; }
 
  .pipe-stats {
    grid-template-columns: 1fr;
    gap: 10px;
  }
}
 
@media (max-width: 480px) {
  .pipe-stats { grid-template-columns: 1fr; }
}
</style>
 
<div class="pipeline-section" data-aos="fade-up">
  <div class="pipeline-card">
    <h3 class="pipeline-card-title">⚙️ Assembly & Validation Pipeline</h3>
    <p class="pipeline-card-desc">
      The insertion-free <strong style="color: #e2e8f0;">"rotate-and-play"</strong> interface eliminates micro-alignment requirements, enabling reproducible assembly by untrained operators with consistent electrical performance.
    </p>
 
    <!-- Pipeline Steps -->
    <div class="pipe-track-wrapper">
      <!-- Track line with flowing light -->
      <div class="pipe-track-line">
        <div class="pipe-flow-light"></div>
      </div>
 
      <div class="pipe-node">
        <div class="pipe-circle">01</div>
        <div class="pipe-label">
          <span class="pipe-icon">🔩</span>
          Seat<br>Pedestal
        </div>
      </div>
 
      <div class="pipe-node">
        <div class="pipe-circle">02</div>
        <div class="pipe-label">
          <span class="pipe-icon">📐</span>
          Place<br>Adapter PCB
        </div>
      </div>
 
      <div class="pipe-node">
        <div class="pipe-circle">03</div>
        <div class="pipe-label">
          <span class="pipe-icon">🧬</span>
          Put<br>Elastomer
        </div>
      </div>
 
      <div class="pipe-node">
        <div class="pipe-circle">04</div>
        <div class="pipe-label">
          <span class="pipe-icon">🔌</span>
          Seat<br>Headstage
        </div>
      </div>
 
      <div class="pipe-node">
        <div class="pipe-circle">05</div>
        <div class="pipe-label">
          <span class="pipe-icon">🔄</span>
          Rotate<br>Threaded Cap
        </div>
      </div>
 
      <div class="pipe-node">
        <div class="pipe-circle">06</div>
        <div class="pipe-label">
          <span class="pipe-icon">✅</span>
          Electrical<br>Verify
        </div>
      </div>
    </div>
 
    <!-- Validation Stats -->
    <div class="pipe-stats">
      <div class="pipe-stat-card">
        <div class="pipe-stat-title">Independent Operators Verified</div>
        <div class="pipe-stat-desc">Consistent connection yield across all users — decoupled from individual technique.</div>
      </div>
      <div class="pipe-stat-card">
        <div class="pipe-stat-title">200+ Mating Cycles</div>
        <div class="pipe-stat-desc">Zero degradation in contact impedance or yield over 5-day longitudinal durability test.</div>
      </div>
      <div class="pipe-stat-card">
        <div class="pipe-stat-title">180 min Vibration</div>
        <div class="pipe-stat-desc">Yield maintained under ~23 m/s² extreme acceleration stress testing.</div>
      </div>
    </div>
  </div>
</div>

<span id="en-components"></span>
## 🧩 System Components

<style>
.xs-sec{max-width:760px;margin:40px auto}
.xs-card{background:rgba(11,17,33,.95);border:1px solid rgba(59,130,246,.25);border-radius:20px;padding:30px 35px;box-shadow:inset 0 0 20px rgba(0,0,0,.4),0 15px 40px rgba(0,0,0,.2)}
.xs-card h3{margin:0 0 6px;color:#93c5fd;font-family:'JetBrains Mono',monospace;font-size:20px;font-weight:700;border-bottom:1px solid rgba(59,130,246,.25);padding-bottom:14px}
.xs-card>p{font-size:14px;color:#94a3b8;margin-bottom:20px;line-height:1.7}
.xs-v{position:relative;width:100%;border-radius:14px;overflow:hidden;border:1px solid rgba(59,130,246,.2);background:#000;margin-bottom:18px}
.xs-v img{width:100%;height:auto;display:block;transition:filter .5s}
.xs-v.focus img{filter:brightness(.9) saturate(.99)}
.xs-v.focus{border-color:rgba(59,130,246,.5);box-shadow:0 0 20px rgba(59,130,246,.2)}
.xs-h{position:absolute;border:2px solid transparent;border-radius:4px;cursor:pointer;transition:all .35s;z-index:3}
.xs-h:hover,.xs-h.on{border-color:var(--c);background:var(--bg);box-shadow:0 0 18px var(--g),inset 0 0 10px var(--g)}
.xs-h::after{content:'';position:absolute;inset:-5px;border-radius:8px;border:1.5px solid var(--c);opacity:0;pointer-events:none}
.xs-h.on::after{animation:xp 1.8s ease-out infinite}
@keyframes xp{0%{transform:scale(1);opacity:.7}to{transform:scale(1.2);opacity:0}}
.xs-b{position:absolute;top:50%;right:-9px;width:20px;height:20px;border-radius:50%;background:var(--c);color:#fff;font-family:'JetBrains Mono',monospace;font-size:12px;font-weight:800;display:flex;align-items:center;justify-content:center;box-shadow:0 0 8px var(--g);opacity:0;transform:translateY(-50%) scale(.5);transition:all .3s;z-index:8;pointer-events:none}
.xs-h:hover .xs-b,.xs-h.on .xs-b{opacity:1;transform:translateY(-50%) scale(1)}
.xs-t{position:absolute;font-family:'JetBrains Mono',monospace;font-size:12px;font-weight:700;color:#fff;background:rgba(0,0,0,.85);border:1px solid var(--c);padding:3px 10px;border-radius:6px;white-space:nowrap;pointer-events:none;opacity:0;transition:all .35s;z-index:11;box-shadow:0 0 10px var(--g)}
.xs-t.on{opacity:1}
.xs-g{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.xs-i{display:flex;gap:10px;padding:12px 14px;background:rgba(15,23,42,.4);border:1px solid rgba(255,255,255,.08);border-radius:10px;cursor:pointer;transition:all .3s;position:relative;align-items:center;box-shadow:0 0 8px rgba(59,130,246,.08)}
.xs-i::before{content:'';position:absolute;left:0;top:0;bottom:0;width:3px;background:var(--c);border-radius:3px 0 0 3px;opacity:0;transition:opacity .3s}
.xs-i:hover{background:rgba(15,23,42,.7);transform:translateX(2px);box-shadow:0 0 12px var(--g)}
.xs-i:hover::before{opacity:.5}
.xs-i.on{background:rgba(59,130,246,.08);border-color:var(--c);border-width:2px;box-shadow:0 0 15px var(--g),0 0 30px var(--g)}
.xs-i.on::before{opacity:1;width:4px}
.xs-n{width:22px;height:22px;border-radius:50%;background:var(--c);color:#fff;font-family:'JetBrains Mono',monospace;font-size:10px;font-weight:800;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.xs-i:hover .xs-n,.xs-i.on .xs-n{box-shadow:0 0 12px var(--g),0 0 24px var(--g)}
.xs-cn{font-family:'JetBrains Mono',monospace;font-size:13px;font-weight:700;color:#e2e8f0}
.xs-cs{font-size:11px;color:#94a3b8;line-height:1.35}
.xs-d{max-height:0;overflow:hidden;transition:max-height .4s,margin .3s;grid-column:1/-1}
.xs-d.open{max-height:140px;margin-top:6px}
.xs-d div{background:rgba(0,0,0,.25);border-radius:8px;padding:12px 16px;font-size:13px;color:#cbd5e1;line-height:1.6;border:1px solid rgba(255,255,255,.04)}
.xs-d strong{color:#93c5fd}
body.light-mode .xs-card{background:#fff;border-color:#cbd5e1}
body.light-mode .xs-card h3{color:#2563eb;border-color:#e2e8f0}
body.light-mode .xs-card>p{color:#475569}
body.light-mode .xs-i{background:#f8fafc;border-color:#e2e8f0}
body.light-mode .xs-cn{color:#1e293b}
body.light-mode .xs-cs{color:#64748b}
body.light-mode .xs-d div{background:#f1f5f9;color:#334155;border-color:#e2e8f0}
body.light-mode .xs-d strong{color:#1d4ed8}
body.light-mode .xs-t{background:rgba(255,255,255,.9);color:#0f172a}
@media(max-width:768px){.xs-card{padding:22px 16px}.xs-g{grid-template-columns:1fr}.xs-t{font-size:9px}}
</style>

<div class="xs-sec" data-aos="fade-up">
<div class="xs-card">
<h3>🔬 Interactive Cross-Section Explorer</h3>
<p>Click any component below or hover directly on the cross-section to highlight the corresponding layer and view specifications.</p>
<div class="xs-v" id="xV">
<img src="{{ '/Images/Assem new.PNG' | relative_url }}" alt="E-Link Cross-Section" loading="lazy">
<span class="xs-h" data-c="spi" style="left:43.5%;top:0%;width:13%;height:41%;--c:#3b82f6;--bg:rgba(59,130,246,.08);--g:rgba(59,130,246,.4)"><span class="xs-b">1</span></span>
<span class="xs-h" data-c="foam" style="left:20%;top:39.5%;width:61%;height:6.46%;z-index:5;--c:#f472b6;--bg:rgba(244,114,182,.15);--g:rgba(244,114,182,.4)"><span class="xs-b">2</span></span>
<span class="xs-h" data-c="cap" style="left:2%;top:36.5%;width:96%;height:26%;--c:#f59e0b;--bg:rgba(245,158,11,.08);--g:rgba(245,158,11,.35)"><span class="xs-b">3</span></span>
<span class="xs-h" data-c="pcb" style="left:17%;top:61.6%;width:65.6%;height:7.5%;--c:#22c55e;--bg:rgba(34,197,94,.08);--g:rgba(34,197,94,.35)"><span class="xs-b">4</span></span>
<span class="xs-h" data-c="elast" style="left:17%;top:68.6%;width:65.6%;height:1.88%;--c:#a78bfa;--bg:rgba(167,139,250,.12);--g:rgba(167,139,250,.4)"><span class="xs-b">5</span></span>
<span class="xs-h" data-c="adapt" style="left:17%;top:70.5%;width:65.6%;height:5%;--c:#eab308;--bg:rgba(234,179,8,.12);--g:rgba(234,179,8,.35)"><span class="xs-b">6</span></span>
<span class="xs-t" data-k="spi" style="--c:#3b82f6;--g:rgba(59,130,246,.4);right:18%;top:18%">1. SPI Cables</span>
<span class="xs-t" data-k="foam" style="--c:#f472b6;--g:rgba(244,114,182,.4);right:18%;top:36%">2. Foam Washer</span>
<span class="xs-t" data-k="cap" style="--c:#f59e0b;--g:rgba(245,158,11,.35);right:18%;top:33%">3. Threaded Cap</span>
<span class="xs-t" data-k="pcb" style="--c:#22c55e;--g:rgba(34,197,94,.35);right:18%;top:58%">4. Headstage PCB</span>
<span class="xs-t" data-k="elast" style="--c:#a78bfa;--g:rgba(167,139,250,.4);right:18%;top:65%">5. Elastomer</span>
<span class="xs-t" data-k="adapt" style="--c:#eab308;--g:rgba(234,179,8,.35);right:18%;top:68%">6. Adapter PCB</span>
</div>
<div class="xs-g" id="xG">
<div class="xs-i" data-c="spi" style="--c:#3b82f6"><span class="xs-n">1</span><div><div class="xs-cn">SPI Cables</div><div class="xs-cs">Dual Omnetics A7621</div></div></div>
<div class="xs-i" data-c="foam" style="--c:#f472b6"><span class="xs-n">2</span><div><div class="xs-cn">Foam Washer</div><div class="xs-cs">Pressure distribution</div></div></div>
<div class="xs-i" data-c="cap" style="--c:#f59e0b"><span class="xs-n">3</span><div><div class="xs-cn">Threaded Cap</div><div class="xs-cs">Compression housing</div></div></div>
<div class="xs-i" data-c="pcb" style="--c:#22c55e"><span class="xs-n">4</span><div><div class="xs-cn">Headstage PCB</div><div class="xs-cs">4× RHD2164 + 4Layer HDI</div></div></div>
<div class="xs-i" data-c="elast" style="--c:#a78bfa"><span class="xs-n">5</span><div><div class="xs-cn">Elastomeric Sheet</div><div class="xs-cs">Z-axis conductor</div></div></div>
<div class="xs-i" data-c="adapt" style="--c:#eab308"><span class="xs-n">6</span><div><div class="xs-cn">Adapter PCB</div><div class="xs-cs">Probe signal routing</div></div></div>
<div class="xs-d" id="xD"><div id="xDI"></div></div>
</div>
</div>
</div>

<script>
(function(){var D={spi:'<strong>Wire:</strong> 32AWG 12-conductor | <strong>Interface:</strong> Dual SPI 2×128ch',foam:'<strong>Material:</strong> Closed-cell silicone | <strong>Thickness:</strong> 1.5→0.8mm | Compensates planarity errors',cap:'<strong>Material:</strong> PEEK/Surgical resin | <strong>Function:</strong> Torque → uniform axial compression across 25mm Ø',pcb:'<strong>ICs:</strong> 4× RHD2164 BGA | <strong>Passives:</strong> 7R+8C LVDS +1 LED | <strong>Bottom:</strong> 256-pad BGA 0.4mm',elast:'<strong>Pitch:</strong> 156µm (3.2× denser than BGA) | Z-axis conduction under compression | Zero insertion force',adapt:'<strong>Layers:</strong> 4L HDI | <strong>Top:</strong> BGA match via elastomer | <strong>Bottom:</strong> Probe bond pads | ENIG finish'};
function go(){var v=document.getElementById('xV'),g=document.getElementById('xG'),d=document.getElementById('xD'),di=document.getElementById('xDI');if(!v||!g)return;
var hs=v.querySelectorAll('.xs-h'),ts=v.querySelectorAll('.xs-t'),cs=g.querySelectorAll('.xs-i'),cur=null;
function act(k){if(cur===k){off();return}cur=k;v.classList.add('focus');
hs.forEach(function(h){h.classList.toggle('on',h.dataset.c===k)});
ts.forEach(function(t){t.classList.toggle('on',t.dataset.k===k)});
cs.forEach(function(c){c.classList.toggle('on',c.dataset.c===k)});
if(D[k]){di.innerHTML=D[k];d.classList.add('open');var ac=g.querySelector('.xs-i[data-c="'+k+'"]');if(ac)ac.after(d)}}
function off(){cur=null;v.classList.remove('focus');hs.forEach(function(h){h.classList.remove('on')});ts.forEach(function(t){t.classList.remove('on')});cs.forEach(function(c){c.classList.remove('on')});d.classList.remove('open')}
hs.forEach(function(h){h.addEventListener('click',function(e){e.stopPropagation();act(h.dataset.c)});
h.addEventListener('mouseenter',function(){if(!cur){ts.forEach(function(t){t.classList.toggle('on',t.dataset.k===h.dataset.c)});cs.forEach(function(c){c.classList.toggle('on',c.dataset.c===h.dataset.c)})}});
h.addEventListener('mouseleave',function(){if(!cur){ts.forEach(function(t){t.classList.remove('on')});cs.forEach(function(c){c.classList.remove('on')})}})});
cs.forEach(function(c){c.addEventListener('click',function(e){e.stopPropagation();act(c.dataset.c)});
c.addEventListener('mouseenter',function(){if(!cur){hs.forEach(function(h){h.classList.toggle('on',h.dataset.c===c.dataset.c)});ts.forEach(function(t){t.classList.toggle('on',t.dataset.k===c.dataset.c)})}});
c.addEventListener('mouseleave',function(){if(!cur){hs.forEach(function(h){h.classList.remove('on')});ts.forEach(function(t){t.classList.remove('on')})}})});
document.addEventListener('click',function(e){if(cur&&!v.contains(e.target)&&!g.contains(e.target))off()});
document.addEventListener('keydown',function(e){if(e.key==='Escape')off()})}
if(document.readyState==='loading')document.addEventListener('DOMContentLoaded',go);else go()})();
</script>

<div align="center">
 <table border="1" style="border-collapse: collapse; width: 90%; text-align: center;">
  <thead>
    <tr style="background-color: #f2f2f2;">
      <th>Component</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Pedestal Housing</b></td>
      <td>3D-printed/machined pedestal providing structural support and cranial fixation</td>
    </tr>
    <tr>
      <td><b>Customized 256Ch Headstage</b></td>
      <td>Form-factor optimized recording interface for high-density 128/256-channel signal acquisition</td>
    </tr>
    <tr>
      <td><b>Foam Washer</b></td>
      <td>Provides compliant compression to ensure uniform electrical contact across the elastomeric interface</td>
    </tr>
    <tr>
      <td><b>Adapter PCB</b></td>
      <td>High-density 4-layer PCB for routing signals from thin-film probes to headstage ball array pattern</td>
    </tr>
    <tr>
      <td><b>Surgical Cap</b></td>
      <td>Protective enclosure preserving electrical and mechanical integrity throughout chronic experiments</td>
    </tr>
  </tbody>
 </table>
</div>
 
---
 
<style>
/* ── Impedance Heatmap Styles ── */
.impedance-section { max-width: 760px; margin: 40px auto; }
 
.impedance-card {
  background: rgba(11, 17, 33, 0.95);
  border: 1px solid rgba(59, 130, 246, 0.25);
  border-radius: 20px;
  padding: 30px 35px;
  box-shadow: inset 0 0 20px rgba(0,0,0,0.4), 0 15px 40px rgba(0,0,0,0.2);
}
 
.impedance-card-title {
  margin: 0 0 6px 0;
  color: #93c5fd;
  font-family: 'JetBrains Mono', monospace;
  font-size: 20px;
  font-weight: 700;
  border-bottom: 1px solid rgba(59, 130, 246, 0.25);
  padding-bottom: 14px;
  letter-spacing: 0.5px;
}
 
.impedance-desc {
  font-size: 14px;
  color: #94a3b8;
  margin-bottom: 24px;
  line-height: 1.7;
}
 
.impedance-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 28px;
  align-items: start;
}
 
.heatmap-wrapper {
  width: 100%;
  aspect-ratio: 1 / 1;
  max-width: 320px;
  margin: 0 auto;
  border-radius: 12px;
  overflow: hidden;
  border: 1px solid rgba(59, 130, 246, 0.25);
  box-shadow: 0 8px 30px rgba(0,0,0,0.3);
}
 
#impedance-canvas {
  width: 100%;
  height: 100%;
  display: block;
  image-rendering: pixelated;
}
 
.heatmap-legend {
  display: flex;
  justify-content: space-between;
  max-width: 320px;
  margin: 10px auto 0;
  font-size: 10px;
  color: #94a3b8;
  font-family: 'JetBrains Mono', monospace;
}
 
.heatmap-legend-bar {
  flex: 1;
  height: 8px;
  margin: 2px 10px;
  border-radius: 4px;
  background: linear-gradient(90deg, 
    hsl(220, 80%, 40%), 
    hsl(180, 70%, 45%), 
    hsl(100, 60%, 48%), 
    hsl(40, 80%, 55%), 
    hsl(0, 80%, 50%)
  );
}
 
.findings-panel {
  background: rgba(15, 23, 42, 0.5);
  padding: 18px;
  border-radius: 12px;
  border: 1px solid rgba(59, 130, 246, 0.2);
  margin-bottom: 16px;
}
 
.findings-label {
  font-size: 12px;
  font-weight: 700;
  color: #93c5fd;
  font-family: 'JetBrains Mono', monospace;
  margin-bottom: 12px;
  letter-spacing: 1.5px;
  text-transform: uppercase;
}
 
.finding-row {
  display: flex;
  gap: 12px;
  margin-bottom: 10px;
  font-size: 14px;
  align-items: baseline;
}
 
.finding-val {
  font-family: 'JetBrains Mono', monospace;
  font-weight: 700;
  white-space: nowrap;
  min-width: 75px;
}
 
.finding-val.good { color: #10b981; }
.finding-val.warn { color: #f59e0b; }
 
.finding-desc { color: #cbd5e1; }
 
.conclusion-box {
  background: rgba(16, 185, 129, 0.06);
  border: 1px solid rgba(16, 185, 129, 0.25);
  border-radius: 10px;
  padding: 14px 18px;
}
 
.conclusion-box p {
  font-size: 14px;
  color: #cbd5e1 !important;
  margin: 0;
  line-height: 1.65;
}
 
/* ── Axis labels ── */
.heatmap-container { position: relative; max-width: 320px; margin: 0 auto; padding-left: 28px; }
 
.axis-x-label, .axis-y-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 10px;
  color: #64748b;
  text-align: center;
}
 
.axis-x-label { margin-top: 6px; }
 
.axis-y-label {
  position: absolute;
  left: -24px;
  top: 50%;
  transform: translateY(-50%) rotate(-90deg);
  white-space: nowrap;
}
 
/* ── Light mode ── */
body.light-mode .impedance-card {
  background: #ffffff;
  border-color: #cbd5e1;
  box-shadow: 0 15px 40px rgba(0,0,0,0.05);
}
 
body.light-mode .impedance-card-title { color: #2563eb; border-bottom-color: #e2e8f0; }
body.light-mode .impedance-desc { color: #475569; }
body.light-mode .findings-panel { background: #f8fafc; border-color: #e2e8f0; }
body.light-mode .findings-label { color: #1d4ed8; }
body.light-mode .finding-desc { color: #334155; }
body.light-mode .conclusion-box { background: rgba(16, 185, 129, 0.05); border-color: rgba(16, 185, 129, 0.2); }
body.light-mode .conclusion-box p { color: #334155 !important; }
body.light-mode .heatmap-legend { color: #64748b; }
 
/* ── Mobile ── */
@media (max-width: 768px) {
  .impedance-grid { grid-template-columns: 1fr; }
  .impedance-card { padding: 25px 18px; }
}
</style>
 
<div class="impedance-section" data-aos="fade-up">
  <div class="impedance-card">
    <h3 class="impedance-card-title">🔬 16×16 Spatial Impedance Mapping</h3>
    <p class="impedance-desc">
      Gold-film test interface validates uniform contact pressure distribution. The threaded housing converts manual torque into uniform axial pressure across the entire 25-mm footprint.
    </p>
 
    <div class="impedance-grid">
      <!-- LEFT: Heatmap -->
      <div>
        <div class="heatmap-container">
          <span class="axis-y-label">Row Index</span>
          <div class="heatmap-wrapper">
            <canvas id="impedance-canvas" width="256" height="256"></canvas>
          </div>
          <div class="axis-x-label">Column Index</div>
        </div>
        <div class="heatmap-legend">
          <span>0.3 kΩ</span>
          <div class="heatmap-legend-bar"></div>
          <span>2.0 kΩ</span>
        </div>
      </div>
 
      <!-- RIGHT: Findings -->
      <div>
        <div class="findings-panel">
          <div class="findings-label">Results</div>
          <div class="finding-row">
            <span class="finding-val good">253 / 256</span>
            <span class="finding-desc">channels within 0.3 – 0.4 kΩ</span>
          </div>
          <div class="finding-row">
            <span class="finding-val warn">3 channels</span>
            <span class="finding-desc">> 1.0 kΩ (BGA reflow defects)</span>
          </div>
          <div class="finding-row">
            <span class="finding-val good">0 failures</span>
            <span class="finding-desc">from connector interface itself</span>
          </div>
        </div>
 
        <div class="conclusion-box">
          <p>
            <strong style="color: #34d399;">Conclusion:</strong> The mechanical connector interface achieves 
            <strong style="color: #ffffff;">100% connection fidelity</strong>.
          </p>
        </div>
      </div>
    </div>
  </div>
</div>
 
<script>
// ── Impedance Heatmap Renderer ──
(function() {
  function renderHeatmap() {
    var canvas = document.getElementById('impedance-canvas');
    if (!canvas || canvas.dataset.rendered === 'true') return;
    var ctx = canvas.getContext('2d');
    var size = 16;
    var cellW = canvas.width / size;
    var cellH = canvas.height / size;
    
    // Seed for reproducible "random" values
    var seed = 42;
    function seededRandom() {
      seed = (seed * 16807 + 0) % 2147483647;
      return (seed - 1) / 2147483646;
    }
    
    for (var r = 0; r < size; r++) {
      for (var c = 0; c < size; c++) {
        var val = 0.3 + seededRandom() * 0.12;
        
        // 3 bad channels — matching paper data
        if ((r === 2 && c === 5) || (r === 10 && c === 3) || (r === 7 && c === 14)) {
          val = 1.2 + seededRandom() * 0.8;
        }
        
        // Slight gradient: edges slightly higher
        var edgeFactor = Math.min(r, c, 15 - r, 15 - c) / 8;
        val += (1 - edgeFactor) * 0.03;
        
        var norm = Math.min(val / 2.0, 1.0);
        var hue = (1 - norm) * 220;
        var sat = 75 + norm * 10;
        var light = 32 + norm * 28;
        
        ctx.fillStyle = 'hsl(' + hue + ', ' + sat + '%, ' + light + '%)';
        ctx.fillRect(c * cellW, r * cellH, cellW - 0.8, cellH - 0.8);
      }
    }
    canvas.dataset.rendered = 'true';
  }
 
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', renderHeatmap);
  } else {
    renderHeatmap();
  }
})();
</script>

<span id="en-features"></span>
## ✨ Key Features
<div class="species-compatibility-container" align="center" style="margin: 40px auto; max-width: 760px;">
  <h3 style="color: #60a5fa; margin-bottom: 20px; font-family: sans-serif;">🌍 Future Application Roadmap </h3>
  
  <div class="species-glass-box">
  <svg class="connection-lines" viewBox="0 0 600 380" preserveAspectRatio="none" style="z-index: 1;">
    <path class="base-line" d="M300,141 L100,225" stroke="rgba(255,255,255,0.1)" fill="none" /> 
    <path class="base-line" d="M300,141 L300,255" stroke="rgba(255,255,255,0.1)" fill="none" /> 
    <path class="base-line" d="M300,141 L500,225" stroke="rgba(255,255,255,0.1)" fill="none" /> 
    
    <path class="pulse-line line-to-mouse" d="M300,141 L100,225" />
    <path class="pulse-line line-to-rat" d="M300,141 L300,255" />
    <path class="pulse-line line-to-monkey" d="M300,141 L500,225" />
  </svg>

 <div class="node center-node">
      <div class="hex-border">
        <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M7 2V4M12 2V4M17 2V4M22 7H20M22 12H20M22 17H20M17 22V20M12 22V20M7 22V20M2 17H4M2 12H4M2 7H4M6 6H18V18H6V6ZM9 9V15H15V9H9Z" stroke="#60a5fa" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
      <div class="node-text pulse-text">E-Link (256)</div>
    </div>

 <div class="animal-nodes">
      
  <div class="node sub-node">
        <div class="icon-circle mouse-glow">
          <span style="font-size: 30px;">🐁</span>
        </div>
        <div class="node-title"><i>Mouse</i></div>
        <div class="node-desc">Housing Removed<br><b><font color="#10b981">2.8g</font> Payload</b></div>
      </div>

  <div class="node sub-node rat-node-adjust">
        <div class="icon-circle rat-glow">
          <span style="font-size: 30px;">🐀</span>
        </div>
        <div class="node-title"><i>Rat</i></div>
        <div class="node-desc">Standard Implant<br><b><font color="#3b82f6">6.6g</font> Total</b></div>
      </div>

  <div class="node sub-node">
        <div class="icon-circle monkey-glow">
          <span style="font-size: 30px;">🐒</span>
        </div>
        <div class="node-title"><i>Macaque</i></div>
        <div class="node-desc">High Durability<br><b><font color="#f59e0b">Multi-Array Scalable</font></b></div>
      </div>

    </div>
  </div>
</div>

<style>
/* ── Scalability Roadmap Styles ── */
.scale-section { max-width: 760px; margin: 40px auto; }
 
.scale-card {
  background: rgba(11, 17, 33, 0.95);
  border: 1px solid rgba(59, 130, 246, 0.25);
  border-radius: 20px;
  padding: 30px 35px;
  box-shadow: inset 0 0 20px rgba(0,0,0,0.4), 0 15px 40px rgba(0,0,0,0.2);
}
 
.scale-card-title {
  margin: 0 0 6px 0;
  color: #93c5fd;
  font-family: 'JetBrains Mono', monospace;
  font-size: 20px;
  font-weight: 700;
  border-bottom: 1px solid rgba(59, 130, 246, 0.25);
  padding-bottom: 14px;
  letter-spacing: 0.5px;
}
 
.scale-desc {
  font-size: 14px;
  color: #94a3b8;
  margin-bottom: 28px;
  line-height: 1.7;
}
 
/* ── Bar chart ── */
.scale-bars {
  display: flex;
  justify-content: center;
  align-items: flex-end;
  gap: 0;
  margin-bottom: 0;
  height: 220px;
  padding: 0 20px;
}
 
.scale-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex: 1;
  max-width: 180px;
}
 
.scale-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 12px;
  font-weight: 700;
  margin-bottom: 8px;
  letter-spacing: 0.5px;
}
 
.scale-bar {
  width: 70%;
  border-radius: 10px 10px 0 0;
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: none;
  position: relative;
  transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}
 
.scale-bar-value {
  font-family: 'JetBrains Mono', monospace;
  font-size: 22px;
  font-weight: 800;
}
 
/* Active (current) */
.scale-bar.active {
  background: linear-gradient(to top, #3b82f6, rgba(59, 130, 246, 0.5));
  border: 1px solid #3b82f6;
  border-bottom: none;
  box-shadow: 0 0 25px rgba(59, 130, 246, 0.25);
}
.scale-bar.active .scale-bar-value { color: #ffffff; }
 
/* Future */
.scale-bar.future {
  border: 1px solid rgba(255,255,255,0.08);
  border-bottom: none;
}
 
.scale-bar.future-green {
  background: linear-gradient(to top, rgba(16, 185, 129, 0.25), rgba(16, 185, 129, 0.08));
  border-color: rgba(16, 185, 129, 0.2);
}
.scale-bar.future-green .scale-bar-value { color: rgba(16, 185, 129, 0.7); }
 
.scale-bar.future-amber {
  background: linear-gradient(to top, rgba(245, 158, 11, 0.25), rgba(245, 158, 11, 0.08));
  border-color: rgba(245, 158, 11, 0.2);
}
.scale-bar.future-amber .scale-bar-value { color: rgba(245, 158, 11, 0.7); }
 
/* Gradient baseline */
.scale-gradient-line {
  height: 3px;
  border-radius: 2px;
  background: linear-gradient(90deg, #3b82f6, #10b981, #f59e0b);
  margin-bottom: 20px;
  box-shadow: 0 0 12px rgba(59, 130, 246, 0.3);
}
 
/* Pitch comparison card */
.pitch-compare {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 14px;
  margin-top: 20px;
}
 
.pitch-box {
  background: rgba(15, 23, 42, 0.5);
  border: 1px solid rgba(59, 130, 246, 0.15);
  border-radius: 12px;
  padding: 16px 20px;
  text-align: center;
  position: relative;
  overflow: hidden;
}
 
.pitch-box::before {
  content: '';
  position: absolute;
  top: 0;
  left: 15%;
  right: 15%;
  height: 2px;
  border-radius: 0 0 4px 4px;
  opacity: 0.5;
}
 
.pitch-box.ours::before { background: #3b82f6; }
.pitch-box.theirs::before { background: #64748b; }
 
.pitch-value {
  font-family: 'JetBrains Mono', monospace;
  font-size: 28px;
  font-weight: 800;
  display: block;
  margin-bottom: 2px;
}
 
.pitch-box.ours .pitch-value { color: #3b82f6; text-shadow: 0 0 15px rgba(59, 130, 246, 0.3); }
.pitch-box.theirs .pitch-value { color: #64748b; }
 
.pitch-label {
  font-size: 12px;
  color: #94a3b8;
  font-family: 'JetBrains Mono', monospace;
  letter-spacing: 0.5px;
}
 
.pitch-tag {
  display: inline-block;
  font-size: 10px;
  padding: 2px 10px;
  border-radius: 10px;
  margin-top: 8px;
  font-weight: 700;
  font-family: 'JetBrains Mono', monospace;
  letter-spacing: 0.5px;
}
 
.pitch-box.ours .pitch-tag {
  background: rgba(59, 130, 246, 0.15);
  color: #60a5fa;
  border: 1px solid rgba(59, 130, 246, 0.3);
}
 
.pitch-box.theirs .pitch-tag {
  background: rgba(148, 163, 184, 0.1);
  color: #94a3b8;
  border: 1px solid rgba(148, 163, 184, 0.2);
}
 
.scale-footer {
  text-align: center;
  font-size: 14px;
  color: #cbd5e1;
  margin-top: 22px;
  line-height: 1.6;
}
 
/* ── Light mode ── */
body.light-mode .scale-card {
  background: #ffffff;
  border-color: #cbd5e1;
  box-shadow: 0 15px 40px rgba(0,0,0,0.05);
}
body.light-mode .scale-card-title { color: #2563eb; border-bottom-color: #e2e8f0; }
body.light-mode .scale-desc { color: #475569; }
body.light-mode .scale-bar.active { background: linear-gradient(to top, #3b82f6, #93c5fd); }
body.light-mode .scale-bar.future-green { background: linear-gradient(to top, rgba(16, 185, 129, 0.15), rgba(16, 185, 129, 0.05)); }
body.light-mode .scale-bar.future-amber { background: linear-gradient(to top, rgba(245, 158, 11, 0.15), rgba(245, 158, 11, 0.05)); }
body.light-mode .pitch-box { background: #f8fafc; border-color: #e2e8f0; }
body.light-mode .scale-footer { color: #334155; }
body.light-mode .pitch-label { color: #64748b; }
 
/* ── IntersectionObserver animated entry ── */
.scale-bar { transform: scaleY(0); transform-origin: bottom; }
.scale-bar.animate-in { transform: scaleY(1); }
 
@media (max-width: 768px) {
  .scale-bars { height: 180px; padding: 0 10px; }
  .scale-bar-value { font-size: 16px; }
  .scale-label { font-size: 10px; margin-bottom: 4px; }
  .pitch-compare { grid-template-columns: 1fr; }
  .pitch-value { font-size: 24px; }
  .scale-bar.active { height: 70px !important; }
  .scale-bar.future-green { height: 115px !important; }
  .scale-bar.future-amber { height: 160px !important; }
}
</style>
 
<div class="scale-section" data-aos="fade-up">
  <div class="scale-card">
    <h3 class="scale-card-title">🚀 Scalability Roadmap: Pathway to 1024 Channels</h3>
    <p class="scale-desc">
      The inherent pitch advantage of anisotropic elastomeric technology enables massive channel scaling within the <strong style="color: #e2e8f0;">same 25-mm diameter footprint</strong>, without modifications to the mechanical compression housing.
    </p>
 
    <!-- Bar Chart -->
    <div class="scale-bars" id="scale-bars-container">
      <div class="scale-col">
        <span class="scale-label" style="color: #3b82f6;">CURRENT</span>
        <div class="scale-bar active" style="height: 90px;" data-target-height="90">
          <span class="scale-bar-value">256</span>
        </div>
      </div>
      <div class="scale-col">
        <span class="scale-label" style="color: #10b981;">NEXT PHASE</span>
        <div class="scale-bar future future-green" style="height: 140px;" data-target-height="140">
          <span class="scale-bar-value">512</span>
        </div>
      </div>
      <div class="scale-col">
        <span class="scale-label" style="color: #f59e0b;">TARGET</span>
        <div class="scale-bar future future-amber" style="height: 195px;" data-target-height="195">
          <span class="scale-bar-value">1024+</span>
        </div>
      </div>
    </div>
 
    <div class="scale-gradient-line"></div>
 
    <!-- Pitch Comparison -->
    <div class="pitch-compare">
      <div class="pitch-box ours">
        <span class="pitch-value">156 µm</span>
        <span class="pitch-label">Elastomeric Pillar Pitch</span>
        <span class="pitch-tag">3.2× DENSER</span>
      </div>
      <div class="pitch-box theirs">
        <span class="pitch-value">500 µm</span>
        <span class="pitch-label">Standard Solder Ball Pitch</span>
        <span class="pitch-tag">INDUSTRY BASELINE</span>
      </div>
    </div>
 
    <p class="scale-footer">
      Same <strong style="color: #ffffff;">25 mm Ø</strong> footprint · HDI PCB fan-out · Fine-pitch elastomer pillar arrangement
    </p>
  </div>
</div>
 
<script>
// ── Scalability Bar Animation (IntersectionObserver) ──
(function() {
  function initScaleAnim() {
    var container = document.getElementById('scale-bars-container');
    if (!container) return;
    
    var bars = container.querySelectorAll('.scale-bar');
    
    var observer = new IntersectionObserver(function(entries) {
      entries.forEach(function(entry) {
        if (entry.isIntersecting) {
          // Stagger the animation
          bars.forEach(function(bar, i) {
            setTimeout(function() {
              bar.classList.add('animate-in');
            }, i * 200);
          });
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.3 });
 
    observer.observe(container);
  }
 
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', initScaleAnim);
  } else {
    initScaleAnim();
  }
})();
</script>

<style>
.species-glass-box { position: relative; background: rgba(15, 23, 42, 0.4); border: 1px solid rgba(59, 130, 246, 0.2); border-radius: 16px; padding: 30px 20px 40px 20px; min-height: 380px; overflow: hidden; box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2); transform: translateZ(0); backface-visibility: hidden; perspective: 1000; will-change: transform; }
.connection-lines { position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 1; pointer-events: none; }
.base-line { fill: none; stroke: rgba(255, 255, 255, 0.1); stroke-width: 2; }
.pulse-line { fill: none; stroke: #60a5fa; stroke-width: 3; stroke-linecap: round; stroke-dasharray: 15 125; animation: data-flow 2.8s linear infinite; filter: drop-shadow(0 0 6px rgba(96, 165, 250, 0.8)); }
.line-to-monkey { stroke: #f59e0b !important; filter: drop-shadow(0 0 6px rgba(245, 158, 11, 0.8)) !important;}
.line-to-mouse { stroke: #10b981 !important; filter: drop-shadow(0 0 6px rgba(16, 185, 129, 0.8)) !important; }
.line-to-rat { stroke-dasharray: 9 106 !important; animation: data-flow-mid 2.3s linear infinite !important; }
@keyframes data-flow-mid { from { stroke-dashoffset: 115; } to { stroke-dashoffset: 0; } }
@keyframes data-flow { from { stroke-dashoffset: 140; } to { stroke-dashoffset: 0; } }

.node { position: relative; z-index: 2; display: flex; flex-direction: column; align-items: center; flex: 1; min-width: 0; }
.center-node { margin-bottom: 20px; flex: none; width: 100%; }
.hex-border { width: 70px; height: 70px; background: radial-gradient(circle, rgba(59,130,246,0.3) 0%, transparent 70%); border: 2px solid #3b82f6; border-radius: 12px; display: flex; justify-content: center; align-items: center; box-shadow: 0 0 15px rgba(59, 130, 246, 0.5); animation: float 3s ease-in-out infinite; }
@keyframes float { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-8px); } }
.node-text { margin-top: 10px; font-weight: bold; color: #fff; font-family: 'JetBrains Mono', monospace; font-size: 14px; }
.pulse-text { text-shadow: 0 0 8px rgba(96, 165, 250, 0.8); }

.animal-nodes { display: flex; justify-content: space-between; width: 100%; align-items: flex-start; margin-top: 60px; }
.rat-node-adjust { transform: translateY(30px) translateZ(0); }
.icon-circle { width: 60px; height: 60px; border-radius: 50%; background: #0f172a; isolation: isolate; border: 1px solid rgba(255,255,255,0.2); display: flex; justify-content: center; align-items: center; position: relative; z-index: 5; transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1), box-shadow 0.3s ease; }
.icon-circle:hover { transform: scale(1.1); border-color: #60a5fa; background: rgba(96, 165, 250, 0.1); }
.mouse-glow { box-shadow: 0 0 10px rgba(16, 185, 129, 0.5); }
.rat-glow { box-shadow: 0 0 10px rgba(59, 130, 246, 0.5); }
.monkey-glow { box-shadow: 0 0 15px rgba(245, 158, 11, 0.6); border-color: rgba(245, 158, 11, 0.5) !important; }
.node-title { margin-top: 8px; font-weight: bold; color: #e2e8f0; font-size: 14px; }
.node-desc { margin-top: 4px; color: #94a3b8; font-size: 11px; text-align: center; line-height: 1.4; font-family: sans-serif; }

@media (max-width: 600px) {
  .species-glass-box { padding: 25px 5px 30px 5px; min-height: 350px; } 
  .center-node .node-text { margin-top: 2px !important; font-size: 13px; }
  .icon-circle { width: 45px; height: 45px; }
  .icon-circle span { font-size: 24px !important; }
  .node-title { font-size: 12px; }
  .node-desc { font-size: 9px; }
  .connection-lines { opacity: 0.8; }
  .pulse-line { stroke-width: 2; }
  .animal-nodes { margin-top: 50px; } 
  .rat-node-adjust { transform: translateY(25px) translateZ(0); }
}
</style> 

<style> 
.watermark-features { color: rgba(148, 163, 184, 0.4); font-size: 0.95em; line-height: 1.7; font-weight: 400; letter-spacing: 0.3px; }
.watermark-features ul { padding-left: 10px; list-style: none; }
.watermark-features li { margin-bottom: 35px; padding-left: 20px; position: relative; transition: all 0.8s cubic-bezier(0.22, 1, 0.36, 1); border-left: 2px solid rgba(59, 130, 246, 0); }
.watermark-features li.aos-animate { color: rgba(241, 245, 249, 0.95); border-left: 2px solid #3b82f6; }
body.light-mode .watermark-features { color: rgba(71, 85, 105, 0.3); }
body.light-mode .watermark-features li.aos-animate { color: #1e293b; border-left-color: #2563eb; }
body.light-mode .watermark-features strong { color: #2563eb; text-shadow: none; }
</style>

<div class="watermark-features">
  <ul>
    <li data-aos="fade-up" data-aos-delay="0">
      <strong>⚡ 256-Channel High-Density & Scalable Interface</strong><br>
      Compact pedestal footprint supporting 256-ch acquisition. The elastomer-based design offers a clear scaling roadmap (up to 1024-ch) without increasing physical size.
    </li>
    <li data-aos="fade-up" data-aos-delay="100">
      <strong>🔌 Zero-Force "Soft" Interconnect</strong><br>
      By replacing rigid pins with Anisotropic Conductive Elastomer, the system shifts from "insertion" to "compression," eliminating common "bent pin" failure modes.
    </li>
    <li data-aos="fade-up" data-aos-delay="200">
      <strong>🎯 Self-Aligning & High Tolerance</strong><br>
      Features high-precision mechanical guidance with "Structural Redundancy," naturally forgiving minor manual misalignments without microscopic assistance.
    </li>
    <li data-aos="fade-up" data-aos-delay="300">
      <strong>🛠️ Modular Maintenance & On-Demand Assembly</strong><br>
      Separable "Sandwich" structure allows independent replacement of damaged modules and supports on-demand chip soldering to save research costs.
    </li>
    <li data-aos="fade-up" data-aos-delay="400">
      <strong>🪶 Detachable Active Electronics</strong><br>
      Easily separate heavy electronics from the implanted pedestal during rest, leaving only a lightweight passive interface to promote natural animal behavior.
    </li>
    <li data-aos="fade-up" data-aos-delay="500">
      <strong>🐭 Optimized for Chronic In-Vivo Research</strong><br>
      Lightweight core (2.8g) and low-profile design compatible with commutators, ensuring robust long-term recording in freely moving animals.
    </li>
    <li data-aos="fade-up" data-aos-delay="600">
      <strong>🧪 Surgical-Grade Integration</strong><br>
      Textured sidewalls for superior adhesion and customizable base curvature to match specific cranial profiles, creating a rock-solid isolation chamber.
    </li>
  </ul>
</div>

<div align="center" data-aos="zoom-in-up" data-aos-duration="1000">
 <br>
 <div class="gif-placeholder">
  <img data-src="Videos/Animation%20repeat.gif" 
        src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7"
        alt="ELINK-256 Animation GIF"
        class="lazy-gif white-bg-gif" 
        decoding="async">
 </div>
</div>

---

<span id="en-signal-demo"></span>
### ⚡ Representative Spike Signal Acquisition (Simulation)

<p style="color: #64748b; font-size: 0.95em; margin-bottom: 20px;">
  An interactive simulation demonstrating the acquisition of extracellular action potentials (spikes). The signals are modeled within a standard spike-band filter (300 Hz – 7.5 kHz) at a 30 kS/s sampling rate, reflecting the expected waveform morphology, thermal noise floor, and signal-to-noise ratio (SNR) during high-density recordings with the E-Link system.
</p>

<style>
/* ===================== Intan RHX 像素级复刻 (双屏优化) ===================== */
.intan-simulator-wrapper { width: 100%; max-width: 860px; margin: 40px auto; background: #2b2b2b; border: 1px solid #1a1a1a; border-radius: 6px; box-shadow: 0 20px 60px rgba(0, 0, 0, 0.8), 0 0 0 1px rgba(255, 255, 255, 0.1) inset; overflow: hidden; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; user-select: none; transform: translateZ(0); }
.intan-title-bar { background: linear-gradient(to bottom, #4a4a4a, #333333); padding: 5px 12px; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid #111; }
.intan-title-text { color: #e0e0e0; font-size: 12px; font-weight: 600; display: flex; align-items: center; gap: 6px; letter-spacing: 0.5px; line-height: 1.3; }
.intan-title-text svg { flex-shrink: 0; }
.intan-window-controls { display: flex; align-items: center; flex-shrink: 0; }
.intan-window-controls span { display: block; width: 12px; height: 12px; border-radius: 50%; margin-left: 6px; background: #555; flex-shrink: 0; }
.intan-window-controls span.close { background: #ff5f56; } .intan-window-controls span.min { background: #ffbd2e; } .intan-window-controls span.max { background: #27c93f; }

.intan-body { display: flex; height: 420px; background: #000; }
.intan-plots-wrapper { flex: 1; display: flex; border-top: 1px solid #222; min-height: 0; }
.intan-plot-pane { flex: 1 1 0%; display: flex; flex-direction: column; position: relative; background: #000000; border-right: 2px solid #333; min-height: 0; }

.intan-time-axis { height: 20px; display: flex; justify-content: space-between; align-items: flex-end; padding: 0 10px 0 100px; border-bottom: 1px solid #444; color: #aaa; font-family: 'JetBrains Mono', monospace; font-size: 10px; background: #000; z-index: 10; flex-shrink: 0; }
.intan-time-axis span { position: relative; }
.intan-time-axis span::after { content: ''; position: absolute; bottom: -5px; left: 50%; transform: translateX(-50%); width: 1px; height: 5px; background: #888; }

.intan-canvas-container { flex: 1 1 0%; position: relative; overflow: hidden; background: #000000; min-height: 0; }
.intan-canvas { position: absolute; top: 0; left: 0; width: 100%; height: 100%; display: block; }

.intan-pane-footer { height: 24px; background: #e0e0e0; display: flex; justify-content: space-between; align-items: center; padding: 0 8px; font-size: 11px; color: #333; font-weight: 500; border-top: 1px solid #111; flex-shrink: 0; white-space: nowrap; overflow: hidden;    }
.intan-footer-tools { display: flex; align-items: center; gap: 6px; color: #555; white-space: nowrap; }
.intan-footer-tools label { display: inline-flex; align-items: center; gap: 3px; margin: 0; padding: 0; font-weight: normal; cursor: pointer; }
.intan-footer-tools input[type="checkbox"] { margin: 0; width: 12px; height: 12px; flex-shrink: 0; }

.intan-sidebar {width: 180px; background: #d4d0c8; padding: 10px; display: flex; flex-direction: column; gap: 10px; box-shadow: inset 1px 0 0 rgba(255,255,255,0.5); border-left: 1px solid #111; overflow-y: auto; }
.intan-btn-group { display: flex; gap: 8px; }
.intan-btn { flex: 1; background: linear-gradient(to bottom, #f0f0f0, #dcdcdc); border: 1px solid #888; border-radius: 3px; padding: 6px 0; font-size: 11px; font-weight: bold; color: #333; cursor: pointer; box-shadow: inset 1px 1px 0 #fff, 1px 1px 2px rgba(0,0,0,0.1); text-align: center;}
.intan-btn:active { background: #d0d0d0; box-shadow: inset 1px 1px 3px rgba(0,0,0,0.2); }
.intan-btn.record::before { content: ''; display: inline-block; width: 6px; height: 6px; background: #ef4444; border-radius: 50%; box-shadow: 0 0 4px #ef4444; margin-right: 4px; animation: rec-blink 1s infinite alternate; }

.intan-panel { background: #f0f0f0; border: 1px solid #aaa; border-radius: 3px; padding: 6px; box-shadow: inset 1px 1px 2px #fff; }
.intan-panel-title { font-size: 9px; color: #555; font-weight: bold; margin-bottom: 4px; border-bottom: 1px solid #ccc; padding-bottom: 2px; }
.intan-setting-row { display: flex; justify-content: space-between; font-size: 10px; color: #111; margin-bottom: 4px; align-items: center; }
.intan-value-box { background: #fff; border: 1px solid #999; padding: 1px 4px; font-family: 'JetBrains Mono', monospace; width: 55px; text-align: right; box-shadow: inset 1px 1px 2px rgba(0,0,0,0.1); }
.intan-ports { display: grid; grid-template-columns: 1fr 1fr; gap: 4px; }
.intan-port { display: flex; align-items: center; gap: 4px; font-size: 9px; color: #333; }
.port-led { width: 8px; height: 8px; border-radius: 50%; }
.port-led.on { background: #27c93f; border: 1px solid #1a8a29; box-shadow: inset -1px -1px 2px rgba(0,0,0,0.3), 0 0 5px #27c93f; }
.port-led.off { background: #666; border: 1px solid #444; box-shadow: inset 1px 1px 2px rgba(0,0,0,0.5); }

/* ===================== 🚀 Intan 模拟器浅色模式专项修复 ===================== */
body.light-mode #main_content .intan-title-text { color: #ffffff !important; }
body.light-mode #main_content .intan-title-text svg { stroke: #ffffff !important; }
body.light-mode #main_content .intan-sidebar .intan-setting-row span, body.light-mode #main_content .intan-sidebar .intan-panel-title { color: #000000 !important; opacity: 1 !important; }
body.light-mode #main_content .intan-sidebar .intan-setting-row[style*="color: #27c93f"], body.light-mode #main_content .intan-sidebar .intan-setting-row[style*="color: #27c93f"] span { color: #15803d !important; font-weight: bold !important; }
body.light-mode #main_content .intan-value-box { color: #000000 !important; background-color: #ffffff !important; border: 1px solid #999999 !important; }
body.light-mode #main_content .intan-pane-footer span, body.light-mode #main_content .intan-pane-footer div { color: #1a1a1a !important; }
body.light-mode #main_content .intan-btn { color: #000000 !important; }
  
@media (max-width: 768px) {
  .intan-body { flex-direction: column; height: auto; }
  .intan-plots-wrapper { flex-direction: column; height: auto; min-height: 0; border-right: none; }
  .intan-plot-pane { flex: none; height: 220px; border-right: none; border-bottom: 2px solid #333; }
  .intan-plot-pane:last-child { border-bottom: none; }
  .intan-time-axis { padding: 0 10px 0 80px; } 
  .intan-sidebar { width: 100%; flex-direction: row; flex-wrap: wrap; border-left: none; border-top: 1px solid #111; padding: 10px; gap: 8px; }
  .intan-btn-group { width: 100%; flex: none; }
  .intan-panel { flex: 1 1 40%; min-width: 130px; margin: 0; }
}

.hw-ports-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 6px; margin-top: 2px; }
.hw-port-box { border: 1.5px solid #522e8a; border-radius: 4px; background: #fff; display: flex; justify-content: space-between; align-items: center; padding: 4px 6px; box-shadow: 1px 1px 2px rgba(0,0,0,0.1); }
.hw-port-left { display: flex; flex-direction: column; align-items: center; gap: 3px; }
.hw-port-label { font-family: Arial, sans-serif; font-size: 13px; font-weight: 800; color: #222; line-height: 1; margin-left: 2px;}
.hw-port-connector { width: 14px; height: 5px; background: #111; border-radius: 1px; border-top: 1px solid #d4af37; }
.hw-port-leds { display: flex; flex-direction: column; gap: 2px; }
.hw-led { width: 4px; height: 4px; border-radius: 50%; background: #444; border: 0.5px solid #222; box-shadow: inset 0.5px 0.5px 1px rgba(0,0,0,0.5); }
.hw-port-box.active .hw-led.green { background: #27c93f; border-color: #1a8a29; box-shadow: 0 0 5px #27c93f, inset -0.5px -0.5px 1px rgba(0,0,0,0.2); }
.hw-port-box.inactive { opacity: 0.45; filter: grayscale(80%); }

/* ====== Spike Scope Win32 Style Replica ====== */
.scope-win-wrapper { width: 100%; max-width: 760px; margin: 40px auto; background: #f0f0f0; border: 1px solid #999; border-radius: 4px; box-shadow: 0 10px 30px rgba(0,0,0,0.3); font-family: 'Segoe UI', Arial, sans-serif; overflow: hidden; user-select: none; color: #000; }
.scope-title-bar { background: #fff; padding: 6px 10px; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid #ccc; font-size: 13px; font-weight: 500; }
.scope-title-left { display: flex; align-items: center; gap: 6px; }
.scope-body { display: flex; height: 440px; background: #f0f0f0; }
.scope-sidebar { width: 240px; padding: 12px 10px; border-right: 1px solid #ccc; display: flex; flex-direction: column; gap: 14px; box-sizing: border-box; overflow-y: auto; color: #000; font-size: 11px; }
.scope-fieldset { border: 1px solid #ccc; border-radius: 2px; padding: 10px 8px 8px 8px; margin: 0; position: relative; }
.scope-legend { font-size: 11px; color: #000; padding: 0 4px; position: absolute; top: -8px; left: 8px; background: #f0f0f0; }
.scope-row { display: flex; align-items: center; margin-bottom: 6px; gap: 6px; color:#000; font-weight: normal; margin-top:0;}
.scope-row input[type="checkbox"] { margin:0; }
.scope-btn { background: #e1e1e1; border: 1px solid #adadad; padding: 4px; text-align: center; cursor: pointer; border-radius: 2px; color:#000; }
.scope-btn:hover { background: #e5f1fb; border-color: #0078d7; }
.scope-input { border: 1px solid #ccc; padding: 2px; text-align: right; font-size: 11px; background: #fff; color: #000; }
.scope-plot-area { flex: 1; background: #000; position: relative; overflow: hidden; }
/* 1. 修复类名为 spike-scope-canvas，加上绝对定位 */
.spike-scope-canvas { width: 100%; height: 100%; display: block; position: absolute; top: 0; left: 0; z-index: 0; }
/* 2. 提升文字的 z-index，防止被画布挡住 */
.scope-overlay-text { position: absolute; font-size: 11px; font-family: 'Segoe UI', sans-serif; pointer-events: none; z-index: 1; }

/* 浅色模式下不要反转示波器背景，强制黑底白字 */
body.light-mode .scope-win-wrapper, 
body.light-mode .scope-win-wrapper * { filter: none !important; }

@media (max-width: 768px) {
  .scope-body { flex-direction: column-reverse; height: auto; }
  .scope-sidebar { width: 100%; border-right: none; border-top: 1px solid #ccc; }
  .scope-plot-area { height: 250px; flex: none; }
}
</style>

<div class="intan-simulator-wrapper" data-aos="fade-up">
  <div class="intan-title-bar">
    <div class="intan-title-text">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M2 12h4l3-9 5 18 3-9h5"/></svg>
      Intan RHX Interface - Simulated E-Link (256-ch) Stream
    </div>
    <div class="intan-window-controls"><span class="close"></span><span class="min"></span><span class="max"></span></div>
  </div>
  
  <div class="intan-body">
    <div class="intan-plots-wrapper">
      <div class="intan-plot-pane">
        <div class="intan-time-axis">
          <span>0</span><span>200</span><span>400</span><span>600</span><span>800</span><span>1000 ms</span>
        </div>
        <div class="intan-canvas-container">
          <canvas class="intan-canvas canvas-left"></canvas>
        </div>
        <div class="intan-pane-footer">
          <span>⛶ Port A (128 ch)</span>
          <div class="intan-footer-tools">
            <span>➕ ➖ ⭱</span>
            <label><input type="checkbox" checked> show pinned</label>
            <span>▤ 🗗</span>
          </div>
        </div>
      </div>
      <div class="intan-plot-pane">
        <div class="intan-time-axis">
          <span>0</span><span>200</span><span>400</span><span>600</span><span>800</span><span>1000 ms</span>
        </div>
        <div class="intan-canvas-container">
          <canvas class="intan-canvas canvas-right"></canvas>
        </div>
        <div class="intan-pane-footer">
          <span>⛶ Port B (128 ch)</span>
          <div class="intan-footer-tools">
            <span>➕ ➖ ⭱</span>
            <label><input type="checkbox" checked> show pinned</label>
            <span>▤ 🗗</span>
          </div>
        </div>
      </div>
    </div>
    
    <div class="intan-sidebar">
      <div class="intan-btn-group"><div class="intan-btn">Run</div><div class="intan-btn record">Record</div></div>
      <div class="intan-panel">
        <div class="intan-panel-title">SPI Ports</div>
        <div class="hw-ports-grid">
          <div class="hw-port-box active">
            <div class="hw-port-left"><span class="hw-port-label">A</span><div class="hw-port-connector"></div></div>
            <div class="hw-port-leds"><div class="hw-led"></div><div class="hw-led"></div><div class="hw-led green"></div></div>
          </div>
          <div class="hw-port-box active">
            <div class="hw-port-left"><span class="hw-port-label">B</span><div class="hw-port-connector"></div></div>
            <div class="hw-port-leds"><div class="hw-led"></div><div class="hw-led"></div><div class="hw-led green"></div></div>
          </div>
          <div class="hw-port-box inactive">
            <div class="hw-port-left"><span class="hw-port-label">C</span><div class="hw-port-connector"></div></div>
            <div class="hw-port-leds"><div class="hw-led"></div><div class="hw-led"></div><div class="hw-led"></div></div>
          </div>
          <div class="hw-port-box inactive">
            <div class="hw-port-left"><span class="hw-port-label">D</span><div class="hw-port-connector"></div></div>
            <div class="hw-port-leds"><div class="hw-led"></div><div class="hw-led"></div><div class="hw-led"></div></div>
          </div>
        </div>
      </div>
      <div class="intan-panel">
        <div class="intan-panel-title">Filter Bandwidth</div>
        <div class="intan-setting-row"><span>High-pass</span><div class="intan-value-box">300 Hz</div></div>
        <div class="intan-setting-row"><span>Low-pass</span><div class="intan-value-box">7.5 kHz</div></div>
      </div>
      <div class="intan-panel">
        <div class="intan-panel-title">System Status</div>
        <div class="intan-setting-row" style="color: #27c93f;"><span>Ports Status</span><span> 2 Detected</span></div>
        <div class="intan-setting-row" style="color: #777;"><span>Unused</span><span>C, D</span></div>
        <div class="intan-setting-row"><span>Sampling Rate</span><div class="intan-value-box" style="border:none;box-shadow:none;background:transparent;text-align:right;">30 kS/s</div></div>
      </div>
    </div>
  </div>
</div>

<div class="scope-win-wrapper" data-aos="fade-up" style="margin-top: 20px;">
  <div class="scope-title-bar">
    <div class="scope-title-left">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#60a5fa" stroke-width="3"><polygon points="12 2 22 22 2 22"/></svg>
      Spike Scope
    </div>
    <div class="intan-window-controls"><span class="close"></span><span class="min"></span><span class="max"></span></div>
  </div>
  
  <div class="scope-body">
    <div class="scope-sidebar">
      <div class="scope-fieldset">
        <div class="scope-legend">Channel</div>
        <div style="margin-bottom: 6px;">A-126</div>
        <label class="scope-row"><input type="checkbox" checked> Lock Plot to Selected</label>
        <div class="scope-btn" style="border-color: #0078d7; background: #e5f1fb; margin-top:2px;">Set to Selected</div>
      </div>
      
      <div class="scope-fieldset">
        <div class="scope-legend">Display Settings</div>
        <div class="scope-row" style="justify-content: space-between;">Voltage Scale <select class="scope-input" style="width:65px"><option>500 µV</option></select></div>
        <div class="scope-row" style="justify-content: space-between;">Time Scale <select class="scope-input" style="width:65px"><option>2 ms</option></select></div>
        <div class="scope-row" style="justify-content: space-between;">Show <select class="scope-input" style="width:45px"><option>20</option></select> spikes</div>
        <div class="scope-btn" style="margin-bottom: 6px;">Clear Scope</div>
        <div class="scope-row" style="margin-bottom:0;"><div class="scope-btn" style="flex:1">Take Snapshot</div><div class="scope-btn" style="flex:1">Clear Snapshot</div></div>
      </div>

      <div class="scope-fieldset">
        <div class="scope-legend">Spike Detection Settings</div>
        <div class="scope-row" style="justify-content: space-between; margin-bottom:0;">Detection Threshold <input type="text" class="scope-input" value="-70 µV" style="width:55px;"></div>
      </div>

      <div class="scope-fieldset">
        <div class="scope-legend">Artifact Suppression</div>
        <label class="scope-row"><input type="checkbox" checked> Enable Suppression</label>
        <label class="scope-row"><input type="checkbox" checked> Show Artifacts</label>
        <div class="scope-row" style="justify-content: space-between; margin-bottom:0;">Artifact Threshold <input type="text" class="scope-input" value="2500 µV" style="width:55px;"></div>
      </div>

      <div class="scope-btn" style="margin-top: -2px;">Load Detection Parameters</div>
      <div class="scope-btn" style="margin-top: -6px;">Save Detection Parameters</div>
    </div>
    
    <div class="scope-plot-area">
      <canvas class="spike-scope-canvas"></canvas>
      <div class="scope-overlay-text" style="top:10px; left:10px; color:#fff;">+500 µV</div>
      <div class="scope-overlay-text" style="top:50%; left:10px; color:#fff; transform:translateY(-50%);">0</div>
      <div class="scope-overlay-text" style="top:calc(50% + 7%); right:10px; color:#ef4444; transform:translateY(2px);">-70 µV</div>
      <div class="scope-overlay-text" style="bottom:20px; left:10px; color:#fff;">-500 µV</div>

      <div class="scope-overlay-text" style="bottom:5px; left:10px; color:#fff;">-1</div>
      <div class="scope-overlay-text" style="bottom:5px; left:33.33%; color:#fff; transform:translateX(-50%);">0</div>
      <div class="scope-overlay-text" style="bottom:5px; left:66.66%; color:#fff; transform:translateX(-50%);">1</div>
      <div class="scope-overlay-text" style="bottom:5px; right:10px; color:#fff;">2 ms</div>

      <div class="scope-overlay-text" style="top:10px; left:50%; transform:translateX(-50%); color:#fff; font-size: 12px; font-weight: bold;">A-126</div>
      <div class="scope-overlay-text scope-dynamic-stats" style="top:28px; left:50%; transform:translateX(-50%); color:#4ade80; white-space: nowrap;">RMS: 9.1 µV &nbsp;&nbsp;|&nbsp;&nbsp; 5 spikes/s</div>
    </div>
  </div>
</div>

---

<span id="en-bom"></span>
### 🛠 Bill of Materials (BOM) of the headstage
 
<div align="center">
 <img src="Images/256HD.png" 
      alt="256Ch Headstage PCBA Assembly" 
      width="460" 
      loading="lazy" decoding="async"
      style="border-radius: 8px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); margin-bottom: 20px;">
 <p style="margin-top: 5px; font-size: 0.9em; color: #64748b;">
   <b>Assembled 256-Channel Headstage (Top View)</b>
 </p>
</div>
 
<div align="center" data-aos="zoom-in-up" data-aos-duration="1000">
 <br>
 <div class="gif-placeholder narrow">
  <img data-src="Videos/Top PCB explosive new.gif" 
        src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7"
        alt="4-Layer PCB Stackup Explosion"
        class="lazy-gif white-bg-gif" 
        decoding="async">
 </div>
  <p style="margin-top: 5px; font-size: 0.9em; color: #64748b;">
   <b> 4-Layer Routing Structure (Top to Bottom)</b>
 </p>
</div>
 
<div style="width: 100%; max-width: 100%; overflow-x: auto; -webkit-overflow-scrolling: touch; padding-bottom: 10px;">
 <table style="margin-left: auto; margin-right: auto; width: 90%; min-width: 600px; text-align: center; border-collapse: collapse; border: 1px solid #e1e4e8;">
  <thead>
    <tr style="background-color: #f6f8fa; border-bottom: 2px solid #e1e4e8;">
      <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">Component</th>
      <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">Description</th>
      <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">Qty</th>
      <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">Package</th>
      <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>Amplifier IC</b></td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">Intan RHD2164</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">4</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">BGA</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>💡 Tip:</b> Ensure correct orientation</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>SPI Connector</b></td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">Omnetics A7621</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">2</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">-</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">12-wire cable harness (32 AWG)</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>Resistors</b></td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">Standard SMD</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">7</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">0402</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">LVDS Configuration</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>Capacitors</b></td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">Standard SMD</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">8</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">0603</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">LVDS Configuration</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>Power LED</b></td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">Green LED</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">1</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">0402</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">Power Indicator</td>
    </tr>
    <tr>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>Solder Balls</b></td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">0.4 mm Lead-free</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">~300</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">-</td>
      <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">For BGA rework/assembly</td>
    </tr>
  </tbody>
 </table>
</div>
 
---
 
## 👥 Developers and Lab
 
* **Tianyu Bai** (Lead Designer) <a href="https://tianyu-bai.github.io/"><img src="https://img.shields.io/badge/Website-Tianyu%20Bai-0077B5?style=flat-square&logo=github&logoColor=white" alt="Website"></a>
* **Gen Li, Ph.D.**
* **Hui Fang, Ph.D.** <a href="https://engineering.dartmouth.edu/community/faculty/hui-fang"><img src="https://img.shields.io/badge/Principal%20Investigator-444444?style=flat-square&logoColor=white" />
 
This project is developed by the **MINE Lab** at Dartmouth College. <a href="https://sites.dartmouth.edu/fang-group/"><img src="https://img.shields.io/badge/VISIT_WEBSITE_%E2%86%97-MINE_Lab-00693E?style=flat-square" alt="MINE Lab"></a>
 
---
 
## 📄 Publication
 
This work is currently **under review** at the *IEEE Journal on Flexible Electronics (JFLEX)*.
 
The hardware designs and visual assets in this repository correspond directly to the system described in the submitted manuscript. To maintain the integrity of the peer-review process:
 
* **Full Citation**: A permanent link to the final paper will be updated here immediately upon formal acceptance.
* **Preprint/Full Paper**: *Coming Soon.*
  
* We welcome feedback and collaboration from the neuroengineering community!
 
* **Inquiries**: Thinking about using E-Link in your lab? We know setting up a new system can be tricky. If you have questions about the PCB design or 3D printing, drop us an email or open an issue. We'd love to help you get started!
  * **Support**: [<font color="#60a5fa">support@ephys.tech</font>](mailto:support@ephys.tech)
  * **Developer (Tianyu)**: [<font color="#60a5fa">tianyu@ephys.tech</font>](mailto:tianyu@ephys.tech)
 
---
 
## 📑 Citation & DOI
 
If you utilize these designs, code, or assets in your research, please cite this repository using the persistent DOI provided by Zenodo:
 
**Current Reference:**
> T. Bai, et al., "E-Link GitHub Repository," v1.0, MINE Lab, Dartmouth College, 2026. [![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.18440104-007EC6?style=flat-square)](https://doi.org/10.5281/zenodo.18440104)
 
---
 
<span id="en-downloads"></span>
## 🔗 Repository & Downloads
 
This project is fully open-source. Upon acceptance of the associated paper, the complete dataset comprising **PCB fabrication files (Gerber/NC Drill)**, **BOM**, and **Mechanical CAD** will be accessible via the link below.
 
<div align="center">
 <p><b>👇 Bookmark the repository for future downloads:</b></p>
 
<div align="center">
 <a href="https://github.com/Tianyu-Bai/ELINK"><img src="https://img.shields.io/badge/GitHub-View_Source_Repository-181717?style=for-the-badge&logo=github&logoColor=white" alt="View on GitHub"></a>
 <img src="https://img.shields.io/badge/Status-Locked_until_Publication-A31F34?style=for-the-badge&logo=private" alt="Status Locked">
</div>
</div>
 
---
 
## 🤝 Acknowledgments
 
The developers gratefully acknowledge support from the **NIH (R01MH139342)** and the **Dartmouth PhD Innovation Fellowship**. 
 
Special thanks to the members of the **MINE Lab** and the **Thayer School of Engineering** for their technical support and feedback throughout the development of the E-Link (256) system.
 
---
 
## 📜 License
 
Copyright © 2026 Tianyu Bai <a href="https://tianyu-bai.github.io/"><img src="https://img.shields.io/badge/Website-Tianyu%20Bai-0077B5?style=flat-square&logo=github&logoColor=white" alt="Website"></a>
 
This project is open-source and available under the **MIT License**. Click the badge below for full license details.
 
<div align="center">
 <a href="https://github.com/tianyu-bai/E-Link/blob/main/LICENSE">
  <img src="https://img.shields.io/badge/License-MIT-A31F34?style=flat-square&logo=opensourceinitiative&logoColor=white" alt="License">
 </a>
</div>
 
<div class="github-only">
 <br>
 <hr>
 <p align="center" style="font-size: 1.5em; font-weight: bold; margin: 20px 0;">
    👇 🇨🇳 Chinese Version / 中文版 👇
 </p>
 <hr>
 <br>
</div>
 
</div> 
 
<div class="lang-zh" markdown="1">
 
<div class="github-only">
 <p align="center">
   <a href="https://tianyu-bai.github.io/E-Link">
     🌐 点击此处进入交互式网站
   </a>
 </p>
</div>
 
<div align="center" class="nav-badges">
 <a href="#cn-overview"><img src="https://img.shields.io/badge/📖_概览-3b82f6?style=flat-square&logoColor=white" alt="Overview"></a>
 <a href="#cn-features"><img src="https://img.shields.io/badge/✨_特性-3b82f6?style=flat-square&logoColor=white" alt="Features"></a>
 <a href="#cn-specs"><img src="https://img.shields.io/badge/📊_规格-3b82f6?style=flat-square&logoColor=white" alt="Specs"></a>
 <a href="#cn-components"><img src="https://img.shields.io/badge/🧩_组件-3b82f6?style=flat-square&logoColor=white" alt="Components"></a>
 <a href="#cn-bom"><img src="https://img.shields.io/badge/🛠_物料清单-3b82f6?style=flat-square&logoColor=white" alt="BOM"></a>
 <a href="#cn-downloads"><img src="https://img.shields.io/badge/🔗_下载-3b82f6?style=flat-square&logoColor=white" alt="Downloads"></a>
</div>
 
<style>
/* 1. 强制重命名的中文专属父容器类 */
.header-sync-pulse-zh { margin: 0; display: flex; align-items: center; justify-content: center; gap: 15px; margin-bottom: 5px; filter: drop-shadow(0 0 8px rgba(96, 165, 250, 0.3)); }
/* 2. 中文版专属图片遮罩扫光 */
.logo-mask-zh { position: relative; display: inline-block; line-height: 0; }
.logo-mask-zh::after { content: ""; position: absolute; inset: 0; -webkit-mask-image: var(--logo-url); mask-image: var(--logo-url); -webkit-mask-size: contain; -webkit-mask-position: center; -webkit-mask-repeat: no-repeat; background: linear-gradient( 105deg, transparent 0%, transparent 20%, rgba(96, 165, 250, 0.4) 35%, rgba(167, 139, 250, 0.95) 50%, rgba(167, 139, 250, 0.95) 60%, rgba(96, 165, 250, 0.4) 75%, transparent 90%, transparent 100% ); background-size: 250% 100%; background-repeat: no-repeat; mix-blend-mode: screen; pointer-events: none; animation: safe-sweep-anim 3s linear infinite; }
@keyframes safe-sweep-anim { 0%   { background-position: 200% 0; } 75%  { background-position: -100% 0; }   100% { background-position: -100% 0; } }
/* 3. 中文纯文本渐变扫光 */
.bi-color-title-sweep-zh { background: linear-gradient(105deg, transparent 0%, rgba(255, 255, 255, 0.5) 25%, rgba(255, 255, 255, 1) 50%, rgba(255, 255, 255, 0.5) 75%, transparent 100%), linear-gradient(90deg, #60a5fa 0%, #a78bfa 55%, #f472b6 100%); background-size: 250% auto, 100% auto; background-repeat: no-repeat; -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; color: transparent; animation: text-searchlight-zh 3s linear infinite; }
@keyframes text-searchlight-zh { 0%    { background-position: -50% center, 0 center; } 70%   { background-position: 150% center, 0 center; }   100%  { background-position: 150% center, 0 center; } }
/* 4. 中文 Logo 图片与文字排版精准控制 */
.main-logo-zh { height: 80px !important; width: auto !important; max-width: 100% !important; object-fit: contain; display: block; filter: brightness(0.95); }
.zh-text-logo-zh { font-size: 55px; font-weight: 800; letter-spacing: 4px; font-family: 'Inter', 'Noto Sans SC', sans-serif; line-height: 1; margin: 0; padding-bottom: 5px; }

/* 手机端适配 */
@media (max-width: 768px) {
 .main-logo-zh { height: 60px !important; } 
 .zh-text-logo-zh { font-size: 40px !important; } 
 .header-sync-pulse-zh { gap: 10px; }
}
</style>
 
<div align="center" style="margin-bottom: 20px;" data-aos="fade-up">
 <h1 class="header-sync-pulse-zh">
   <span class="logo-mask-zh" style="--logo-url: url('{{ "/Images/ELink Logo color.png" | relative_url }}');">
     <img src="{{ '/Images/ELink Logo color.png' | relative_url }}" alt="E-Link Logo color" class="main-logo-zh">
   </span>
   <span class="bi-color-title-sweep-zh zh-text-logo-zh">易链</span>
 </h1>
</div>
 
<h2 class="sub-title" data-aos="fade-up" data-aos-delay="200">
  一种基于弹性导电体互连技术的<br class="mobile-only-br">高密度柔性神经接口连接器
</h2>
 
 <div align="center" style="margin-top: 15px;">
   <a href="https://sites.dartmouth.edu/fang-group/"><img src="https://img.shields.io/badge/达特茅斯学院-00693E?style=flat-square" alt="方辉组"></a>
   <img src="https://img.shields.io/badge/已验证-256通道-FFA500?style=flat-square" alt="Verified" />
   <a href="https://tianyu-bai.github.io/"><img src="https://img.shields.io/badge/个人主页-Tianyu%20Bai-0077B5?style=flat-square&logo=github&logoColor=white" alt="Website"></a>
   <a href="https://www.linkedin.com/in/tianyubai/"><img src="https://img.shields.io/badge/领英-主页-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
    <a href="https://github.com/tianyu-bai/E-Link/blob/main/LICENSE"><img src="https://img.shields.io/badge/开源协议-MIT-A31F34?style=flat-square&logo=opensourceinitiative&logoColor=white" alt="License"></a>
 </div>
 <div align="center">
 <br>
 <img src="Images/001_CN.png" alt="E-Link_256 分解图" width="750" loading="lazy" decoding="async">
 <p style="margin-top: 5px; font-size: 0.95em; color: #3b82f6;">
   <b>E-Link易链(256) 的插拔动态（左）和结构分解（右）</b>
 </p>
</div>
 
## 🔬 **E-Link ：3D 交互式集成视图**
 
<div class="model-block" data-lenis-prevent align="center" style="position: relative; max-width: 760px; margin: 0 auto; min-height: 460px;">
 <model-viewer
   class="custom-model-viewer"
   src="{{ '/Videos/On skull_3.16MB.glb' | relative_url }}"
   alt="E Link on Skull 3D Model"
   loading="lazy"  reveal="manual"
   poster="{{ '/Images/poster.webp' | relative_url }}"
   camera-controls interpolation-decay="200" bounds="tight" field-of-view="30deg" auto-rotate  rotation-per-second="15deg"
   interaction-prompt="none" environment-image="neutral" exposure="0.75" shadow-intensity="0" tone-mapping="commerce">
 
   <div slot="poster" style="position: relative; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; width: 100%; background: radial-gradient(circle at center, #111827 0%, #020617 100%); font-family: 'JetBrains Mono', monospace; overflow: hidden; border-radius: 16px; cursor: pointer;">
     <div style="position: absolute; inset: 0; background-image: linear-gradient(rgba(59, 130, 246, 0.08) 1px, transparent 1px), linear-gradient(90deg, rgba(59, 130, 246, 0.08) 1px, transparent 1px); background-size: 25px 25px; z-index: 0;"></div>
     <div class="scanline" style="z-index: 1;"></div>
     <div class="hud-corner hud-tl" style="z-index: 1;"></div>
     <div class="hud-corner hud-tr" style="z-index: 1;"></div>
     <div class="hud-corner hud-bl" style="z-index: 1;"></div>
     <div class="hud-corner hud-br" style="z-index: 1;"></div>
     <div style="z-index: 2; display: flex; flex-direction: column; align-items: center;">
       <div class="cyber-loader"></div>
       <p style="margin-top: 25px; margin-bottom: 5px; font-size: 0.95rem; font-weight: 600; letter-spacing: 3px; color: #93c5fd; text-shadow: 0 0 10px rgba(96, 165, 250, 0.8); animation: text-blink 1.5s ease-in-out infinite;">正在初始化 3D 信号...</p>
       <p class="click-to-load-glow" style="margin: 0; font-size: 0.65rem; color: #a78bfa; letter-spacing: 1px; font-weight: bold;">[ 滑动或点击接入引擎 ]</p>
     </div>
   </div>
    
   <div class="model-watermark-text">版权所有 © 2026 Tianyu Bai</div>
    
   <div class="gesture-hud">
     <span>↺ 旋转：拖拽</span>
 <span class="pc-only">缩放：Ctrl键 + 鼠标滚轮/触控板捏合</span>
 <span class="mobile-only">缩放：双指捏合</span>
</div>
 
   <div class="gesture-overlay mode-drag">
     <div class="icon-box"><div class="hand-icon">👆</div></div>
     <div class="gesture-text">拖拽以旋转</div>
   </div>
 
   <div class="gesture-overlay mode-zoom">
 <div class="icon-box">
   <div class="hand-icon hand-left">👉</div>
   <div class="hand-icon hand-right">👈</div>
 </div>
 <div class="gesture-text">
   <span class="pc-tip">Ctrl键 + 鼠标滚轮以缩放</span>
   <span class="mobile-tip">双指捏合屏幕以缩放</span>
 </div>
</div>
    
   <button class="reset-btn"
 onclick="
   const mv = this.closest('model-viewer');
   mv.setAttribute('camera-orbit','45deg 55deg auto');
   mv.setAttribute('field-of-view','30deg');
 ">
     ⟲ 重置视角
   </button>
 </model-viewer>
</div>
 
## 🔬 E-Link 三维交互模型
 
<div class="model-block" data-lenis-prevent align="center" style="position: relative; max-width: 760px; margin: 0 auto; min-height: 460px;">
 <model-viewer
   class="custom-model-viewer"
   src="{{ '/Videos/Whole_2.34MB.glb' | relative_url }}"
   alt="E Link 3D Model" 
   loading="lazy"      reveal="manual"
   poster="{{ '/Images/poster.webp' | relative_url }}"
   camera-controls interpolation-decay="200" bounds="tight" field-of-view="30deg" auto-rotate  rotation-per-second="15deg"
   interaction-prompt="none" environment-image="neutral" exposure="0.75" shadow-intensity="0" tone-mapping="commerce">
 
   <div slot="poster" style="position: relative; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; width: 100%; background: radial-gradient(circle at center, #111827 0%, #020617 100%); font-family: 'JetBrains Mono', monospace; overflow: hidden; border-radius: 16px; cursor: pointer;">
     <div style="position: absolute; inset: 0; background-image: linear-gradient(rgba(59, 130, 246, 0.08) 1px, transparent 1px), linear-gradient(90deg, rgba(59, 130, 246, 0.08) 1px, transparent 1px); background-size: 25px 25px; z-index: 0;"></div>
     <div class="scanline" style="z-index: 1;"></div>
     <div class="hud-corner hud-tl" style="z-index: 1;"></div>
     <div class="hud-corner hud-tr" style="z-index: 1;"></div>
     <div class="hud-corner hud-bl" style="z-index: 1;"></div>
     <div class="hud-corner hud-br" style="z-index: 1;"></div>
     <div style="z-index: 2; display: flex; flex-direction: column; align-items: center;">
       <div class="cyber-loader"></div>
       <p style="margin-top: 25px; margin-bottom: 5px; font-size: 0.95rem; font-weight: 600; letter-spacing: 3px; color: #93c5fd; text-shadow: 0 0 10px rgba(96, 165, 250, 0.8); animation: text-blink 1.5s ease-in-out infinite;">正在初始化 3D 信号...</p>
       <p class="click-to-load-glow" style="margin: 0; font-size: 0.65rem; color: #a78bfa; letter-spacing: 1px; font-weight: bold;">[ 滑动或点击接入引擎 ]</p>
     </div>
   </div>
    
   <div class="model-watermark-text">版权所有 © 2026 Tianyu Bai</div>
    
   <div class="gesture-hud">
       <span>↺ 旋转：拖拽</span>
 <span class="pc-only">缩放：Ctrl键 + 鼠标滚轮/触控板捏合</span>
 <span class="mobile-only">缩放：双指捏合</span>
</div>
 
   <div class="gesture-overlay mode-drag">
     <div class="icon-box"><div class="hand-icon">👆</div></div>
     <div class="gesture-text">拖拽以旋转</div>
   </div>
 
   <div class="gesture-overlay mode-zoom">
 <div class="icon-box">
   <div class="hand-icon hand-left">👉</div>
   <div class="hand-icon hand-right">👈</div>
 </div>
 <div class="gesture-text">
   <span class="pc-tip">Ctrl键 + 鼠标滚轮以缩放</span>
   <span class="mobile-tip">双指捏合屏幕以缩放</span>
 </div>
</div>
   <div class="gesture-overlay mode-drag">
     <div class="icon-box"><div class="hand-icon">👆</div></div>
     <div class="gesture-text">拖拽以旋转</div>
 </div>
  <button class="reset-btn"
 onclick="
   const mv = this.closest('model-viewer');
   mv.setAttribute('camera-orbit','45deg 55deg auto');
   mv.setAttribute('field-of-view','30deg');
 ">
     ⟲ 重置视角
   </button>
 </model-viewer>
</div> 
 
## 🔬 256通道定制放大器 – 三维交互模型
 
<div class="model-block" data-lenis-prevent align="center" style="position: relative; max-width: 760px; margin: 0 auto; min-height: 460px;">
 <model-viewer
   class="custom-model-viewer"
   src="{{ '/Videos/3D_1.85MB.glb' | relative_url }}"
   alt="E-Link 256-Channel Custom Headstage 3D Model"
   loading="lazy"      reveal="manual"
   poster="{{ '/Images/poster.webp' | relative_url }}"
   camera-controls interpolation-decay="200" bounds="tight" field-of-view="30deg" auto-rotate  rotation-per-second="15deg"
   interaction-prompt="none" environment-image="neutral" exposure="0.75" shadow-intensity="0" tone-mapping="commerce">
 
   <div slot="poster" style="position: relative; display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100%; width: 100%; background: radial-gradient(circle at center, #111827 0%, #020617 100%); font-family: 'JetBrains Mono', monospace; overflow: hidden; border-radius: 16px; cursor: pointer;">
     <div style="position: absolute; inset: 0; background-image: linear-gradient(rgba(59, 130, 246, 0.08) 1px, transparent 1px), linear-gradient(90deg, rgba(59, 130, 246, 0.08) 1px, transparent 1px); background-size: 25px 25px; z-index: 0;"></div>
     <div class="scanline" style="z-index: 1;"></div>
     <div class="hud-corner hud-tl" style="z-index: 1;"></div>
     <div class="hud-corner hud-tr" style="z-index: 1;"></div>
     <div class="hud-corner hud-bl" style="z-index: 1;"></div>
     <div class="hud-corner hud-br" style="z-index: 1;"></div>
     <div style="z-index: 2; display: flex; flex-direction: column; align-items: center;">
       <div class="cyber-loader"></div>
       <p style="margin-top: 25px; margin-bottom: 5px; font-size: 0.95rem; font-weight: 600; letter-spacing: 3px; color: #93c5fd; text-shadow: 0 0 10px rgba(96, 165, 250, 0.8); animation: text-blink 1.5s ease-in-out infinite;">正在初始化 3D 信号...</p>
       <p class="click-to-load-glow" style="margin: 0; font-size: 0.65rem; color: #a78bfa; letter-spacing: 1px; font-weight: bold;">[ 滑动或点击接入引擎 ]</p>
     </div>
   </div>
    
   <div class="model-watermark-text">版权所有 © 2026 Tianyu Bai </div>
    
   <div class="gesture-hud">
     <span>↺ 旋转：拖拽</span>
 <span class="pc-only">缩放：Ctrl键 + 鼠标滚轮/触控板捏合</span>
 <span class="mobile-only">缩放：双指捏合</span>
</div>
 
   <div class="gesture-overlay mode-drag">
     <div class="icon-box"><div class="hand-icon">👆</div></div>
     <div class="gesture-text">拖拽以旋转</div>
   </div>
 
   <div class="gesture-overlay mode-zoom">
 <div class="icon-box">
   <div class="hand-icon hand-left">👉</div>
   <div class="hand-icon hand-right">👈</div>
 </div>
 <div class="gesture-text">
   <span class="pc-tip">Ctrl键 + 鼠标滚轮以缩放</span>
   <span class="mobile-tip">双指捏合屏幕以缩放</span>
 </div>
</div>
 
   <button class="reset-btn"
 onclick="
   const mv = this.closest('model-viewer');
   mv.setAttribute('camera-orbit','45deg 55deg auto');
   mv.setAttribute('field-of-view','30deg');
 ">
     ⟲ 重置视角
   </button>
 </model-viewer>
</div>
 
<div class="metrics-grid-v2" data-aos="fade-up">
 <div class="metric-card-v2" style="--card-accent: #10b981;" data-type="ring" data-percent="100" data-value="2.8" data-is-float="true">
   <div class="card-label">重量</div>
   <div class="v2-chart-box">
     <svg viewBox="0 0 100 100"><circle class="bg-ring" cx="50" cy="50" r="45"></circle><circle class="fg-ring weight-color" cx="50" cy="50" r="45"></circle></svg>
     <div class="ring-inner">
       <div class="v2-val-wrap">
         <span class="card-value v2-count v2-val-sm">0</span><span class="card-unit">克</span>
       </div>
     </div>
   </div>
   <div class="card-sub">轻量化</div>
 </div>
 
 <div class="metric-card-v2" style="--card-accent: #3b82f6;" data-type="ring" data-percent="100" data-value="256" data-is-float="false">
   <div class="card-label">通道数</div>
   <div class="v2-chart-box">
     <svg viewBox="0 0 100 100"><circle class="bg-ring" cx="50" cy="50" r="45"></circle><circle class="fg-ring channel-color" cx="50" cy="50" r="45"></circle></svg>
     <div class="ring-inner">
       <div class="v2-val-wrap">
         <span class="card-value v2-count v2-val-sm">0</span>
       </div>
     </div>
   </div>
   <div class="card-sub">高密度采集</div>
 </div>
 
 <div class="metric-card-v2" style="--card-accent: #f59e0b;" data-type="ring" data-percent="100" data-value="4" data-is-float="false">
   <div class="card-label">PCB 层数</div>
   <div class="v2-chart-box">
     <svg viewBox="0 0 100 100"><circle class="bg-ring" cx="50" cy="50" r="45"></circle><circle class="fg-ring pcb-color" cx="50" cy="50" r="45"></circle></svg>
     <div class="ring-inner">
       <div class="v2-val-wrap">
         <span class="card-value v2-count v2-val-sm">0</span>
       </div>
     </div>
   </div>
   <div class="card-sub">定制化布线</div>
 </div>
 
 <div class="metric-card-v2" style="--card-accent: #ef4444;" data-type="thermo" data-value="30.5" data-max="50">
   <div class="card-label">工作温度</div>
   <div class="thermo-wrapper">
     <div class="thermo-track">
       <div class="thermo-fill"></div>
       <div class="thermo-safe-line"></div>
       <div class="thermo-safe-label">37°C</div>
     </div>
     <div class="thermo-bulb"></div>
   </div>
   <div class="v2-val-wrap">
     <div class="card-value v2-count v2-val-sm">0</div><span class="card-unit">°C</span>
   </div>
   <div class="card-sub">低于生物阈值</div>
 </div>
 
 <div class="metric-card-v2" style="--card-accent: #a78bfa;" data-type="waveform" data-value="2.68" data-is-float="true" data-decimals="2">
   <div class="card-label">系统底噪</div>
   <div class="waveform-box"><canvas class="waveform-canvas"></canvas></div>
   <div class="v2-val-wrap">
     <div class="card-value v2-count v2-val-sm">0</div><span class="card-unit">微伏</span>
   </div>
   <div class="card-sub">接近芯片性能极值</div>
 </div>
 
 <div class="metric-card-v2" style="--card-accent: #10b981;" data-type="cycles" data-value="300">
 <div class="card-label">按压连接测试</div>
 <div class="cycles-viz">
   <div class="press-icon">🫸</div>
   <div class="press-ripple"></div>
   <div class="cycles-counter-flash">+1</div>
 </div>
 <div class="v2-val-wrap">
   <span class="card-value v2-val-sm" style="margin-right: 4px;">&gt;</span>
   <div class="card-value v2-count v2-val-sm">0</div><span class="card-unit">次</span>
 </div>
 <div class="card-sub">保持 97%+ 连接良率</div>
</div>
</div>
 
<br> <span id="cn-overview"></span>
 
## 📖 概览
 
**E-Link易链**，是一款基于弹性导电体互连技术（Elastomer Interconnection）的开源微型基座连接系统。它为柔性神经探针提供了稳固且可扩展的接口，专为自由活动动物的长期实验而优化设计
 
<div align="center" data-aos="zoom-in-up" data-aos-duration="1000">
 <br>
 <div class="gif-placeholder">
  <img data-src="Videos/Demo%20new%20new.gif" 
        src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7"
        alt="ELINK-256 组装演示 GIF"
        class="lazy-gif white-bg-gif" 
        decoding="async">
 </div>
</div>
 
---
 
> [!NOTE]
> **核心创新：** 本连接器是一种完全一体化的 “即拧即用” 数据采集方案。该系统利用弹性导电介质连接高密度 PCB，并封装于轻量级基座中。其最大的突破在于实现了“零力插拔”，免去使用者用力插拔的动作，有效规避了高密度引脚连接器常见的断针和弯针风险。
 
---
 
<span id="cn-specs"></span>
 
### 📊 规格参数
 
<div style="width: 100%; max-width: 100%; overflow-x: auto; -webkit-overflow-scrolling: touch; padding-bottom: 10px;">
 <table style="margin-left: auto; margin-right: auto; width: 90%; min-width: 600px; text-align: center; border-collapse: collapse; border: 1px solid #e1e4e8;">
   <thead>
     <tr style="background-color: #f6f8fa; border-bottom: 2px solid #e1e4e8;">
       <th style="padding: 10px; border: 1px solid #e1e4e8;">规格项目</th>
       <th style="padding: 10px; border: 1px solid #e1e4e8;">E-Link(256)_V1.0</th>
     </tr>
   </thead>
   <tbody>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>通道数</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">128或 256 通道 (支持单/双 SPI 端口)</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>总质量</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">6.6 g (含外壳)<br>2.8 g (不含外壳)</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>互连类型</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">免焊各向异性弹性体</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>兼容采集系统</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">Intan Recording Controller (512ch/1024ch)<br>Open-Ephys DAQ box<br>NeuroNexus Smartbox<br>OmniPlex DAQ box</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8;"><b>外壳材料</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8;">3D 打印 PEEK / 手术级树脂</td>
     </tr>
   </tbody>
 </table>
</div>

---

## ✨ 流程图
<div class="pipeline-section" data-aos="fade-up">
  <div class="pipeline-card">
    <h3 class="pipeline-card-title">⚙️ 装配与验证流程</h3>
    <p class="pipeline-card-desc">
      免插拔的<strong style="color: #e2e8f0;">"旋转即用"</strong>接口设计消除了微米级对准的需求，使未经培训的操作者也能实现可重复的组装，并保持一致的电气性能。
    </p>

    <!-- 流程步骤 -->
    <div class="pipe-track-wrapper">
      <div class="pipe-track-line">
        <div class="pipe-flow-light"></div>
      </div>

      <div class="pipe-node">
        <div class="pipe-circle">01</div>
        <div class="pipe-label">
          <span class="pipe-icon">🔩</span>
          安置<br>基座
        </div>
      </div>

      <div class="pipe-node">
        <div class="pipe-circle">02</div>
        <div class="pipe-label">
          <span class="pipe-icon">📐</span>
          放置<br>转接 PCB
        </div>
      </div>

      <div class="pipe-node">
        <div class="pipe-circle">03</div>
        <div class="pipe-label">
          <span class="pipe-icon">🧬</span>
          铺设<br>弹性导电体
        </div>
      </div>

      <div class="pipe-node">
        <div class="pipe-circle">04</div>
        <div class="pipe-label">
          <span class="pipe-icon">🔌</span>
          安置<br>放大器板
        </div>
      </div>

      <div class="pipe-node">
        <div class="pipe-circle">05</div>
        <div class="pipe-label">
          <span class="pipe-icon">🔄</span>
          旋紧<br>螺纹顶盖
        </div>
      </div>

      <div class="pipe-node">
        <div class="pipe-circle">06</div>
        <div class="pipe-label">
          <span class="pipe-icon">✅</span>
          电气<br>验证
        </div>
      </div>
    </div>

    <!-- 验证数据 -->
    <div class="pipe-stats">
      <div class="pipe-stat-card">
        <div class="pipe-stat-title">多操作者独立验证</div>
        <div class="pipe-stat-desc">所有用户均获得一致的连接良率——与个人操作技巧无关。</div>
      </div>
      <div class="pipe-stat-card">
        <div class="pipe-stat-title">200+ 次插拔循环</div>
        <div class="pipe-stat-desc">5 天纵向耐久性测试中，接触阻抗和良率零退化。</div>
      </div>
      <div class="pipe-stat-card">
        <div class="pipe-stat-title">180 分钟振动测试</div>
        <div class="pipe-stat-desc">在约 23 m/s² 极端加速度冲击下仍保持连接良率。</div>
      </div>
    </div>
  </div>
</div>

---

<span id="cn-components"></span> 
## 🧩 系统组件

<div class="xs-sec" data-aos="fade-up">
<div class="xs-card">
<h3>🔬 交互式截面结构浏览器</h3>
<p>将鼠标悬停在截面结构图或点击下方任意组件，即可高亮对应层并查看详细规格。</p>
<div class="xs-v" id="xV2">
<img src="{{ '/Images/Assem new.PNG' | relative_url }}" alt="E-Link 截面结构" loading="lazy">
<span class="xs-h" data-c="spi" style="left:43.5%;top:0%;width:13%;height:41%;--c:#3b82f6;--bg:rgba(59,130,246,.08);--g:rgba(59,130,246,.4)"><span class="xs-b">1</span></span>
<span class="xs-h" data-c="foam" style="left:20%;top:39.5%;width:61%;height:6.46%;z-index:5;--c:#f472b6;--bg:rgba(244,114,182,.15);--g:rgba(244,114,182,.4)"><span class="xs-b">2</span></span>
<span class="xs-h" data-c="cap" style="left:2%;top:36.5%;width:96%;height:26%;--c:#f59e0b;--bg:rgba(245,158,11,.08);--g:rgba(245,158,11,.35)"><span class="xs-b">3</span></span>
<span class="xs-h" data-c="pcb" style="left:17%;top:61.6%;width:65.6%;height:7.5%;--c:#22c55e;--bg:rgba(34,197,94,.08);--g:rgba(34,197,94,.35)"><span class="xs-b">4</span></span>
<span class="xs-h" data-c="elast" style="left:17%;top:68.6%;width:65.6%;height:1.88%;--c:#a78bfa;--bg:rgba(167,139,250,.12);--g:rgba(167,139,250,.4)"><span class="xs-b">5</span></span>
<span class="xs-h" data-c="adapt" style="left:17%;top:70.5%;width:65.6%;height:5%;--c:#eab308;--bg:rgba(234,179,8,.12);--g:rgba(234,179,8,.35)"><span class="xs-b">6</span></span>
<span class="xs-t" data-k="spi" style="--c:#3b82f6;--g:rgba(59,130,246,.4);right:18%;top:18%">1. SPI 线缆</span>
<span class="xs-t" data-k="foam" style="--c:#f472b6;--g:rgba(244,114,182,.4);right:18%;top:36%">2. 泡沫垫圈</span>
<span class="xs-t" data-k="cap" style="--c:#f59e0b;--g:rgba(245,158,11,.35);right:18%;top:33%">3. 顶部螺纹盖</span>
<span class="xs-t" data-k="pcb" style="--c:#22c55e;--g:rgba(34,197,94,.35);right:18%;top:58%">4. 放大器电路板</span>
<span class="xs-t" data-k="elast" style="--c:#a78bfa;--g:rgba(167,139,250,.4);right:18%;top:65%">5. 弹性导电体</span>
<span class="xs-t" data-k="adapt" style="--c:#eab308;--g:rgba(234,179,8,.35);right:18%;top:68%">6. 转接电路板</span>
</div>
<div class="xs-g" id="xG2">
<div class="xs-i" data-c="spi" style="--c:#3b82f6"><span class="xs-n">1</span><div><div class="xs-cn">SPI 线缆</div><div class="xs-cs">双路 Omnetics A7621</div></div></div>
<div class="xs-i" data-c="foam" style="--c:#f472b6"><span class="xs-n">2</span><div><div class="xs-cn">泡沫垫圈</div><div class="xs-cs">压力均匀分布</div></div></div>
<div class="xs-i" data-c="cap" style="--c:#f59e0b"><span class="xs-n">3</span><div><div class="xs-cn">顶部螺纹盖</div><div class="xs-cs">压缩外壳</div></div></div>
<div class="xs-i" data-c="pcb" style="--c:#22c55e"><span class="xs-n">4</span><div><div class="xs-cn">放大器电路板</div><div class="xs-cs">4个RHD2164芯片 + 4层HDI</div></div></div>
<div class="xs-i" data-c="elast" style="--c:#a78bfa"><span class="xs-n">5</span><div><div class="xs-cn">弹性导电体</div><div class="xs-cs">Z轴导电介质</div></div></div>
<div class="xs-i" data-c="adapt" style="--c:#eab308"><span class="xs-n">6</span><div><div class="xs-cn">转接电路板</div><div class="xs-cs">探针布局规则化</div></div></div>
<div class="xs-d" id="xD2"><div id="xDI2"></div></div>
</div>
</div>
</div>

<script>
(function(){var D={spi:'<strong>线材：</strong>32AWG 12 芯线 | <strong>接口：</strong>双路 SPI 2×128ch',foam:'<strong>材料：</strong>闭孔硅胶 | <strong>厚度：</strong>1.5→0.8mm | 补偿平面度误差',cap:'<strong>材料：</strong>PEEK/手术级树脂 | <strong>功能：</strong>扭矩 → 25mm Ø 范围内均匀轴向压缩',pcb:'<strong>芯片：</strong>4× RHD2164 BGA | <strong>无源器件：</strong>7电阻+8电容 LVDS +1 LED | <strong>底面：</strong>256焊盘 BGA 0.4mm',elast:'<strong>间距：</strong>156µm（比 BGA 密 3.2 倍）| 压缩下 Z 轴导通 | 零插拔力',adapt:'<strong>层数：</strong>4层 HDI | <strong>顶面：</strong>经弹性体匹配 BGA | <strong>底面：</strong>探针焊盘 | ENIG 表面处理'};
function go(){var v=document.getElementById('xV2'),g=document.getElementById('xG2'),d=document.getElementById('xD2'),di=document.getElementById('xDI2');if(!v||!g)return;
var hs=v.querySelectorAll('.xs-h'),ts=v.querySelectorAll('.xs-t'),cs=g.querySelectorAll('.xs-i'),cur=null;
function act(k){if(cur===k){off();return}cur=k;v.classList.add('focus');
hs.forEach(function(h){h.classList.toggle('on',h.dataset.c===k)});
ts.forEach(function(t){t.classList.toggle('on',t.dataset.k===k)});
cs.forEach(function(c){c.classList.toggle('on',c.dataset.c===k)});
if(D[k]){di.innerHTML=D[k];d.classList.add('open');var ac=g.querySelector('.xs-i[data-c="'+k+'"]');if(ac)ac.after(d)}}
function off(){cur=null;v.classList.remove('focus');hs.forEach(function(h){h.classList.remove('on')});ts.forEach(function(t){t.classList.remove('on')});cs.forEach(function(c){c.classList.remove('on')});d.classList.remove('open')}
hs.forEach(function(h){h.addEventListener('click',function(e){e.stopPropagation();act(h.dataset.c)});
h.addEventListener('mouseenter',function(){if(!cur){ts.forEach(function(t){t.classList.toggle('on',t.dataset.k===h.dataset.c)});cs.forEach(function(c){c.classList.toggle('on',c.dataset.c===h.dataset.c)})}});
h.addEventListener('mouseleave',function(){if(!cur){ts.forEach(function(t){t.classList.remove('on')});cs.forEach(function(c){c.classList.remove('on')})}})});
cs.forEach(function(c){c.addEventListener('click',function(e){e.stopPropagation();act(c.dataset.c)});
c.addEventListener('mouseenter',function(){if(!cur){hs.forEach(function(h){h.classList.toggle('on',h.dataset.c===c.dataset.c)});ts.forEach(function(t){t.classList.toggle('on',t.dataset.k===c.dataset.c)})}});
c.addEventListener('mouseleave',function(){if(!cur){hs.forEach(function(h){h.classList.remove('on')});ts.forEach(function(t){t.classList.remove('on')})}})});
document.addEventListener('click',function(e){if(cur&&!v.contains(e.target)&&!g.contains(e.target))off()});
document.addEventListener('keydown',function(e){if(e.key==='Escape')off()})}
if(document.readyState==='loading')document.addEventListener('DOMContentLoaded',go);else go()})();
</script>
 
 ---
 
<span id="cn-features"></span>
 
## ✨ 核心特性
<div class="species-compatibility-container" align="center" style="margin: 40px auto; max-width: 760px;">
 <h3 style="color: #60a5fa; margin-bottom: 20px; font-family: sans-serif;">🌍 跨物种适用性展望 </h3>
  
 <div class="species-glass-box">
 <svg class="connection-lines" viewBox="0 0 600 380" preserveAspectRatio="none" style="z-index: 1;">
   <path class="base-line" d="M300,141 L100,225" stroke="rgba(255,255,255,0.1)" fill="none" /> 
   <path class="base-line" d="M300,141 L300,255" stroke="rgba(255,255,255,0.1)" fill="none" /> 
   <path class="base-line" d="M300,141 L500,225" stroke="rgba(255,255,255,0.1)" fill="none" /> 
    
   <path class="pulse-line line-to-mouse" d="M300,141 L100,225" />
   <path class="pulse-line line-to-rat" d="M300,141 L300,255" />
   <path class="pulse-line line-to-monkey" d="M300,141 L500,225" />
 </svg>
 
   <div class="node center-node">
     <div class="hex-border">
       <svg width="40" height="40" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
         <path d="M7 2V4M12 2V4M17 2V4M22 7H20M22 12H20M22 17H20M17 22V20M12 22V20M7 22V20M2 17H4M2 12H4M2 7H4M6 6H18V18H6V6ZM9 9V15H15V9H9Z" stroke="#60a5fa" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
       </svg>
     </div>
     <div class="node-text pulse-text">E-Link (256)</div>
   </div>
 
   <div class="animal-nodes">
     
     <div class="node sub-node">
       <div class="icon-circle mouse-glow">
         <span style="font-size: 30px;">🐁</span>
       </div>
       <div class="node-title"><i>小鼠</i></div>
       <div class="node-desc">顶盖移除后<br><b><font color="#10b981">2.8g</font> 载荷</b></div>
     </div>
 
     <div class="node sub-node rat-node-adjust">
       <div class="icon-circle rat-glow">
         <span style="font-size: 30px;">🐀</span>
       </div>
       <div class="node-title"><i>大鼠</i></div>
       <div class="node-desc">长期佩戴<br><b><font color="#3b82f6">6.6g</font> 共计</b></div>
     </div>
 
     <div class="node sub-node">
       <div class="icon-circle monkey-glow">
         <span style="font-size: 30px;">🐒</span>
       </div>
       <div class="node-title"><i>灵长类</i></div>
       <div class="node-desc">高耐久性<br><b><font color="#f59e0b">可拓展矩阵</font></b></div>
     </div>
 
   </div>
 </div>
</div>
 
<div class="watermark-features">
 <ul>
   <li data-aos="fade-up" data-aos-delay="0">
     <strong>⚡ 256通道高密度与可扩展接口</strong><br>
     在有限基座占地面积内实现256通道数据采集。得益于弹性体互连的高集成度，该系统提供了清晰的扩展路径（可达1024通道），且不会增加额外的手术复杂度。
   </li>
   <li data-aos="fade-up" data-aos-delay="100">
     <strong>🔌 零插拔力，以柔克刚</strong><br>
     利用各向异性导电弹性体取代传统刚性插针。通过“旋紧结构”将扭矩转化为均匀压力，从物理层面彻底规避了高密度连接器常见的断针、弯针等失效模式。
   </li>
   <li data-aos="fade-up" data-aos-delay="200">
     <strong>🎯 自对准与高容错连接</strong><br>
     系统具备优异的机械限位与电气容错率。无需微米级精密对齐，只需简单旋紧即可实现稳定连接，极大降低了手动操作的难度和失败风险。
   </li>
   <li data-aos="fade-up" data-aos-delay="300">
     <strong>🛠️ 模块化维护与按需组装</strong><br>
     采用“三明治”式分离结构（外壳、适配板、放大器板）。支持损坏模块的单独更换，并允许根据实验需求灵活焊接芯片，显著降低了科研成本。
   </li>
   <li data-aos="fade-up" data-aos-delay="400">
     <strong>🪶 电子模块即插即拆，释放头部负担</strong><br>
     在非记录期间，有源电路可与底座快速分离，仅在颅骨留下极轻量的无源接口。这大幅减轻了动物的物理载荷，保障其在实验间隙的自然活动状态。
   </li>
   <li data-aos="fade-up" data-aos-delay="500">
     <strong>🐭 专为自由活动动物实验优化</strong><br>
     核心组件仅重 2.8g。低剖面设计完美适配换向器 (Commutator)，有效管理线缆并确保动物在长期慢性实验中的自然行为，提升动物福利。
   </li>
   <li data-aos="fade-up" data-aos-delay="600">
     <strong>🧪 手术级一体化与解剖结构适配</strong><br>
     侧壁纹理增强了与牙科水泥的附着力。基座底部的打印弧度可根据不同动物头部曲线进行定制调整，实现完美贴合，构建出全封闭的防护舱。
   </li>
 </ul>
</div>
 
<div align="center" data-aos="zoom-in-up" data-aos-duration="1000">
 <br>
 <div class="gif-placeholder">
  <img data-src="Videos/Animation%20repeat.gif" 
        src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7"
        alt="ELINK-256 动画演示 GIF"
        class="lazy-gif white-bg-gif" 
        decoding="async">
 </div>
</div>
 
<span id="cn-signal-demo"></span>
### ⚡ 代表性 Spike 信号采集示意
 
<p style="color: #64748b; font-size: 0.95em; margin-bottom: 20px;">
  本交互模块为模拟演示，展示了系统在标准 Spike 频段（300 Hz – 7.5 kHz）下的胞外动作电位采集能力。该模型以 30 kS/s 的采样率，直观呈现了使用 E-Link 系统进行高密度记录时预期的波形动力学特征、系统热噪声底噪以及信噪比 (SNR) 表现。
</p>
 
<div class="intan-simulator-wrapper" data-aos="fade-up">
 <div class="intan-title-bar">
   <div class="intan-title-text">
     <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M2 12h4l3-9 5 18 3-9h5"/></svg>
     Intan RHX Interface - Simulated E-Link (256-ch) Stream
   </div>
   <div class="intan-window-controls"><span class="close"></span><span class="min"></span><span class="max"></span></div>
 </div>
  
 <div class="intan-body">
   <div class="intan-plots-wrapper">
     <div class="intan-plot-pane">
       <div class="intan-time-axis">
         <span>0</span><span>200</span><span>400</span><span>600</span><span>800</span><span>1000 ms</span>
       </div>
       <div class="intan-canvas-container">
         <canvas class="intan-canvas canvas-left"></canvas>
       </div>
       <div class="intan-pane-footer">
         <span>⛶ Port A (128 ch)</span>
         <div class="intan-footer-tools">
           <span>➕ ➖ ⭱</span>
           <label><input type="checkbox" checked> show pinned</label>
           <span>▤ 🗗</span>
         </div>
       </div>
     </div>
     <div class="intan-plot-pane">
       <div class="intan-time-axis">
         <span>0</span><span>200</span><span>400</span><span>600</span><span>800</span><span>1000 ms</span>
       </div>
       <div class="intan-canvas-container">
         <canvas class="intan-canvas canvas-right"></canvas>
       </div>
       <div class="intan-pane-footer">
         <span>⛶ Port B (128 ch)</span>
         <div class="intan-footer-tools">
           <span>➕ ➖ ⭱</span>
           <label><input type="checkbox" checked> show pinned</label>
           <span>▤ 🗗</span>
         </div>
       </div>
     </div>
   </div>
    
   <div class="intan-sidebar">
     <div class="intan-btn-group"><div class="intan-btn">Run</div><div class="intan-btn record">Record</div></div>
    <div class="intan-panel">
       <div class="intan-panel-title">Hardware Ports</div>
       <div class="hw-ports-grid">
         <div class="hw-port-box active">
           <div class="hw-port-left"><span class="hw-port-label">A</span><div class="hw-port-connector"></div></div>
           <div class="hw-port-leds"><div class="hw-led"></div><div class="hw-led"></div><div class="hw-led green"></div></div>
         </div>
         <div class="hw-port-box active">
           <div class="hw-port-left"><span class="hw-port-label">B</span><div class="hw-port-connector"></div></div>
           <div class="hw-port-leds"><div class="hw-led"></div><div class="hw-led"></div><div class="hw-led green"></div></div>
         </div>
         <div class="hw-port-box inactive">
           <div class="hw-port-left"><span class="hw-port-label">C</span><div class="hw-port-connector"></div></div>
           <div class="hw-port-leds"><div class="hw-led"></div><div class="hw-led"></div><div class="hw-led"></div></div>
         </div>
         <div class="hw-port-box inactive">
           <div class="hw-port-left"><span class="hw-port-label">D</span><div class="hw-port-connector"></div></div>
           <div class="hw-port-leds"><div class="hw-led"></div><div class="hw-led"></div><div class="hw-led"></div></div>
         </div>
       </div>
     </div>
     <div class="intan-panel">
       <div class="intan-panel-title">Filter Bandwidth</div>
       <div class="intan-setting-row"><span>High-pass</span><div class="intan-value-box">300 Hz</div></div>
       <div class="intan-setting-row"><span>Low-pass</span><div class="intan-value-box">7.5 kHz</div></div>
     </div>
     <div class="intan-panel">
       <div class="intan-panel-title">System Status</div>
       <div class="intan-setting-row" style="color: #27c93f; font-weight: bold;"><span>SPI Links</span><span>A, B Locked</span></div>
       <div class="intan-setting-row" style="color: #777;"><span>Unused</span><span>C, D</span></div>
       <div class="intan-setting-row"><span>Sampling</span><div class="intan-value-box" style="border:none;box-shadow:none;background:transparent;text-align:right;">30 kS/s</div></div>
     </div>
   </div>
 </div>
</div>

<div class="scope-win-wrapper" data-aos="fade-up" style="margin-top: 20px;">
  <div class="scope-title-bar">
    <div class="scope-title-left">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="#60a5fa" stroke-width="3"><polygon points="12 2 22 22 2 22"/></svg>
      Spike Scope
    </div>
    <div class="intan-window-controls"><span class="close"></span><span class="min"></span><span class="max"></span></div>
  </div>
  
  <div class="scope-body">
    <div class="scope-sidebar">
      <div class="scope-fieldset">
        <div class="scope-legend">通道</div>
        <div style="margin-bottom: 6px;">A-126</div>
        <label class="scope-row"><input type="checkbox" checked> 锁定绘图至选中通道</label>
        <div class="scope-btn" style="border-color: #0078d7; background: #e5f1fb; margin-top:2px;">设置为选中通道</div>
      </div>
      
      <div class="scope-fieldset">
        <div class="scope-legend">显示设置</div>
        <div class="scope-row" style="justify-content: space-between;">电压量程 <select class="scope-input" style="width:65px"><option>500 µV</option></select></div>
        <div class="scope-row" style="justify-content: space-between;">时间刻度 <select class="scope-input" style="width:65px"><option>2 ms</option></select></div>
        <div class="scope-row" style="justify-content: space-between;">显示 <select class="scope-input" style="width:45px"><option>20</option></select> 个波形</div>
        <div class="scope-btn" style="margin-bottom: 6px;">清除画面</div>
        <div class="scope-row" style="margin-bottom:0;"><div class="scope-btn" style="flex:1">截取快照</div><div class="scope-btn" style="flex:1">清除快照</div></div>
      </div>

      <div class="scope-fieldset">
        <div class="scope-legend">动作电位检测设置</div>
        <div class="scope-row" style="justify-content: space-between; margin-bottom:0;">检测阈值 <input type="text" class="scope-input" value="-70 µV" style="width:55px;"></div>
      </div>

      <div class="scope-fieldset">
        <div class="scope-legend">伪影抑制</div>
        <label class="scope-row"><input type="checkbox" checked> 启用抑制</label>
        <label class="scope-row"><input type="checkbox" checked> 显示伪影</label>
        <div class="scope-row" style="justify-content: space-between; margin-bottom:0;">伪影阈值 <input type="text" class="scope-input" value="2500 µV" style="width:55px;"></div>
      </div>

      <div class="scope-btn" style="margin-top: -2px;">加载检测参数</div>
      <div class="scope-btn" style="margin-top: -6px;">保存检测参数</div>
    </div>
    
    <div class="scope-plot-area">
      <canvas class="spike-scope-canvas"></canvas>
      <div class="scope-overlay-text" style="top:10px; left:10px; color:#fff;">+500 µV</div>
      <div class="scope-overlay-text" style="top:50%; left:10px; color:#fff; transform:translateY(-50%);">0</div>
      <div class="scope-overlay-text" style="top:calc(50% + 7%); left:10px; color:#ef4444; transform:translateY(-50%);">-70</div>
      <div class="scope-overlay-text" style="bottom:20px; left:10px; color:#fff;">-500 µV</div>

      <div class="scope-overlay-text" style="bottom:5px; left:10px; color:#fff;">-1</div>
      <div class="scope-overlay-text" style="bottom:5px; left:33.33%; color:#fff; transform:translateX(-50%);">0</div>
      <div class="scope-overlay-text" style="bottom:5px; left:66.66%; color:#fff; transform:translateX(-50%);">1</div>
      <div class="scope-overlay-text" style="bottom:5px; right:10px; color:#fff;">2 ms</div>

      <div class="scope-overlay-text" style="top:10px; left:50%; transform:translateX(-50%); color:#fff; font-size: 12px; font-weight: bold;">A-126</div>
      <div class="scope-overlay-text scope-dynamic-stats" style="top:28px; left:50%; transform:translateX(-50%); color:#4ade80; white-space: nowrap;">RMS: 9.1 µV &nbsp;&nbsp;|&nbsp;&nbsp; 5 spikes/s</div>
    </div>
  </div>
</div>
 
---
 
<span id="cn-bom"></span>
 
### 🛠 放大器物料清单 (BOM)
 
<div align="center">
 <img src="Images/256HD.png" 
      alt="256通道放大器组装实物图" 
      width="460" 
      loading="lazy" decoding="async"
      style="border-radius: 8px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); margin-bottom: 20px;">
 <p style="margin-top: 5px; font-size: 0.9em; color: #64748b;">
   <b>已组装的 256 通道前置放大器 (顶视图)</b>
 </p>
</div>
 
<div align="center" data-aos="zoom-in-up" data-aos-duration="1000">
 <br>
 <div class="gif-placeholder narrow">
  <img data-src="Videos/Top PCB explosive new.gif" 
        src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7"
        alt="顶部4层电路板的设计爆炸动图"
        class="lazy-gif white-bg-gif" 
        decoding="async">
 </div>
</div>
     
<div style="width: 100%; max-width: 100%; overflow-x: auto; -webkit-overflow-scrolling: touch; padding-bottom: 10px;">
 <table style="margin-left: auto; margin-right: auto; width: 90%; min-width: 600px; text-align: center; border-collapse: collapse; border: 1px solid #e1e4e8;">
   <thead>
     <tr style="background-color: #f6f8fa; border-bottom: 2px solid #e1e4e8;">
       <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">组件</th>
       <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">描述</th>
       <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">数量</th>
       <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">封装</th>
       <th style="padding: 10px; border: 1px solid #e1e4e8; text-align: center;">备注</th>
     </tr>
   </thead>
   <tbody>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>放大器 IC</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">Intan RHD2164</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">4</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">BGA</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>关键：</b> 确保方向正确</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>SPI 连接器</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">Omnetics A7621</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">2</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">-</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">12 线线束 (32 AWG)</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>电阻</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">标准贴片</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">7</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">0402</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">LVDS 配置</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>电容</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">标准贴片</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">8</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">0603</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">LVDS 配置</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b>电源 LED</b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">绿色 LED</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">1</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">0402</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">自检状态灯</td>
     </tr>
     <tr>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;"><b> BGA锡球 </b></td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">0.4 mm 无铅</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">约300</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">-</td>
       <td style="padding: 8px; border: 1px solid #e1e4e8; text-align: center;">用于 BGA 组装</td>
     </tr>
   </tbody>
 </table>
</div>
 
---
 
## 👥 开发者与实验室
 
* **白天宇** (主导研发及设计) <a href="https://tianyu-bai.github.io/"><img src="https://img.shields.io/badge/个人主页-Tianyu%20Bai-0077B5?style=flat-square&logo=github&logoColor=white" alt="Website"></a>
* **李根**
* **方辉教授** <a href="https://engineering.dartmouth.edu/community/faculty/hui-fang"><img src="https://img.shields.io/badge/首席研究员_(PI)-444444?style=flat-square&logoColor=white" />
 
本项目由达特茅斯学院的 **MINE Lab**团队开发。<a href="https://sites.dartmouth.edu/fang-group/"><img src="https://img.shields.io/badge/访问网站_%E2%86%97-MINE_Lab-00693E?style=flat-square" alt="MINE Lab"></a>
 
---
 
## 📄 出版物
 
相关工作目前正在 **IEEE Journal on Flexible Electronics (JFLEX)** 审稿中。
 
本仓库中的硬件设计和视觉资产直接对应于投稿中描述的系统。
 
* **完整引用**：正式录用后，最终论文的永久链接将立即在此处更新。
* **预印本/全文**：*即将推出。*
  
* 🤝 **我们诚挚欢迎神经工程科研同行的反馈与合作！**
 
* **技术咨询**：有意部署 E-Link易链？作为开发者深知从零搭建一套新系统往往伴随诸多挑战。无论您在 PCB 设计、3D 打印制造，还是系统组装方面遇到任何问题，都欢迎随时通过邮件与我们取得联系。将为您提供技术支持！
  * **技术支持**: [<font color="#60a5fa">support@ephys.tech</font>](mailto:support@ephys.tech)
  * **留言**: [<font color="#60a5fa">tianyu@ephys.tech</font>](mailto:tianyu@ephys.tech)
 
---
 
## 📑 引用与 DOI
 
如果您在研究中使用了这些设计、代码或资产，需使用 Zenodo 提供的永久 DOI 引用本仓库：
 
**当前引用源：**
> T. Bai, et al., "E-Link GitHub Repository," v1.0, MINE Lab, Dartmouth College, 2026. [![DOI](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.18440104-007EC6?style=flat-square)](https://doi.org/10.5281/zenodo.18440104)
 
---
 
<span id="cn-downloads"></span>
 
## 🔗 仓库与下载
 
本项目完全开源。相关论文录用后，包含 **PCB 制造文件 (Gerber)** 和 **3D打印文件** 的完整数据集将通过以下链接提供访问。
 
<div align="center">
 <p><b>👇 欢迎收藏本仓库以便未来下载：</b></p>
 
<div align="center">
 <a href="https://github.com/Tianyu-Bai/ELINK"><img src="https://img.shields.io/badge/GitHub-查看源仓库-181717?style=for-the-badge&logo=github&logoColor=white" alt="View on GitHub"></a>
 <img src="https://img.shields.io/badge/状态-锁定中，直到发表-A31F34?style=for-the-badge&logo=private" alt="Status Locked">
</div>
</div>
 
---
 
## 🤝 致谢
 
开发者感谢 **美国国立卫生研究院 NIH R01MH139342** 和 **达特茅斯博士生创新奖学金 (Dartmouth PhD Innovation Fellowship)** 的支持。
 
特别感谢 **达特茅斯Thayer工学院** 的相关成员在易链系统开发过程中提供的技术支持和反馈。
 
---
 
## 📜 许可协议
 
版权所有 © 2026 Tianyu Bai <a href="https://tianyu-bai.github.io/"><img src="https://img.shields.io/badge/个人主页-Tianyu%20Bai-0077B5?style=flat-square&logo=github&logoColor=white" alt="Website"></a>
 
本项目为开源硬件，在以下许可下可用。点击下方徽章查看完整许可详情。
 
* **硬件源文件** (KiCad/Gerbers/STL 文件)：在 **MIT 许可** 下授权。
* **文档、原理图 (PDF) 和图像**：在 **CC BY 4.0 国际许可** 下授权。
 
<div align="center">
 <a href="https://github.com/tianyu-bai/E-Link/blob/main/LICENSE">
   <img src="https://img.shields.io/badge/开源协议-MIT-A31F34?style=flat-square&logo=opensourceinitiative&logoColor=white" alt="License">
 </a>
</div>
 
</div> 
 
<script>
 document.addEventListener("DOMContentLoaded", () => {
 
   // ===================== E-Link 动态数据面板 =====================
   const dashboardObserver = new IntersectionObserver((entries) => {
     entries.forEach(entry => {
       const card = entry.target;
       const fgRing = card.querySelector('.fg-ring');
       const numberEl = card.querySelector('.count-up') || card.querySelector('.v2-count');
       if (!numberEl) return;
 
       const targetValue = parseFloat(card.dataset.value);
       const isFloat = card.dataset.isFloat === "true";
       const decimals = parseInt(card.dataset.decimals) || 1;
       const circumference = 283;
       const duration = 2000;
 
       if (entry.isIntersecting) {
         if (card.dataset.dashboardInView === "true") return;
         card.dataset.dashboardInView = "true";
 
         let startTimestamp = null;
         const animate = (timestamp) => {
           if (card.dataset.dashboardInView !== "true") return;
           if (!startTimestamp) startTimestamp = timestamp;
           const elapsed = timestamp - startTimestamp;
           const progress = Math.min(elapsed / duration, 1);
           const easeProgress = progress === 1 ? 1 : 1 - Math.pow(2, -10 * progress);
           const currentValue = easeProgress * targetValue;
           
           numberEl.innerText = isFloat ? currentValue.toFixed(decimals) : Math.round(currentValue);
           
           if (card.dataset.type === 'ring' && fgRing) {
               fgRing.style.strokeDashoffset = circumference - (circumference * easeProgress);
           } else if (card.dataset.type === 'thermo') {
               const fill = card.querySelector('.thermo-fill');
               const maxTemp = parseFloat(card.dataset.max) || 50;
               if (fill) fill.style.height = ((currentValue / maxTemp) * 100) + '%';
           }
 
           if (progress < 1) {
              card.dashboardAnimFrame = requestAnimationFrame(animate);
           }
         };
         cancelAnimationFrame(card.dashboardAnimFrame);
         card.dashboardAnimFrame = requestAnimationFrame(animate);
 
       } else {
         card.dataset.dashboardInView = "false";
         if (card.dashboardAnimFrame) {
           cancelAnimationFrame(card.dashboardAnimFrame);
           card.dashboardAnimFrame = null;
         }
       }
     });
   }, { threshold: 0.25, rootMargin: "0px 0px -5% 0px" });
 
   document.querySelectorAll('.metric-card, .metric-card-v2').forEach(card => dashboardObserver.observe(card));
 
   // ===================== 3D 模型交互（修复显存溢出与闪退）=====================
   const models = Array.from(document.querySelectorAll('model-viewer'));
   if (models.length > 0) {
     let isScrolling = false;
     let scrollEndTimer = null;
     
     function isSlowNetwork() {
       const conn = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
       if (!conn) return false;
       return ['slow-2g', '2g'].includes(conn.effectiveType);
     }
     
     const MAX_LIVE_CONTEXTS = 2; 
     const liveContextQueue = [];
 
     function reclaimContext(viewer) {
       if (viewer.dataset.loaded === "true") {
         viewer.pause();
         viewer._cachedSrc = viewer._cachedSrc || viewer.src;
         viewer.src = '';
         viewer.dataset.loaded = "reclaimed";
       }
     }
 
     function ensureContextSlot(viewer) {
       const idx = liveContextQueue.indexOf(viewer);
       if (idx !== -1) liveContextQueue.splice(idx, 1);
       liveContextQueue.push(viewer);
 
       while (liveContextQueue.length > MAX_LIVE_CONTEXTS) {
         const victim = liveContextQueue.shift();
         if (victim !== viewer) {
           reclaimContext(victim);
         }
       }
     }
 
     const activateViewer = async (viewer, force = false) => {
       if (isScrolling && !force) return;
       ensureContextSlot(viewer);
 
       if (viewer.getAttribute('reveal') === 'manual' && viewer.dataset.loaded !== "true") {
         if (viewer.dataset.loaded === "reclaimed" && viewer._cachedSrc) {
           viewer.src = viewer._cachedSrc;
         } else if (viewer.dataset.src) {
           viewer.src = viewer.dataset.src; 
         }
         viewer.dataset.loaded = "true";
         const loadHandler = () => {
           viewer.removeEventListener('load', loadHandler);
           try { viewer.play(); } catch(e) {}
         };
         viewer.addEventListener('load', loadHandler);
         await new Promise(resolve => requestAnimationFrame(resolve));
         viewer.dismissPoster();
         return;
       }
 
       if (viewer.dataset.loaded === "reclaimed" && viewer._cachedSrc) {
         viewer.src = viewer._cachedSrc;
         viewer.dataset.loaded = "true";
         const reloadHandler = () => {
           viewer.removeEventListener('load', reloadHandler);
           try { viewer.play(); } catch(e) {}
         };
         viewer.addEventListener('load', reloadHandler);
         return;
       }
 
       if (viewer.paused) {
         try { viewer.play(); } catch(e) {}
       }
 
       if (viewer.dataset.overlayDisabled !== "true") {
         clearTimeout(viewer.hudTimer);
         viewer.hudTimer = setTimeout(() => {
           viewer.querySelectorAll('.gesture-overlay').forEach(el => el.classList.add('gesture-active'));
         }, 500);
       }
     };
 
     const checkAndActivateBestModel = () => {
       if (isSlowNetwork()) return;
       models.forEach(viewer => {
         if (viewer.dataset.inView === "true") {
           activateViewer(viewer);
         }
       });
     };
 
     window.addEventListener('scroll', () => {
       isScrolling = true;
       clearTimeout(scrollEndTimer);
       scrollEndTimer = setTimeout(() => {
         isScrolling = false;
         checkAndActivateBestModel();
       }, 150);
     }, { passive: true });
 
     models.forEach(viewer => {
       viewer.addEventListener('click', () => {
         activateViewer(viewer, true);
       });
 
       viewer.addEventListener('error', (e) => {
         console.warn('[E-Link] model-viewer GL error triggered.');
         viewer._cachedSrc = viewer._cachedSrc || viewer.src;
         viewer.src = '';
         viewer.dataset.loaded = "reclaimed";
       });
 
       const handleCameraChange = (event) => {
         if (event.detail.source === 'user-interaction' && viewer.dataset.overlayDisabled !== "true") {
           viewer.querySelectorAll('.gesture-overlay, .gesture-hud').forEach(el => {
             el.classList.add('gesture-hidden');
           });
           viewer.dataset.overlayDisabled = "true";
           viewer.removeEventListener('camera-change', handleCameraChange);
         }
       };
       viewer.addEventListener('camera-change', handleCameraChange);
     });
 
     const modelObserver = new IntersectionObserver((entries) => {
       entries.forEach(entry => {
         const viewer = entry.target;
         if (entry.isIntersecting) {
           viewer.dataset.inView = "true";
           if (!isScrolling) checkAndActivateBestModel();
         } else {
           viewer.dataset.inView = "false";
           viewer.pause();
           viewer.querySelectorAll('.gesture-overlay').forEach(el => el.classList.remove('gesture-active'));
         }
       });
     }, { threshold: 0.1 });
 
     models.forEach(model => modelObserver.observe(model));
   }
 
   // ===================== Intan 双屏示波器引擎 =====================
   const intanSimulators = document.querySelectorAll('.intan-simulator-wrapper');
 
   const intanColors = [
     '#e04a4a', '#d49b38', '#3dc94d', '#3dc98b', '#3da1c9', '#3d61c9', '#573dc9',
     '#993dc9', '#c93d9e', '#c93d5a', '#d47238', '#b8c93d', '#70c93d', '#3dc9c7', '#3d94c9',
     '#3d51c9', '#6d3dc9', '#b53dc9', '#c93da6', '#c93d4a', '#d48838', '#d4b338', '#99c93d',
     '#3dc958', '#3dc99e', '#3dbbc9', '#3d6ec9', '#4d3dc9', '#8b3dc9', '#c93dbb', '#c93d70'
   ];
 
   intanSimulators.forEach(sim => {
     const canvasL = sim.querySelector('.canvas-left');
     const canvasR = sim.querySelector('.canvas-right');
     if (!canvasL || !canvasR) return;
 
     const ctxL = canvasL.getContext('2d', { alpha: false });
     const ctxR = canvasR.getContext('2d', { alpha: false });
     
     let width, height;
     let lastWidth = 0; 
     const NUM_CHANNELS = 20; 
     const LABEL_WIDTH = 100; 
     let scanX = LABEL_WIDTH;  
     const scanSpeed = 5.0; 
     let animationFrame;
     
     function resizeIntanCanvas() {
       if(canvasL.parentElement.clientWidth === 0) return;
       const newWidth = canvasL.parentElement.clientWidth;
       const newHeight = canvasL.parentElement.clientHeight;
       
       if (lastWidth === newWidth) return; 
       lastWidth = newWidth;
 
       const dpr = Math.min(window.devicePixelRatio || 1, 2);
       width = newWidth;
       height = newHeight;
       
       [canvasL, canvasR].forEach(canvas => {
         canvas.width = width * dpr;
         canvas.height = height * dpr;
         const ctx = canvas.getContext('2d');
         ctx.scale(dpr, dpr);
         ctx.fillStyle = '#000000';
         ctx.fillRect(0, 0, width, height);
       });
 
       scanX = window.innerWidth <= 768 ? 80 : LABEL_WIDTH;
     }
       
     window.addEventListener('resize', resizeIntanCanvas);
     resizeIntanCanvas();
     new ResizeObserver(resizeIntanCanvas).observe(canvasL.parentElement);
 
     function generateChannels(prefix) {
       const arr = [];
       for (let i = 0; i < NUM_CHANNELS; i++) {
         let isBad = false;
         let imp = (316 + Math.random() * 100).toFixed(0) + " kΩ";
         
         if ((prefix === 'A' && i === 2) || (prefix === 'B' && i === 8)) {
           isBad = true;
           imp = (15 + Math.random() * 5).toFixed(1) + " MΩ"; 
         }
 
         let chColor = isBad ? '#6b6b6b' : intanColors[i % intanColors.length];
         let idStr = (i + 108).toString().padStart(3, '0');
         
         arr.push({
           id: `${prefix}-${idStr}`, 
           imp: imp,                 
           color: chColor, 
           isBad: isBad,
           baseY: 0, 
           lastY: 0, 
           currentNoise: 0, 
           isSpiking: false, 
           spikeProgress: 0, 
           spikeAmp: 0,
           firingRate: isBad ? 0 : (0.001 + Math.random() * 0.006) 
         });
       }
       return arr;
     }
     
     const channelsL = generateChannels('A');
     const channelsR = generateChannels('B');
 
     function drawPane(ctx, channelsData, isLeftPane) {
       const isMobile = window.innerWidth <= 768;
       const currentLabelWidth = isMobile ? 80 : LABEL_WIDTH; 
       const eraseWidth = 7; 
       ctx.fillStyle = '#000000';
       
       if (scanX + eraseWidth > width) {
         ctx.fillRect(scanX, 0, width - scanX, height);
         ctx.fillRect(currentLabelWidth, 0, eraseWidth - (width - scanX), height);
       } else {
         ctx.fillRect(scanX, 0, eraseWidth, height);
       }
 
       const gap = height / (NUM_CHANNELS + 0.5);
       const maxAmplitude = gap * 0.65; 
 
       for (let i = 0; i < NUM_CHANNELS; i++) {
         const ch = channelsData[i];
         ch.baseY = Math.floor(gap * (i + 0.5)) + 0.5;
         let signal = 0;
 
         if (ch.isBad) {
           ch.isSpiking = false; 
           // 修复 1: 放弃绝对时间，直接用屏幕宽度比例生成密集的工频干扰波 (一屏约 15~20 个周期)
           // 修复 2: 将干扰振幅从 0.15 暴增到 0.8，让它霸占整个通道的高度！
           const powerLineInterference = Math.sin((scanX / width) * 20 * Math.PI * 2) * 0.8;
           
           // 坏通道的随机底噪可以压低一点，突出巨大的正弦波轮廓
           ch.currentNoise = ch.currentNoise * 0.3 + (Math.random() - 0.5) * 0.1; 
           signal = powerLineInterference + ch.currentNoise;
          }
         else {
           ch.currentNoise = ch.currentNoise * 0.15 + (Math.random() - 0.5) * 0.35;
           signal = ch.currentNoise; 
           
           if (!ch.isSpiking && Math.random() < ch.firingRate) {
              ch.isSpiking = true; 
              ch.spikeProgress = 0; 
              ch.spikeAmp = 0.8 + Math.random() * 0.5; 
           }
 
           if (ch.isSpiking) {
              let t = ch.spikeProgress;
              let spikeShape = 
                -2.0 * Math.exp(-Math.pow((t - 0.24) * 18, 2)) +  
                 0.9 * Math.exp(-Math.pow((t - 0.55) * 7, 2)) +   
                 0.1 * Math.exp(-Math.pow((t - 0.80) * 4, 2));    
 
              signal += spikeShape * ch.spikeAmp;
              ch.spikeProgress += 0.12; 
              if (ch.spikeProgress >= 1) ch.isSpiking = false;
           }
         }
 
         const currentY = Math.floor(ch.baseY + signal * maxAmplitude) + 0.5;
         
         if (scanX > currentLabelWidth + scanSpeed) {
           ctx.beginPath();
           ctx.strokeStyle = ch.color; 
           ctx.lineWidth = 1.2;
           ctx.lineJoin = 'round'; 
           ctx.lineCap = 'round';
           ctx.moveTo(scanX - scanSpeed, ch.lastY);
           ctx.lineTo(scanX, currentY);
           ctx.stroke();
         }
         ch.lastY = currentY;
       }
 
       ctx.fillStyle = '#000000';
       ctx.fillRect(0, 0, currentLabelWidth, height);
       
       const fontSize = isMobile ? 7.5 : 10;
       const blockHeight = isMobile ? 8 : 11;
       const blockOffsetY = blockHeight / 2;
       
       ctx.font = `${fontSize}px "Segoe UI", "Arial", sans-serif`;
       ctx.textBaseline = 'middle';
       
       const padding = isMobile ? 3 : 4; 
       const iconSize = isMobile ? 7 : 7; 
       const idOffsetX = padding + iconSize + (isMobile ? 3 : 4); 
       const rightEdge = currentLabelWidth - padding - 1;
 
       for (let i = 0; i < NUM_CHANNELS; i++) {
         const ch = channelsData[i];
         const textY = ch.baseY + (isMobile ? 0.5 : 1); 
         
         ctx.fillStyle = ch.color;
         ctx.fillRect(0, ch.baseY - blockOffsetY, currentLabelWidth - 3, blockHeight);
         
         const themeColor = ch.isBad ? 'rgba(0,0,0,0.7)' : '#fff';
         ctx.fillStyle = themeColor;
 
         const iconY = textY - iconSize / 2;
         ctx.fillRect(padding, iconY, iconSize, iconSize);
         ctx.fillStyle = ch.color;
         ctx.fillRect(padding + iconSize * 0.2, iconY + iconSize * 0.1, iconSize * 0.6, iconSize * 0.3);
         ctx.fillStyle = themeColor;
 
         ctx.textAlign = 'left';
         ctx.fillText(ch.id, idOffsetX, textY);
         
         ctx.textAlign = 'right';
         ctx.fillText(ch.imp, rightEdge, textY);
       }
 
       if (isLeftPane) {
         const scaleY = channelsData[3].baseY + (gap * 0.3); 
         const lineHeight = 6; 
         const scaleX = currentLabelWidth + (isMobile ? 25 : 50);
         
         ctx.strokeStyle = 'rgba(255, 255, 255, 0.8)'; 
         ctx.lineWidth = 1;
         ctx.beginPath();
         ctx.moveTo(scaleX, scaleY - lineHeight); 
         ctx.lineTo(scaleX, scaleY + lineHeight);
         ctx.stroke();
 
         ctx.textAlign = 'left'; 
         ctx.fillStyle = '#fff';
         ctx.font = `${isMobile ? 7 : 9}px "Segoe UI", sans-serif`;
         ctx.fillText("50 µV", scaleX + 6, scaleY + 1);
       }
     }
 
     function renderDualSweep() {
       if (!window.isPageScrolling) {
         drawPane(ctxL, channelsL, true);
         drawPane(ctxR, channelsR, false);
 
         scanX += scanSpeed;
         if (scanX >= width) {
           scanX = window.innerWidth <= 768 ? 80 : LABEL_WIDTH;
         }
       }
       animationFrame = requestAnimationFrame(renderDualSweep);
     }
 
     const observer = new IntersectionObserver((entries) => {
       if (entries[0].isIntersecting && canvasL.offsetParent !== null) {
         if (!animationFrame) renderDualSweep();
       } else {
         if (animationFrame) cancelAnimationFrame(animationFrame);
         animationFrame = null;
       }
     }, { threshold: 0.1 });
     observer.observe(sim);
   });
 
   // ===================== GIF 懒加载 =====================
   const gifObserver = new IntersectionObserver((entries, observer) => {
     entries.forEach(entry => {
       if (entry.isIntersecting) {
         const img = entry.target;
         observer.unobserve(img); 
 
         const markLoaded = () => {
           requestAnimationFrame(() => {
              img.classList.add('is-loaded'); 
           });
         };
 
         img.addEventListener('load', markLoaded, { once: true });
         img.src = img.dataset.src;
 
         if (img.complete && img.naturalWidth > 1) {
           markLoaded();
         }
       }
     });
   }, { threshold: 0.1, rootMargin: "50px 0px" });
 
   document.querySelectorAll('img.lazy-gif').forEach(gif => {
     gifObserver.observe(gif);
   });

   // ===================== 全新重写的 Spike Scope 波形引擎 =====================
   const scopeWrappers = document.querySelectorAll('.scope-plot-area');
   scopeWrappers.forEach(wrapper => {
     const canvas = wrapper.querySelector('.spike-scope-canvas');
     const ctx = canvas.getContext('2d');
     let sWidth, sHeight;
     let spikes = [];
     let animationFrame;

     function resizeScope() {
        if (wrapper.clientWidth === 0) return;
        const dpr = window.devicePixelRatio || 1;
        sWidth = wrapper.clientWidth;
        sHeight = wrapper.clientHeight;
        
        // 设定物理分辨率（高清）
        canvas.width = sWidth * dpr;
        canvas.height = sHeight * dpr;
        
        // 【关键修复】强制锁定 CSS 逻辑尺寸，不让它挤压父容器
        canvas.style.width = sWidth + 'px';
        canvas.style.height = sHeight + 'px';
        
        ctx.scale(dpr, dpr);
      }
     
     window.addEventListener('resize', resizeScope);
     resizeScope();
     new ResizeObserver(resizeScope).observe(wrapper);

     // 特征的 Spike 生成器 (包含真实带通底噪与触发点收束)
      function generateSpike() {
        const trace = [];
        const points = 250; 
        const tMin = -1, tMax = 2;
        const dt = (tMax - tMin) / points;
        
        const isOutlier = Math.random() < 0.1;
        const ampJitter = 0.9 + Math.random() * 0.2; 
        
        const peakAmpJitter1 = 0.85 + Math.random() * 0.35; 
        const peakAmpJitter2 = 0.8 + Math.random() * 0.4;

        let currentNoise = 0; // 用于生成平滑带通噪声的状态变量

        for(let i = 0; i < points; i++) {
          let t = tMin + i * dt;
          
          // 🌟 1. 生成逼真的带通滤波底噪
          // 降低平滑权重(0.5 -> 0.3)，增加白噪声比例，让底噪看起来更刺、更清脆
           currentNoise = currentNoise * 0.3 + (Math.random() - 0.5) * 20; 
           let pureWhiteNoise = (Math.random() - 0.5) * 16;
           let totalNoise = currentNoise + pureWhiteNoise;
          
          // 🌟 2. 模拟真实示波器的“触发点打结”效应
          // 在 t=0 触发点附近强行收束噪声，让它们完美交汇于 -70，远离触发点则恢复毛躁
          let noiseSuppression = 1;
          if (t > -0.06 && t < 0.08) {
              // 使用次指数平滑衰减，在 t=0 时噪点绝对为 0
              let dist = t < 0 ? Math.abs(t) / 0.06 : t / 0.08;
              noiseSuppression = Math.pow(dist, 1.2); 
          }
          totalNoise *= noiseSuppression;

          let val = 0;
          
          if (!isOutlier) {
              // 📈 主波形集群
              if (t >= -0.2 && t <= 0) {
                  let norm = (t + 0.2) / 0.2; 
                  val = -70 * Math.pow(norm, 2); 
              } else if (t > 0 && t <= 0.12) {
                  let norm = t / 0.12; 
                  val = -70 - 90 * Math.sin(norm * Math.PI / 2); 
              } else if (t > 0.12 && t <= 0.6) {
                  let norm = (t - 0.12) / 0.48;
                  val = -160 + (260 * peakAmpJitter1) * (1 - Math.cos(norm * Math.PI)) / 2; 
              } else if (t > 0.6 && t <= 1.2) {
                  let norm = (t - 0.6) / 0.6;
                  val = (100 * peakAmpJitter1) * Math.cos(norm * Math.PI / 2); 
              }
          } else {
              // 📉 尖锐离群波形
              if (t >= -0.1 && t <= 0) {
                  let norm = (t + 0.1) / 0.1;
                  val = -70 * Math.pow(norm, 2); 
              } else if (t > 0 && t <= 0.05) {
                  let norm = t / 0.05;
                  val = -70 - 180 * Math.sin(norm * Math.PI / 2); 
              } else if (t > 0.05 && t <= 0.3) {
                  let norm = (t - 0.05) / 0.25;
                  val = -250 + (470 * peakAmpJitter2) * (1 - Math.cos(norm * Math.PI)) / 2; 
              } else if (t > 0.3 && t <= 0.6) {
                  let norm = (t - 0.3) / 0.3;
                  val = (220 * peakAmpJitter2) * Math.cos(norm * Math.PI / 2); 
              }
          }
          
          // 最终坐标 = (基准波形 * 幅度抖动) + 滤波噪声
          trace.push((val * ampJitter) + totalNoise);
        }
        return trace;
      }

    // 初始预填充6个波形 (Pixel-perfect thickness)
     for(let i = 0; i < 6; i++) spikes.push(generateSpike());

     // 获取我们要动态更新的文字容器，并设置时间戳变量
     const statsOverlay = wrapper.querySelector('.scope-dynamic-stats');
     let lastStatsUpdate = 0;

     // 👇 注意这里加上了 timestamp 参数
     function drawScope(timestamp) {
       if (!window.isPageScrolling) {
       
         // --- 新增：每 800ms 动态刷新一次 RMS 和 Spike 数目 ---
         if (timestamp - lastStatsUpdate > 800) {
           if (statsOverlay) {
             // 模拟真实的微小波动：RMS 在 8.5 ~ 9.8 之间跳动，Spike 率在 3 ~ 7 之间跳动
             const dynamicRms = (8.5 + Math.random() * 1.3).toFixed(1);
             const dynamicRate = Math.floor(Math.random() * 5) + 3;
             statsOverlay.innerHTML = `RMS: ${dynamicRms} µV &nbsp;&nbsp;|&nbsp;&nbsp; ${dynamicRate} spikes/s`;
           }
           lastStatsUpdate = timestamp;
         }
         
         // 填充纯黑底色
         ctx.fillStyle = '#000000';
         ctx.fillRect(0, 0, sWidth, sHeight);

         // 绘制网格与参考线
         const x0 = sWidth / 3;
         const x1 = 2 * sWidth / 3;
         const y0 = sHeight / 2;
         const yThresh = y0 + (70 / 500) * (sHeight / 2);

         ctx.lineWidth = 1;
         ctx.strokeStyle = '#333333';
         
         // 纵向参考线 (0 和 1ms)
         ctx.beginPath(); ctx.moveTo(x0, 0); ctx.lineTo(x0, sHeight); ctx.stroke();
         ctx.beginPath(); ctx.moveTo(x1, 0); ctx.lineTo(x1, sHeight); ctx.stroke();
         
         // 零点横向线 (0µV)
         ctx.strokeStyle = '#444444';
         ctx.beginPath(); ctx.moveTo(0, y0); ctx.lineTo(sWidth, y0); ctx.stroke();

         // 红色阈值线 (-70µV)
         ctx.strokeStyle = '#ef4444';
         ctx.beginPath(); ctx.moveTo(0, yThresh); ctx.lineTo(sWidth, yThresh); ctx.stroke();

         // 偶尔抓取新的 Spike 进缓冲区 (Maintain Pixel-perfect thickness)
            if (Math.random() < 0.16) { 
  spikes.push(generateSpike());
  // 核心修复：只保留最近的 8 个波形，多余的剔除，防止糊成一团
  if (spikes.length > 8) spikes.shift(); 
}

         // 叠加绘制波形 (加入真实的余辉褪色效应)
ctx.lineWidth = 1.2;
ctx.lineJoin = 'round';
spikes.forEach((spike, idx) => {
  
  // 核心修复：最新触发的波形高亮 (alpha 0.9)，历史波形迅速变暗 (alpha 0.15~0.4)
  let alpha;
  if (idx === spikes.length - 1) {
      alpha = 0.9; // 最新波形
  } else {
      alpha = 0.15 + (idx / spikes.length) * 0.25; // 历史余辉
  }
  
  ctx.strokeStyle = `rgba(255, 255, 255, ${alpha})`;
  ctx.beginPath();
  for(let i = 0; i < spike.length; i++) {
    let px = (i / (spike.length - 1)) * sWidth;
    let py = y0 - (spike[i] / 500) * (sHeight / 2);
    i === 0 ? ctx.moveTo(px, py) : ctx.lineTo(px, py);
  }
     ctx.stroke();
        });
       }
       animationFrame = requestAnimationFrame(drawScope);
     }

     const scopeObserver = new IntersectionObserver((entries) => {
       if (entries[0].isIntersecting && wrapper.offsetParent !== null) {
         if (!animationFrame) drawScope();
       } else {
         if (animationFrame) cancelAnimationFrame(animationFrame);
         animationFrame = null;
       }
     }, { threshold: 0.1 });
     
     scopeObserver.observe(wrapper);
   });
 });

  // ===================== 仪表盘：2.68µV 底噪波形动画 (Noise Floor) =====================
    const waveformCanvases = document.querySelectorAll('.waveform-canvas');
    waveformCanvases.forEach(canvas => {
      const ctx = canvas.getContext('2d');
      let width, height;
      let animFrame;
      let inView = false;

      function resizeWaveform() {
        const parent = canvas.parentElement;
        if (!parent || parent.clientWidth === 0) return;
        const dpr = window.devicePixelRatio || 1;
        width = parent.clientWidth;
        height = parent.clientHeight;
        
        canvas.width = width * dpr;
        canvas.height = height * dpr;
        canvas.style.width = width + 'px';
        canvas.style.height = height + 'px';
        ctx.scale(dpr, dpr);
      }

      window.addEventListener('resize', resizeWaveform);
      resizeWaveform();
      new ResizeObserver(resizeWaveform).observe(canvas.parentElement);

      function drawWaveform() {
        if (!inView || !width || !height) return;
        
        // 每次清空画布
        ctx.clearRect(0, 0, width, height);
        ctx.beginPath();
        // 使用契合卡片主题的紫色
        ctx.strokeStyle = '#a78bfa'; 
        ctx.lineWidth = 1.2;
        ctx.lineJoin = 'round';

        // 密集采样点以模拟高频噪声
        const points = 80; 
        const sliceWidth = width / (points - 1);
        let x = 0;

        for (let i = 0; i < points; i++) {
          // 生成随机白噪声，幅度为画布高度的 40%
          const noise = (Math.random() - 0.5) * (height * 0.4);
          const y = (height / 2) + noise;

          if (i === 0) {
            ctx.moveTo(x, y);
          } else {
            ctx.lineTo(x, y);
          }
          x += sliceWidth;
        }
        ctx.stroke();

        // 故意降低一点刷新率 (约30fps)，让白噪声看起来更写实、不那么眼晕
        setTimeout(() => {
          if (inView) {
            animFrame = requestAnimationFrame(drawWaveform);
          }
        }, 35); 
      }

      // 性能优化：只有在用户滚动到该卡片时才渲染动画
      const waveObserver = new IntersectionObserver((entries) => {
        if (entries[0].isIntersecting && canvas.offsetParent !== null) {
          inView = true;
          resizeWaveform();
          if (!animFrame) drawWaveform();
        } else {
          inView = false;
          if (animFrame) cancelAnimationFrame(animFrame);
          animFrame = null;
        }
      }, { threshold: 0.1 });
      
      waveObserver.observe(canvas.parentElement);
    });
</script>
