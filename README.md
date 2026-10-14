<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>GitHub Profile Preview — Lê Ngọc Tú</title>
  <style>
    :root {
      --gh-bg: #0d1117;
      --gh-card: #161b22;
      --gh-border: #30363d;
      --gh-text: #e6edf3;
      --gh-muted: #8b949e;
      --gh-accent: #38bdf8;
      --gh-blue: #2f81f7;
      --gh-green: #238636;
      --gh-code-bg: #1f242c;
    }
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      background-color: var(--gh-bg);
      color: var(--gh-text);
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Noto Sans", Helvetica, Arial, sans-serif;
      line-height: 1.6;
      padding-bottom: 60px;
    }
    /* Top Toolbar */
    .studio-bar {
      position: sticky;
      top: 0;
      z-index: 100;
      background: rgba(22, 27, 34, 0.92);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--gh-border);
      padding: 12px 24px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 12px;
    }
    .studio-title {
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 600;
      font-size: 14px;
      color: var(--gh-text);
    }
    .studio-title span.tag {
      background: rgba(56, 189, 248, 0.15);
      color: var(--gh-accent);
      border: 1px solid rgba(56, 189, 248, 0.35);
      padding: 2px 8px;
      border-radius: 999px;
      font-size: 12px;
    }
    .studio-actions {
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .tab-btn {
      background: var(--gh-code-bg);
      color: var(--gh-muted);
      border: 1px solid var(--gh-border);
      padding: 7px 14px;
      border-radius: 6px;
      font-size: 13px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.15s ease;
    }
    .tab-btn.active {
      background: #21262d;
      color: var(--gh-text);
      border-color: var(--gh-accent);
    }
    .copy-btn {
      background: var(--gh-green);
      color: #fff;
      border: 1px solid rgba(240, 246, 252, 0.1);
      padding: 7px 16px;
      border-radius: 6px;
      font-size: 13px;
      font-weight: 600;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: background 0.15s ease;
    }
    .copy-btn:hover {
      background: #2ea043;
    }
    /* Main Container */
    .container {
      max-width: 980px;
      margin: 24px auto;
      padding: 0 16px;
    }
    .readme-box {
      background: var(--gh-bg);
      border: 1px solid var(--gh-border);
      border-radius: 8px;
      overflow: hidden;
    }
    .readme-header {
      background: var(--gh-card);
      border-bottom: 1px solid var(--gh-border);
      padding: 10px 16px;
      font-size: 13px;
      color: var(--gh-muted);
      font-family: ui-monospace, SFMono-Regular, SF Mono, Menlo, Consolas, monospace;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .readme-body {
      padding: 32px;
    }
    /* Hero Wave SVG */
    .hero-banner {
      width: 100%;
      border-radius: 10px;
      overflow: hidden;
      margin-bottom: 16px;
      background: linear-gradient(135deg, #0f172a 0%, #1e3a8a 50%, #0284c7 100%);
      position: relative;
      text-align: center;
      padding: 38px 20px 48px;
      box-shadow: 0 8px 30px rgba(2, 132, 199, 0.2);
    }
    .hero-banner h1 {
      font-size: 40px;
      font-weight: 800;
      color: #ffffff;
      letter-spacing: -0.5px;
      margin-bottom: 8px;
      border: none;
    }
    .hero-banner p.subtitle {
      font-size: 17px;
      color: #e0f2fe;
      font-weight: 500;
    }
    .hero-wave {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 28px;
    }
    /* Typing Animation Simulation */
    .typing-container {
      text-align: center;
      margin: 14px 0 20px;
      font-family: "Fira Code", ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
      font-size: 18px;
      font-weight: 600;
      color: var(--gh-accent);
      min-height: 30px;
    }
    .cursor {
      display: inline-block;
      width: 10px;
      height: 20px;
      background: var(--gh-accent);
      vertical-align: middle;
      margin-left: 4px;
      animation: blink 1s infinite;
    }
    @keyframes blink {
      0%, 49% { opacity: 1; }
      50%, 100% { opacity: 0; }
    }
    /* Badges */
    .badge-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 8px;
      margin-bottom: 12px;
    }
    .badge-row.left {
      justify-content: flex-start;
    }
    .gh-badge {
      display: inline-flex;
      align-items: center;
      border-radius: 4px;
      overflow: hidden;
      font-size: 11px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      text-decoration: none;
      box-shadow: 0 1px 3px rgba(0,0,0,0.3);
      transition: transform 0.15s ease;
    }
    .gh-badge:hover {
      transform: translateY(-1px);
    }
    .gh-badge .b-label {
      background: #21262d;
      color: #fff;
      padding: 6px 10px;
      display: inline-flex;
      align-items: center;
      gap: 5px;
    }
    .gh-badge .b-val {
      padding: 6px 10px;
      color: #fff;
    }
    .gh-badge.single {
      padding: 6px 12px;
      color: #fff;
    }
    /* Typography & Layout */
    hr {
      border: 0;
      border-top: 1px solid var(--gh-border);
      margin: 28px 0;
    }
    h2 {
      font-size: 22px;
      font-weight: 600;
      padding-bottom: 8px;
      border-bottom: 1px solid var(--gh-border);
      margin: 24px 0 16px;
      color: var(--gh-text);
    }
    h3 {
      font-size: 17px;
      font-weight: 600;
      margin: 16px 0 10px;
      color: var(--gh-text);
    }
    p {
      margin-bottom: 12px;
    }
    ul {
      padding-left: 24px;
      margin-bottom: 16px;
    }
    li {
      margin-bottom: 8px;
    }
    code {
      background: rgba(110, 118, 129, 0.25);
      padding: 2px 6px;
      border-radius: 4px;
      font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
      font-size: 85%;
      color: #79c0ff;
    }
    pre {
      background: var(--gh-card);
      border: 1px solid var(--gh-border);
      border-radius: 6px;
      padding: 16px;
      overflow-x: auto;
      font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
      font-size: 13px;
      line-height: 1.5;
      color: #e6edf3;
      margin: 16px 0;
    }
    /* Tables */
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 16px 0;
      font-size: 14px;
    }
    th, td {
      border: 1px solid var(--gh-border);
      padding: 12px 14px;
      text-align: left;
      vertical-align: top;
    }
    th {
      background: var(--gh-card);
      font-weight: 600;
      color: var(--gh-text);
    }
    tr:nth-child(even) td {
      background: rgba(22, 27, 34, 0.45);
    }
    a {
      color: var(--gh-blue);
      text-decoration: none;
    }
    a:hover {
      text-decoration: underline;
    }
    /* Grid Cards for Projects */
    .bento-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(380px, 1fr));
      gap: 16px;
      margin: 16px 0;
    }
    .bento-card {
      background: var(--gh-card);
      border: 1px solid var(--gh-border);
      border-radius: 8px;
      padding: 20px;
    }
    .bento-card.full {
      grid-column: 1 / -1;
    }
    .bento-card h3 {
      margin-top: 0;
      color: #58a6ff;
    }
    /* Analytics Cards */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 16px;
      margin: 16px 0;
    }
    .stat-card {
      background: #1a1b27;
      border: 1px solid #2f334d;
      border-radius: 8px;
      padding: 18px;
    }
    .stat-card h4 {
      color: #70a5fd;
      font-size: 15px;
      margin-bottom: 12px;
    }
    .stat-item {
      display: flex;
      justify-content: space-between;
      font-size: 13px;
      padding: 4px 0;
      color: #a9b1d6;
    }
    .stat-item strong {
      color: #bb9af7;
    }
    .lang-bar {
      display: flex;
      height: 8px;
      border-radius: 4px;
      overflow: hidden;
      margin: 10px 0;
    }
    /* Quote Box */
    .quote-banner {
      background: linear-gradient(90deg, #1e293b 0%, #0f172a 100%);
      border: 1px solid #38bdf8;
      border-radius: 8px;
      padding: 18px 24px;
      text-align: center;
      color: #38bdf8;
      font-weight: 600;
      font-size: 16px;
      margin: 16px 0;
    }
    /* Raw Code View */
    #raw-view {
      display: none;
    }
    #raw-textarea {
      width: 100%;
      height: 680px;
      background: #090d11;
      color: #79c0ff;
      border: 1px solid var(--gh-border);
      border-radius: 6px;
      padding: 16px;
      font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
      font-size: 13px;
      line-height: 1.5;
      resize: vertical;
    }
  </style>
