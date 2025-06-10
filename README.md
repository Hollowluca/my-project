# my-project
test
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Luca's Multi-Theme Space</title>
    <style>
        /* 基础样式 */
        :root {
            --primary-color: #4a6fa5;
            --secondary-color: #6b8cae;
            --accent-color: #ff7e5f;
            --bg-color: #f8f9fa;
            --text-color: #2d3748;
            --container-bg: white;
            --border-color: #ddd;
            --shadow-color: rgba(0, 0, 0, 0.1);
            --game-card-bg: white;
            --game-card-border: #ddd;
            --header-border: #4a6fa5;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            color: var(--text-color);
            line-height: 1.6;
            overflow-x: hidden;
            position: relative;
            min-height: 100vh;
            background-color: var(--bg-color);
            transition: all 0.5s ease;
        }

        /* 加载动画 */
        .loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: var(--bg-color);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }
        
        .loader-content {
            text-align: center;
        }
        
        .loader-spinner {
            border: 5px solid var(--secondary-color);
            border-top: 5px solid var(--primary-color);
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 0 auto 20px;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* 主题切换按钮 */
        .settings-btn {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--primary-color);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            font-size: 20px;
            cursor: pointer;
            z-index: 100;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
        }

        .settings-btn:hover {
            transform: rotate(30deg) scale(1.1);
        }

        .theme-selector {
            position: fixed;
            top: 70px;
            right: 20px;
            background: var(--container-bg);
            border-radius: 8px;
            padding: 15px;
            box-shadow: 0 5px 15px var(--shadow-color);
            z-index: 99;
            width: 200px;
            display: none;
            border: 1px solid var(--border-color);
            opacity: 0;
            transform: translateY(-10px);
            transition: opacity 0.3s ease, transform 0.3s ease;
        }

        .theme-selector.show {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

        .theme-selector h3 {
            margin-top: 0;
            margin-bottom: 10px;
            color: var(--primary-color);
        }

        .theme-option {
            display: block;
            width: 100%;
            padding: 8px;
            margin-bottom: 5px;
            border: none;
            border-radius: 4px;
            background-color: var(--secondary-color);
            color: white;
            cursor: pointer;
            text-align: left;
            transition: all 0.2s ease;
        }

        .theme-option:hover {
            opacity: 0.9;
            transform: translateX(-3px);
        }

        /* 主容器样式 */
        .container {
            max-width: 900px;
            margin: 2rem auto;
            background-color: var(--container-bg);
            padding: 2rem;
            border-radius: 12px;
            box-shadow: 0 10px 30px var(--shadow-color);
            position: relative;
            border: 1px solid var(--border-color);
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.5s ease, transform 0.5s ease;
        }
        
        .container.show {
            opacity: 1;
            transform: translateY(0);
        }
        
        header {
            text-align: center;
            margin-bottom: 2rem;
            padding-bottom: 1rem;
            border-bottom: 2px solid var(--header-border);
        }
        
        h1 {
            color: var(--primary-color);
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            font-weight: 700;
        }
        
        h3 {
            color: var(--secondary-color);
            font-weight: 400;
            font-size: 1.3rem;
        }
        
        .hr-custom {
            border: 0;
            height: 1px;
            background-image: linear-gradient(to right, rgba(0, 0, 0, 0), var(--primary-color), rgba(0, 0, 0, 0));
            margin: 1.5rem 0;
        }
        
        /* 游戏卡片样式 */
        .game-container {
            display: grid;
            grid-template-columns: 1fr;
            gap: 2rem;
            margin-top: 2rem;
        }
        
        .game-card {
            background: var(--game-card-bg);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px var(--shadow-color);
            transition: all 0.3s ease;
            border: 1px solid var(--game-card-border);
        }
        
        .game-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px var(--shadow-color);
        }
        
        .game-iframe {
            width: 100%;
            height: 400px;
            border: none;
        }
        
        .game-info {
            padding: 1.2rem;
            background-color: rgba(0, 0, 0, 0.03);
        }
        
        .game-title {
            color: var(--primary-color);
            margin: 0 0 0.5rem 0;
            font-size: 1.2rem;
        }
        
        /* Bilibili跳转按钮 */
        .bilibili-link {
            display: inline-block;
            padding: 10px 20px;
            background-color: #fb7299;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            margin: 10px 0;
            transition: all 0.3s ease;
        }

        .bilibili-link:hover {
            background-color: #ff9db5;
            transform: scale(1.05);
        }

        /* 画板样式 */
        .drawing-container {
            margin: 2rem 0;
            padding: 1.5rem;
            background-color: var(--container-bg);
            border-radius: 10px;
            box-shadow: 0 5px 15px var(--shadow-color);
            border: 1px solid var(--border-color);
        }
        
        .drawing-title {
            color: var(--primary-color);
            margin-top: 0;
            margin-bottom: 1rem;
        }
        
        .drawing-tools {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            flex-wrap: wrap;
        }
        
        .drawing-tool {
            padding: 5px 10px;
            background-color: var(--secondary-color);
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s ease;
        }
        
        .drawing-tool:hover {
            background-color: var(--primary-color);
        }
        
        .drawing-tool.active {
            background-color: var(--accent-color);
        }
        
        .color-picker {
            width: 30px;
            height: 30px;
            border: none;
            cursor: pointer;
            vertical-align: middle;
        }
        
        .brush-size {
            width: 60px;
            padding: 5px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
        }
        
        .drawing-canvas {
            width: 100%;
            height: 400px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            background-color: white;
            cursor: crosshair;
            touch-action: none;
        }
        
        /* 微信号样式 */
        .wechat-info {
            text-align: center;
            margin: 2rem 0;
            padding: 1rem;
            background-color: rgba(74, 111, 165, 0.1);
            border-radius: 8px;
            border-left: 4px solid var(--primary-color);
        }
        
        .wechat-id {
            font-weight: bold;
            color: var(--primary-color);
            font-size: 1.2rem;
        }

       {
            transform: scale(1.1) rotate(10deg);
        }

        /* 页脚样式 */
        footer {
            text-align: center;
            margin-top: 3rem;
            color: var(--secondary-color);
            font-size: 0.9rem;
            padding: 1rem;
            border-top: 1px solid var(--border-color);
        }

        /* 响应式设计 */
        @media (max-width: 768px) {
            .container {
                margin: 1rem;
                padding: 1.5rem;
            }
            
            .game-iframe, .drawing-canvas {
                height: 300px;
            }
            
            .theme-selector {
                width: 180px;
                right: 10px;
            }
        }
    </style>
