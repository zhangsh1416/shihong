---
layout: none
permalink: /tiktok-upload-demo/
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Upload to TikTok - Demo App</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: #f0f2f5;
            min-height: 100vh;
            padding: 20px;
        }
        
        .header {
            background: white;
            padding: 20px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            margin-bottom: 30px;
            border-radius: 8px;
        }
        
        .header h1 {
            color: #333;
            font-size: 28px;
            margin-bottom: 5px;
        }
        
        .header .url {
            color: #666;
            font-size: 14px;
            font-family: monospace;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .card {
            background: white;
            border-radius: 12px;
            padding: 30px;
            margin-bottom: 20px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        
        .card h2 {
            color: #333;
            margin-bottom: 20px;
            font-size: 22px;
            display: flex;
            align-items: center;
        }
        
        .step-badge {
            background: #fe2c55;
            color: white;
            width: 32px;
            height: 32px;
            border-radius: 50%;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            margin-right: 12px;
            font-size: 16px;
        }
        
        .btn {
            padding: 14px 32px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .btn-primary {
            background: #fe2c55;
            color: white;
        }
        
        .btn-primary:hover:not(:disabled) {
            background: #d91d45;
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(254, 44, 85, 0.3);
        }
        
        .btn-secondary {
            background: #4a90e2;
            color: white;
        }
        
        .btn-secondary:hover:not(:disabled) {
            background: #357ab8;
            transform: translateY(-2px);
        }
        
        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .status-box {
            padding: 15px;
            border-radius: 8px;
            margin: 15px 0;
            display: none;
        }
        
        .status-box.show {
            display: block;
        }
        
        .status-box.success {
            background: #e8f5e9;
            border: 2px solid #4caf50;
            color: #2e7d32;
        }
        
        .status-box.info {
            background: #e3f2fd;
            border: 2px solid #2196f3;
            color: #1565c0;
        }
        
        .file-input-wrapper {
            position: relative;
            display: inline-block;
            width: 100%;
        }
        
        .file-input-wrapper input[type="file"] {
            position: absolute;
            opacity: 0;
            width: 100%;
            height: 100%;
            cursor: pointer;
        }
        
        .file-input-label {
            display: block;
            padding: 40px;
            border: 3px dashed #ddd;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
            background: #fafafa;
        }
        
        .file-input-label:hover {
            border-color: #fe2c55;
            background: #fff5f7;
        }
        
        .file-input-label.has-file {
            border-color: #4caf50;
            background: #f1f8f4;
        }
        
        .selected-file {
            margin-top: 15px;
            padding: 15px;
            background: #f5f5f5;
            border-radius: 8px;
            display: none;
        }
        
        .selected-file.show {
            display: block;
        }
        
        .progress-container {
            margin: 20px 0;
            display: none;
        }
        
        .progress-container.show {
            display: block;
        }
        
        .progress-bar-bg {
            width: 100%;
            height: 8px;
            background: #e0e0e0;
            border-radius: 4px;
            overflow: hidden;
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #fe2c55, #ff6b6b);
            width: 0%;
            transition: width 0.3s;
        }
        
        .progress-text {
            margin-top: 10px;
            color: #666;
            font-size: 14px;
            text-align: center;
        }
        
        .upload-log {
            background: #1e1e1e;
            color: #00ff00;
            padding: 20px;
            border-radius: 8px;
            font-family: 'Courier New', monospace;
            font-size: 13px;
            max-height: 300px;
            overflow-y: auto;
            display: none;
        }
        
        .upload-log.show {
            display: block;
        }
        
        .log-entry {
            margin: 5px 0;
            line-height: 1.6;
        }
        
        .log-timestamp {
            color: #888;
        }
        
        .log-success {
            color: #00ff00;
        }
        
        .log-info {
            color: #00bfff;
        }
        
        .user-info {
            display: none;
            padding: 15px;
            background: #f5f5f5;
            border-radius: 8px;
            margin: 15px 0;
        }
        
        .user-info.show {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .user-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: #fe2c55;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
        }
        
        .scopes-list {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 10px;
        }
        
        .scope-badge {
            background: #fff;
            border: 2px solid #fe2c55;
            color: #fe2c55;
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 13px;
            font-weight: 600;
        }
        
        .tiktok-icon {
            width: 24px;
            height: 24px;
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>🎬 Video Upload to TikTok</h1>
        <div class="url">https://zhangsh1416.github.io/shihong/</div>
    </div>

    <div class="container">
        <!-- Step 1: Login -->
        <div class="card">
            <h2>
                <span class="step-badge">1</span>
                Connect with TikTok
            </h2>
            
            <div id="loginStatus" class="status-box info show">
                Click the button below to authenticate with TikTok and grant upload permissions.
            </div>
            
            <div class="scopes-list">
                <span class="scope-badge">user.info.basic</span>
                <span class="scope-badge">video.upload</span>
                <span class="scope-badge">video.publish</span>
            </div>
            
            <div style="margin-top: 20px;">
                <button id="loginBtn" class="btn btn-primary" onclick="handleLogin()">
                    <svg class="tiktok-icon" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M19.59 6.69a4.83 4.83 0 0 1-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 0 1-5.2 1.74 2.89 2.89 0 0 1 2.31-4.64 2.93 2.93 0 0 1 .88.13V9.4a6.84 6.84 0 0 0-1-.05A6.33 6.33 0 0 0 5 20.1a6.34 6.34 0 0 0 10.86-4.43v-7a8.16 8.16 0 0 0 4.77 1.52v-3.4a4.85 4.85 0 0 1-1-.1z"/>
                    </svg>
                    Login with TikTok
                </button>
            </div>
            
            <div id="userInfo" class="user-info">
                <div class="user-avatar">👤</div>
                <div>
                    <strong id="userName">Demo User</strong><br>
                    <small style="color: #666;">Connected • Access granted</small>
                </div>
            </div>
        </div>

        <!-- Step 2: Select File -->
        <div class="card" id="uploadSection" style="opacity: 0.5; pointer-events: none;">
            <h2>
                <span class="step-badge">2</span>
                Select Video File
            </h2>
            
            <div class="file-input-wrapper">
                <input type="file" id="fileInput" accept="video/*" onchange="handleFileSelect(event)">
                <label class="file-input-label" id="fileLabel">
                    <div style="font-size: 48px; margin-bottom: 10px;">📹</div>
                    <div style="font-size: 16px; color: #333; font-weight: 600;">Click to select video</div>
                    <div style="font-size: 14px; color: #666; margin-top: 5px;">MP4, MOV, AVI (Max 4GB)</div>
                </label>
            </div>
            
            <div id="selectedFile" class="selected-file">
                <strong>Selected file:</strong>
                <div id="fileName" style="margin-top: 5px; color: #666;"></div>
            </div>
        </div>

        <!-- Step 3: Upload -->
        <div class="card" id="uploadActionSection" style="opacity: 0.5; pointer-events: none;">
            <h2>
                <span class="step-badge">3</span>
                Upload to TikTok
            </h2>
            
            <button id="uploadBtn" class="btn btn-secondary" onclick="handleUpload()">
                <span>🚀 Start Upload</span>
            </button>
            
            <div id="progressContainer" class="progress-container">
                <div class="progress-bar-bg">
                    <div id="progressBar" class="progress-bar"></div>
                </div>
                <div id="progressText" class="progress-text">Preparing upload...</div>
            </div>
            
            <div id="uploadStatus" class="status-box"></div>
        </div>

        <!-- Step 4: Upload Log -->
        <div class="card" id="logSection" style="display: none;">
            <h2>
                <span class="step-badge">4</span>
                Upload Process Log
            </h2>
            
            <div id="uploadLog" class="upload-log"></div>
        </div>
    </div>

    <script>
        let isLoggedIn = false;
        let selectedFile = null;
        let uploadLog = [];

        function addLog(message, type = 'info') {
            const timestamp = new Date().toLocaleTimeString();
            const logEntry = `<div class="log-entry"><span class="log-timestamp">[${timestamp}]</span> <span class="log-${type}">${message}</span></div>`;
            uploadLog.push(logEntry);
            
            const logContainer = document.getElementById('uploadLog');
            logContainer.innerHTML = uploadLog.join('');
            logContainer.scrollTop = logContainer.scrollHeight;
        }

        function handleLogin() {
            const loginBtn = document.getElementById('loginBtn');
            const loginStatus = document.getElementById('loginStatus');
            const userInfo = document.getElementById('userInfo');
            const uploadSection = document.getElementById('uploadSection');
            
            loginBtn.disabled = true;
            loginBtn.innerHTML = '<span>🔄 Connecting...</span>';
            
            loginStatus.className = 'status-box info show';
            loginStatus.textContent = '🔄 Redirecting to TikTok authorization...';
            
            setTimeout(() => {
                loginStatus.textContent = '🔄 User granting permissions...';
            }, 1000);
            
            setTimeout(() => {
                loginStatus.textContent = '🔄 Receiving authorization token...';
            }, 2000);
            
            setTimeout(() => {
                isLoggedIn = true;
                loginStatus.className = 'status-box success show';
                loginStatus.innerHTML = '✅ <strong>Successfully connected to TikTok!</strong><br>Scopes granted: user.info.basic, video.upload, video.publish';
                
                userInfo.classList.add('show');
                document.getElementById('userName').textContent = 'Demo User (@demouser)';
                
                loginBtn.innerHTML = '✓ Connected';
                loginBtn.style.background = '#4caf50';
                
                uploadSection.style.opacity = '1';
                uploadSection.style.pointerEvents = 'auto';
                
                addLog('✓ OAuth authentication successful', 'success');
                addLog('✓ Access token received: act.demo_***', 'success');
                addLog('✓ Scopes verified: video.upload, video.publish', 'info');
            }, 3000);
        }

        function handleFileSelect(event) {
            const file = event.target.files[0];
            if (!file) return;
            
            selectedFile = file;
            
            const fileLabel = document.getElementById('fileLabel');
            const selectedFileDiv = document.getElementById('selectedFile');
            const fileName = document.getElementById('fileName');
            const uploadActionSection = document.getElementById('uploadActionSection');
            
            fileLabel.classList.add('has-file');
            fileLabel.innerHTML = `
                <div style="font-size: 48px; margin-bottom: 10px;">✓</div>
                <div style="font-size: 16px; color: #4caf50; font-weight: 600;">File selected</div>
            `;
            
            const fileSizeMB = (file.size / 1024 / 1024).toFixed(2);
            fileName.innerHTML = `<strong>${file.name}</strong><br><small>Size: ${fileSizeMB} MB • Type: ${file.type}</small>`;
            selectedFileDiv.classList.add('show');
            
            uploadActionSection.style.opacity = '1';
            uploadActionSection.style.pointerEvents = 'auto';
            
            addLog(`✓ File selected: ${file.name} (${fileSizeMB} MB)`, 'success');
        }

        function handleUpload() {
            if (!selectedFile) return;
            
            const uploadBtn = document.getElementById('uploadBtn');
            const progressContainer = document.getElementById('progressContainer');
            const progressBar = document.getElementById('progressBar');
            const progressText = document.getElementById('progressText');
            const uploadStatus = document.getElementById('uploadStatus');
            const logSection = document.getElementById('logSection');
            const uploadLog = document.getElementById('uploadLog');
            
            uploadBtn.disabled = true;
            uploadBtn.innerHTML = '<span>⏳ Uploading...</span>';
            
            progressContainer.classList.add('show');
            logSection.style.display = 'block';
            uploadLog.classList.add('show');
            
            // Phase 1: Initialize
            addLog('→ POST /share/video/upload/', 'info');
            addLog('→ Requesting upload URLs...', 'info');
            
            setTimeout(() => {
                progressBar.style.width = '20%';
                progressText.textContent = 'Phase 1: Initializing upload session...';
                addLog('✓ Upload session created', 'success');
                addLog('✓ Publish ID: pub_demo_12345', 'success');
                addLog('✓ Upload URL received', 'success');
            }, 1000);
            
            // Phase 2: Upload chunks
            setTimeout(() => {
                progressBar.style.width = '40%';
                progressText.textContent = 'Phase 2: Uploading video chunks (1/3)...';
                addLog('→ PUT /upload/chunk/1', 'info');
            }, 2000);
            
            setTimeout(() => {
                progressBar.style.width = '60%';
                progressText.textContent = 'Phase 2: Uploading video chunks (2/3)...';
                addLog('✓ Chunk 1 uploaded', 'success');
                addLog('→ PUT /upload/chunk/2', 'info');
            }, 3500);
            
            setTimeout(() => {
                progressBar.style.width = '80%';
                progressText.textContent = 'Phase 2: Uploading video chunks (3/3)...';
                addLog('✓ Chunk 2 uploaded', 'success');
                addLog('→ PUT /upload/chunk/3', 'info');
            }, 5000);
            
            // Phase 3: Finalize
            setTimeout(() => {
                progressBar.style.width = '90%';
                progressText.textContent = 'Phase 3: Finalizing upload...';
                addLog('✓ All chunks uploaded', 'success');
                addLog('→ POST /share/video/publish/', 'info');
            }, 6500);
            
            // Complete
            setTimeout(() => {
                progressBar.style.width = '100%';
                progressText.textContent = '✓ Upload completed successfully!';
                
                uploadStatus.className = 'status-box success show';
                uploadStatus.innerHTML = `
                    <strong>✅ Video uploaded to TikTok Draft!</strong><br>
                    <small>Video ID: vid_demo_67890</small><br>
                    <small>The video is now in your TikTok drafts and ready to publish.</small>
                `;
                
                uploadBtn.innerHTML = '✓ Upload Complete';
                uploadBtn.style.background = '#4caf50';
                
                addLog('✓ Video published to draft', 'success');
                addLog('✓ Video ID: vid_demo_67890', 'success');
                addLog('✓ Status: PROCESSING_UPLOAD → PUBLISH_COMPLETE', 'success');
                addLog('═══════════════════════════════════════', 'success');
                addLog('✓ UPLOAD SUCCESSFUL - Video ready in TikTok app', 'success');
            }, 8000);
        }
    </script>
</body>
</html>