</head>
<body>

  <div class="studio-bar">
    <div class="studio-title">
      <span>🐙 Le-Ngoc-Tu / README.md</span>
      <span class="tag">GitHub Dark Mode Live Render</span>
    </div>
    <div class="studio-actions">
      <button class="tab-btn active" id="btn-preview" onclick="switchTab('preview')">👁️ Xem bản Render (Visual Preview)</button>
      <button class="tab-btn" id="btn-raw" onclick="switchTab('raw')">💻 Xem mã nguồn Markdown (Raw Code)</button>
      <button class="copy-btn" onclick="copyMarkdown()" id="copy-btn">📋 Copy toàn bộ README.md</button>
    </div>
  </div>

  <div class="container">
    <div class="readme-box">
      <div class="readme-header">
        <span>📖 README.md — Bản hiển thị trực quan chuẩn GitHub Profile</span>
      </div>

      <!-- VISUAL RENDER VIEW -->
      <div class="readme-body" id="preview-view">
        
        <!-- HERO BANNER -->
        <div class="hero-banner">
          <h1>Lê Ngọc Tú 👋</h1>
          <p class="subtitle">🤖 AI Engineer | LLM · RAG · Vietnamese NLP · Computer Vision</p>
          <svg class="hero-wave" viewBox="0 0 1440 100" preserveAspectRatio="none">
            <path fill="#0d1117" d="M0,40 C360,100 1080,0 1440,60 L1440,100 L0,100 Z"></path>
          </svg>
        </div>

        <!-- TYPING ANIMATION -->
        <div class="typing-container">
          <span id="typed-text">Building Production-Ready LLM & RAG Systems 🚀</span><span class="cursor"></span>
        </div>

        <!-- SOCIAL & CONTACT BAR -->
        <div class="badge-row">
          <a class="gh-badge" href="https://lengoctu.com" target="_blank">
            <span class="b-label">🌐 Portfolio</span>
            <span class="b-val" style="background:#0284c7;">lengoctu.com</span>
          </a>
          <a class="gh-badge" href="https://huggingface.co/LeNgocTu" target="_blank">
            <span class="b-label">🤗 HuggingFace</span>
            <span class="b-val" style="background:#eab308;color:#000;">LeNgocTu</span>
          </a>
          <a class="gh-badge" href="https://www.linkedin.com/in/le-ngoc-tu-8562a2347" target="_blank">
            <span class="b-label">💼 LinkedIn</span>
            <span class="b-val" style="background:#0077b5;">Lê Ngọc Tú</span>
          </a>
          <a class="gh-badge" href="https://github.com/Le-Ngoc-Tu" target="_blank">
            <span class="b-label">🐙 GitHub</span>
            <span class="b-val" style="background:#334155;">Le-Ngoc-Tu</span>
          </a>
          <a class="gh-badge" href="mailto:lntu2003.dev@gmail.com">
            <span class="b-label">✉️ Gmail</span>
            <span class="b-val" style="background:#ea4335;">lntu2003.dev@gmail.com</span>
          </a>
          <a class="gh-badge" href="https://zalo.me/0969691930" target="_blank">
            <span class="b-label">💬 Zalo</span>
            <span class="b-val" style="background:#0068ff;">0969 691 930</span>
          </a>
        </div>

        <div class="badge-row">
          <span class="gh-badge"><span class="b-label">📍 Địa điểm</span><span class="b-val" style="background:#10b981;">Phan Thiết, Lâm Đồng, Việt Nam</span></span>
          <span class="gh-badge"><span class="b-label">🕐 Múi giờ</span><span class="b-val" style="background:#6366f1;">UTC +07:00</span></span>
          <span class="gh-badge"><span class="b-label">🎓 Đại học Phan Thiết</span><span class="b-val" style="background:#0e75b6;">GPA 3.77 / 4.0</span></span>
        </div>

        <hr />

        <!-- ABOUT ME -->
        <h2>👨‍💻 Giới thiệu (About Me)</h2>
        <p>
          Xin chào! Tôi là <strong>Lê Ngọc Tú</strong> — <strong>AI Engineer</strong> chuyên nghiên cứu, huấn luyện và triển khai các hệ thống <strong>LLM, Agentic RAG, Speech (TTS/STT) và Computer Vision</strong> vào thực tế cho khối doanh nghiệp và cơ quan hành chính công.
        </p>
        <ul>
          <li>🏢 <strong>Công việc hiện tại:</strong> AI Engineer tại <strong>Công ty TNHH Giải pháp phần mềm Nguyên Luân (NLTECH)</strong> <em>(12/2024 – Hiện tại)</em></li>
          <li>🎓 <strong>Học vấn:</strong> Cử nhân Công nghệ Thông tin – <strong>Đại học Phan Thiết</strong> <em>(09/2021 – 01/2025 | GPA: <strong>3.77 / 4.0</strong>)</em></li>
          <li>🤗 <strong>Open-Source AI:</strong> Fine-tune &amp; công bố các mô hình tiếng Việt trên <a href="https://huggingface.co/LeNgocTu" target="_blank">HuggingFace</a> <em>(TTS song ngữ Việt–Nhật, LLM Persona GGUF, Vietnamese Embedding)</em></li>
          <li>🧠 <strong>Thế mạnh cốt lõi:</strong> <code>Python</code> · <code>FastAPI</code> · <code>LLM Fine-tuning (LoRA)</code> · <code>RAG (LlamaIndex / Qdrant / FAISS)</code> · <code>YOLO &amp; FaceNet</code></li>
          <li>⚡ <strong>Châm ngôn làm việc:</strong> <em>Code by day, research by night</em> 🌙</li>
        </ul>

