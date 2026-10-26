<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>R - Custom Rhythm Game</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        body, html { margin: 0; padding: 0; width: 100%; height: 100%; background-color: #030308; overflow: hidden; font-family: 'Inter', sans-serif; touch-action: none; user-select: none; }
        canvas { display: block; width: 100%; height: 100%; position: absolute; top: 0; left: 0; z-index: 1; }
        
        #startPanel, #resultPanel { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); background: rgba(10, 15, 30, 0.85); border: 2px solid #007bff; border-radius: 20px; padding: 40px; text-align: center; color: white; box-shadow: 0 0 40px rgba(0, 123, 255, 0.4); backdrop-filter: blur(10px); z-index: 100; min-width: 320px; }
        #resultPanel { display: none; }
        h1 { font-size: 32px; font-weight: 900; margin-bottom: 10px; color: #00e5ff; text-shadow: 0 0 15px rgba(0, 229, 255, 0.8); }
        
        .btn { background: linear-gradient(45deg, #00509e, #007bff); border: none; padding: 15px 30px; font-size: 18px; font-weight: bold; color: white; border-radius: 10px; cursor: pointer; transition: all 0.2s; margin: 10px 0; width: 100%; box-shadow: 0 5px 15px rgba(0, 123, 255, 0.3); }
        .btn:hover { transform: scale(1.05); background: linear-gradient(45deg, #007bff, #00a8ff); box-shadow: 0 8px 20px rgba(0, 168, 255, 0.5); }
        .btn-editor { background: linear-gradient(45deg, #00897b, #00acc1); box-shadow: 0 5px 15px rgba(0, 172, 193, 0.3); }
        .btn-editor:hover { background: linear-gradient(45deg, #00acc1, #00bcd4); }

        #hud { position: absolute; top: 0; left: 0; width: 100%; padding: 20px; box-sizing: border-box; display: none; justify-content: space-between; align-items: flex-start; z-index: 50; pointer-events: none; }
        .hud-left { display: flex; flex-direction: column; gap: 10px; }
        #scoreDisplay { font-size: 24px; font-weight: 900; color: white; text-shadow: 0 0 10px rgba(255,255,255,0.5); }
        #comboDisplay { font-size: 32px; font-weight: 900; color: #00e5ff; text-shadow: 0 0 20px rgba(0, 229, 255, 0.8); }
        
        /* 콤보 위치를 상단(15%)으로 끌어올림 */
        #centerComboOverlay { position: absolute; top: 15%; left: 50%; transform: translate(-50%, -50%); font-size: 100px; font-weight: 900; font-style: italic; color: rgba(255, 255, 255, 0.9); text-shadow: 0 0 40px #00e5ff, 0 0 20px #00a8ff; display: none; z-index: 40; pointer-events: none; text-align: center; }
        @keyframes comboPop { 0% { transform: translate(-50%, -50%) scale(1.3); opacity: 1; } 100% { transform: translate(-50%, -50%) scale(1); opacity: 0; } }
        .combo-anim { animation: comboPop 0.5s ease-out forwards; }

        /* 판정 글씨 (PERFECT, GREAT 등) - 시야 확보를 위해 위로 올림 */
        #judgmentOverlay { position: absolute; top: 25%; left: 50%; transform: translate(-50%, -50%); font-size: 60px; font-weight: 900; font-style: italic; display: none; z-index: 45; pointer-events: none; text-align: center; }
        @keyframes judgePop { 0% { transform: translate(-50%, -50%) scale(1.5); opacity: 1; } 100% { transform: translate(-50%, -50%) scale(1); opacity: 0; } }
        .judge-anim { animation: judgePop 0.4s ease-out forwards; }

        #hpContainer { width: 200px; height: 15px; background: rgba(255, 255, 255, 0.2); border-radius: 10px; overflow: hidden; border: 1px solid rgba(255,255,255,0.5); }
        #hpBar { width: 100%; height: 100%; background: linear-gradient(90deg, #ff0055, #00ffcc); transition: width 0.2s ease-out; }
        
        #modeIndicator { position: absolute; top: 80px; left: 50%; transform: translateX(-50%); background: rgba(255, 0, 85, 0.8); padding: 10px 20px; border-radius: 20px; color: white; font-weight: bold; display: none; z-index: 50; animation: pulse 1s infinite; }
        @keyframes pulse { 0% { opacity: 1; transform: translateX(-50%) scale(1); } 50% { opacity: 0.8; transform: translateX(-50%) scale(1.05); } 100% { opacity: 1; transform: translateX(-50%) scale(1); } }
        
        #countdownOverlay { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); font-size: 120px; font-weight: 900; color: white; text-shadow: 0 0 40px #00e5ff; display: none; z-index: 200; pointer-events: none; }
        .overload-warning { position: absolute; top: 30%; left: 50%; transform: translate(-50%, -50%); font-size: 60px; font-weight: 900; color: #ff0055; text-shadow: 0 0 30px #ff0055; display: none; z-index: 60; pointer-events: none; }
        
        .stat-row { display: flex; justify-content: space-between; font-size: 18px; margin: 5px 0; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 5px; }
        .stat-row span:nth-child(2) { font-weight: bold; color: #00e5ff; }

        /* 🔥 화면 왼쪽 아래 가로형 D, F, J, K 키 가이드 패널 (크기업 & 위로 튀어오름) 🔥 */
        #keyGuidePanel { 
            position: absolute; 
            bottom: 8%; 
            left: 3%; 
            display: flex; 
            flex-direction: row; /* 가로 배치 */
            gap: 15px; 
            z-index: 100; 
            pointer-events: none; 
        }
        .guide-key { 
            width: 80px; /* 크기 빵빵하게 증가 */
            height: 80px; /* 크기 빵빵하게 증가 */
            display: flex; 
            justify-content: center; 
            align-items: center; 
            background: rgba(0, 0, 0, 0.5); 
            border: 2px solid rgba(255, 255, 255, 0.3); 
            border-radius: 16px; 
            font-size: 36px; /* 글씨 크기 증가 */
            font-weight: 900; 
            color: rgba(255, 255, 255, 0.3); 
            transition: all 0.08s cubic-bezier(0.25, 0.46, 0.45, 0.94); /* 쫀득한 타이밍 */
            backdrop-filter: blur(5px);
        }
        .guide-active { 
            background: rgba(255, 255, 255, 0.15);
        }

        /* 🔥 역으로 솟구치는 키뷰어 타일 CSS 추가 🔥 */
        .viewer-tile {
            position: absolute;
            bottom: 95px; /* DFJK 패드 바로 위에서 출발 */
            width: 80px; /* DFJK 패드 폭에 딱 맞춤 */
            height: 25px; /* 날아가는 타일 두께 */
            border-radius: 8px;
            pointer-events: none;
            z-index: 80;
            animation: shootUp 0.3s ease-out forwards; 
        }
        
        @keyframes shootUp {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-400px); opacity: 0; }
        }
    </style>
</head>
<body>
    <canvas id="gameCanvas"></canvas>

    <!-- 왼쪽 뚜렷한 키 가이드 패널 -->
    <div id="keyGuidePanel">
        <div class="guide-key" id="guide-D">D</div>
        <div class="guide-key" id="guide-F">F</div>
        <div class="guide-key" id="guide-J">J</div>
        <div class="guide-key" id="guide-K">K</div>
    </div>

    <!-- 시작 메뉴 -->
    <div id="startPanel">
        <h1 id="titleText">R <br><span style="font-size:18px; color:#00a8ff;">RHYTHM GAME (3D)</span></h1>
        
        <button class="btn" id="btnCustomMap">내 커스텀 맵 플레이</button>
        <button class="btn btn-editor" id="btnEditor">✍️ 새 맵 만들기 (에디터 모드)</button>
        
        <div style="margin-top: 15px; display: flex; gap: 10px; justify-content: center;">
            <label style="font-size: 12px; color: #ccc; display: flex; align-items: center; gap: 5px;">
                <input type="checkbox" id="invincibleMode"> 무적 모드
            </label>
        </div>
    </div>
    
    <!-- 결과 창 -->
    <div id="resultPanel">
        <h1 id="resultTitle">STAGE CLEAR</h1>
        <div class="stat-row"><span>Score</span><span id="resScore">0</span></div>
        <div class="stat-row"><span>Accuracy</span><span id="resAcc">0%</span></div>
        <div class="stat-row"><span>Max Combo</span><span id="resCombo">0</span></div>
        <div style="margin: 15px 0; padding: 10px; background: rgba(0,0,0,0.5); border-radius: 10px;">
            <div class="stat-row" style="color: #00e5ff;"><span>PERFECT</span><span id="resPerfect">0</span></div>
            <div class="stat-row" style="color: #00b894;"><span>GREAT</span><span id="resGreat">0</span></div>
            <div class="stat-row" style="color: #f1c40f;"><span>GOOD</span><span id="resGood">0</span></div>
            <div class="stat-row" style="color: #ff0055; border:none;"><span>MISS</span><span id="resMiss">0</span></div>
        </div>
        <button class="btn" onclick="location.reload()">메인으로 돌아가기</button>
    </div>

    <!-- 인게임 UI 오버레이 -->
    <div id="modeIndicator">✍️ 채보 녹화 중... (D, F, J, K로 노트를 찍으세요!)</div>
    <div id="countdownOverlay">3</div>
    <div id="overloadWarning" class="overload-warning">과부하! (OVERLOAD)</div>
    <div id="centerComboOverlay"></div>
    <div id="judgmentOverlay"></div>

    <div id="msgBox" style="display:none; position:fixed; top:50%; left:50%; transform:translate(-50%,-50%); background:rgba(10,15,30,0.95); border:2px solid #00e5ff; padding:30px; border-radius:10px; z-index:9999; color:white; text-align:center; box-shadow:0 0 30px rgba(0,229,255,0.4);">
        <p id="msgText" style="margin-bottom:20px; font-size:18px; font-weight:bold; color:#00e5ff;"></p>
        <div style="display:flex; gap:10px; justify-content:center;">
            <button class="btn" onclick="document.getElementById('msgBox').style.display='none'" style="margin:0; width:120px;">확인</button>
        </div>
    </div>

    <div id="hud">
        <div class="hud-left">
            <div id="scoreDisplay">SCORE: 0</div>
            <div id="comboDisplay">0 COMBO</div>
        </div>
        <div id="hpContainer"><div id="hpBar"></div></div>
    </div>

    <script>
        const startPanel = document.getElementById('startPanel');
        const resultPanel = document.getElementById('resultPanel');
        const hud = document.getElementById('hud');
        const scoreDisplay = document.getElementById('scoreDisplay');
        const comboDisplay = document.getElementById('comboDisplay');
        const centerComboOverlay = document.getElementById('centerComboOverlay');
        const judgmentOverlay = document.getElementById('judgmentOverlay');
        const hpBar = document.getElementById('hpBar');
        const invincibleMode = document.getElementById('invincibleMode');
        const modeIndicator = document.getElementById('modeIndicator');
        const countdownOverlay = document.getElementById('countdownOverlay');
        const overloadWarning = document.getElementById('overloadWarning');

        // 왼쪽 키 가이드 DOM 엘리먼트 가져오기
        const guideDOMs = [
            document.getElementById('guide-D'),
            document.getElementById('guide-F'),
            document.getElementById('guide-J'),
            document.getElementById('guide-K')
        ];

        // 원상복구된 140초짜리 풀버전 맵 데이터
        const COMPRESSED_CHART = [{"lane":0,"time":1.6349999999999998},{"lane":1,"time":1.7256666666666653},{"lane":2,"time":1.9656666666666656},{"lane":0,"time":2.285666666666666},{"lane":3,"time":2.635},{"lane":0,"time":2.7656666666666663},{"lane":1,"time":2.9256666666666664},{"lane":0,"time":3.285666666666666},{"lane":2,"time":3.6243333333333325},{"lane":2,"time":3.9256666666666664},{"lane":3,"time":4.096333333333332},{"lane":0,"time":4.275},{"lane":3,"time":4.605666666666666},{"lane":2,"time":4.965666666666667},{"lane":3,"time":5.285666666666668},{"lane":1,"time":5.645666666666667},{"lane":2,"time":5.794999999999998},{"lane":3,"time":5.954999999999998},{"lane":0,"time":6.285666666666668},{"lane":0,"time":6.6243333333333325},{"lane":1,"time":6.805666666666667},{"lane":2,"time":6.954999999999998},{"lane":3,"time":7.314999999999998},{"lane":2,"time":7.634999999999998},{"lane":3,"time":7.944333333333333},{"lane":0,"time":8.114999999999998},{"lane":1,"time":8.274999999999999},{"lane":0,"time":8.624333333333333},{"lane":2,"time":8.965666666666667},{"lane":2,"time":9.285666666666668},{"lane":3,"time":9.464333333333332},{"lane":0,"time":9.624333333333333},{"lane":1,"time":9.965666666666667},{"lane":0,"time":10.296333333333333},{"lane":3,"time":10.605666666666668},{"lane":1,"time":10.976333333333333},{"lane":2,"time":11.165666666666667},{"lane":3,"time":11.304333333333332},{"lane":0,"time":11.456333333333333},{"lane":1,"time":11.634999999999998},{"lane":2,"time":11.794999999999998},{"lane":3,"time":11.944333333333333},{"lane":0,"time":12.114999999999998},{"lane":1,"time":12.264333333333333},{"lane":0,"time":12.634999999999998},{"lane":3,"time":12.976333333333333},{"lane":2,"time":13.285666666666668},{"lane":3,"time":13.464333333333332},{"lane":0,"time":13.634999999999998},{"lane":1,"time":13.954999999999998},{"lane":2,"time":14.285666666666668},{"lane":1,"time":14.594999999999999},{"lane":2,"time":14.805666666666667},{"lane":3,"time":14.965666666666667},{"lane":1,"time":15.325666666666667},{"lane":2,"time":15.645666666666667},{"lane":3,"time":15.954999999999998},{"lane":0,"time":16.285666666666664},{"lane":1,"time":16.445666666666668},{"lane":2,"time":16.595},{"lane":1,"time":16.925666666666665},{"lane":3,"time":17.29633333333333},{"lane":0,"time":17.485666666666667},{"lane":1,"time":17.634999999999998},{"lane":3,"time":17.984333333333332},{"lane":2,"time":18.304333333333332},{"lane":2,"time":18.61633333333333},{"lane":3,"time":18.794999999999995},{"lane":0,"time":18.944333333333333},{"lane":1,"time":19.275},{"lane":0,"time":19.624333333333333},{"lane":1,"time":19.93633333333333},{"lane":2,"time":20.136333333333333},{"lane":3,"time":20.304333333333332},{"lane":0,"time":20.485666666666667},{"lane":1,"time":20.645666666666664},{"lane":2,"time":20.78433333333333},{"lane":3,"time":20.875},{"lane":0,"time":20.944333333333333},{"lane":1,"time":21.04566666666667},{"lane":2,"time":21.10433333333333},{"lane":3,"time":21.205666666666666},{"lane":0,"time":21.25633333333333},{"lane":1,"time":21.36566666666667},{"lane":2,"time":21.435000000000002},{"lane":3,"time":21.645666666666664},{"lane":0,"time":21.805666666666667},{"lane":1,"time":21.984333333333332},{"lane":2,"time":22.136333333333333},{"lane":3,"time":22.304333333333332},{"lane":0,"time":22.456333333333333},{"lane":1,"time":22.795},{"lane":2,"time":22.925666666666665},{"lane":0,"time":23.304333333333332},{"lane":2,"time":23.634999999999998},{"lane":3,"time":23.955},{"lane":0,"time":24.10433333333333},{"lane":1,"time":24.275},{"lane":2,"time":24.445666666666668},{"lane":3,"time":24.61633333333333},{"lane":1,"time":24.965666666666664},{"lane":0,"time":25.285666666666664},{"lane":1,"time":25.456333333333333},{"lane":2,"time":25.634999999999998},{"lane":3,"time":25.795},{"lane":0,"time":25.955},{"lane":3,"time":26.285666666666664},{"lane":2,"time":26.605666666666664},{"lane":1,"time":26.965666666666664},{"lane":2,"time":27.125666666666667},{"lane":3,"time":27.285666666666664},{"lane":1,"time":27.634999999999998},{"lane":0,"time":27.965666666666664},{"lane":1,"time":28.136333333333333},{"lane":2,"time":28.29633333333333},{"lane":3,"time":28.456333333333333},{"lane":0,"time":28.61633333333333},{"lane":3,"time":28.93633333333333},{"lane":1,"time":29.285666666666664},{"lane":2,"time":29.464333333333336},{"lane":3,"time":29.634999999999998},{"lane":0,"time":29.805666666666667},{"lane":1,"time":29.97633333333333},{"lane":0,"time":30.285666666666664},{"lane":2,"time":30.624333333333333},{"lane":3,"time":30.805666666666667},{"lane":0,"time":30.955},{"lane":1,"time":31.125666666666667},{"lane":2,"time":31.29633333333333},{"lane":0,"time":31.634999999999998},{"lane":2,"time":31.925666666666665},{"lane":3,"time":32.32566666666666},{"lane":0,"time":32.48566666666667},{"lane":1,"time":32.64566666666666},{"lane":2,"time":32.81633333333333},{"lane":3,"time":32.97633333333333},{"lane":0,"time":33.12566666666667},{"lane":1,"time":33.475},{"lane":3,"time":33.80566666666667},{"lane":1,"time":34.144333333333336},{"lane":2,"time":34.32566666666666},{"lane":3,"time":34.48566666666667},{"lane":0,"time":34.64566666666666},{"lane":1,"time":34.81633333333333},{"lane":2,"time":35.32566666666666},{"lane":3,"time":35.48566666666667},{"lane":0,"time":35.97633333333333},{"lane":1,"time":36.12566666666667},{"lane":0,"time":36.475},{"lane":1,"time":36.795},{"lane":0,"time":37.12566666666667},{"lane":1,"time":37.464333333333336},{"lane":2,"time":37.955},{"lane":3,"time":38.12566666666667},{"lane":0,"time":38.595},{"lane":1,"time":38.77633333333333},{"lane":2,"time":39.155},{"lane":2,"time":39.475},{"lane":3,"time":39.66433333333333},{"lane":0,"time":39.81633333333333},{"lane":1,"time":39.965666666666664},{"lane":2,"time":40.13633333333333},{"lane":3,"time":40.49633333333333},{"lane":0,"time":40.66433333333333},{"lane":1,"time":40.714999999999996},{"lane":2,"time":40.795},{"lane":3,"time":41.155},{"lane":2,"time":41.48566666666667},{"lane":3,"time":41.80566666666667},{"lane":0,"time":41.965666666666664},{"lane":3,"time":42.285666666666664},{"lane":1,"time":42.62433333333333},{"lane":2,"time":42.795},{"lane":3,"time":43.13633333333333},{"lane":0,"time":43.285666666666664},{"lane":3,"time":43.64566666666666},{"lane":1,"time":43.98433333333333},{"lane":2,"time":44.12566666666667},{"lane":3,"time":44.45633333333333},{"lane":3,"time":44.795},{"lane":0,"time":44.995},{"lane":1,"time":45.16566666666667},{"lane":2,"time":45.32566666666666},{"lane":3,"time":45.48566666666667},{"lane":0,"time":45.965666666666664},{"lane":1,"time":46.12566666666667},{"lane":2,"time":46.656333333333336},{"lane":3,"time":46.824333333333335},{"lane":2,"time":47.12566666666667},{"lane":0,"time":47.475},{"lane":2,"time":47.80566666666667},{"lane":0,"time":48.13633333333333},{"lane":0,"time":48.635},{"lane":1,"time":48.795},{"lane":2,"time":49.29633333333333},{"lane":3,"time":49.48566666666667},{"lane":0,"time":49.795},{"lane":0,"time":50.144333333333336},{"lane":1,"time":50.30433333333333},{"lane":2,"time":50.48566666666667},{"lane":3,"time":50.635},{"lane":0,"time":50.795},{"lane":1,"time":51.144333333333336},{"lane":2,"time":51.29633333333333},{"lane":3,"time":51.36566666666667},{"lane":0,"time":51.44566666666667},{"lane":1,"time":51.80566666666667},{"lane":2,"time":51.965666666666664},{"lane":3,"time":52.144333333333336},{"lane":0,"time":52.30433333333333},{"lane":1,"time":52.48566666666667},{"lane":2,"time":52.656333333333336},{"lane":3,"time":52.965666666666664},{"lane":0,"time":53.12566666666666},{"lane":1,"time":53.28566666666667},{"lane":2,"time":53.48566666666666},{"lane":3,"time":53.82433333333333},{"lane":0,"time":53.995000000000005},{"lane":1,"time":54.05633333333333},{"lane":2,"time":54.136333333333326},{"lane":3,"time":54.46433333333333},{"lane":0,"time":54.635000000000005},{"lane":1,"time":54.69633333333333},{"lane":2,"time":54.795},{"lane":3,"time":55.12566666666666},{"lane":0,"time":55.315},{"lane":1,"time":55.81633333333333},{"lane":1,"time":56.12566666666666},{"lane":2,"time":56.28566666666667},{"lane":0,"time":56.62433333333334},{"lane":3,"time":57.00566666666667},{"lane":0,"time":57.275000000000006},{"lane":1,"time":57.435},{"lane":2,"time":57.504333333333335},{"lane":3,"time":57.605666666666664},{"lane":0,"time":57.795},{"lane":1,"time":57.92566666666667},{"lane":2,"time":57.995000000000005},{"lane":3,"time":58.08566666666667},{"lane":0,"time":58.29633333333334},{"lane":1,"time":58.46433333333333},{"lane":2,"time":58.656333333333336},{"lane":3,"time":58.70433333333334},{"lane":0,"time":58.81633333333333},{"lane":1,"time":58.965666666666664},{"lane":2,"time":59.30433333333333},{"lane":3,"time":59.376333333333335},{"lane":0,"time":59.474999999999994},{"lane":1,"time":59.56566666666667},{"lane":2,"time":59.64566666666667},{"lane":3,"time":59.74433333333333},{"lane":0,"time":59.834999999999994},{"lane":1,"time":59.92566666666667},{"lane":2,"time":60.00566666666667},{"lane":3,"time":60.08566666666667},{"lane":0,"time":60.16566666666667},{"lane":1,"time":60.44566666666667},{"lane":1,"time":60.885666666666665},{"lane":2,"time":61.00566666666667},{"lane":3,"time":61.29633333333334},{"lane":0,"time":61.36566666666667},{"lane":1,"time":61.41633333333333},{"lane":2,"time":61.776333333333326},{"lane":0,"time":62.12566666666666},{"lane":2,"time":62.44566666666667},{"lane":2,"time":62.795},{"lane":3,"time":62.84566666666666},{"lane":0,"time":62.92566666666667},{"lane":1,"time":63.10433333333333},{"lane":2,"time":63.28566666666667},{"lane":3,"time":63.34433333333334},{"lane":0,"time":63.435},{"lane":1,"time":63.61633333333333},{"lane":2,"time":63.784333333333336},{"lane":3,"time":63.85633333333334},{"lane":0,"time":63.97633333333333},{"lane":1,"time":64.17633333333333},{"lane":2,"time":64.28566666666667},{"lane":3,"time":64.36566666666667},{"lane":0,"time":64.45633333333333},{"lane":1,"time":64.53633333333333},{"lane":2,"time":64.61633333333333},{"lane":3,"time":64.715},{"lane":0,"time":64.795},{"lane":1,"time":64.88566666666667},{"lane":2,"time":64.96566666666666},{"lane":3,"time":65.05633333333333},{"lane":0,"time":65.12566666666666},{"lane":1,"time":65.22433333333333},{"lane":2,"time":65.28566666666667},{"lane":3,"time":65.40566666666666},{"lane":0,"time":65.44566666666667},{"lane":1,"time":65.82433333333333},{"lane":2,"time":65.995},{"lane":1,"time":66.40566666666666},{"lane":3,"time":66.76566666666666},{"lane":0,"time":66.92566666666667},{"lane":2,"time":67.275},{"lane":1,"time":67.61633333333333},{"lane":2,"time":67.76566666666666},{"lane":3,"time":67.93633333333334},{"lane":0,"time":68.08566666666667},{"lane":1,"time":68.17633333333333},{"lane":2,"time":68.25633333333333},{"lane":3,"time":68.44566666666667},{"lane":0,"time":68.58433333333333},{"lane":2,"time":68.955},{"lane":0,"time":69.28566666666667},{"lane":1,"time":69.795},{"lane":2,"time":69.97633333333333},{"lane":3,"time":70.04566666666666},{"lane":0,"time":70.13633333333333},{"lane":1,"time":70.235},{"lane":2,"time":70.30433333333333},{"lane":3,"time":70.40566666666666},{"lane":0,"time":70.45633333333333},{"lane":1,"time":70.58433333333333},{"lane":2,"time":70.64566666666667},{"lane":3,"time":70.76566666666666},{"lane":0,"time":70.92566666666667},{"lane":1,"time":71.00566666666667},{"lane":2,"time":71.10433333333333},{"lane":3,"time":71.28566666666667},{"lane":0,"time":71.32566666666666},{"lane":1,"time":71.435},{"lane":2,"time":71.60566666666666},{"lane":3,"time":71.69633333333333},{"lane":0,"time":71.85633333333334},{"lane":1,"time":72.05633333333333},{"lane":2,"time":72.12566666666666},{"lane":3,"time":72.21633333333334},{"lane":0,"time":72.29633333333334},{"lane":1,"time":72.38433333333333},{"lane":2,"time":72.46433333333333},{"lane":3,"time":72.55499999999999},{"lane":0,"time":72.635},{"lane":1,"time":72.73633333333333},{"lane":2,"time":72.81633333333333},{"lane":3,"time":72.92566666666667},{"lane":0,"time":72.995},{"lane":1,"time":73.09633333333333},{"lane":2,"time":73.16566666666667},{"lane":3,"time":73.26433333333333},{"lane":0,"time":73.34433333333334},{"lane":1,"time":73.44566666666667},{"lane":2,"time":73.60566666666666},{"lane":3,"time":73.675},{"lane":0,"time":73.76566666666666},{"lane":1,"time":73.96566666666666},{"lane":2,"time":74.035},{"lane":3,"time":74.12566666666666},{"lane":0,"time":74.28566666666667},{"lane":1,"time":74.355},{"lane":2,"time":74.44566666666667},{"lane":3,"time":74.62433333333334},{"lane":0,"time":74.78433333333334},{"lane":1,"time":74.96566666666666},{"lane":2,"time":75.12566666666666},{"lane":3,"time":75.30433333333333},{"lane":0,"time":75.41633333333333},{"lane":1,"time":75.48566666666666},{"lane":2,"time":75.58433333333333},{"lane":3,"time":75.66433333333333},{"lane":0,"time":75.77633333333333},{"lane":1,"time":75.96566666666666},{"lane":2,"time":76.13633333333333},{"lane":1,"time":76.56566666666667},{"lane":0,"time":77.08566666666667},{"lane":3,"time":77.44566666666667},{"lane":1,"time":77.94433333333333},{"lane":0,"time":78.45633333333333},{"lane":1,"time":78.80566666666667},{"lane":2,"time":79.28566666666667},{"lane":0,"time":79.76566666666666},{"lane":2,"time":80.09633333333333},{"lane":3,"time":80.45633333333333},{"lane":0,"time":80.635},{"lane":1,"time":80.77633333333333},{"lane":2,"time":81.12566666666666},{"lane":1,"time":81.45633333333333},{"lane":3,"time":81.94433333333333},{"lane":2,"time":82.29633333333334},{"lane":3,"time":82.475},{"lane":0,"time":82.80566666666667},{"lane":1,"time":82.94433333333333},{"lane":2,"time":83.13633333333333},{"lane":3,"time":83.28566666666667},{"lane":0,"time":83.64566666666667},{"lane":1,"time":83.80566666666667},{"lane":2,"time":83.955},{"lane":3,"time":84.12566666666666},{"lane":0,"time":84.475},{"lane":1,"time":84.635},{"lane":0,"time":84.96566666666666},{"lane":2,"time":85.32566666666666},{"lane":2,"time":85.68566666666666},{"lane":3,"time":85.955},{"lane":0,"time":86.02433333333333},{"lane":1,"time":86.09633333333333},{"lane":2,"time":86.195},{"lane":3,"time":86.38433333333333},{"lane":0,"time":86.58433333333333},{"lane":1,"time":86.74433333333333},{"lane":2,"time":87.28566666666667},{"lane":1,"time":87.80566666666667},{"lane":0,"time":88.12566666666666},{"lane":1,"time":88.60566666666666},{"lane":3,"time":89.13633333333333},{"lane":0,"time":89.45633333333333},{"lane":2,"time":89.93633333333334},{"lane":3,"time":90.42433333333334},{"lane":0,"time":90.76566666666666},{"lane":2,"time":91.115},{"lane":3,"time":91.275},{"lane":0,"time":91.41633333333333},{"lane":1,"time":91.755},{"lane":3,"time":92.08566666666667},{"lane":1,"time":92.41633333333333},{"lane":2,"time":92.57633333333334},{"lane":3,"time":92.915},{"lane":0,"time":93.09633333333333},{"lane":1,"time":93.45633333333333},{"lane":2,"time":93.60566666666666},{"lane":3,"time":93.77633333333333},{"lane":0,"time":93.94433333333333},{"lane":1,"time":94.29633333333334},{"lane":2,"time":94.45633333333333},{"lane":3,"time":94.60566666666666},{"lane":0,"time":94.77633333333333},{"lane":1,"time":95.115},{"lane":2,"time":95.28566666666667},{"lane":3,"time":95.62433333333334},{"lane":0,"time":95.96566666666666},{"lane":3,"time":96.29633333333334},{"lane":0,"time":96.52566666666667},{"lane":1,"time":96.61633333333333},{"lane":2,"time":96.69633333333333},{"lane":3,"time":96.89633333333333},{"lane":0,"time":96.92566666666667},{"lane":1,"time":97.06433333333334},{"lane":2,"time":97.24566666666666},{"lane":3,"time":97.435},{"lane":2,"time":97.77633333333333},{"lane":0,"time":98.10433333333333},{"lane":1,"time":98.28566666666667},{"lane":2,"time":98.435},{"lane":1,"time":98.78433333333334},{"lane":3,"time":99.12566666666666},{"lane":0,"time":99.29633333333334},{"lane":1,"time":99.61633333333333},{"lane":2,"time":99.76566666666666},{"lane":3,"time":100.115},{"lane":2,"time":100.46433333333333},{"lane":3,"time":100.89633333333333},{"lane":0,"time":101.08566666666667},{"lane":1,"time":101.44566666666667},{"lane":2,"time":101.77633333333333},{"lane":1,"time":102.12566666666666},{"lane":2,"time":102.275},{"lane":3,"time":102.44566666666667},{"lane":0,"time":102.61633333333333},{"lane":1,"time":102.795},{"lane":2,"time":103.12566666666666},{"lane":2,"time":103.45633333333333},{"lane":3,"time":103.64566666666667},{"lane":0,"time":103.78433333333334},{"lane":1,"time":104.12566666666666},{"lane":2,"time":104.29633333333334},{"lane":3,"time":104.45633333333333},{"lane":0,"time":104.61633333333333},{"lane":1,"time":104.94433333333333},{"lane":2,"time":105.12566666666666},{"lane":3,"time":105.44566666666667},{"lane":1,"time":105.78433333333334},{"lane":2,"time":106.14433333333334},{"lane":1,"time":106.48566666666666},{"lane":0,"time":106.795},{"lane":3,"time":107.25633333333333},{"lane":0,"time":107.435},{"lane":1,"time":107.57633333333334},{"lane":2,"time":107.60566666666666},{"lane":3,"time":107.62433333333334},{"lane":0,"time":107.74433333333333},{"lane":1,"time":107.97633333333333},{"lane":2,"time":108.12566666666666},{"lane":1,"time":108.475},{"lane":3,"time":108.80566666666667},{"lane":0,"time":108.96566666666666},{"lane":1,"time":109.14433333333334},{"lane":0,"time":109.48566666666666},{"lane":2,"time":109.80566666666667},{"lane":3,"time":109.94433333333333},{"lane":0,"time":110.33633333333333},{"lane":1,"time":110.45633333333333},{"lane":3,"time":110.795},{"lane":2,"time":111.16566666666667},{"lane":3,"time":111.315},{"lane":0,"time":111.64566666666667},{"lane":1,"time":111.795},{"lane":0,"time":112.12566666666666},{"lane":1,"time":112.44566666666667},{"lane":2,"time":112.80566666666667},{"lane":3,"time":112.97633333333333},{"lane":0,"time":113.13633333333333},{"lane":1,"time":113.28566666666667},{"lane":2,"time":113.435},{"lane":3,"time":113.80566666666667},{"lane":3,"time":114.12566666666666},{"lane":0,"time":114.28566666666667},{"lane":1,"time":114.44566666666667},{"lane":2,"time":114.78433333333334},{"lane":3,"time":114.955},{"lane":0,"time":115.12566666666666},{"lane":1,"time":115.26433333333333},{"lane":2,"time":115.60566666666666},{"lane":3,"time":115.76566666666666},{"lane":2,"time":116.115},{"lane":0,"time":116.57633333333334},{"lane":1,"time":116.73633333333333},{"lane":2,"time":117.275},{"lane":3,"time":117.44566666666665},{"lane":0,"time":117.78433333333334},{"lane":0,"time":118.13633333333334},{"lane":1,"time":118.28566666666666},{"lane":2,"time":118.46433333333334},{"lane":3,"time":118.62433333333334},{"lane":0,"time":118.79499999999999},{"lane":1,"time":118.85633333333334},{"lane":2,"time":118.96566666666666},{"lane":3,"time":119.035},{"lane":0,"time":119.12566666666666},{"lane":1,"time":119.20566666666667},{"lane":2,"time":119.30433333333335},{"lane":3,"time":119.36566666666667},{"lane":0,"time":119.475},{"lane":1,"time":119.555},{"lane":2,"time":119.65633333333332},{"lane":3,"time":119.73633333333333},{"lane":0,"time":119.83500000000001},{"lane":1,"time":119.90433333333334},{"lane":2,"time":120.00566666666666},{"lane":3,"time":120.08566666666667},{"lane":0,"time":120.195},{"lane":1,"time":120.24566666666666},{"lane":2,"time":120.36566666666667},{"lane":3,"time":120.42433333333332},{"lane":0,"time":120.54433333333333},{"lane":1,"time":120.61633333333333},{"lane":2,"time":120.72566666666665},{"lane":3,"time":120.80566666666667},{"lane":0,"time":120.91499999999999},{"lane":1,"time":120.98433333333332},{"lane":2,"time":121.08566666666667},{"lane":3,"time":121.16566666666665},{"lane":0,"time":121.275},{"lane":1,"time":121.34433333333334},{"lane":2,"time":121.45633333333333},{"lane":3,"time":121.52566666666667},{"lane":0,"time":121.64566666666667},{"lane":1,"time":121.70433333333332},{"lane":2,"time":121.80566666666667},{"lane":3,"time":121.88566666666668},{"lane":0,"time":121.97633333333334},{"lane":1,"time":122.05633333333333},{"lane":2,"time":122.16566666666665},{"lane":3,"time":122.24566666666666},{"lane":0,"time":122.33633333333333},{"lane":1,"time":122.41633333333334},{"lane":2,"time":122.51499999999999},{"lane":3,"time":122.60566666666668},{"lane":0,"time":122.68566666666666},{"lane":1,"time":122.77633333333333},{"lane":2,"time":122.86433333333332},{"lane":3,"time":122.96566666666666},{"lane":0,"time":123.04566666666668},{"lane":1,"time":123.13633333333334},{"lane":2,"time":123.23500000000001},{"lane":3,"time":123.30433333333335},{"lane":0,"time":123.40566666666666},{"lane":1,"time":123.48566666666667},{"lane":2,"time":123.56566666666666},{"lane":3,"time":123.64566666666667},{"lane":0,"time":123.74433333333334},{"lane":1,"time":123.82433333333333},{"lane":2,"time":123.92566666666667},{"lane":3,"time":124.00566666666666},{"lane":0,"time":124.08566666666667},{"lane":1,"time":124.17633333333333},{"lane":2,"time":124.275},{"lane":3,"time":124.35499999999999},{"lane":0,"time":124.44566666666665},{"lane":1,"time":124.52566666666667},{"lane":2,"time":124.62433333333334},{"lane":3,"time":124.68566666666666},{"lane":0,"time":124.80566666666667},{"lane":1,"time":124.86433333333332},{"lane":2,"time":124.98433333333332},{"lane":3,"time":125.04566666666668},{"lane":0,"time":125.16566666666665},{"lane":1,"time":125.20566666666667},{"lane":2,"time":125.32566666666668},{"lane":3,"time":125.39500000000001},{"lane":0,"time":125.63499999999999},{"lane":1,"time":125.68566666666666},{"lane":2,"time":125.77633333333333},{"lane":3,"time":125.92566666666667},{"lane":0,"time":126.02433333333335},{"lane":1,"time":126.08566666666667},{"lane":2,"time":126.28566666666666},{"lane":3,"time":126.32566666666668},{"lane":0,"time":126.435},{"lane":1,"time":126.62433333333334},{"lane":2,"time":126.80566666666667},{"lane":3,"time":126.96566666666666},{"lane":0,"time":127.155},{"lane":1,"time":127.26433333333333},{"lane":2,"time":127.435},{"lane":3,"time":127.45633333333333},{"lane":0,"time":127.51499999999999},{"lane":1,"time":127.61633333333333},{"lane":2,"time":127.68566666666666},{"lane":3,"time":127.77633333333333},{"lane":0,"time":127.93633333333332},{"lane":1,"time":128.08566666666667},{"lane":2,"time":128.14433333333332},{"lane":3,"time":128.26433333333333},{"lane":0,"time":128.33633333333333},{"lane":1,"time":128.435},{"lane":2,"time":128.50433333333334},{"lane":3,"time":128.595},{"lane":0,"time":128.66433333333333},{"lane":1,"time":128.72566666666665},{"lane":2,"time":128.72566666666665},{"lane":3,"time":128.80566666666667},{"lane":0,"time":128.88566666666668},{"lane":1,"time":128.96566666666666},{"lane":2,"time":129.04566666666668},{"lane":3,"time":129.12566666666666},{"lane":0,"time":129.22433333333333},{"lane":1,"time":129.30433333333335},{"lane":2,"time":129.40566666666666},{"lane":3,"time":129.475},{"lane":0,"time":129.595},{"lane":1,"time":129.65633333333332},{"lane":2,"time":129.76566666666668},{"lane":3,"time":129.84566666666666},{"lane":0,"time":129.94433333333333},{"lane":1,"time":130.05633333333333},{"lane":2,"time":130.13633333333334},{"lane":3,"time":130.24566666666666},{"lane":0,"time":130.32566666666668},{"lane":1,"time":130.42433333333332},{"lane":2,"time":130.49633333333333},{"lane":3,"time":130.60566666666668},{"lane":0,"time":130.675},{"lane":1,"time":130.76566666666668},{"lane":2,"time":130.85633333333334},{"lane":3,"time":130.94433333333333},{"lane":0,"time":131.02433333333335},{"lane":1,"time":131.115},{"lane":2,"time":131.20566666666667},{"lane":3,"time":131.28566666666666},{"lane":0,"time":131.38433333333333},{"lane":1,"time":131.46433333333334},{"lane":2,"time":131.56566666666666},{"lane":3,"time":131.64566666666667},{"lane":0,"time":131.74433333333334},{"lane":1,"time":131.835},{"lane":2,"time":131.92566666666667},{"lane":3,"time":132.00566666666666},{"lane":0,"time":132.08566666666667},{"lane":1,"time":132.195},{"lane":2,"time":132.26433333333333},{"lane":3,"time":132.36566666666667},{"lane":0,"time":132.44566666666665},{"lane":1,"time":132.53633333333335},{"lane":2,"time":132.62433333333334},{"lane":3,"time":132.70433333333332},{"lane":0,"time":132.795},{"lane":1,"time":132.88566666666668},{"lane":2,"time":132.96566666666666},{"lane":3,"time":133.05633333333333},{"lane":0,"time":133.14433333333332},{"lane":1,"time":133.22433333333333},{"lane":2,"time":133.30433333333335},{"lane":3,"time":133.395},{"lane":0,"time":133.475},{"lane":1,"time":133.54433333333333},{"lane":2,"time":133.62433333333334},{"lane":3,"time":133.715},{"lane":0,"time":133.795},{"lane":1,"time":133.86433333333332},{"lane":2,"time":133.96566666666666},{"lane":3,"time":134.04566666666668},{"lane":0,"time":134.13633333333334},{"lane":1,"time":134.20566666666667},{"lane":2,"time":134.315},{"lane":3,"time":134.38433333333333},{"lane":0,"time":134.48566666666667},{"lane":1,"time":134.54433333333333},{"lane":2,"time":134.66433333333333},{"lane":3,"time":134.72566666666665},{"lane":0,"time":134.835},{"lane":1,"time":134.90433333333334},{"lane":2,"time":135.01633333333334},{"lane":3,"time":135.08566666666667},{"lane":0,"time":135.195},{"lane":1,"time":135.26433333333333},{"lane":2,"time":135.36566666666667},{"lane":3,"time":135.435},{"lane":0,"time":135.54433333333333},{"lane":1,"time":135.60566666666668},{"lane":2,"time":135.715},{"lane":3,"time":135.755},{"lane":0,"time":135.88566666666668},{"lane":1,"time":136.00566666666666},{"lane":2,"time":136.24566666666666},{"lane":3,"time":136.32566666666668},{"lane":0,"time":136.395},{"lane":1,"time":136.56566666666666},{"lane":2,"time":136.65633333333332},{"lane":3,"time":136.72566666666665},{"lane":0,"time":136.93633333333332},{"lane":1,"time":136.96566666666666},{"lane":2,"time":137.08566666666667},{"lane":3,"time":137.32566666666668},{"lane":0,"time":137.42433333333332},{"lane":1,"time":137.94433333333333},{"lane":2,"time":138.115},{"lane":3,"time":138.61633333333333},{"lane":0,"time":138.76566666666668},{"lane":3,"time":139.10433333333333},{"lane":1,"time":139.44566666666665},{"lane":2,"time":139.62433333333334},{"lane":3,"time":139.68566666666666},{"lane":0,"time":139.77633333333333},{"lane":1,"time":139.96566666666666},{"lane":2,"time":140.00566666666666},{"lane":3,"time":140.10433333333333}];

        let bgm = new Audio('mc.mp4');
        let baseVolume = 0.5;

        let gameState = 'menu';
        let chart = [];
        let activeNotes = [];
        let score = 0, combo = 0, maxCombo = 0;
        let hp = 100;
        let gameStartTime = 0;
        let lastTime = 0;
        
        let perfects = 0, greats = 0, goods = 0, misses = 0;
        let recordedNotes = [];

        const keys = ['d', 'f', 'j', 'k'];
        const laneColors = [0x422fe3, 0x0d6efd, 0x00c3ff, 0x00ffcc]; // 푸른 계열 그라데이션
        const hexColors = ['#422fe3', '#0d6efd', '#00c3ff', '#00ffcc']; // 네온 효과용 Hex 색상
        const activeKeys = [false, false, false, false];

        const canvas = document.getElementById('gameCanvas');
        const scene = new THREE.Scene();
        scene.fog = new THREE.FogExp2(0x030308, 0.012);

        const camera = new THREE.PerspectiveCamera(65, window.innerWidth / window.innerHeight, 0.1, 200);
        camera.position.set(0, 8, 12); 
        camera.lookAt(0, 0, -20);

        const renderer = new THREE.WebGLRenderer({ canvas: canvas, antialias: true, alpha: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        renderer.setPixelRatio(window.devicePixelRatio);
        renderer.setClearColor(0x030308);

        const laneWidth = 3;
        const laneXs = [-4.5, -1.5, 1.5, 4.5];
        const hitZ = 5;       
        const spawnZ = -120;  
        const speed = 120; // 🚀 속도감 극한 상향 (사정없이 꽂힘)
        const trackY = 1.8; // 🔥 전체 높이를 화면 위로 올려 보기 편하게

        // 🔥 세련된 네온 시안(청록색) 빛나는 일자 판정선 🔥
        // 폭을 정확히 4개의 레인 너비에만 맞췄습니다 (약 11.8)
        const judgmentLineGeo = new THREE.BoxGeometry(11.8, 0.08, 0.2);
        const judgmentLineMat = new THREE.MeshBasicMaterial({ 
            color: 0x00e5ff, 
            transparent: true, 
            opacity: 0.7 
        }); 
        const judgmentLine = new THREE.Mesh(judgmentLineGeo, judgmentLineMat);
        judgmentLine.position.set(0, trackY, hitZ);
        scene.add(judgmentLine);

        for (let i = 0; i < 4; i++) {
            // 🔥 바닥 불빛 (스틱색) 투명도 0으로 완전히 삭제 🔥
            const padGeo = new THREE.PlaneGeometry(laneWidth - 0.2, 20);
            const padMat = new THREE.MeshBasicMaterial({ color: laneColors[i], transparent: true, opacity: 0.0, side: THREE.DoubleSide });
            const pad = new THREE.Mesh(padGeo, padMat);
            pad.rotation.x = -Math.PI / 2;
            pad.position.set(laneXs[i], trackY - 0.35, hitZ - 9.8);
            scene.add(pad);

            const trackGeo = new THREE.PlaneGeometry(laneWidth - 0.2, 200);
            const trackMat = new THREE.MeshBasicMaterial({ color: laneColors[i], transparent: true, opacity: 0.1 }); 
            const track = new THREE.Mesh(trackGeo, trackMat);
            track.rotation.x = -Math.PI / 2;
            track.position.set(laneXs[i], trackY - 0.45, -50); 
            scene.add(track);
        }

        const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
        scene.add(ambientLight);
        const hitLight = new THREE.PointLight(0xffffff, 0, 20);
        hitLight.position.set(0, trackY + 2, hitZ); 
        scene.add(hitLight);

        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });

        const sharedNoteGeo = new THREE.BoxGeometry(laneWidth - 0.4, 0.8, 1.5);
        const sharedNoteMats = laneColors.map(c => new THREE.MeshStandardMaterial({ color: 0xffffff, emissive: c, emissiveIntensity: 0.8 }));
        const sharedParticleGeo = new THREE.RingGeometry(0.5, 2, 32);
        const sharedParticleMats = laneColors.map(c => new THREE.MeshBasicMaterial({ color: c, transparent: true, side: THREE.DoubleSide }));

        class Note3D {
            constructor(lane, targetTime) {
                this.lane = lane;
                this.targetTime = targetTime;
                this.hit = false;
                this.missed = false;
                
                this.mesh = new THREE.Mesh(sharedNoteGeo, sharedNoteMats[this.lane]);
                this.mesh.position.set(laneXs[lane], trackY, spawnZ); 
                scene.add(this.mesh);
            }
            update(currentTime) {
                const timeDiff = this.targetTime - currentTime;
                this.mesh.position.z = hitZ - (timeDiff * speed);
                this.mesh.position.y = trackY + Math.sin(timeDiff * 10) * 0.2; 
            }
            hide() {
                if(this.mesh) this.mesh.visible = false;
            }
            destroy() {
                scene.remove(this.mesh);
            }
        }

        class HitParticle {
            constructor() {
                this.mesh = new THREE.Mesh(sharedParticleGeo, sharedParticleMats[0]);
                this.mesh.position.set(0, trackY + 0.1, hitZ);
                this.mesh.rotation.x = -Math.PI / 2;
                this.mesh.visible = false;
                scene.add(this.mesh);
                this.life = 0;
                this.active = false;
            }
            spawn(lane) {
                this.mesh.material = sharedParticleMats[lane];
                this.mesh.position.x = laneXs[lane];
                this.mesh.position.y = trackY + 0.1;
                this.mesh.scale.set(1, 1, 1);
                this.life = 1.0;
                this.mesh.material.opacity = 1.0;
                this.mesh.visible = true;
                this.active = true;
            }
            update(dt) {
                if(!this.active) return;
                this.life -= dt * 4;
                this.mesh.scale.addScalar(dt * 15);
                this.mesh.material.opacity = this.life;
                if (this.life <= 0) {
                    this.mesh.visible = false;
                    this.active = false;
                }
            }
        }

        const MAX_PARTICLES = 20; 
        const particlePool = [];
        for(let i=0; i<MAX_PARTICLES; i++) particlePool.push(new HitParticle());

        function spawnParticle(lane) {
            let p = particlePool.find(p => !p.active);
            if(!p) { p = new HitParticle(); particlePool.push(p); }
            p.spawn(lane);
        }

        let lastInputTime = 0;
        let spamCount = 0;
        let fallbackTime = 0; 

        // 오디오 칼싱크 보정
        function getCurrentTime() {
            if (gameState === 'playing' || gameState === 'recording') {
                if (bgm && !bgm.paused && bgm.currentTime > 0) {
                    return bgm.currentTime; 
                } else {
                    return fallbackTime; 
                }
            }
            return 0;
        }

        function handleKeyDown(idx) {
            if (activeKeys[idx]) return;
            activeKeys[idx] = true;

            // 🔥 키 누를 때 왼쪽 네온 가이드 켜기 🔥
            if(guideDOMs[idx]) {
                guideDOMs[idx].classList.add('guide-active');
                guideDOMs[idx].style.borderColor = hexColors[idx];
                guideDOMs[idx].style.color = hexColors[idx];
                guideDOMs[idx].style.textShadow = `0 0 15px ${hexColors[idx]}`;
                guideDOMs[idx].style.boxShadow = `0 0 15px ${hexColors[idx]} inset, 0 0 15px ${hexColors[idx]}`;
                
                // 🚀 키뷰어 타일 생성해서 위로 발사 🚀
                const panel = document.getElementById('keyGuidePanel');
                const tile = document.createElement('div');
                tile.className = 'viewer-tile';
                
                // 버튼 크기(80px) + 간격(15px) = 95px 간격으로 타일 X 좌표 세팅
                tile.style.left = (idx * 95) + 'px'; 
                tile.style.background = hexColors[idx];
                tile.style.boxShadow = `0 0 15px ${hexColors[idx]}`;
                
                panel.appendChild(tile);
                
                // 애니메이션(0.5초)이 끝나면 쓰레기(div) 삭제해서 렉 방지
                setTimeout(() => {
                    if (tile.parentElement) tile.parentElement.removeChild(tile);
                }, 500);
            }

            if (gameState === 'recording') {
                spawnParticle(idx);
                recordedNotes.push({ lane: idx, time: getCurrentTime() });
            } else if (gameState === 'playing') {
                processHit(idx);
            }
        }

        function handleKeyUp(idx) {
            activeKeys[idx] = false;

            // 🔥 키 뗄 때 왼쪽 네온 가이드 끄기 🔥
            if(guideDOMs[idx]) {
                guideDOMs[idx].classList.remove('guide-active');
                guideDOMs[idx].style.borderColor = 'rgba(255, 255, 255, 0.3)';
                guideDOMs[idx].style.color = 'rgba(255, 255, 255, 0.3)';
                guideDOMs[idx].style.textShadow = 'none';
                guideDOMs[idx].style.boxShadow = 'none';
            }
        }

        window.addEventListener('keydown', (e) => {
            const idx = keys.indexOf(e.key.toLowerCase());
            if (idx > -1) handleKeyDown(idx);
        });
        window.addEventListener('keyup', (e) => {
            const idx = keys.indexOf(e.key.toLowerCase());
            if (idx > -1) handleKeyUp(idx);
        });

        window.addEventListener('touchstart', (e) => {
            const w = window.innerWidth / 4;
            for(let i=0; i<e.changedTouches.length; i++) {
                const t = e.changedTouches[i];
                const idx = Math.floor(t.clientX / w);
                if(idx >= 0 && idx <= 3) handleKeyDown(idx);
            }
        });
        window.addEventListener('touchend', (e) => {
            [0,1,2,3].forEach(idx => handleKeyUp(idx));
        });

        function processHit(laneIdx) {
            const now = performance.now() / 1000;
            
            if (now - lastInputTime < 0.1) spamCount++;
            else spamCount = Math.max(0, spamCount - 1);
            lastInputTime = now;

            let hitSomething = false;
            const currentTime = getCurrentTime();

            for (let i = 0; i < activeNotes.length; i++) {
                const note = activeNotes[i];
                if (note.lane !== laneIdx || note.hit || note.missed) continue;

                const diff = Math.abs(note.targetTime - currentTime);
                
                // 🔥 빡센 칼판정 로직 (0.08초 지나면 무조건 MISS)
                if (diff < 0.08) { 
                    note.hit = true;
                    note.hide(); 
                    
                    hitSomething = true;
                    combo++;
                    maxCombo = Math.max(maxCombo, combo);
                    
                    spawnParticle(laneIdx);
                    hitLight.intensity = 1.5;
                    hitLight.color.setHex(laneColors[laneIdx]);
                    
                    showComboPop();
                    
                    if (diff < 0.03) { 
                        perfects++; score += 100; hp = Math.min(100, hp + 2); 
                        bgm.volume = 1.0; 
                        showJudgment("PERFECT", "#00e5ff");
                    }
                    else if (diff < 0.055) { 
                        greats++; score += 50; hp = Math.min(100, hp + 1); 
                        showJudgment("GREAT", "#00ffcc");
                    }
                    else { 
                        goods++; score += 10; 
                        showJudgment("GOOD", "#f1c40f");
                    }
                    
                    break;
                }
            }

            if (!hitSomething && spamCount > 3) {
                combo = 0;
                hp -= 5;
                bgm.volume = 0.2; 
                
                overloadWarning.style.display = 'block';
                setTimeout(() => overloadWarning.style.display = 'none', 500);
            }
            updateHUD();
        }

        function showComboPop() {
            centerComboOverlay.innerText = combo;
            centerComboOverlay.style.display = 'block';
            centerComboOverlay.classList.remove('combo-anim');
            requestAnimationFrame(() => {
                requestAnimationFrame(() => {
                    centerComboOverlay.classList.add('combo-anim');
                });
            });
        }

        function showJudgment(text, color) {
            judgmentOverlay.innerText = text;
            judgmentOverlay.style.color = color;
            judgmentOverlay.style.textShadow = `0 0 30px ${color}`;
            judgmentOverlay.style.display = 'block';
            judgmentOverlay.classList.remove('judge-anim');
            requestAnimationFrame(() => {
                requestAnimationFrame(() => {
                    judgmentOverlay.classList.add('judge-anim');
                });
            });
        }

        function updateHUD() {
            scoreDisplay.innerText = `SCORE: ${score}`;
            comboDisplay.innerText = `${combo} COMBO`;
            hpBar.style.width = `${Math.max(0, hp)}%`;
            hpBar.style.background = hp < 30 ? 'red' : 'linear-gradient(90deg, #ff0055, #00ffcc)';
        }

        function distributeLanes(rawPairs) {
            let lastLane = -1;
            let hand = 0; 
            
            return rawPairs.map((pair, idx) => {
                let timeDiff = idx > 0 ? pair.time - rawPairs[idx-1].time : 999;
                let newLane;
                
                if (timeDiff < 0.25) { 
                    hand = 1 - hand;
                    let possibleLanes = hand === 0 ? [0, 1] : [2, 3];
                    newLane = possibleLanes[Math.floor(Math.random() * possibleLanes.length)];
                } else { 
                    let attempts = 0;
                    do {
                        newLane = Math.floor(Math.random() * 4);
                        attempts++;
                    } while (newLane === lastLane && attempts < 10);
                    hand = newLane <= 1 ? 0 : 1; 
                }
                
                lastLane = newLane;
                return { lane: newLane, time: pair.time, hit: false, missed: false };
            });
        }

        document.getElementById('btnCustomMap').addEventListener('click', () => {
            const btn = document.getElementById('btnCustomMap');
            const originalText = btn.innerText;
            btn.innerText = "로딩 중...";

            bgm.load();
            
            setTimeout(() => {
                btn.innerText = originalText;
                chart = distributeLanes(COMPRESSED_CHART);
                startGame(chart);
            }, 500);
        });

        document.getElementById('btnEditor').addEventListener('click', () => {
            bgm.load();
            setTimeout(() => {
                startEditor();
            }, 500);
        });

        function startGame(mapData) {
            startPanel.style.display = 'none';
            hud.style.display = 'flex';
            
            activeNotes.forEach(n => n.destroy());
            particlePool.forEach(p => { p.active = false; p.mesh.visible = false; }); 
            
            score = 0; combo = 0; hp = 100; maxCombo = 0;
            perfects = 0; greats = 0; goods = 0; misses = 0;
            fallbackTime = 0; 
            updateHUD();

            activeNotes = mapData.map(n => new Note3D(n.lane, n.time));

            let count = 3;
            countdownOverlay.style.display = 'block';
            countdownOverlay.innerText = count;

            const intv = setInterval(() => {
                count--;
                if (count > 0) countdownOverlay.innerText = count;
                else {
                    clearInterval(intv);
                    countdownOverlay.style.display = 'none';
                    gameState = 'playing';
                    playMusic();
                }
            }, 1000);
        }

        function startEditor() {
            startPanel.style.display = 'none';
            modeIndicator.style.display = 'block';
            recordedNotes = [];
            
            let count = 3;
            countdownOverlay.style.display = 'block';
            countdownOverlay.innerText = count;

            const intv = setInterval(() => {
                count--;
                if (count > 0) countdownOverlay.innerText = count;
                else {
                    clearInterval(intv);
                    countdownOverlay.style.display = 'none';
                    gameState = 'recording';
                    playMusic();
                }
            }, 1000);
        }

        function playMusic() {
            bgm.currentTime = 0;
            bgm.volume = baseVolume;
            fallbackTime = 0;
            
            let playPromise = bgm.play();
            if (playPromise !== undefined) {
                playPromise.catch(e => {
                    console.warn("오디오 차단됨 - 강제 모드로 진행합니다.");
                });
            }

            bgm.onended = () => {
                if (gameState === 'recording') {
                    gameState = 'menu';
                    modeIndicator.style.display = 'none';
                    downloadMap();
                    location.reload();
                } else if (gameState === 'playing' && hp > 0) {
                    showResult();
                }
            };
        }

        function showMsg(text) {
            document.getElementById('msgText').innerText = text;
            document.getElementById('msgBox').style.display = 'block';
        }

        function downloadMap() {
            const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(recordedNotes));
            const dl = document.createElement('a');
            dl.setAttribute("href", dataStr);
            dl.setAttribute("download", "plum_custom_chart.json");
            dl.click();
            showMsg("녹화 완료! 채보 파일이 다운로드 되었습니다.");
        }

        function showResult(cleared = true) {
            gameState = 'result';
            hud.style.display = 'none';
            resultPanel.style.display = 'block';
            document.getElementById('resultTitle').innerText = cleared ? "STAGE CLEAR" : "GAME OVER";
            document.getElementById('resultTitle').style.color = cleared ? "#00e5ff" : "#ff0055";
            
            document.getElementById('resScore').innerText = score;
            document.getElementById('resCombo').innerText = maxCombo;
            document.getElementById('resPerfect').innerText = perfects;
            document.getElementById('resGreat').innerText = greats;
            document.getElementById('resGood').innerText = goods;
            document.getElementById('resMiss').innerText = misses;
            
            const totalHits = perfects + greats + goods + misses;
            let acc = 0;
            if(totalHits > 0) acc = ((perfects * 100 + greats * 80 + goods * 50) / (totalHits * 100)) * 100;
            document.getElementById('resAcc').innerText = acc.toFixed(2) + "%";
        }

        function animate(time) {
            requestAnimationFrame(animate);
            let dt = (time - lastTime) / 1000;
            lastTime = time;

            hitLight.intensity = Math.max(0, hitLight.intensity - dt * 5);

            if (gameState === 'playing') {
                fallbackTime += dt; 
                const currentTime = getCurrentTime();
                let allDone = true;

                for (let i = 0; i < activeNotes.length; i++) {
                    const note = activeNotes[i];
                    if (!note.hit && !note.missed) {
                        allDone = false;
                        note.update(currentTime);
                        
                        // 빡센 미스 판정
                        if (currentTime - note.targetTime > 0.08) {
                            note.missed = true;
                            note.hide(); 
                            combo = 0;
                            misses++;
                            bgm.volume = 0.2; 
                            showJudgment("MISS", "#ff0055");
                            
                            if (!invincibleMode.checked) {
                                hp -= 10;
                                if (hp <= 0) { gameState = 'menu'; bgm.pause(); showResult(false); }
                            }
                            updateHUD();
                        }
                    }
                }
                if (allDone && activeNotes.length > 0 && currentTime > activeNotes[activeNotes.length-1].targetTime + 2) showResult();
            }

            for (let i = 0; i < particlePool.length; i++) {
                particlePool[i].update(dt);
            }

            renderer.render(scene, camera);
        }

        lastTime = performance.now();
        animate(lastTime);
    </script>
</body>
</html>