</head>
<body>
    <!-- 加载动画 -->
    <div class="loader">
        <div class="loader-content">
            <div class="loader-spinner"></div>
            <p>加载中...</p>
        </div>
    </div>

    <!-- 设置按钮 -->
    <button class="settings-btn">⚙️</button>
    <div class="theme-selector">
        <h3>选择主题</h3>
        <button class="theme-option" data-theme="default">默认主题</button>
        <button class="theme-option" data-theme="hacker">黑客主题</button>
        <button class="theme-option" data-theme="nature">大自然主题</button>
        <button class="theme-option" data-theme="win95">Windows 95</button>
        <button class="theme-option" data-theme="backrooms">后室主题</button>
        <button class="theme-option" data-theme="minecraft">我的世界</button>
        <button class="theme-option" data-theme="cyberpunk">赛博朋克</button>
    </div>

    <!-- Scratch吉祥物 -->
    <img src="https://scratch.mit.edu/images/scratch-cat.png" alt="Scratch Cat" class="scratch-cat">

    <div class="container">
        <header>
            <h1>LUCA'S MULTI-THEME SPACE</h1>
            <h3>点击右上角齿轮切换主题风格</h3>
            <div class="hr-custom"></div>
        </header>

        <!-- 微信号信息 -->
        <div class="wechat-info">
            <h3>我的微信号</h3>
            <p class="wechat-id">luca5418114514</p>
            <p>欢迎添加我的微信交流！</p>
        </div>

        <div class="game-container">
            <div class="game-card">
                <iframe class="game-iframe"
                    src="https://www.ccw.site/embed?id=64df5b3a5304406de77813ee&type=player"
                    title="方块跑酷[双人]"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                    allowfullscreen>
                </iframe>
                <div class="game-info">
                    <h3 class="game-title">方块跑酷[双人]</h3>
                    <p>和朋友一起挑战这个有趣的跑酷游戏！</p>
                </div>
            </div>
            
            <div class="game-card">
                <iframe class="game-iframe"
                    src="https://www.ccw.site/embed?id=667fca218994b73608d05168&type=player"
                    title="SECUREGAME[电脑病毒游戏]"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                    allowfullscreen>
                </iframe>
                <div class="game-info">
                    <h3 class="game-title">SECUREGAME[电脑病毒游戏]</h3>
                    <p>体验刺激的电脑病毒防御游戏！</p>
                </div>
            </div>
            
            <div class="game-card">
                <iframe class="game-iframe"
                    src="https://www.ccw.site/embed?id=65c486434149ae5cb087d873&type=player"
                    title="作业の战争【MMO】"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                    allowfullscreen>
                </iframe>
                <div class="game-info">
                    <h3 class="game-title">作业の战争【MMO】</h3>
                    <p>在作业的海洋中战斗吧！</p>
                </div>
            </div>
            
            <div class="game-card">
                <iframe class="game-iframe"
                    src="https://www.ccw.site/embed?id=65afb03b9e4c3a63338ea760&type=player"
                    title="[WGJ]破晓之车"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                    allowfullscreen>
                </iframe>
                <div class="game-info">
                    <h3 class="game-title">[WGJ]破晓之车</h3>
                    <p>驾驶战车迎接破晓的挑战！</p>
                </div>
            </div>
            
            <div class="game-card">
                <div class="game-info" style="text-align: center;">
                    <h3 class="game-title">我的Bilibili主页</h3>
                    <p>欢迎访问我的Bilibili频道，查看更多内容！</p>
                    <a href="https://space.bilibili.com/1890138609?spm_id_from=333.337.0.0" class="bilibili-link" target="_blank">前往Bilibili主页</a>
                </div>
            </div>
        </div>
        
        <!-- 画板功能 -->
        <div class="drawing-container">
            <h3 class="drawing-title">创意画板</h3>
            <div class="drawing-tools">
                <button class="drawing-tool active" data-tool="brush">画笔</button>
                <button class="drawing-tool" data-tool="eraser">橡皮擦</button>
                <input type="color" class="color-picker" value="#000000" title="选择颜色">
                <select class="brush-size" title="画笔大小">
                    <option value="1">1px</option>
                    <option value="3" selected>3px</option>
                    <option value="5">5px</option>
                    <option value="10">10px</option>
                    <option value="15">15px</option>
                </select>
                <button class="drawing-tool" data-tool="clear">清空画布</button>
                <button class="drawing-tool" data-tool="save">保存图片</button>
            </div>
            <canvas class="drawing-canvas"></canvas>
        </div>
        
        <footer>
            <p>© 2023 Luca's Multi-Theme Space. All rights reserved.</p>
        </footer>
    </div>

    <script>
        // 等待页面加载完成
        window.addEventListener('DOMContentLoaded', () => {
            // 隐藏加载动画，显示内容
            setTimeout(() => {
                document.querySelector('.loader').style.opacity = '0';
                document.querySelector('.container').classList.add('show');
                
                setTimeout(() => {
                    document.querySelector('.loader').style.display = 'none';
                }, 500);
            }, 1000);
            
            // 主题切换功能
            const settingsBtn = document.querySelector('.settings-btn');
            const themeSelector = document.querySelector('.theme-selector');
            
            settingsBtn.addEventListener('click', (e) => {
                e.stopPropagation();
                themeSelector.classList.toggle('show');
            });
            
            // 关闭主题选择器当点击外部
            document.addEventListener('click', (e) => {
                if (!themeSelector.contains(e.target) && e.target !== settingsBtn) {
                    themeSelector.classList.remove('show');
                }
            });
            
            // 主题定义
            const themes = {
                default: {
                    '--primary-color': '#4a6fa5',
                    '--secondary-color': '#6b8cae',
                    '--accent-color': '#ff7e5f',
                    '--bg-color': '#f8f9fa',
                    '--text-color': '#2d3748',
                    '--container-bg': 'white',
                    '--border-color': '#ddd',
                    '--shadow-color': 'rgba(0, 0, 0, 0.1)',
                    '--game-card-bg': 'white',
                    '--game-card-border': '#ddd',
                    '--header-border': '#4a6fa5',
                    'font-family': '"Segoe UI", Tahoma, Geneva, Verdana, sans-serif'
                },
                hacker: {
                    '--primary-color': '#00ff41',
                    '--secondary-color': '#008f11',
                    '--accent-color': '#00bfff',
                    '--bg-color': '#0a0a0a',
                    '--text-color': '#e0e0e0',
                    '--container-bg': 'rgba(10, 10, 10, 0.8)',
                    '--border-color': '#00ff41',
                    '--shadow-color': 'rgba(0, 255, 65, 0.1)',
                    '--game-card-bg': 'rgba(20, 20, 20, 0.7)',
                    '--game-card-border': '#008f11',
                    '--header-border': '#00ff41',
                    'font-family': '"Courier New", monospace'
                },
                nature: {
                    '--primary-color': '#2e8b57',
                    '--secondary-color': '#3cb371',
                    '--accent-color': '#ffa07a',
                    '--bg-color': '#f5fffa',
                    '--text-color': '#2f4f4f',
                    '--container-bg': 'rgba(255, 255, 255, 0.9)',
                    '--border-color': '#98fb98',
                    '--shadow-color': 'rgba(46, 139, 87, 0.1)',
                    '--game-card-bg': 'rgba(255, 255, 255, 0.8)',
                    '--game-card-border': '#98fb98',
                    '--header-border': '#2e8b57',
                    'font-family': '"Arial", sans-serif'
                },
                win95: {
                    '--primary-color': '#000080',
                    '--secondary-color': '#808080',
                    '--accent-color': '#ff0000',
                    '--bg-color': '#008080',
                    '--text-color': '#000000',
                    '--container-bg': '#c0c0c0',
                    '--border-color': '#808080',
                    '--shadow-color': 'rgba(0, 0, 0, 0.3)',
                    '--game-card-bg': '#ffffff',
                    '--game-card-border': '#000000',
                    '--header-border': '#000080',
                    'font-family': '"MS Sans Serif", sans-serif'
                },
                backrooms: {
                    '--primary-color': '#ffff00',
                    '--secondary-color': '#cccc00',
                    '--accent-color': '#ff5555',
                    '--bg-color': '#eeeeee',
                    '--text-color': '#333333',
                    '--container-bg': 'rgba(255, 255, 255, 0.7)',
                    '--border-color': '#ffff00',
                    '--shadow-color': 'rgba(255, 255, 0, 0.2)',
                    '--game-card-bg': 'rgba(255, 255, 255, 0.8)',
                    '--game-card-border': '#ffff00',
                    '--header-border': '#ffff00',
                    'font-family': '"Arial", sans-serif'
                },
                minecraft: {
                    '--primary-color': '#55ff55',
                    '--secondary-color': '#00aa00',
                    '--accent-color': '#ffaa00',
                    '--bg-color': '#7a7a7a',
                    '--text-color': '#ffffff',
                    '--container-bg': '#4a4a4a',
                    '--border-color': '#55ff55',
                    '--shadow-color': 'rgba(0, 0, 0, 0.5)',
                    '--game-card-bg': '#5a5a5a',
                    '--game-card-border': '#00aa00',
                    '--header-border': '#55ff55',
                    'font-family': '"Minecraft", sans-serif'
                },
                cyberpunk: {
                    '--primary-color': '#ff00ff',
                    '--secondary-color': '#00ffff',
                    '--accent-color': '#ffff00',
                    '--bg-color': '#1a1a2e',
                    '--text-color': '#ffffff',
                    '--container-bg': 'rgba(26, 26, 46, 0.8)',
                    '--border-color': '#ff00ff',
                    '--shadow-color': 'rgba(255, 0, 255, 0.2)',
                    '--game-card-bg': 'rgba(46, 26, 71, 0.7)',
                    '--game-card-border': '#00ffff',
                    '--header-border': '#ff00ff',
                    'font-family': '"Courier New", monospace'
                }
            };
            
            // 检查本地存储中的主题设置
            const savedTheme = localStorage.getItem('selectedTheme') || 'default';
            applyTheme(savedTheme);
            
            // 应用主题
            function applyTheme(themeName) {
                const theme = themes[themeName];
                
                for (const property in theme) {
                    document.documentElement.style.setProperty(property, theme[property]);
                }
                
                // 保存主题选择
                localStorage.setItem('selectedTheme', themeName);
                
                // 特殊处理：如果是黑客主题，添加矩阵效果
                if (themeName === 'hacker') {
                    initMatrixEffect();
                } else {
                    const matrixCanvas = document.getElementById('matrix');
                    if (matrixCanvas) {
                        matrixCanvas.remove();
                    }
                }
            }
            
            // 主题选项点击事件
            document.querySelectorAll('.theme-option').forEach(option => {
                option.addEventListener('click', () => {
                    const themeName = option.getAttribute('data-theme');
                    applyTheme(themeName);
                    themeSelector.classList.remove('show');
                });
            });
            
            // 黑客主题的矩阵效果
            function initMatrixEffect() {
                const existingCanvas = document.getElementById('matrix');
                if (existingCanvas) return;
                
                const canvas = document.createElement('canvas');
                canvas.id = 'matrix';
                canvas.style.position = 'fixed';
                canvas.style.top = '0';
                canvas.style.left = '0';
                canvas.style.zIndex = '-1';
                document.body.prepend(canvas);
                
                const ctx = canvas.getContext('2d');
                canvas.width = window.innerWidth;
                canvas.height = window.innerHeight;
                
                const katakana = '1234567890';
                const latin = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
                const nums = '0123456789';
                const alphabet = katakana + latin + nums;
                
                const fontSize = 16;
                const columns = canvas.width / fontSize;
                const rainDrops = [];
                
                for (let x = 0; x < columns; x++) {
                    rainDrops[x] = 1;
                }
                
                const draw = () => {
                    ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
                    ctx.fillRect(0, 0, canvas.width, canvas.height);
                    
                    ctx.fillStyle = 'rgba(0, 255, 65, 0.8)';
                    ctx.font = fontSize + 'px monospace';
                    
                    for (let i = 0; i < rainDrops.length; i++) {
                        const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length));
                        ctx.fillText(text, i * fontSize, rainDrops[i] * fontSize);
                        
                        if (rainDrops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                            rainDrops[i] = 0;
                        }
                        rainDrops[i]++;
                    }
                };
                
                setInterval(draw, 30);
                
                window.addEventListener('resize', () => {
                    canvas.width = window.innerWidth;
                    canvas.height = window.innerHeight;
                });
            }
            
            // 画板功能实现
            const canvas = document.querySelector('.drawing-canvas');
            const ctx = canvas.getContext('2d');
            const colorPicker = document.querySelector('.color-picker');
            const brushSize = document.querySelector('.brush-size');
            const tools = document.querySelectorAll('.drawing-tool[data-tool]');
            
            // 设置画布大小
            function resizeCanvas() {
                const container = canvas.parentElement;
                canvas.width = container.clientWidth;
                canvas.height = 400; // 固定高度
                
                // 设置初始画布背景为白色
                ctx.fillStyle = 'white';
                ctx.fillRect(0, 0, canvas.width, canvas.height);
            }
            
            resizeCanvas();
            window.addEventListener('resize', resizeCanvas);
            
            // 绘画状态变量
            let isDrawing = false;
            let currentTool = 'brush';
            let currentColor = '#000000';
            let currentSize = 3;
            
            // 工具按钮点击事件
            tools.forEach(tool => {
                tool.addEventListener('click', () => {
                    const toolName = tool.getAttribute('data-tool');
                    
                    // 更新当前工具
                    if (toolName === 'brush' || toolName === 'eraser') {
                        currentTool = toolName;
                        tools.forEach(t => t.classList.remove('active'));
                        tool.classList.add('active');
                    } else if (toolName === 'clear') {
                        // 清空画布
                        ctx.fillStyle = 'white';
                        ctx.fillRect(0, 0, canvas.width, canvas.height);
                    } else if (toolName === 'save') {
                        // 保存画布为图片
                        saveCanvasAsImage();
                    }
                });
            });
            
            // 颜色选择器事件
            colorPicker.addEventListener('input', (e) => {
                currentColor = e.target.value;
            });
            
            // 画笔大小选择事件
            brushSize.addEventListener('change', (e) => {
                currentSize = parseInt(e.target.value);
            });
            
            // 保存画布为图片
            function saveCanvasAsImage() {
                const link = document.createElement('a');
                link.download = 'lucas-drawing-' + new Date().toISOString().slice(0, 10) + '.png';
                link.href = canvas.toDataURL('image/png');
                link.click();
            }
            
            // 鼠标/触摸事件处理
            function startDrawing(e) {
                isDrawing = true;
                draw(e);
            }
            
            function stopDrawing() {
                isDrawing = false;
                ctx.beginPath();
            }
            
            function draw(e) {
                if (!isDrawing) return;
                
                ctx.lineWidth = currentSize;
                ctx.lineCap = 'round';
                ctx.lineJoin = 'round';
                
                // 获取坐标
                let x, y;
                if (e.type.includes('touch')) {
                    const rect = canvas.getBoundingClientRect();
                    x = e.touches[0].clientX - rect.left;
                    y = e.touches[0].clientY - rect.top;
                } else {
                    x = e.offsetX;
                    y = e.offsetY;
                }
                
                // 根据工具设置样式
                if (currentTool === 'brush') {
                    ctx.strokeStyle = currentColor;
                    ctx.globalCompositeOperation = 'source-over';
                } else if (currentTool === 'eraser') {
                    ctx.strokeStyle = 'white';
                    ctx.globalCompositeOperation = 'destination-out';
                }
                
                // 绘制
                ctx.lineTo(x, y);
                ctx.stroke();
                ctx.beginPath();
                ctx.moveTo(x, y);
            }
            
            // 鼠标事件监听
            canvas.addEventListener('mousedown', startDrawing);
            canvas.addEventListener('mousemove', draw);
            canvas.addEventListener('mouseup', stopDrawing);
            canvas.addEventListener('mouseout', stopDrawing);
            
            // 触摸事件监听
            canvas.addEventListener('touchstart', (e) => {
                e.preventDefault();
                startDrawing(e);
            });
            
            canvas.addEventListener('touchmove', (e) => {
                e.preventDefault();
                draw(e);
            });
            
            canvas.addEventListener('touchend', (e) => {
                e.preventDefault();
                stopDrawing();
            });
        });
    </script>
</body>
</html>