<pre>name: "Lê Ngọc Tú"
role: "AI Engineer @ NLTECH"
location: "Phan Thiết, Lâm Đồng, Việt Nam (UTC+7)"
education: "Cử nhân CNTT — Đại học Phan Thiết (09/2021 – 01/2025 | GPA: 3.77/4.0)"
research_focus:
  - "Large Language Models (LoRA Fine-tuning, Quantization GGUF, vLLM, Ollama)"
  - "Agentic RAG Pipelines (LlamaIndex, Strands Agents, Qdrant, FAISS)"
  - "Speech & Multimodal AI (Bilingual VI-JA TTS, YOLO, FaceNet)"
mission: "Đóng góp giá trị thực tế thông qua các ứng dụng AI/ML vào sản xuất"</pre>

        <!-- HUGGINGFACE MODELS -->
        <h2>🤗 Mô hình AI Công bố trên HuggingFace (Open-Source Models)</h2>
        <p>Các mô hình được trực tiếp fine-tune, tối ưu hóa cho tiếng Việt và chia sẻ mã nguồn mở cho cộng đồng AI:</p>
        <table>
          <thead>
            <tr>
              <th>Mô hình</th>
              <th>Lĩnh vực</th>
              <th>Mô tả &amp; Điểm nhấn kỹ thuật</th>
              <th>HuggingFace</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><strong>🗣️ Irodori-Sen-TTS</strong></td>
              <td><code>Text-to-Speech</code> <code>VI-JA</code></td>
              <td>Mô hình tổng hợp giọng nói song ngữ <strong>Việt – Nhật</strong> được fine-tune hướng tới độ tự nhiên cao, ngữ điệu mượt mà.</td>
              <td><a href="https://huggingface.co/LeNgocTu/Irodori-Sen-TTS" target="_blank">🤗 LeNgocTu/Irodori-Sen-TTS</a></td>
            </tr>
            <tr>
              <td><strong>🧩 gemma-4-E2B Vietnam Personas</strong></td>
              <td><code>LLM</code> <code>GGUF</code> <code>Edge AI</code></td>
              <td>Mô hình <strong>Gemma (E2B)</strong> fine-tune với bộ dữ liệu Persona tiếng Việt, lượng tử hóa <strong>GGUF</strong> chạy suy luận cục bộ trên thiết bị cấu hình thấp / Edge.</td>
              <td><a href="https://huggingface.co/LeNgocTu/gemma-4-E2B-vietnam-personas-gguf" target="_blank">🤗 LeNgocTu/gemma-4-E2B-gguf</a></td>
            </tr>
            <tr>
              <td><strong>🔎 vietnamese-embeddinggemma-300m</strong></td>
              <td><code>Embedding</code> <code>RAG</code></td>
              <td>Mô hình <strong>EmbeddingGemma 300M</strong> tối ưu chuyên sâu cho ngữ nghĩa tiếng Việt, phục vụ Semantic Search và pipeline RAG.</td>
              <td><a href="https://huggingface.co/LeNgocTu/vietnamese-embeddinggemma-300m" target="_blank">🤗 LeNgocTu/vietnamese-embedding</a></td>
            </tr>
          </tbody>
        </table>

        <!-- TECH STACK -->
        <h2>🛠️ Hệ sinh thái Công nghệ (Tech Stack)</h2>
        <table>
          <thead>
            <tr>
              <th width="28%">Nhóm công nghệ</th>
              <th>Công cụ &amp; Frameworks</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><strong>🤖 LLMs &amp; Agentic RAG</strong></td>
              <td>
                <div class="badge-row left" style="margin:0;">
                  <span class="gh-badge single" style="background:#eab308;color:#000;">🤗 HuggingFace</span>
                  <span class="gh-badge single" style="background:#412991;">🧠 LLMs</span>
                  <span class="gh-badge single" style="background:#ee4c2c;">🔥 Fine-tuning (LoRA)</span>
                  <span class="gh-badge single" style="background:#2563eb;">📚 LlamaIndex / FAISS</span>
                  <span class="gh-badge single" style="background:#6366f1;">🤖 Strands Agents</span>
                  <span class="gh-badge single" style="background:#5c3ee8;">🔎 Vietnamese Embedding</span>
                </div>
              </td>
            </tr>
            <tr>
              <td><strong>👁️ Computer Vision &amp; Speech</strong></td>
              <td>
                <div class="badge-row left" style="margin:0;">
                  <span class="gh-badge single" style="background:#06b6d4;color:#000;">🎯 YOLO</span>
                  <span class="gh-badge single" style="background:#ff6f00;">👤 FaceNet</span>
                  <span class="gh-badge single" style="background:#5c3ee8;">👁️ OpenCV</span>
                  <span class="gh-badge single" style="background:#ff9900;color:#000;">🎙️ TTS / STT</span>
                  <span class="gh-badge single" style="background:#ea580c;">🔊 OmniVoice TTS</span>
                </div>
              </td>
            </tr>
            <tr>
              <td><strong>⚡ AI Serving &amp; Inference</strong></td>
              <td>
                <div class="badge-row left" style="margin:0;">
                  <span class="gh-badge single" style="background:#fdba12;color:#000;">⚡ vLLM</span>
                  <span class="gh-badge single" style="background:#21262d;border:1px solid #484f58;">🦙 Ollama</span>
                  <span class="gh-badge single" style="background:#f55036;">🚀 Groq</span>
                  <span class="gh-badge single" style="background:#412991;">✨ OpenAI API</span>
                  <span class="gh-badge single" style="background:#8e75b2;">💎 Gemini API</span>
                </div>
              </td>
            </tr>
            <tr>
              <td><strong>💻 Backend, Frontend &amp; DB</strong></td>
              <td>
                <div class="badge-row left" style="margin:0;">
                  <span class="gh-badge single" style="background:#3776ab;">🐍 Python</span>
                  <span class="gh-badge single" style="background:#009688;">⚡ FastAPI</span>
                  <span class="gh-badge single" style="background:#339933;">🟢 Node.js / Express</span>
                  <span class="gh-badge single" style="background:#61dafb;color:#000;">⚛️ React / Next.js</span>
                  <span class="gh-badge single" style="background:#dc244c;">🗄️ Qdrant Vector DB</span>
                  <span class="gh-badge single" style="background:#4169e1;">🐘 PostgreSQL / MySQL / MariaDB</span>
                </div>
              </td>
            </tr>
            <tr>
              <td><strong>🚀 DevOps &amp; MLOps</strong></td>
              <td>
                <div class="badge-row left" style="margin:0;">
                  <span class="gh-badge single" style="background:#2496ed;">🐳 Docker</span>
                  <span class="gh-badge single" style="background:#fcc624;color:#000;">🐧 Linux</span>
                  <span class="gh-badge single" style="background:#009639;">🌐 Nginx</span>
                  <span class="gh-badge single" style="background:#2088ff;">⚙️ GitHub Actions</span>
                  <span class="gh-badge single" style="background:#499848;">🦄 Uvicorn</span>
                </div>
              </td>
            </tr>
          </tbody>
        </table>

        <!-- WORK EXPERIENCE -->
        <h2>💼 Kinh nghiệm làm việc (Work Experience)</h2>
        <h3>🏢 AI Engineer — Công ty TNHH Giải pháp phần mềm Nguyên Luân (NLTECH)</h3>
        <p style="color:var(--gh-muted);">📅 <strong>12/2024 – Hiện tại</strong> &nbsp;|&nbsp; 📍 <strong>Phan Thiết, Lâm Đồng, Việt Nam</strong></p>
        <ul>
          <li>🔬 <strong>Nghiên cứu &amp; Fine-tuning:</strong> Huấn luyện chuyên sâu các mô hình AI tiếng Việt <em>(Embedding, LLM Persona, Text-to-Speech)</em> và công bố mô hình trên HuggingFace.</li>
          <li>🧠 <strong>Kiến trúc RAG &amp; LLM:</strong> Xây dựng pipeline RAG &amp; LLM (<code>LlamaIndex</code>, <code>Qdrant</code>, <code>FAISS</code>) để tự động hóa truy xuất thông tin và sinh câu trả lời chính xác.</li>
          <li>👁️ <strong>Thị giác máy tính (Computer Vision):</strong> Phát triển tính năng nhận diện khuôn mặt, phát hiện đối tượng và tích hợp vào backend đưa vào sản xuất.</li>
          <li>🚀 <strong>Triển khai End-to-End:</strong> Đưa giải pháp AI thực tế vào vận hành cho khách hàng doanh nghiệp và đơn vị hành chính công / chính phủ.</li>
        </ul>

        <!-- FEATURED PROJECTS BENTO GRID -->
        <h2>🚀 Dự án Tiêu biểu (Featured Systems &amp; Projects)</h2>
        <div class="bento-grid">
          <div class="bento-card">
            <h3>🏛️ Kiosk AI Hỗ trợ Thủ tục Hành chính (AAAS Chatbot)</h3>
            <p>Chatbot AI đa tác tử (Multi-Agent) triển khai trên Kiosk dịch vụ công, hỗ trợ tra cứu thủ tục hành chính bằng giọng nói tự nhiên kết hợp truy xuất RAG.</p>
            <p style="margin-top:10px;">
              <code>FastAPI</code> <code>React</code> <code>LlamaIndex</code> <code>Qdrant</code> <code>OmniVoice TTS</code> <code>LLMs</code>
            </p>
          </div>
          <div class="bento-card">
            <h3>🎧 Hệ thống AI Hỗ trợ Học tập Tiếng Anh (IELTS)</h3>
            <p>Hệ thống luyện thi IELTS toàn diện 4 kỹ năng (Writing, Speaking, Reading, Listening); ứng dụng Agentic Workflow kết hợp RAG để phản hồi cá nhân hóa và chấm điểm.</p>
            <p style="margin-top:10px;">
              <code>FastAPI</code> <code>React</code> <code>Strands Agents</code> <code>Qdrant</code> <code>Groq</code> <code>Ollama</code>
            </p>
          </div>
          <div class="bento-card full">
            <h3>📄 PDF Translation Tool — Công cụ Dịch thuật Tài liệu PDF Giữ nguyên Bố cục</h3>
            <p>Công cụ dịch tài liệu PDF thông minh giữ nguyên bố cục trang, bảng biểu và định dạng gốc; hỗ trợ xử lý hàng loạt tài liệu dung lượng lớn qua Cloud &amp; Local LLMs.</p>
            <p style="margin-top:10px;">
              <code>PyMuPDF</code> <code>OpenAI API</code> <code>Gemini API</code> <code>Ollama</code>
            </p>
          </div>
        </div>

        <!-- RESEARCH & AWARDS -->
        <h2>📚 Nghiên cứu Khoa học &amp; Giải thưởng (Research &amp; Awards)</h2>
        <table>
          <thead>
            <tr>
              <th>Năm</th>
              <th>Công trình Nghiên cứu / Giải thưởng</th>
              <th>Đơn vị / Công nghệ</th>
              <th>Kết quả</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><strong>2025</strong></td>
              <td><strong>"Exam Fraud Detection Using YOLO Model"</strong></td>
              <td><em>Tạp chí Nhà giáo Việt Nam</em> (<code>YOLO</code>, <code>CV</code>)</td>
              <td>📰 <strong>Bài báo Khoa học</strong></td>
            </tr>
            <tr>
              <td><strong>11/2024</strong></td>
              <td><strong>Giải thưởng Sinh viên Nghiên cứu Khoa học — Euréka 2024</strong></td>
              <td><em>ĐH Quốc gia TP.HCM &amp; Thành Đoàn TP.HCM</em></td>
              <td>🏆 <strong>Chứng nhận Euréka</strong></td>
            </tr>
            <tr>
              <td><strong>2024</strong></td>
              <td><strong>"Hệ thống điểm danh bằng nhận diện khuôn mặt"</strong></td>
              <td>Nghiên cứu ứng dụng <code>Python</code> + <code>FaceNet</code></td>
              <td>🥇 <strong>Đạt loại Xuất sắc</strong></td>
            </tr>
            <tr>
              <td><strong>2023</strong></td>
              <td><strong>"Hệ thống hỏi đáp tự động tư vấn tuyển sinh"</strong></td>
              <td>Nghiên cứu ứng dụng <code>NLP</code> &amp; <code>Chatbot</code></td>
              <td>🥇 <strong>Đạt loại Xuất sắc</strong></td>
            </tr>
          </tbody>
        </table>

        <!-- GITHUB ANALYTICS PREVIEW -->
        <h2>📈 GitHub Analytics (TokyoNight Theme)</h2>
        <div class="stats-grid">
          <div class="stat-card">
            <h4>📊 Le-Ngoc-Tu's GitHub Stats</h4>
            <div class="stat-item"><span>⭐ Total Stars Earned:</span><strong>Active</strong></div>
            <div class="stat-item"><span>🔄 Total Commits (All-time):</span><strong>Included (Private + Public)</strong></div>
            <div class="stat-item"><span>📦 Public &amp; AI Repos:</span><strong>LLMs · RAG · CV · TTS</strong></div>
            <div class="stat-item"><span>🏆 GitHub Theme:</span><strong>TokyoNight</strong></div>
          </div>
          <div class="stat-card">
            <h4>🔥 Most Used Languages</h4>
            <div class="lang-bar">
              <div style="width:62%;background:#3572A5;"></div>
              <div style="width:20%;background:#f1e05a;"></div>
              <div style="width:12%;background:#3178c6;"></div>
              <div style="width:6%;background:#e34c26;"></div>
            </div>
            <div class="stat-item"><span>🐍 Python (AI / FastAPI / PyTorch)</span><strong>Primary</strong></div>
            <div class="stat-item"><span>⚛️ JavaScript / TypeScript (React / Next.js)</span><strong>Full-stack</strong></div>
          </div>
        </div>

        <!-- QUOTE & FOOTER -->
        <h2>🎯 Định hướng &amp; Triết lý Làm việc</h2>
        <div class="quote-banner">
          "Không phải ai cũng có cơ hội làm lại từ đầu, nhưng ai cũng có thể bắt đầu từ hôm nay."
        </div>
        <div class="badge-row" style="margin-top:16px;">
          <span class="gh-badge"><span class="b-label" style="background:#ffcd00;color:#000;">🇻🇳 Tinh thần</span><span class="b-val" style="background:#da251d;">Việt Nam</span></span>
          <span class="gh-badge"><span class="b-label">🎯 Mục tiêu</span><span class="b-val" style="background:#10b981;">Phát triển AI/ML Thực tiễn</span></span>
          <span class="gh-badge"><span class="b-label">💪 Mindset</span><span class="b-val" style="background:#0e75b6;">Luôn tiến về phía trước</span></span>
        </div>

      </div>

      <!-- RAW CODE VIEW -->
      <div class="readme-body" id="raw-view">
        <p style="color:var(--gh-muted);margin-bottom:12px;">
          💡 Đây là mã nguồn <code>README.md</code> hoàn chỉnh (đã sửa toàn bộ lỗi cú pháp URL trong bảng và banner để hiển thị 100% trên GitHub Profile). Bạn chỉ cần nhấn nút <strong>"📋 Copy toàn bộ README.md"</strong> ở góc phải phía trên và dán vào file <code>README.md</code> trên GitHub của bạn:
        </p>
        <textarea id="raw-textarea" readonly><!-- ================= HERO HEADER BANNER ================= -->
