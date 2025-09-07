<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>美髮經營課程</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;800&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6;
            padding: 1rem;
        }
        @media (min-width: 640px) {
            body {
                padding: 2rem;
            }
        }
        .container {
            max-width: 64rem;
            margin: auto;
            background-color: white;
            border-radius: 1.5rem;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            padding: 1.5rem;
            border-width: 4px;
            border-color: #a855f7;
        }
        @media (min-width: 640px) {
            .container {
                padding: 2.5rem;
            }
        }
        .text-center {
            text-align: center;
        }
        .title {
            font-size: 2.25rem;
            line-height: 2.5rem;
            font-weight: 800;
            background-image: linear-gradient(to right, #9333ea, #ec4899);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 0.5rem;
        }
        @media (min-width: 640px) {
            .title {
                font-size: 3rem;
                line-height: 1;
            }
        }
        .subtitle {
            color: #6b7280;
            font-size: 0.875rem;
            line-height: 1.25rem;
        }
        @media (min-width: 640px) {
            .subtitle {
                font-size: 1rem;
                line-height: 1.5rem;
            }
        }
        .grid-container {
            display: grid;
            gap: 1rem;
            margin-bottom: 2rem;
            text-align: center;
        }
        @media (min-width: 640px) {
            .grid-container {
                grid-template-columns: repeat(3, minmax(0, 1fr));
            }
        }
        .data-card {
            background-color: #f3e8ff;
            border-radius: 0.75rem;
            padding: 1rem;
            box-shadow: inset 0 2px 4px 0 rgba(0, 0, 0, 0.06);
        }
        .data-label {
            color: #6b7280;
            font-size: 0.875rem;
            line-height: 1.25rem;
        }
        .data-value {
            font-size: 1.5rem;
            line-height: 2rem;
            font-weight: 700;
            color: #7e22ce;
            margin-top: 0.25rem;
        }
        .progress-bar {
            position: relative;
            padding-top: 0.25rem;
            margin-top: 0.5rem;
        }
        .progress-bar-bg {
            overflow: hidden;
            height: 1rem;
            margin-bottom: 1rem;
            font-size: 0.75rem;
            display: flex;
            border-radius: 9999px;
            background-color: #e9d5ff;
        }
        .progress-bar-inner {
            box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
            display: flex;
            flex-direction: column;
            text-align: center;
            white-space: nowrap;
            color: white;
            justify-content: center;
            background-image: linear-gradient(to right, #9333ea, #ec4899);
            border-radius: 9999px;
            transition: width 0.5s ease-in-out;
        }
        .modules-container {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }
        .module-card {
            padding: 1.5rem;
            border-radius: 1.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            border-width: 2px;
            transition: transform 0.2s, box-shadow 0.2s;
            cursor: pointer;
        }
        .module-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        .module-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 0.5rem;
        }
        .module-title {
            font-size: 1.125rem;
            line-height: 1.75rem;
            font-weight: 700;
        }
        @media (min-width: 640px) {
            .module-title {
                font-size: 1.25rem;
                line-height: 1.75rem;
            }
        }
        .module-subtitle {
            font-size: 0.875rem;
            line-height: 1.25rem;
            font-style: italic;
            margin-bottom: 1rem;
        }
        .module-content {
            font-size: 0.875rem;
            line-height: 1.25rem;
        }
        .module-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 1rem;
        }
        .module-points {
            font-size: 0.875rem;
            line-height: 1.25rem;
            font-weight: 600;
        }
        .module-button {
            padding: 0.5rem 1rem;
            border-radius: 9999px;
            font-weight: 600;
            color: white;
            transition-property: background-color;
            transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
            transition-duration: 150ms;
        }
        .locked {
            filter: grayscale(80%);
            cursor: not-allowed;
            background-color: #f3f4f6;
            color: #9ca3af;
            border-color: #d1d5db;
        }
        .locked .lock-icon {
            display: block;
        }
        .unlocked .lock-icon {
            display: none;
        }
        .locked button {
            background-color: #9ca3af;
        }
        .completed {
            background-color: #f0fdf4;
            color: #166534;
            border-color: #22c55e;
        }
        .completed button {
            background-color: #22c55e;
        }
        .uncompleted {
            background-color: #f5f3ff;
            color: #6b21a8;
            border-color: #8b5cf6;
        }
        .uncompleted button {
            background-color: #7c3aed;
        }
        .uncompleted button:hover {
            background-color: #6d28d9;
        }
        .message-container {
            margin-top: 2rem;
            display: none;
            background-color: #dcfce7;
            border-left-width: 4px;
            border-color: #22c55e;
            color: #15803d;
            padding: 1rem;
            border-radius: 0.75rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
        .message-container.visible {
            display: block;
        }
        .message-title {
            font-weight: 700;
        }
        /* Video Modal Styles */
        .video-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            backdrop-filter: blur(5px);
            -webkit-backdrop-filter: blur(5px);
            padding: 1rem;
            visibility: hidden;
            opacity: 0;
            transition: visibility 0s, opacity 0.5s linear;
        }
        .video-modal.visible {
            visibility: visible;
            opacity: 1;
        }
        .video-modal-content {
            background-color: white;
            border-radius: 1.5rem;
            padding: 1.5rem;
            width: 100%;
            max-width: 768px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            position: relative;
        }
        .video-player-container {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            height: 0;
            margin-bottom: 1rem;
            border-radius: 1rem;
            overflow: hidden;
        }
        .video-player-container video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border-radius: 1rem;
        }
        .close-button {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background-color: #fca5a5;
            color: white;
            border: none;
            width: 2.5rem;
            height: 2.5rem;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            font-size: 1.5rem;
            line-height: 1;
        }
        /* 新增：用於隱藏/顯示按鈕 */
        .hidden {
            display: none;
        }
    </style>