<div align="center">
  <img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0e75b6&height=200&section=header&text=L%C3%AA%20Ng%E1%BB%8Dc%20T%C3%BA&fontSize=50&fontColor=ffffff&fontAlignY=38&desc=AI%20Engineer%20%7C%20LLM%20%C2%B7%20RAG%20%C2%B7%20Vietnamese%20NLP%20%C2%B7%20Computer%20Vision&descSize=18&descAlignY=60&animation=fadeIn" alt="Lê Ngọc Tú Header Banner" />
</div>

<!-- ================= TYPING SVG ================= -->
<div align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&pause=1000&color=38BDF8&center=true&vCenter=true&random=false&width=700&lines=Xin+ch%C3%A0o%2C+t%C3%B4i+l%C3%A0+L%C3%AA+Ng%E1%BB%8Dc+T%C3%BA+%F0%9F%91%8B;Building+Production-Ready+LLM+%26+RAG+Systems;Fine-tuning+Vietnamese+LLM%2C+Embedding+%26+TTS+Models;Computer+Vision+%26+YOLO+for+Real-World+Applications;Code+by+Day%2C+Research+by+Night" alt="Typing SVG" />
  </a>
</div>

<!-- ================= QUICK SOCIAL & CONTACT BAR ================= -->
<p align="center">
  <a href="https://lengoctu.com">
    <img src="https://img.shields.io/badge/Website-lengoctu.com-0F172A?style=for-the-badge&logo=googlechrome&logoColor=00D9FF" alt="Website" />
  </a>
  <a href="https://huggingface.co/LeNgocTu">
    <img src="https://img.shields.io/badge/HuggingFace-LeNgocTu-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" alt="HuggingFace" />
  </a>
  <a href="https://www.linkedin.com/in/le-ngoc-tu-8562a2347">
    <img src="https://img.shields.io/badge/LinkedIn-Le%20Ngoc%20Tu-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="https://github.com/Le-Ngoc-Tu">
    <img src="https://img.shields.io/badge/GitHub-Le--Ngoc--Tu-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  </a>
  <a href="mailto:lntu2003.dev@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-lntu2003.dev%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail" />
  </a>
  <a href="https://zalo.me/0969691930">
    <img src="https://img.shields.io/badge/Zalo-0969%20691%20930-0068FF?style=for-the-badge&logo=zalo&logoColor=white" alt="Zalo" />
  </a>
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=Le-Ngoc-Tu&label=Profile%20Views&color=0e75b6&style=flat-square" alt="Profile Views" />
  <a href="https://github.com/Le-Ngoc-Tu?tab=followers">
    <img src="https://img.shields.io/github/followers/Le-Ngoc-Tu?label=Followers&style=flat-square&color=0284c7" alt="GitHub Followers" />
  </a>
  <img src="https://img.shields.io/badge/📍-Phan%20Thiet%2C%20Lam%20Dong%2C%20Vietnam-success?style=flat-square" alt="Location" />
  <img src="https://img.shields.io/badge/🕐-UTC%20%2B07%3A00-blue?style=flat-square" alt="Timezone" />