</head>
<body class="p-4 sm:p-8">
    <div class="container">
        <!-- 核心目標與標題 -->
        <div class="text-center mb-8">
            <h1 class="title">美髮經營策略家</h1>
            <p class="subtitle">美髮經營課程 | 讓您成為頂尖沙龍管理者！</p>
        </div>

        <!-- 遊戲化數據顯示區 -->
        <div class="grid-container">
            <div class="data-card">
                <p class="data-label">當前等級</p>
                <p id="player-level" class="data-value">初階學徒</p>
            </div>
            <div class="data-card">
                <p class="data-label">學習點數</p>
                <p id="player-points" class="data-value">0</p>
            </div>
            <div class="data-card">
                <p class="data-label">課程進度</p>
                <div class="progress-bar">
                    <div class="progress-bar-bg">
                        <div id="progress-bar" style="width: 0%" class="progress-bar-inner"></div>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- 使用者 ID 與狀態顯示區 -->
        <div class="text-center text-sm text-gray-500 mb-8">
            <p id="user-id-display" class="break-words">使用者ID: 載入中...</p>
            <p id="status-display" class="font-bold text-blue-500">正在連接...</p>
        </div>

        <!-- 課程模組區 -->
        <div class="modules-container" id="modules-container">
            <div id="loading-spinner" class="text-center py-10">
                <div class="animate-spin rounded-full h-12 w-12 border-t-4 border-b-4 border-purple-500 mx-auto"></div>
                <p class="text-gray-500 mt-4">載入進度中...</p>
            </div>
        </div>

        <!-- 訊息與提示區 -->
        <div id="message-container" class="message-container">
            <p class="message-title">恭喜！</p>
            <p id="message-text">您已完成本模組！</p>
        </div>
    </div>

    <!-- Video Modal -->
    <div id="video-modal" class="video-modal hidden">
        <div class="video-modal-content">
            <h3 id="video-modal-title" class="text-2xl font-bold text-center mb-4 text-gray-800">影片標題</h3>
            <div class="video-player-container">
                <video id="video-player" controls>
                    您的瀏覽器不支援影片播放。
                </video>
            </div>
            <div class="flex flex-col sm:flex-row justify-center space-y-4 sm:space-y-0 sm:space-x-4">
                <!-- 影片看完後才會出現的提示文字 -->
                <p id="video-complete-message" class="hidden text-center text-sm text-green-600 font-bold">影片已播放完畢，您可以領取點數了！</p>
                <!-- 在影片播放結束前，此按鈕會被隱藏 -->
                <button id="complete-task-btn" class="module-button w-full sm:w-auto bg-green-600 hover:bg-green-700 hidden">完成任務並領取點數</button>
                <button id="close-modal-btn" class="module-button w-full sm:w-auto bg-gray-500 hover:bg-gray-600">返回課程</button>
            </div>
        </div>
    </div>

    <script type="module">
        // Import Firebase modules. These are hosted on Google's CDN for easy access.
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, getDoc, setDoc, setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Your Firebase project configuration.
        const firebaseConfig = {
            apiKey: "“AIzaSyCOhBN9TH3UJSOSx5XVyQ08f_2RUckvXYU” ",
            authDomain: "holyhairsalon-f73bf.firebaseapp.com",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_STORAGE_BUCKET",
            messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
            appId: "YOUR_APP_ID",
            measurementId: "YOUR_MEASUREMENT_ID"
        };
        
        let db, auth;
        let userId = '';
        const app_id = "hair_salon_course"; // A fixed app ID for this project.

        // Initialize Firebase services and handle potential errors.
        try {
            const app = initializeApp(firebaseConfig);
            db = getFirestore(app);
            auth = getAuth(app);
            setLogLevel('Debug');
        } catch (error) {
            console.error("Firebase initialization failed:", error);
            document.getElementById('status-display').textContent = '初始化失敗，請檢查設定。';
        }

        const gameDataCollection = `artifacts/${app_id}/users/`;

        // Game State and Module Definitions
        let gameState = {
            points: 0,
            level: '初階學徒',
            currentModuleIndex: 0,
            modules: [
                {
                    title: '1. 市場調查',
                    subtitle: '我的目標客戶是誰？',
                    subtitle: '我的競爭對手是誰？',
                     subtitle: '市場上有什麼空白需求可以滿足？',
                    content: '了解如何快速完成一份有效的市場調查，並將結果應用到實際的沙龍經營中。',
                    points: 50,
                    completed: false,
                    videoUrl1: 'https://drive.google.com/file/d/1U8qQb6Ob_0pLR-KxtTLDnYcuh0fqqFtW/view?usp=sharing'
                },
                {
                    title: '2. 目標客群分析',
                    subtitle: '了解潛在顧客的一個重要步驟',
                    content: '目標客群分析是針對你的美髮創業展店來識別。',
                    points: 75,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1K4_D47lq7gVnBl-OFApHuedFwgC3KAjV/view?usp=sharing'
                },
                {
                    title: '3. 競爭者研究',
                    subtitle: '制定有效策略的重要步驟',
                    content: '競爭者研究是瞭解你的美髮創業展店在市場環境中的位置。',
                    isAction: true,
                    points: 100,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1O5YKOSNwJkiSZS_4sjJvEI0dwKD-CxnR/view?usp=sharing'
                },
                {
                    title: '4. 行業趨勢與需求評估',
                    subtitle: '需求評估',
                    content: '行業趨勢與需求評估對於美髮創業展店的成功至關重要。',
                    points: 150,
                    completed: false,
                    videoUrl: 'https://drive.google.com/file/d/1cC2envJ3VySRqNahyUsLbST1U5Nw-T2I/view?usp=sharing'
                },
                {
                    title: '實作：模擬預約系統',
                    subtitle: '體驗後台管理，優化預約流程',
                    content: '模擬操作沙龍預約系統，並練習處理常見的預約問題。',
                    isAction: true,
                    points: 125,
                    completed: false,
                    videoUrl: 'https://www.w3schools.com/html/mov_bbb.mp4'
                },
                {
                    title: '4. 評估與優化',
                    subtitle: '數據導向，持續精進經營策略',
                    content: '學習如何收集與分析數據，評估會員方案成效，並進行優化。',
                    points: 200,
                    completed: false,
                    videoUrl: 'https://www.w3schools.com/html/mov_bbb.mp4'
                },
                {
                    title: '期末專案：創業計劃書',
                    subtitle: '提交您的最終成果，展現學習成就',
                    content: '撰寫一份完整的案例分析報告，展現您對沙龍經營策略的理解與應用能力。',
                    isAction: true,
                    points: 300,
                    completed: false,
                    videoUrl: 'https://www.w3schools.com/html/mov_bbb.mp4'
                }
            ]
        };

        const playerLevelMap = [
            { threshold: 0, name: '初階學徒' },
            { threshold: 300, name: '中階經營者' },
            { threshold: 600, name: '高階策略師' },
            { threshold: 1000, name: '課程畢業生' }
        ];

        // UI Elements
        const modulesContainer = document.getElementById('modules-container');
        const playerPointsEl = document.getElementById('player-points');
        const playerLevelEl = document.getElementById('player-level');
        const progressBarEl = document.getElementById('progress-bar');
        const messageContainer = document.getElementById('message-container');
        const messageTextEl = document.getElementById('message-text');
        const loadingSpinner = document.getElementById('loading-spinner');
        const statusDisplay = document.getElementById('status-display');
        const userIdDisplay = document.getElementById('user-id-display');

        // Video Modal Elements
        const videoModal = document.getElementById('video-modal');
        const videoModalTitle = document.getElementById('video-modal-title');
        const videoPlayer = document.getElementById('video-player');
        const completeTaskBtn = document.getElementById('complete-task-btn');
        const closeModalBtn = document.getElementById('close-modal-btn');
        const videoCompleteMessage = document.getElementById('video-complete-message');
        let currentModuleIndex = -1;

        // --- Firebase Integration Functions ---
        async function loadGameState() {
            if (!userId) {
                console.error("User ID is not set. Cannot load game state.");
                return;
            }
            statusDisplay.textContent = '正在載入進度...';
            try {
                const docRef = doc(db, gameDataCollection + userId, userId);
                const docSnap = await getDoc(docRef);

                if (docSnap.exists()) {
                    const savedState = docSnap.data();
                    gameState.points = savedState.points;
                    gameState.currentModuleIndex = savedState.currentModuleIndex;
                    
                    if (savedState.modules) {
                        gameState.modules = savedState.modules;
                    }
                    console.log("Game state loaded from Firestore.");
                    statusDisplay.textContent = '進度載入完成！';
                } else {
                    console.log("No saved game state found. Starting new game.");
                    statusDisplay.textContent = '新遊戲已啟動。';
                }
            } catch (e) {
                console.error("Error loading game state:", e);
                statusDisplay.textContent = '載入進度失敗，請重新整理。';
            } finally {
                loadingSpinner.style.display = 'none';
                updateUI();
            }
        }

        async function saveGameState() {
            if (!userId) {
                console.error("User ID is not set. Cannot save game state.");
                return;
            }
            try {
                const docRef = doc(db, gameDataCollection + userId, userId);
                await setDoc(docRef, {
                    points: gameState.points,
                    currentModuleIndex: gameState.currentModuleIndex,
                    modules: gameState.modules,
                });
                console.log("Game state saved to Firestore.");
            } catch (e) {
                console.error("Error saving game state:", e);
            }
        }

        // --- UI and Game Logic Functions ---

        // Update UI state
        function updateUI() {
            playerPointsEl.textContent = gameState.points;
            const currentLevel = playerLevelMap.find(level => gameState.points >= level.threshold) || playerLevelMap[0];
            playerLevelEl.textContent = currentLevel.name;

            const totalModules = gameState.modules.length;
            const completedModules = gameState.modules.filter(m => m.completed).length;
            const progressPercentage = (completedModules / totalModules) * 100;
            progressBarEl.style.width = `${progressPercentage}%`;

            renderModules();
        }

        // Render module cards
        function renderModules() {
            modulesContainer.innerHTML = '';
            loadingSpinner.style.display = 'none';
            gameState.modules.forEach((module, index) => {
                const isLocked = index > gameState.currentModuleIndex;
                const isCompleted = module.completed;
                
                let cardClass = 'module-card';
                let buttonClass = 'module-button';
                let buttonText = '';

                if (isLocked) {
                    cardClass += ' locked';
                    buttonClass += ' bg-gray-400';
                    buttonText = '鎖定中';
                } else if (isCompleted) {
                    cardClass += ' completed';
                    buttonClass += ' bg-green-500';
                    buttonText = '已完成';
                } else {
                    cardClass += ' uncompleted';
                    buttonClass += ' bg-purple-600 hover:bg-purple-700';
                    buttonText = module.isAction ? '開始實作' : '開始學習';
                }

                const cardHtml = `
                    <div class="${cardClass}" data-index="${index}">
                        <div class="module-header">
                            <h2 class="module-title">${module.title}</h2>
                            <div class="lock-icon text-xl text-gray-400">🔒</div>
                            <div class="completion-icon text-xl text-green-500 ${isCompleted ? '' : 'hidden'}">✅</div>
                        </div>
                        <p class="module-subtitle">${module.subtitle}</p>
                        <p class="module-content">${module.content}</p>
                        <div class="module-footer">
                            <span class="module-points">${module.isAction ? '實作' : '學習'}點數: +${module.points}</span>
                            <button class="${buttonClass}" ${isLocked || isCompleted ? 'disabled' : ''}>
                                ${buttonText}
                            </button>
                        </div>
                    </div>
                `;
                modulesContainer.innerHTML += cardHtml;
            });

            document.querySelectorAll('.module-card button').forEach(button => {
                button.addEventListener('click', handleModuleClick);
            });
        }

        // Handle module click to open video modal
        function handleModuleClick(event) {
            const card = event.currentTarget.closest('.module-card');
            const index = parseInt(card.dataset.index);
            const module = gameState.modules[index];

            if (index > gameState.currentModuleIndex || module.completed) {
                return;
            }
            
            currentModuleIndex = index;
            openVideoModal(module.videoUrl, module.title);
        }

        // Open the video modal with the correct video
        function openVideoModal(videoUrl, title) {
            videoModalTitle.textContent = title;
            videoPlayer.src = videoUrl;
            videoModal.classList.remove('hidden');
            videoModal.classList.add('visible');
            
            // 影片模態視窗開啟時，隱藏「完成任務」按鈕和提示文字
            completeTaskBtn.classList.add('hidden');
            videoCompleteMessage.classList.add('hidden');
        }

        // Close the video modal
        function closeVideoModal() {
            videoPlayer.pause();
            videoPlayer.src = '';
            videoModal.classList.remove('visible');
            videoModal.classList.add('hidden');
        }

        // Handle task completion from within the video modal
        async function completeTask() {
            const module = gameState.modules[currentModuleIndex];
            if (!module) return;

            gameState.points += module.points;
            module.completed = true;

            if (gameState.currentModuleIndex < gameState.modules.length - 1) {
                gameState.currentModuleIndex++;
            }

            await saveGameState();
            showMessage(`恭喜完成《${module.title}》！獲得 ${module.points} 點數。`);
            updateUI();
            closeVideoModal();
        }
        
        // --- 新增：監聽影片播放結束事件 ---
        videoPlayer.addEventListener('ended', () => {
            // 當影片播放結束時，顯示「完成任務」按鈕和提示文字
            completeTaskBtn.classList.remove('hidden');
            videoCompleteMessage.classList.remove('hidden');
        });

        // Event listeners for video modal buttons
        completeTaskBtn.addEventListener('click', completeTask);
        closeModalBtn.addEventListener('click', closeVideoModal);

        function showMessage(text) {
            messageContainer.classList.add('visible');
            messageTextEl.textContent = text;
            
            setTimeout(() => {
                messageContainer.classList.remove('visible');
            }, 3000);
        }

        // --- Main execution flow ---
        onAuthStateChanged(auth, async (user) => {
            if (user) {
                userId = user.uid;
                userIdDisplay.textContent = `使用者ID: ${userId}`;
                statusDisplay.textContent = '已連接。';
                await loadGameState();
            } else {
                try {
                    await signInAnonymously(auth);
                } catch (error) {
                    console.error("Authentication error: ", error);
                    userIdDisplay.textContent = '使用者ID: 認證失敗';
                    statusDisplay.textContent = '認證失敗，請重新載入。';
                    loadingSpinner.style.display = 'none';
                    renderModules();
                }
            }
        });

    </script>
</body>
</html>