</p>

---

## 👨‍💻 Giới thiệu (About Me)

<img align="right" alt="Coding" width="340" src="https://user-images.githubusercontent.com/74038190/229223263-cf2e4b07-2615-4f87-9c38-e37600f8381a.gif" />

Xin chào! Tôi là **Lê Ngọc Tú** — **AI Engineer** với niềm đam mê mạnh mẽ dành cho **AI và Machine Learning**. Tập trung vào **LLMs, RAG và Computer Vision**, đồng thời fine-tune các mô hình AI cho tiếng Việt và đưa vào các hệ thống thực tế trong môi trường doanh nghiệp và chính phủ.

- 🔭 **Công việc hiện tại:** AI Engineer tại **Công ty TNHH Giải pháp phần mềm Nguyên Luân (NLTECH)** *(12/2024 – Hiện tại)*
- 🎓 **Học vấn:** Cử nhân Công nghệ Thông tin – **Đại học Phan Thiết** *(09/2021 – 01/2025 | GPA: **3.77 / 4.0**)*
- 🤗 **Open-Source AI:** Fine-tune và công bố model trên [HuggingFace](https://huggingface.co/LeNgocTu): **TTS Việt–Nhật, LLM persona, embedding tiếng Việt**
- 💬 **Chuyên môn cốt lõi:** `Python` · `FastAPI` · `LLM/RAG` · `YOLO` · `Face Recognition`
- 🎯 **Mục tiêu:** Đóng góp giá trị thực tế thông qua AI/ML
- ⚡ **Fun fact:** *Code by day, research by night* 🌙

<br clear="both" />

```yaml
name: "Lê Ngọc Tú"
role: "AI Engineer @ NLTECH"
location: "Phan Thiết, Lâm Đồng, Việt Nam (UTC+7)"
education: "Cử nhân CNTT — Đại học Phan Thiết (09/2021 – 01/2025 | GPA: 3.77/4.0)"
research_focus:
  - "Large Language Models (LoRA Fine-tuning, Quantization GGUF, vLLM, Ollama)"
  - "Agentic RAG Pipelines (LlamaIndex, Strands Agents, Qdrant, FAISS)"
  - "Speech & Multimodal AI (Bilingual VI-JA TTS, YOLO, FaceNet)"
```

---

## 🤗 Mô hình AI Công bố trên HuggingFace (Open-Source Models)

| Mô hình | Lĩnh vực | Mô tả & Điểm nhấn kỹ thuật | Liên kết Model |
| :--- | :--- | :--- | :---: |
| **🗣️ Irodori-Sen-TTS** | `Text-to-Speech` `VI-JA` | Fine-tune mô hình Text-to-Speech tổng hợp giọng nói tiếng Việt và tiếng Nhật, hướng tới chất lượng tự nhiên. | [![HuggingFace](https://img.shields.io/badge/🤗%20HuggingFace-Irodori--Sen--TTS-FFD21E?style=flat-square&logoColor=black)](https://huggingface.co/LeNgocTu/Irodori-Sen-TTS) |
| **🧩 gemma-4-E2B Vietnam Personas** | `LLM` `GGUF` `Edge AI` | Fine-tune mô hình Gemma (E2B) với bộ persona tiếng Việt, lượng tử hóa GGUF để chạy suy luận cục bộ trên phần cứng cấu hình thấp / edge. | [![HuggingFace](https://img.shields.io/badge/🤗%20HuggingFace-gemma--4--E2B--gguf-FFD21E?style=flat-square&logoColor=black)](https://huggingface.co/LeNgocTu/gemma-4-E2B-vietnam-personas-gguf) |
| **🔎 vietnamese-embeddinggemma-300m** | `Embedding` `RAG` | Fine-tune mô hình embedding 300M (EmbeddingGemma) cho tiếng Việt, phục vụ tìm kiếm ngữ nghĩa và pipeline RAG. | [![HuggingFace](https://img.shields.io/badge/🤗%20HuggingFace-vietnamese--embedding-FFD21E?style=flat-square&logoColor=black)](https://huggingface.co/LeNgocTu/vietnamese-embeddinggemma-300m) |

---

## 🛠️ Hệ sinh thái Công nghệ (Tech Stack)

### 🤖 AI, LLMs & Computer Vision
<p align="left">
  <img src="https://img.shields.io/badge/HuggingFace-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" alt="HuggingFace" />
  <img src="https://img.shields.io/badge/LLMs-412991?style=for-the-badge&logo=openai&logoColor=white" alt="LLMs" />
  <img src="https://img.shields.io/badge/Fine--tuning_LoRA-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="Fine-tuning LoRA" />
  <img src="https://img.shields.io/badge/RAG_LlamaIndex_FAISS-4285F4?style=for-the-badge&logo=google&logoColor=white" alt="RAG" />
  <img src="https://img.shields.io/badge/Strands_Agents-6366F1?style=for-the-badge&logo=openai&logoColor=white" alt="Strands Agents" />
  <img src="https://img.shields.io/badge/Embedding-5C3EE8?style=for-the-badge&logo=databricks&logoColor=white" alt="Embedding" />
  <img src="https://img.shields.io/badge/TTS_%26_STT-FF9900?style=for-the-badge&logo=amazon&logoColor=white" alt="TTS STT" />
  <img src="https://img.shields.io/badge/YOLO-00FFFF?style=for-the-badge&logo=yolo&logoColor=black" alt="YOLO" />
  <img src="https://img.shields.io/badge/FaceNet-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" alt="FaceNet" />
  <img src="https://img.shields.io/badge/Computer_Vision-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" alt="Computer Vision" />
</p>

### ⚡ AI Serving, Inference & APIs
<p align="left">
  <img src="https://img.shields.io/badge/vLLM-FDBA12?style=for-the-badge&logoColor=black" alt="vLLM" />
  <img src="https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white" alt="Ollama" />
  <img src="https://img.shields.io/badge/Groq-F55036?style=for-the-badge&logo=groq&logoColor=white" alt="Groq" />
  <img src="https://img.shields.io/badge/OpenAI_API-412991?style=for-the-badge&logo=openai&logoColor=white" alt="OpenAI API" />
  <img src="https://img.shields.io/badge/Gemini_API-8E75B2?style=for-the-badge&logo=google&logoColor=white" alt="Gemini API" />
  <img src="https://img.shields.io/badge/Uvicorn-499848?style=for-the-badge&logo=gunicorn&logoColor=white" alt="Uvicorn" />
  <img src="https://img.shields.io/badge/REST_API-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="REST API" />
</p>

### 💻 Backend, Frontend, Database & DevOps
<p align="left">
  <img src="https://skillicons.dev/icons?i=python,fastapi,nodejs,express,react,nextjs,postgres,mysql,mariadb,docker,linux,nginx,git,github,githubactions" alt="Tech Stack Icons" />
</p>
<p align="left">
  <img src="https://img.shields.io/badge/Qdrant_Vector_DB-DC244C?style=for-the-badge&logo=qdrant&logoColor=white" alt="Qdrant" />
</p>

---

## 💼 Kinh nghiệm làm việc (Work Experience)

### 🏢 AI Engineer – Công ty TNHH Giải pháp phần mềm Nguyên Luân (NLTECH)
**📅 12/2024 – Hiện tại** | 📍 **Phan Thiết, Lâm Đồng, Việt Nam**

- 🔬 Nghiên cứu, fine-tune và huấn luyện các mô hình AI cho tiếng Việt *(embedding, LLM persona, TTS)*; công bố mô hình trên HuggingFace
- 🧠 Xây dựng pipeline RAG & LLM (`LlamaIndex`, `Qdrant`, `FAISS`) để tự động hóa truy xuất thông tin và sinh câu trả lời
- 👁️ Phát triển tính năng thị giác máy tính *(nhận diện khuôn mặt, phát hiện đối tượng)* và tích hợp vào backend đưa vào sản xuất
- 🚀 Triển khai giải pháp AI end-to-end cho khách hàng doanh nghiệp và đơn vị chính phủ

---

## 🚀 Dự án Tiêu biểu (Featured Systems & Projects)

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>🏛️ Kiosk AI Hỗ trợ Thủ tục Hành chính (AAAS Chatbot)</h3>
      <p>🎯 Chatbot AI đa agent trên kiosk, hỗ trợ tra cứu thủ tục hành chính bằng giọng nói kết hợp RAG.</p>
      <p>
        <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" />
        <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" />
        <img src="https://img.shields.io/badge/LlamaIndex-000000?style=flat-square&logo=meta&logoColor=white" />
        <img src="https://img.shields.io/badge/Qdrant-DC244C?style=flat-square&logo=qdrant&logoColor=white" />
        <img src="https://img.shields.io/badge/OmniVoice_TTS-FF9900?style=flat-square&logo=amazon&logoColor=white" />
        <img src="https://img.shields.io/badge/LLMs-412991?style=flat-square&logo=openai&logoColor=white" />
      </p>
    </td>
    <td width="50%" valign="top">
      <h3>🎧 Hệ thống AI Hỗ trợ Học tập Tiếng Anh (IELTS)</h3>
      <p>📝 Hệ thống luyện thi IELTS với 4 kỹ năng Writing, Speaking, Reading, Listening; agentic workflow kết hợp RAG, phản hồi cá nhân hóa và chấm điểm.</p>
      <p>
        <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" />
        <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" />
        <img src="https://img.shields.io/badge/Strands_Agents-412991?style=flat-square&logo=openai&logoColor=white" />
        <img src="https://img.shields.io/badge/Qdrant-DC244C?style=flat-square&logo=qdrant&logoColor=white" />
        <img src="https://img.shields.io/badge/Groq-F55036?style=flat-square&logo=groq&logoColor=white" />
        <img src="https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white" />
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top">
      <h3>📄 PDF Translation Tool – Công cụ Dịch thuật PDF Giữ nguyên Bố cục</h3>
      <p>🌍 Công cụ dịch tài liệu PDF thông minh, giữ nguyên bố cục, hỗ trợ xử lý hàng loạt tài liệu lớn.</p>
      <p>
        <img src="https://img.shields.io/badge/PyMuPDF-3776AB?style=flat-square&logo=python&logoColor=white" />
        <img src="https://img.shields.io/badge/OpenAI_API-412991?style=flat-square&logo=openai&logoColor=white" />
        <img src="https://img.shields.io/badge/Gemini_API-8E75B2?style=flat-square&logo=google&logoColor=white" />
        <img src="https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white" />
      </p>
      <p align="center">
        <img src="https://raw.githubusercontent.com/Le-Ngoc-Tu/Le-Ngoc-Tu/main/pdftranslate1.png" width="48%" alt="PDF Translate Screenshot 1" />
        <img src="https://raw.githubusercontent.com/Le-Ngoc-Tu/Le-Ngoc-Tu/main/pdftranslate2.png" width="48%" alt="PDF Translate Screenshot 2" />
      </p>
    </td>
  </tr>
</table>

---

## 📚 Nghiên cứu Khoa học & Giải thưởng (Research & Awards)

| 📅 Năm | 📝 Công trình Nghiên cứu / Giải thưởng | 🏫 Đơn vị / Công nghệ | 🏆 Kết quả |
| :---: | :--- | :--- | :---: |
| **2025** | **"Exam Fraud Detection Using YOLO Model"** | *Tạp chí Nhà giáo Việt Nam* (`YOLO`) | 📰 **Bài báo Khoa học** |
| **11/2024** | **Giải thưởng Sinh viên Nghiên cứu Khoa học Euréka 2024** | *ĐH Quốc gia TP.HCM & Thành Đoàn TP.HCM* | 🏆 **Chứng nhận Euréka** |
| **2024** | **"Hệ thống điểm danh bằng nhận diện khuôn mặt"** | `Python` + `FaceNet` | 🥇 **Xuất sắc** |
| **2023** | **"Hệ thống hỏi đáp tự động tư vấn tuyển sinh"** | `NLP` & `Chatbot` | 🥇 **Xuất sắc** |

---

## 📈 GitHub Analytics

<div align="center">
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=Le-Ngoc-Tu&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&include_all_commits=true&cache_seconds=1800" alt="GitHub Stats" />
  <img height="165" src="https://streak-stats.demolab.com/?user=Le-Ngoc-Tu&theme=tokyonight&hide_border=true&date_format=M%20j%5B%2C%20Y%5D" alt="GitHub Streak" />
</div>

<div align="center">
  <img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Le-Ngoc-Tu&layout=compact&theme=tokyonight&hide_border=true&langs_count=8&cache_seconds=1800" alt="Top Languages" />
</div>

---

## 💬 Trích dẫn & Mục tiêu

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=rect&color=DA251D&height=60&text=%22Kh%C3%B4ng%20ph%E1%BA%A3i%20ai%20c%C5%A9ng%20c%C3%B3%20c%C6%A1%20h%E1%BB%99i%20l%C3%A0m%20l%E1%BA%A1i%20t%E1%BB%AB%20%C4%91%E1%BA%A7u%2C%20nh%C6%B0ng%20ai%20c%C5%A9ng%20c%C3%B3%20th%E1%BB%83%20b%E1%BA%AFt%20%C4%91%E1%BA%A7u%20t%E1%BB%AB%20h%C3%B4m%20nay.%22&fontColor=FFCD00&fontSize=18&fontAlign=50&fontAlignY=50" alt="Quote" />
</div>

<p align="center">
  <img src="https://img.shields.io/badge/🇻🇳_Tinh_thần-Việt_Nam-DA251D?style=for-the-badge&labelColor=FFCD00" alt="Tinh thần Việt Nam" />
  <img src="https://img.shields.io/badge/✅-Phát_triển_AI%2FML_Thực_tiễn-28a745?style=for-the-badge" alt="Phát triển AI/ML" />
  <img src="https://img.shields.io/badge/💪_Mindset-Luôn_tiến_về_phía_trước-0e75b6?style=for-the-badge" alt="Mindset" />
</p>

<!-- ================= FOOTER WAVE ================= -->
<div align="center">
  <img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0e75b6&height=110&section=footer&text=Let's%20Build%20Something%20Amazing%20Together!%20%F0%9F%9A%80&fontSize=20&fontColor=ffffff&fontAlignY=65" alt="Footer Banner" />
</div>

<!-- SEO Keywords (Hidden) -->
<!--
Keywords: Lê Ngọc Tú, Le Ngoc Tu, AI Engineer Vietnam, Machine Learning Engineer, LLM Engineer,
RAG Systems, Fine-tuning LLM, Vietnamese NLP, Vietnamese Embedding Model, Text-to-Speech Vietnamese,
Face Recognition Developer, Computer Vision Vietnam, YOLO Developer, Python Developer, FastAPI Developer,
HuggingFace, EmbeddingGemma, Gemma Fine-tuning, Qdrant, FAISS, LlamaIndex, Ollama, vLLM,
Đại học Phan Thiết, Vietnamese Software Engineer, AI Research Vietnam, NLTECH, Nguyen Luan Company,
Phan Thiet Developer, Lam Dong IT, Vietnam Tech, AI Engineer Vietnam
--></textarea>
      </div>

    </div>
  </div>

  <script>
    const phrases = [
      "Xin chào, tôi là Lê Ngọc Tú 👋",
      "Building Production-Ready LLM & RAG Systems 🚀",
      "Fine-tuning Vietnamese LLM, Embedding & TTS Models 🤗",
      "Computer Vision & YOLO for Enterprise & Government 👁️",
      "Code by Day, Research by Night 🌙"
    ];
    let pIndex = 0;
    let cIndex = 0;
    let deleting = false;
    const typedEl = document.getElementById("typed-text");

    function typeLoop() {
      const current = phrases[pIndex];
      if (!deleting) {
        typedEl.textContent = current.substring(0, cIndex + 1);
        cIndex++;
        if (cIndex === current.length) {
          deleting = true;
          setTimeout(typeLoop, 1800);
          return;
        }
        setTimeout(typeLoop, 45);
      } else {
        typedEl.textContent = current.substring(0, cIndex - 1);
        cIndex--;
        if (cIndex === 0) {
          deleting = false;
          pIndex = (pIndex + 1) % phrases.length;
          setTimeout(typeLoop, 300);
          return;
        }
        setTimeout(typeLoop, 25);
      }
    }
    setTimeout(typeLoop, 1200);

    function switchTab(tab) {
      const previewView = document.getElementById("preview-view");
      const rawView = document.getElementById("raw-view");
      const btnPreview = document.getElementById("btn-preview");
      const btnRaw = document.getElementById("btn-raw");
      if (tab === "preview") {
        previewView.style.display = "block";
        rawView.style.display = "none";
        btnPreview.classList.add("active");
        btnRaw.classList.remove("active");
      } else {
        previewView.style.display = "none";
        rawView.style.display = "block";
        btnRaw.classList.add("active");
        btnPreview.classList.remove("active");
      }
    }

    function copyMarkdown() {
      const textarea = document.getElementById("raw-textarea");
      navigator.clipboard.writeText(textarea.value).then(() => {
        const btn = document.getElementById("copy-btn");
        btn.textContent = "✅ Đã Copy thành công!";
        setTimeout(() => {
          btn.textContent = "📋 Copy toàn bộ README.md";
        }, 2200);
      });
    }
  </script>
</body>
</html>
