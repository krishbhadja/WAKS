<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KALI CERAMIC LLP - Weighbridge Kiosk</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            touch-action: manipulation;
            overflow: hidden;
        }

        .kiosk-container {
            width: 100%;
            max-width: 1200px;
            height: 700px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
        }

        .header {
            background: linear-gradient(45deg, #2c3e50, #3498db);
            color: white;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .back-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
        }

        .company-info {
            display: flex;
            align-items: center;
        }

        .logo {
            width: 50px;
            height: 50px;
            background: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            font-size: 20px;
            color: #3498db;
            font-weight: bold;
        }

        .company-name {
            font-size: 1.6em;
            font-weight: bold;
        }

        .subtitle {
            font-size: 0.9em;
            opacity: 0.9;
        }

        .history-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .history-btn:hover {
            background: rgba(255, 255, 255, 0.3);
        }

        .main-content {
            flex: 1;
            display: flex;
            overflow: hidden;
        }

        .screen-container {
            width: 100%;
            height: 100%;
            position: relative;
        }

        .screen {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: none;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 20px;
            transition: transform 0.4s ease;
            background: white;
        }

        .screen.active {
            display: flex;
            transform: translateX(0);
        }

        .button-group {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin: 20px 0;
            width: 100%;
            max-width: 500px;
        }

        .btn {
            padding: 18px;
            font-size: 1.4em;
            font-weight: bold;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
            text-transform: uppercase;
            width: 100%;
        }

        .btn:active {
            transform: scale(0.98);
        }

        .btn-primary {
            background: linear-gradient(45deg, #3498db, #2980b9);
            color: white;
        }

        .btn-success {
            background: linear-gradient(45deg, #27ae60, #229954);
            color: white;
        }

        .btn-warning {
            background: linear-gradient(45deg, #f39c12, #e67e22);
            color: white;
        }

        .btn-info {
            background: linear-gradient(45deg, #17a2b8, #138496);
            color: white;
        }

        .btn-danger {
            background: linear-gradient(45deg, #e74c3c, #c0392b);
            color: white;
        }

        .input-group {
            margin: 20px 0;
            text-align: center;
            width: 100%;
            max-width: 500px;
        }

        .input-label {
            font-size: 1.3em;
            font-weight: bold;
            margin-bottom: 15px;
            color: #2c3e50;
        }

        .text-input {
            padding: 15px;
            font-size: 1.4em;
            border: 3px solid #3498db;
            border-radius: 10px;
            text-align: center;
            width: 100%;
            margin-bottom: 15px;
        }

        .demo-numbers {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 15px;
            justify-content: center;
        }

        .demo-btn {
            padding: 8px 15px;
            background: #3498db;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9em;
        }

        .weight-display {
            background: #2c3e50;
            color: white;
            padding: 25px;
            border-radius: 15px;
            font-size: 2.2em;
            font-weight: bold;
            margin: 20px 0;
            text-align: center;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 400px;
        }

        .weight-info {
            font-size: 1.2em;
            margin: 10px 0;
            padding: 10px;
            border-radius: 8px;
            background: #f39c12;
            color: white;
            text-align: center;
        }

        .slip-preview {
            background: white;
            border: 2px solid #2c3e50;
            border-radius: 10px;
            padding: 20px;
            margin: 15px 0;
            font-family: monospace;
            font-size: 1.1em;
            line-height: 1.6;
            width: 100%;
            max-width: 800px;
            max-height: 500px;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
            overflow-y: auto;
        }

        .slip-header {
            text-align: center;
            border-bottom: 2px solid #000;
            padding-bottom: 10px;
            margin-bottom: 15px;
        }

        .slip-company {
            font-weight: bold;
            font-size: 1.4em;
            margin-bottom: 5px;
        }

        .slip-address {
            font-size: 0.9em;
            margin-bottom: 10px;
        }

        .slip-details {
            width: 100%;
            border-collapse: collapse;
            margin: 10px 0;
        }

        .slip-details td {
            padding: 8px 5px;
            vertical-align: top;
            border-bottom: 1px dashed #ccc;
        }

        .slip-details td:nth-child(odd) {
            font-weight: bold;
            width: 40%;
        }

        .slip-footer {
            margin-top: 15px;
            padding-top: 10px;
            border-top: 1px dashed #000;
            text-align: center;
            font-style: italic;
        }

        .signature-area {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }

        .signature-box {
            text-align: center;
            width: 45%;
        }

        .signature-line {
            border-top: 1px solid #000;
            margin-top: 60px;
            padding-top: 5px;
        }

        .status-indicator {
            background: #27ae60;
            color: white;
            padding: 10px 20px;
            border-radius: 25px;
            margin: 15px 0;
            font-weight: bold;
            text-align: center;
        }

        .timer {
            position: absolute;
            top: 20px;
            right: 20px;
            background: #e74c3c;
            color: white;
            padding: 10px 20px;
            border-radius: 25px;
            font-size: 1.2em;
            font-weight: bold;
            z-index: 100;
        }

        .payment-options {
            display: flex;
            gap: 15px;
            margin: 20px 0;
            flex-wrap: wrap;
            justify-content: center;
        }

        .payment-btn {
            padding: 15px 25px;
            font-size: 1.2em;
            font-weight: bold;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            min-width: 120px;
        }

        .payment-btn:active {
            transform: scale(0.98);
        }

        .cash-btn {
            background: linear-gradient(45deg, #27ae60, #229954);
            color: white;
        }

        .upi-btn {
            background: linear-gradient(45deg, #3498db, #2980b9);
            color: white;
        }

        .scenario-info {
            background: #f8f9fa;
            border-radius: 10px;
            padding: 15px;
            margin: 15px 0;
            border-left: 5px solid #3498db;
            text-align: center;
        }

        .scenario-title {
            font-weight: bold;
            color: #2c3e50;
            margin-bottom: 10px;
            font-size: 1.2em;
        }

        h2 {
            font-size: 2em;
            margin-bottom: 25px;
            color: #2c3e50;
            text-align: center;
        }

        .nav-dots {
            position: absolute;
            bottom: 15px;
            left: 0;
            width: 100%;
            display: flex;
            justify-content: center;
            gap: 10px;
        }

        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #ccc;
            cursor: pointer;
        }

        .dot.active {
            background: #3498db;
        }

        .input-method-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin: 20px 0;
            width: 100%;
            max-width: 700px;
        }

        .input-method {
            background: white;
            border: 2px solid #3498db;
            border-radius: 15px;
            padding: 20px;
            width: 200px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.1);
        }

        .input-method:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 20px rgba(0, 0, 0, 0.15);
        }

        .input-method i {
            font-size: 3em;
            margin-bottom: 15px;
            color: #3498db;
        }

        .input-method h3 {
            margin-bottom: 10px;
            color: #2c3e50;
        }

        .input-method p {
            color: #7f8c8d;
            font-size: 0.9em;
        }

        .voice-recognition {
            border-color: #27ae60;
        }

        .voice-recognition i {
            color: #27ae60;
        }

        .bill-recognition {
            border-color: #f39c12;
        }

        .bill-recognition i {
            color: #f39c12;
        }

        .ai-interaction {
            border-color: #9b59b6;
        }

        .ai-interaction i {
            color: #9b59b6;
        }

        .recording-indicator {
            background: #e74c3c;
            color: white;
            padding: 10px;
            border-radius: 5px;
            margin: 15px 0;
            display: none;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }

        .phone-slot {
            width: 300px;
            height: 100px;
            background: #f1f2f6;
            border: 3px dashed #7f8c8d;
            border-radius: 15px;
            margin: 20px 0;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }

        .phone-slot i {
            font-size: 2.5em;
            color: #7f8c8d;
            margin-bottom: 10px;
        }

        .phone-slot p {
            color: #7f8c8d;
        }

        .bill-upload {
            width: 300px;
            height: 200px;
            background: #f1f2f6;
            border: 3px dashed #7f8c8d;
            border-radius: 15px;
            margin: 20px 0;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            cursor: pointer;
        }

        .bill-upload i {
            font-size: 2.5em;
            color: #7f8c8d;
            margin-bottom: 10px;
        }

        .bill-upload p {
            color: #7f8c8d;
        }

        .fixed-charge-note {
            background: #ffeaa7;
            padding: 10px;
            border-radius: 8px;
            margin: 15px 0;
            text-align: center;
            font-weight: bold;
        }

        .language-options {
            display: flex;
            flex-direction: row;
            gap: 20px;
            margin: 30px 0;
            width: 100%;
            justify-content: center;
        }

        .language-btn {
            padding: 25px;
            font-size: 1.6em;
            font-weight: bold;
            border: none;
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
            width: 250px;
            height: 150px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .language-btn:active {
            transform: scale(0.98);
        }

        .language-btn i {
            font-size: 2em;
            margin-bottom: 15px;
        }

        .hindi-btn {
            background: linear-gradient(45deg, #ff7e5f, #feb47b);
            color: white;
        }

        .english-btn {
            background: linear-gradient(45deg, #3498db, #2980b9);
            color: white;
        }

        .gujarati-btn {
            background: linear-gradient(45deg, #27ae60, #229954);
            color: white;
        }

        .swipe-instruction {
            position: absolute;
            bottom: 50px;
            width: 100%;
            text-align: center;
            color: #7f8c8d;
            font-style: italic;
        }

        .swipe-instruction i {
            margin: 0 10px;
            font-size: 1.2em;
        }

        .password-prompt {
            background: #f8f9fa;
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            width: 100%;
            max-width: 400px;
            text-align: center;
        }

        .password-input {
            padding: 15px;
            font-size: 1.4em;
            border: 3px solid #3498db;
            border-radius: 10px;
            text-align: center;
            width: 100%;
            margin-bottom: 15px;
        }

        .material-calculation {
            background: #e8f4fc;
            border-radius: 10px;
            padding: 15px;
            margin: 15px 0;
            width: 100%;
            max-width: 500px;
        }

        .calculation-formula {
            font-family: monospace;
            font-size: 1.2em;
            margin: 10px 0;
            text-align: center;
        }

        .purpose-buttons {
            display: flex;
            flex-direction: column;
            gap: 15px;
            width: 100%;
            max-width: 500px;
        }

        .purpose-btn {
            padding: 20px;
            font-size: 1.3em;
            font-weight: bold;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            text-align: center;
        }

        .purpose-btn:active {
            transform: scale(0.98);
        }

        .purpose-inbound {
            background: linear-gradient(45deg, #3498db, #2980b9);
            color: white;
        }

        .purpose-outbound {
            background: linear-gradient(45deg, #f39c12, #e67e22);
            color: white;
        }

        .vehicle-input-group {
            margin: 20px 0;
            text-align: center;
            width: 100%;
            max-width: 500px;
        }

        .vehicle-input {
            padding: 15px;
            font-size: 1.8em;
            border: 3px solid #3498db;
            border-radius: 10px;
            text-align: center;
            width: 100%;
            margin-bottom: 15px;
        }

        .submit-btn {
            padding: 15px 30px;
            font-size: 1.4em;
            font-weight: bold;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            background: linear-gradient(45deg, #27ae60, #229954);
            color: white;
            margin-top: 15px;
        }

        .submit-btn:active {
            transform: scale(0.98);
        }

        @media (max-width: 900px) {
            .kiosk-container {
                height: 100vh;
                border-radius: 0;
            }
            
            .btn {
                padding: 15px;
                font-size: 1.2em;
            }
            
            h2 {
                font-size: 1.8em;
            }
            
            .text-input {
                font-size: 1.2em;
            }
            
            .input-method-container {
                flex-direction: column;
                align-items: center;
            }
            
            .input-method {
                width: 100%;
                max-width: 300px;
            }
            
            .language-options {
                flex-direction: column;
                align-items: center;
            }
            
            .language-btn {
                width: 100%;
                max-width: 300px;
                height: 120px;
            }
            
            .slip-preview {
                font-size: 0.9em;
                padding: 15px;
            }
            
            .vehicle-input {
                font-size: 1.4em;
            }
        }
    </style>
</head>
<body>
    <div class="kiosk-container">
        <div class="header">
            <div class="header-left">
                <button class="back-btn" id="backBtn" style="display: none;">
                    <i class="fas fa-arrow-left"></i>
                </button>
                <div class="company-info">
                    <div class="logo">KC</div>
                    <div>
                        <div class="company-name">KALI CERAMIC LLP</div>
                        <div class="subtitle">Automated Weighbridge System</div>
                    </div>
                </div>
            </div>
            <button class="history-btn" id="historyBtn">
                <i class="fas fa-history"></i> History
            </button>
        </div>

        <div class="timer" id="timer" style="display: none;">Auto Return: <span id="countdown">8</span>s</div>

        <div class="main-content">
            <div class="screen-container">
                <!-- Splash Screen -->
                <div class="screen active" id="splashScreen">
                    <div class="company-info" style="flex-direction: column; text-align: center;">
                        <div class="logo" style="width: 80px; height: 80px; font-size: 30px; margin-bottom: 20px;">KC</div>
                        <div class="company-name" style="font-size: 2.5em;">KALI CERAMIC LLP</div>
                        <div class="subtitle" style="font-size: 1.2em;">Weighbridge Automation System</div>
                    </div>
                    <div class="status-indicator" style="margin-top: 30px;">
                        Loading System...
                    </div>
                </div>

                <!-- Language Selection Screen -->
                <div class="screen" id="languageScreen">
                    <h2>भाषा चुनें / Select Language / ભાષા પસંદ કરો</h2>
                    <div class="language-options">
                        <button class="language-btn hindi-btn" onclick="selectLanguage('hindi')">
                            <i class="fas fa-language"></i>
                            हिन्दी
                        </button>
                        <button class="language-btn english-btn" onclick="selectLanguage('english')">
                            <i class="fas fa-language"></i>
                            English
                        </button>
                        <button class="language-btn gujarati-btn" onclick="selectLanguage('gujarati')">
                            <i class="fas fa-language"></i>
                            ગુજરાતી
                        </button>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Direction Selection Screen -->
                <div class="screen" id="directionScreen">
                    <h2 id="directionTitle">Select Direction</h2>
                    <div class="button-group">
                        <button class="btn btn-primary" onclick="selectDirection('IN')" id="inboundBtn">
                            अंदर / ENTRY / અંદર
                        </button>
                        <button class="btn btn-warning" onclick="selectDirection('OUT')" id="outboundBtn">
                            बाहर / EXIT / બહાર
                        </button>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Purpose Selection Screen -->
                <div class="screen" id="purposeScreen">
                    <h2 id="purposeTitle">Select Purpose</h2>
                    <div class="purpose-buttons" id="purposeButtons">
                        <!-- Purpose buttons will be dynamically added here -->
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Vehicle Number Entry Screen -->
                <div class="screen" id="vehicleScreen">
                    <h2 id="vehicleTitle">Enter Vehicle Number</h2>
                    <div class="vehicle-input-group">
                        <input type="text" class="vehicle-input" id="vehicleNumber" placeholder="GJ01AB1234" maxlength="15">
                        <div class="demo-numbers">
                            <button class="demo-btn" onclick="setDemoNumber()" id="demoBtn">
                                DEMO NUMBER
                            </button>
                        </div>
                        <button class="submit-btn" onclick="submitVehicleNumber()" id="submitVehicleBtn">
                            SUBMIT
                        </button>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Weight Detection Screen -->
                <div class="screen" id="weightScreen">
                    <h2 id="weightTitle">Weight Measurement</h2>
                    <div class="weight-display" id="weightDisplay">0 KG</div>
                    <div class="weight-info" id="weightInfo"></div>
                    <div class="status-indicator" id="weightStatus">Please wait for weight measurement...</div>
                    <button class="btn btn-primary" onclick="processWeight()" id="processWeightBtn">
                        Continue
                    </button>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Input Method Selection Screen -->
                <div class="screen" id="inputMethodScreen">
                    <h2 id="inputMethodTitle">Provide Supplier & Material Details</h2>
                    <div class="fixed-charge-note" id="fixedChargeNote">
                        Fixed Charge: ₹100 if material weight > 0
                    </div>
                    <div class="input-method-container">
                        <div class="input-method voice-recognition" onclick="selectInputMethod('voice')">
                            <i class="fas fa-microphone"></i>
                            <h3 id="voiceTitle">Voice Input</h3>
                            <p id="voiceDesc">Speak supplier and material details</p>
                        </div>
                        <div class="input-method bill-recognition" onclick="selectInputMethod('bill')">
                            <i class="fas fa-receipt"></i>
                            <h3 id="billTitle">Bill Recognition</h3>
                            <p id="billDesc">Upload or scan your bill</p>
                        </div>
                        <div class="input-method ai-interaction" onclick="selectInputMethod('ai')">
                            <i class="fas fa-phone-alt"></i>
                            <h3 id="aiTitle">AI Interaction</h3>
                            <p id="aiDesc">Talk to our AI assistant</p>
                        </div>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Voice Input Screen -->
                <div class="screen" id="voiceInputScreen">
                    <h2 id="voiceInputTitle">Voice Input</h2>
                    <div class="input-group">
                        <div class="input-label" id="voiceInputLabel">Speak clearly into the microphone</div>
                        <div class="recording-indicator" id="recordingIndicator">
                            <i class="fas fa-microphone"></i> Recording...
                        </div>
                        <button class="btn btn-primary" onclick="startVoiceRecognition()" id="startVoiceBtn">
                            <i class="fas fa-microphone"></i> Start Recording
                        </button>
                        <button class="btn btn-success" onclick="processVoiceInput()" style="display:none" id="processVoiceBtn">
                            Process Recording
                        </button>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Bill Recognition Screen -->
                <div class="screen" id="billRecognitionScreen">
                    <h2 id="billRecognitionTitle">Bill Recognition</h2>
                    <div class="input-group">
                        <div class="input-label" id="billRecognitionLabel">Upload or scan your bill</div>
                        <div class="bill-upload" onclick="simulateBillUpload()">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <p>Click here to upload bill</p>
                            <p>or place bill in the scanner</p>
                        </div>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- AI Interaction Screen -->
                <div class="screen" id="aiInteractionScreen">
                    <h2 id="aiInteractionTitle">AI Interaction</h2>
                    <div class="input-group">
                        <div class="input-label" id="aiInteractionLabel">Place your phone in the slot to talk to our AI assistant</div>
                        <div class="phone-slot">
                            <i class="fas fa-mobile-alt"></i>
                            <p>Phone slot</p>
                        </div>
                        <button class="btn btn-primary" onclick="simulateAIInteraction()" id="simulateAIBtn">
                            Simulate AI Interaction
                        </button>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Payment Screen -->
                <div class="screen" id="paymentScreen">
                    <h2 id="paymentTitle">Payment Required</h2>
                    <div class="scenario-info">
                        <div class="scenario-title" id="paymentInfoTitle">Payment Information</div>
                        <p>Weight: <span id="paymentWeight">0</span> KG</p>
                        <p>Material Weight: <span id="paymentMaterialWeight">0</span> KG</p>
                        <p>Charges: ₹<span id="paymentAmount">100</span> (Fixed Charge)</p>
                    </div>
                    <div class="input-group">
                        <div class="input-label" id="paymentMethodLabel">Select Payment Method</div>
                        <div class="payment-options">
                            <button class="payment-btn cash-btn" onclick="processPayment('cash')" id="cashPaymentBtn">
                                <i class="fas fa-money-bill-wave"></i> Cash
                            </button>
                            <button class="payment-btn upi-btn" onclick="processPayment('upi')" id="upiPaymentBtn">
                                <i class="fas fa-mobile-alt"></i> UPI
                            </button>
                        </div>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Material Calculation Screen -->
                <div class="screen" id="calculationScreen">
                    <h2 id="calculationTitle">Material Calculation</h2>
                    <div class="material-calculation">
                        <div class="calculation-formula" id="calculationFormula">
                            Exit Weight - Entry Weight = Material Weight
                        </div>
                        <div class="calculation-formula" id="calculationResult">
                            28,700 kg - 12,500 kg = 16,200 kg
                        </div>
                        <div class="calculation-formula">
                            Material Value: ₹100 (Flat Rate)
                        </div>
                    </div>
                    <button class="btn btn-primary" onclick="continueAfterCalculation()" id="continueCalculationBtn">
                        Continue
                    </button>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Slip Generation Screen -->
                <div class="screen" id="slipScreen">
                    <h2 id="slipTitle">Transaction Slip</h2>
                    <div class="slip-preview" id="slipPreview">
                        <div class="slip-header">
                            <div class="slip-company">KALI CERAMIC LLP</div>
                            <div class="slip-address">SURVEY NO.: 575/2, BH ISWIND GRANT PVT LTD., JEITPAR ROAD, RANDPAR VILLAGE, MORBI - 363642</div>
                        </div>
                        <table class="slip-details">
                            <tr>
                                <td>FSI No.:</td>
                                <td id="slipFsi">113</td>
                            </tr>
                            <tr>
                                <td>Vehicle:</td>
                                <td id="slipTruck">GJ 13/W/8917</td>
                            </tr>
                            <tr>
                                <td>Party:</td>
                                <td id="slipParty">L.J.A2 MATI</td>
                            </tr>
                            <tr>
                                <td>Material:</td>
                                <td id="slipMaterial">PURCHASE</td>
                            </tr>
                            <tr>
                                <td>Gross Weight:</td>
                                <td id="slipGrossWeight">61,670 Kg.</td>
                            </tr>
                            <tr>
                                <td>Gross Date/Time:</td>
                                <td id="slipGrossDateTime">05-08-2025 08:58 AM</td>
                            </tr>
                            <tr>
                                <td>Tare Weight:</td>
                                <td id="slipTareWeight">14,610 Kg.</td>
                            </tr>
                            <tr>
                                <td>Tare Date/Time:</td>
                                <td id="slipTareDateTime">05-08-2025 09:10 AM</td>
                            </tr>
                            <tr>
                                <td>Net Weight:</td>
                                <td id="slipNetWeight">47,060 Kg.</td>
                            </tr>
                            <tr>
                                <td>Amount:</td>
                                <td id="slipAmount">₹100</td>
                            </tr>
                        </table>
                        <div class="slip-footer">
                            <div class="signature-area">
                                <div class="signature-box">
                                    <div class="signature-line"></div>
                                </div>
                                <div class="signature-box">
                                    <div class="signature-line"></div>
                                </div>
                            </div>
                            <div style="margin-top: 20px; text-align: center;">
                                <div class="signature-line" style="width: 60%; margin: 0 auto;"></div>
                            </div>
                            <div style="margin-top: 30px;">
                                Thank you, Visit Again
                            </div>
                        </div>
                    </div>
                    <button class="btn btn-success" onclick="printSlip()" id="printSlipBtn">
                        Print Slip
                    </button>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- Password Screen -->
                <div class="screen" id="passwordScreen">
                    <h2 id="passwordTitle">Access History</h2>
                    <div class="password-prompt">
                        <div class="input-label" id="passwordLabel">Enter Password</div>
                        <input type="password" class="password-input" id="passwordInput" placeholder="Enter password">
                        <button class="btn btn-primary" onclick="checkPassword()" id="passwordBtn">
                            Submit
                        </button>
                    </div>
                    <div class="swipe-instruction">
                        <i class="fas fa-arrow-left"></i> Swipe left/right to navigate <i class="fas fa-arrow-right"></i>
                    </div>
                </div>

                <!-- History Screen -->
                <div class="screen" id="historyScreen">
                    <h2 id="historyTitle">Transaction History</h2>
                    <div class="slip-preview">
                        <div class="slip-header">
                            <div class="slip-company">KALI CERAMIC LLP</div>
                            <div>HISTORY</div>
                        </div>
                        <table class="slip-details">
                            <tr>
                                <td>Date</td>
                                <td>Truck No</td>
                                <td>Weight</td>
                                <td>Material</td>
                                <td>Type</td>
                                <td>Charges</td>
                            </tr>
                            <tr>
                                <td>21/08/2025</td>
                                <td>GJ05AX1234</td>
                                <td>52,528 KG</td>
                                <td>16,200 KG</td>
                                <td>IN</td>
                                <td>₹100</td>
                            </tr>
                            <tr>
                                <td>20/08/2025</td>
                                <td>GJ03CD4567</td>
                                <td>15,820 KG</td>
                                <td>0 KG</td>
                                <td>OUT</td>
                                <td>₹0</td>
                            </tr>
                            <tr>
                                <td>20/08/2025</td>
                                <td>GJ08EF9012</td>
                                <td>38,450 KG</td>
                                <td>12,500 KG</td>
                                <td>IN</td>
                                <td>₹100</td>
                            </tr>
                            <tr>
                                <td>19/08/2025</td>
                                <td>GJ12GH3456</td>
                                <td>16,310 KG</td>
                                <td>0 KG</td>
                                <td>OUT</td>
                                <td>₹0</td>
                            </tr>
                        </table>
                        <div class="slip-footer">
                            Last 4 transactions shown
                        </div>
                    </div>
                    <button class="btn btn-warning" onclick="showScreen('languageScreen')" id="backToMainBtn">
                        Back to Main
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // System State
        let systemState = {
            language: 'english',
            direction: '',
            purpose: '',
            truckNumber: '',
            weight: 0,
            materialWeight: 0,
            materialValue: 0,
            isEmpty: false,
            timestamp: null,
            charges: 0,
            supplier: '',
            material: '',
            slipType: 'kachchi', // 'kachchi' or 'pakki'
            paymentMethod: '',
            inputMethod: '', // 'voice', 'bill', or 'ai'
            entryWeight: 0,
            exitWeight: 0,
            transactions: [],
            requiresSupplierMaterial: false,
            weightThreshold: 15000, // Default threshold
            defaultCharge: 100, // Default charge
            historyPin: '993996' // PIN for history access
        };

        // Demo vehicle numbers
        const demoNumbers = [
            'GJ05AX1234',
            'GJ09BM5678',
            'GJ12CD9012',
            'GJ15EF3456',
            'GJ18GH7890'
        ];
        let demoNumberIndex = 0;

        // Language dictionaries
        const languageText = {
            'english': {
                'directionTitle': 'Select Direction',
                'inboundBtn': 'ENTRY',
                'outboundBtn': 'EXIT',
                'purposeTitle': 'Select Purpose',
                'purposeInbound1': 'Empty the material',
                'purposeInbound2': 'Fill the material',
                'purposeOutbound3': 'The material have been emptied',
                'purposeOutbound4': 'The material are being taken after loading',
                'vehicleTitle': 'Enter Vehicle Number',
                'demoBtn': 'DEMO NUMBER',
                'weightTitle': 'Weight Measurement',
                'processWeightBtn': 'Continue',
                'inputMethodTitle': 'Provide Supplier & Material Details',
                'fixedChargeNote': 'Fixed Charge: ₹100 if material weight > 0',
                'voiceTitle': 'Voice Input',
                'voiceDesc': 'Speak supplier and material details',
                'billTitle': 'Bill Recognition',
                'billDesc': 'Upload or scan your bill',
                'aiTitle': 'AI Interaction',
                'aiDesc': 'Talk to our AI assistant',
                'voiceInputTitle': 'Voice Input',
                'voiceInputLabel': 'Speak clearly into the microphone',
                'startVoiceBtn': 'Start Recording',
                'processVoiceBtn': 'Process Recording',
                'billRecognitionTitle': 'Bill Recognition',
                'billRecognitionLabel': 'Upload or scan your bill',
                'aiInteractionTitle': 'AI Interaction',
                'aiInteractionLabel': 'Place your phone in the slot to talk to our AI assistant',
                'simulateAIBtn': 'Simulate AI Interaction',
                'paymentTitle': 'Payment Required',
                'paymentInfoTitle': 'Payment Information',
                'paymentMethodLabel': 'Select Payment Method',
                'cashPaymentBtn': 'Cash',
                'upiPaymentBtn': 'UPI',
                'calculationTitle': 'Material Calculation',
                'continueCalculationBtn': 'Continue',
                'slipTitle': 'Transaction Slip',
                'printSlipBtn': 'Print Slip',
                'passwordTitle': 'Access History',
                'passwordLabel': 'Enter Password',
                'passwordBtn': 'Submit',
                'historyTitle': 'Transaction History',
                'backToMainBtn': 'Back to Main'
            },
            'hindi': {
                'directionTitle': 'दिशा चुनें',
                'inboundBtn': 'अंदर',
                'outboundBtn': 'बाहर',
                'purposeTitle': 'उद्देश्य चुनें',
                'purposeInbound1': 'माल खाली करना है',
                'purposeInbound2': 'माल भरना है',
                'purposeOutbound3': 'माल खाली हो गया है',
                'purposeOutbound4': 'माल भर के जा रहे हैं',
                'vehicleTitle': 'वाहन नंबर दर्ज करें',
                'demoBtn': 'डेमो नंबर',
                'weightTitle': 'वजन माप',
                'processWeightBtn': 'जारी रखें',
                'inputMethodTitle': 'आपूर्तिकर्ता और सामग्री का विवरण दें',
                'fixedChargeNote': 'निश्चित शुल्क: ₹100 अगर सामग्री का वजन > 0',
                'voiceTitle': 'वॉयस इनपुट',
                'voiceDesc': 'आपूर्तिकर्ता और सामग्री का विवरण बोलें',
                'billTitle': 'बिल मान्यता',
                'billDesc': 'अपना बिल अपलोड या स्कैन करें',
                'aiTitle': 'एआई इंटरैक्शन',
                'aiDesc': 'हमारे एआई सहायक से बात करें',
                'voiceInputTitle': 'वॉयस इनपुट',
                'voiceInputLabel': 'माइक्रोफोन में स्पष्ट रूप से बोलें',
                'startVoiceBtn': 'रिकॉर्डिंग शुरू करें',
                'processVoiceBtn': 'रिकॉर्डिंग संसाधित करें',
                'billRecognitionTitle': 'बिल मान्यता',
                'billRecognitionLabel': 'अपना बिल अपलोड या स्कैन करें',
                'aiInteractionTitle': 'एआई इंटरैक्शन',
                'aiInteractionLabel': 'हमारे एआई सहायक से बात करने के लिए अपना फोन स्लॉट में रखें',
                'simulateAIBtn': 'एआई इंटरैक्शन अनुकरण करें',
                'paymentTitle': 'भुगतान आवश्यक',
                'paymentInfoTitle': 'भुगतान जानकारी',
                'paymentMethodLabel': 'भुगतान का तरीका चुनें',
                'cashPaymentBtn': 'नकद',
                'upiPaymentBtn': 'यूपीआई',
                'calculationTitle': 'सामग्री गणना',
                'continueCalculationBtn': 'जारी रखें',
                'slipTitle': 'लेन-देन स्लिप',
                'printSlipBtn': 'स्लिप प्रिंट करें',
                'passwordTitle': 'इतिहास तक पहुंच',
                'passwordLabel': 'पासवर्ड दर्ज करें',
                'passwordBtn': 'जमा करें',
                'historyTitle': 'लेन-देन इतिहास',
                'backToMainBtn': 'मुख्य मेनू पर वापस जाएं'
            },
            'gujarati': {
                'directionTitle': 'દિશા પસંદ કરો',
                'inboundBtn': 'અંદર',
                'outboundBtn': 'બહાર',
                'purposeTitle': 'હેતુ પસંદ કરો',
                'purposeInbound1': 'માલ ખાલી કરવાનો છે',
                'purposeInbound2': 'માલ ભરવાનું છે',
                'purposeOutbound3': 'માલ ખાલી થઈ ગયો છે',
                'purposeOutbound4': 'માલ લઈને બહાર જવાનું છે',
                'vehicleTitle': 'વાહન નંબર દાખલ કરો',
                'demoBtn': 'ડેમો નંબર',
                'weightTitle': 'વજન માપ',
                'processWeightBtn': 'ચાલુ રાખો',
                'inputMethodTitle': 'સપ્લાયર અને સામગ્રીની વિગતો આપો',
                'fixedChargeNote': 'નિશ્ચિત ચાર્જ: ₹100 જો સामગ્રીનું વજन > 0',
                'voiceTitle': 'વ voiceઇસ ઇનપુટ',
                'voiceDesc': 'સપ્લાયર અને સામગ્રીની વિગતો બોલો',
                'billTitle': 'બિલ માન્યતા',
                'billDesc': 'તમારું બિલ અપલોડ અથવા સ્કેન કરો',
                'aiTitle': 'AI ઇંટરેક્શન',
                'aiDesc': 'અમારા AI સહાયક સાથે વાત કરો',
                'voiceInputTitle': 'વ voiceઇસ ઇનપુટ',
                'voiceInputLabel': 'માઇક્રોફોનમાં સ્પષ્ટ બોલો',
                'startVoiceBtn': 'રેકોર્ડિંઅ શરૂ કરો',
                'processVoiceBtn': 'રેકોર્ડિંગ પ્રોસેસ કરો',
                'billRecognitionTitle': 'બિલ માન્યતા',
                'billRecognitionLabel': 'તમારું બિલ અપલોડ અથવા સ્કેન કરો',
                'aiInteractionTitle': 'AI ઇંટરેક્શન',
                'aiInteractionLabel': 'અમારા AI સહાયક સાથે વાત કરવા માટે તમારો ફોન સ્લોટમાં મૂકો',
                'simulateAIBtn': 'AI ઇંટરેક્શન સિમ્યુલેટ કરો',
                'paymentTitle': 'ચુકવણી આવશ્યક',
                'paymentInfoTitle': 'ચુકવણી માહિતી',
                'paymentMethodLabel': 'ચુકવણીની પદ્ધતિ પસંદ કરો',
                'cashPaymentBtn': 'નગદ',
                'upiPaymentBtn': 'UPI',
                'calculationTitle': 'સામગ્રી ગણતરી',
                'continueCalculationBtn': 'ચાલુ રાખો',
                'slipTitle': 'વ્યવહાર સ્લિપ',
                'printSlipBtn': 'સ્લિપ પ્રિન્ટ કરો',
                'passwordTitle': 'ઇતિહાસ ઍક્સેસ',
                'passwordLabel': 'પાસવર્ડ દાખલ કરો',
                'passwordBtn': 'સબમિટ કરો',
                'historyTitle': 'વ્યવહાર ઇતિહાસ',
                'backToMainBtn': 'મુખ્ય મેનુ પર પાછા જાવ'
            }
        };

        // Previous records for outbound trucks
        const previousRecords = {
            'GJ05AX1234': { supplier: 'SHREE SUPPLIERS', material: 'BALL CLAY', entryWeight: 36528 },
            'GJ09BM5678': { supplier: 'AMRIT CERAMICS', material: 'SAND', entryWeight: 12500 },
            'GJ12CD9012': { supplier: 'MORBI MINERALS', material: 'FELDSPAR', entryWeight: 15000 }
        };

        // Initialize the UI
        function init() {
            // Set up back button functionality
            document.getElementById('backBtn').addEventListener('click', goBack);
            
            // Set up history button functionality
            document.getElementById('historyBtn').addEventListener('click', showPasswordScreen);
            
            // Show splash screen first, then language screen
            setTimeout(() => {
                showScreen('languageScreen');
            }, 2000);
        }

        function selectLanguage(lang) {
            systemState.language = lang;
            updateLanguage();
            showScreen('directionScreen');
        }

        function updateLanguage() {
            const lang = systemState.language;
            const texts = languageText[lang];
            
            for (const [key, value] of Object.entries(texts)) {
                const element = document.getElementById(key);
                if (element) {
                    element.textContent = value;
                }
            }
        }

        function selectDirection(direction) {
            systemState.direction = direction;
            showPurposeScreen();
        }

        function showPurposeScreen() {
            const purposeButtons = document.getElementById('purposeButtons');
            purposeButtons.innerHTML = '';
            
            if (systemState.direction === 'IN') {
                // Inbound purposes
                const purpose1 = document.createElement('button');
                purpose1.className = 'purpose-btn purpose-inbound';
                purpose1.textContent = languageText[systemState.language].purposeInbound1;
                purpose1.onclick = () => selectPurpose('empty_in');
                
                const purpose2 = document.createElement('button');
                purpose2.className = 'purpose-btn purpose-inbound';
                purpose2.textContent = languageText[systemState.language].purposeInbound2;
                purpose2.onclick = () => selectPurpose('fill_in');
                
                purposeButtons.appendChild(purpose1);
                purposeButtons.appendChild(purpose2);
            } else {
                // Outbound purposes
                const purpose3 = document.createElement('button');
                purpose3.className = 'purpose-btn purpose-outbound';
                purpose3.textContent = languageText[systemState.language].purposeOutbound3;
                purpose3.onclick = () => selectPurpose('empty_out');
                
                const purpose4 = document.createElement('button');
                purpose4.className = 'purpose-btn purpose-outbound';
                purpose4.textContent = languageText[systemState.language].purposeOutbound4;
                purpose4.onclick = () => selectPurpose('fill_out');
                
                purposeButtons.appendChild(purpose3);
                purposeButtons.appendChild(purpose4);
            }
            
            showScreen('purposeScreen');
        }

        function selectPurpose(purpose) {
            systemState.purpose = purpose;
            showScreen('vehicleScreen');
        }

        function setDemoNumber() {
            demoNumberIndex = (demoNumberIndex + 1) % demoNumbers.length;
            document.getElementById('vehicleNumber').value = demoNumbers[demoNumberIndex];
        }

        function submitVehicleNumber() {
            const truckNum = document.getElementById('vehicleNumber').value.trim();
            if (truckNum.length < 4) {
                alert('Please enter a valid truck number');
                return;
            }
            
            systemState.truckNumber = truckNum;
            showScreen('weightScreen');
            simulateWeightReading();
        }

        function simulateWeightReading() {
            // Determine weight based on purpose
            if (systemState.direction === 'IN') {
                if (systemState.purpose === 'empty_in') {
                    // Inbound to empty - truck is loaded
                    systemState.weight = Math.floor(Math.random() * 10000) + systemState.weightThreshold;
                    systemState.isEmpty = false;
                } else {
                    // Inbound to fill - truck is empty
                    systemState.weight = Math.floor(Math.random() * 5000) + 10000;
                    systemState.isEmpty = true;
                }
                systemState.entryWeight = systemState.weight;
            } else {
                // Outbound
                if (systemState.purpose === 'empty_out') {
                    // Outbound after emptying - truck is empty
                    systemState.weight = Math.floor(Math.random() * 5000) + 10000;
                    systemState.isEmpty = true;
                } else {
                    // Outbound after filling - truck is loaded
                    systemState.weight = Math.floor(Math.random() * 10000) + systemState.weightThreshold;
                    systemState.isEmpty = false;
                }
                systemState.exitWeight = systemState.weight;
                
                // Try to find previous record for this truck
                if (previousRecords[systemState.truckNumber]) {
                    systemState.entryWeight = previousRecords[systemState.truckNumber].entryWeight;
                    systemState.supplier = previousRecords[systemState.truckNumber].supplier;
                    systemState.material = previousRecords[systemState.truckNumber].material;
                }
                
                // Calculate material weight and value
                systemState.materialWeight = Math.abs(systemState.exitWeight - systemState.entryWeight);
                systemState.materialValue = systemState.materialWeight > 0 ? systemState.defaultCharge : 0;
            }
            
            // Simulate weight reading delay
            setTimeout(() => {
                document.getElementById('weightDisplay').textContent = systemState.weight.toLocaleString() + ' KG';
                
                // Display weight information
                const weightInfo = document.getElementById('weightInfo');
                if (systemState.isEmpty) {
                    weightInfo.textContent = 'Truck is empty';
                    weightInfo.style.background = '#27ae60';
                } else {
                    weightInfo.textContent = 'Truck has material';
                    weightInfo.style.background = '#f39c12';
                }
                
                document.getElementById('weightStatus').textContent = 'Weight detected successfully';
            }, 2000);
        }

        function processWeight() {
            // Determine next steps based on direction and purpose
            if (systemState.direction === 'IN') {
                if (systemState.purpose === 'empty_in' && !systemState.isEmpty) {
                    // Inbound to empty with material - requires payment and supplier details
                    showScreen('inputMethodScreen');
                } else {
                    // Inbound to fill or empty truck without material - generate slip directly
                    systemState.slipType = 'kachchi';
                    generateSlip();
                }
            } else {
                // Outbound
                if (systemState.purpose === 'empty_out' && systemState.isEmpty) {
                    // Outbound after emptying - generate pakki slip
                    systemState.slipType = 'pakki';
                    showCalculationScreen();
                } else if (systemState.purpose === 'fill_out' && !systemState.isEmpty) {
                    // Outbound after filling - may need supplier details
                    if (systemState.supplier && systemState.material) {
                        systemState.slipType = 'pakki';
                        showCalculationScreen();
                    } else {
                        showScreen('inputMethodScreen');
                    }
                } else {
                    // Other cases - generate slip directly
                    systemState.slipType = 'pakki';
                    showCalculationScreen();
                }
            }
        }

        function showInputMethodScreen() {
            showScreen('inputMethodScreen');
        }

        function selectInputMethod(method) {
            systemState.inputMethod = method;
            
            if (method === 'voice') {
                showScreen('voiceInputScreen');
            } else if (method === 'bill') {
                showScreen('billRecognitionScreen');
            } else if (method === 'ai') {
                showScreen('aiInteractionScreen');
            }
        }

        function startVoiceRecognition() {
            const recordingIndicator = document.getElementById('recordingIndicator');
            const processVoiceBtn = document.getElementById('processVoiceBtn');
            
            recordingIndicator.style.display = 'block';
            
            // Simulate voice recording
            setTimeout(() => {
                recordingIndicator.style.display = 'none';
                processVoiceBtn.style.display = 'block';
                alert('Voice recording completed. Click "Process Recording" to continue.');
            }, 3000);
        }

        function processVoiceInput() {
            // Simulate voice recognition
            const suppliers = ['SHREE SUPPLIERS', 'AMRIT CERAMICS', 'MORBI MINERALS', 'GUJARAT CLAY WORKS'];
            const materials = ['BALL CLAY', 'SAND', 'FELDSPAR', 'QUARTZ'];
            
            systemState.supplier = suppliers[Math.floor(Math.random() * suppliers.length)];
            systemState.material = materials[Math.floor(Math.random() * materials.length)];
            
            alert(`Voice recognition completed:\nSupplier: ${systemState.supplier}\nMaterial: ${systemState.material}`);
            
            if (systemState.direction === 'IN' && systemState.purpose === 'empty_in' && !systemState.isEmpty) {
                showPaymentScreen();
            } else {
                if (systemState.direction === 'IN') {
                    systemState.slipType = 'kachchi';
                    generateSlip();
                } else {
                    systemState.slipType = 'pakki';
                    showCalculationScreen();
                }
            }
        }

        function simulateBillUpload() {
            // Simulate bill upload and recognition
            const suppliers = ['SHREE SUPPLIERS', 'AMRIT CERAMICS', 'MORBI MINERALS', 'GUJARAT CLAY WORKS'];
            const materials = ['BALL CLAY', 'SAND', 'FELDSPAR', 'QUARTZ'];
            
            systemState.supplier = suppliers[Math.floor(Math.random() * suppliers.length)];
            systemState.material = materials[Math.floor(Math.random() * materials.length)];
            
            alert(`Bill recognition completed:\nSupplier: ${systemState.supplier}\nMaterial: ${systemState.material}`);
            
            if (systemState.direction === 'IN' && systemState.purpose === 'empty_in' && !systemState.isEmpty) {
                showPaymentScreen();
            } else {
                if (systemState.direction === 'IN') {
                    systemState.slipType = 'kachchi';
                    generateSlip();
                } else {
                    systemState.slipType = 'pakki';
                    showCalculationScreen();
                }
            }
        }

        function simulateAIInteraction() {
            // Simulate AI interaction
            const suppliers = ['SHREE SUPPLIERS', 'AMRIT CERAMICS', 'MORBI MINERALS', 'GUJARAT CLAY WORKS'];
            const materials = ['BALL CLAY', 'SAND', 'FELDSPAR', 'QUARTZ'];
            
            systemState.supplier = suppliers[Math.floor(Math.random() * suppliers.length)];
            systemState.material = materials[Math.floor(Math.random() * materials.length)];
            
            alert(`AI interaction completed:\nSupplier: ${systemState.supplier}\nMaterial: ${systemState.material}`);
            
            if (systemState.direction === 'IN' && systemState.purpose === 'empty_in' && !systemState.isEmpty) {
                showPaymentScreen();
            } else {
                if (systemState.direction === 'IN') {
                    systemState.slipType = 'kachchi';
                    generateSlip();
                } else {
                    systemState.slipType = 'pakki';
                    showCalculationScreen();
                }
            }
        }

        function showPaymentScreen() {
            document.getElementById('paymentWeight').textContent = systemState.weight.toLocaleString();
            document.getElementById('paymentMaterialWeight').textContent = systemState.materialWeight.toLocaleString();
            document.getElementById('paymentAmount').textContent = systemState.materialValue;
            showScreen('paymentScreen');
        }

        function processPayment(method) {
            systemState.paymentMethod = method;
            
            // Simulate payment processing
            setTimeout(() => {
                systemState.slipType = 'kachchi';
                generateSlip();
            }, 2000);
        }

        function showCalculationScreen() {
            document.getElementById('calculationFormula').textContent = 
                'Exit Weight - Entry Weight = Material Weight';
            document.getElementById('calculationResult').textContent = 
                `${systemState.exitWeight.toLocaleString()} kg - ${systemState.entryWeight.toLocaleString()} kg = ${systemState.materialWeight.toLocaleString()} kg`;
            showScreen('calculationScreen');
        }

        function continueAfterCalculation() {
            generateSlip();
        }

        function generateSlip() {
            // Update slip content according to the provided format
            document.getElementById('slipFsi').textContent = Math.floor(100 + Math.random() * 900);
            document.getElementById('slipTruck').textContent = systemState.truckNumber;
            document.getElementById('slipParty').textContent = systemState.supplier || 'L.J.A2 MATI';
            document.getElementById('slipMaterial').textContent = systemState.material || 'PURCHASE';
            
            if (systemState.direction === 'IN') {
                document.getElementById('slipGrossWeight').textContent = systemState.weight.toLocaleString() + ' Kg.';
                document.getElementById('slipTareWeight').textContent = (systemState.weight - Math.floor(Math.random() * 10000) - 10000).toLocaleString() + ' Kg.';
            } else {
                document.getElementById('slipGrossWeight').textContent = systemState.entryWeight.toLocaleString() + ' Kg.';
                document.getElementById('slipTareWeight').textContent = systemState.exitWeight.toLocaleString() + ' Kg.';
            }
            
            const now = new Date();
            const grossDate = new Date(now);
            const tareDate = new Date(now);
            tareDate.setMinutes(tareDate.getMinutes() + 12);
            
            document.getElementById('slipGrossDateTime').textContent = 
                formatDate(grossDate) + ' ' + formatTime(grossDate);
            document.getElementById('slipTareDateTime').textContent = 
                formatDate(tareDate) + ' ' + formatTime(tareDate);
            document.getElementById('slipNetWeight').textContent = systemState.materialWeight.toLocaleString() + ' Kg.';
            document.getElementById('slipAmount').textContent = '₹' + systemState.materialValue;
            
            // Save transaction to history
            saveTransaction();
            
            showScreen('slipScreen');
            startAutoReturn();
        }

        function formatDate(date) {
            return date.getDate() + '-' + (date.getMonth() + 1) + '-' + date.getFullYear();
        }

        function formatTime(date) {
            const hours = date.getHours();
            const minutes = date.getMinutes();
            const ampm = hours >= 12 ? 'PM' : 'AM';
            const formattedHours = hours % 12 || 12;
            return (formattedHours < 10 ? '0' : '') + formattedHours + ':' + 
                   (minutes < 10 ? '0' : '') + minutes + ' ' + ampm;
        }

        function saveTransaction() {
            const transaction = {
                id: Math.floor(1000000000000 + Math.random() * 9000000000000),
                date: new Date(),
                truckNumber: systemState.truckNumber,
                weight: systemState.weight,
                materialWeight: systemState.materialWeight,
                materialValue: systemState.materialValue,
                direction: systemState.direction,
                purpose: systemState.purpose,
                supplier: systemState.supplier,
                material: systemState.material,
                slipType: systemState.slipType,
                paymentMethod: systemState.paymentMethod
            };
            
            systemState.transactions.push(transaction);
        }

        function printSlip() {
            // Simulate printing
            alert('Slip sent to printer successfully!');
            startAutoReturn();
        }

        function startAutoReturn() {
            let countdown = 8;
            const timer = document.getElementById('timer');
            const countdownElement = document.getElementById('countdown');
            
            timer.style.display = 'block';
            countdownElement.textContent = countdown;
            
            const interval = setInterval(() => {
                countdown--;
                countdownElement.textContent = countdown;
                
                if (countdown <= 0) {
                    clearInterval(interval);
                    resetSystem();
                }
            }, 1000);
        }

        function resetSystem() {
            // Reset all system state
            systemState = {
                language: systemState.language,
                direction: '',
                purpose: '',
                truckNumber: '',
                weight: 0,
                materialWeight: 0,
                materialValue: 0,
                isEmpty: false,
                timestamp: null,
                charges: 0,
                supplier: '',
                material: '',
                slipType: 'kachchi',
                paymentMethod: '',
                inputMethod: '',
                entryWeight: 0,
                exitWeight: 0,
                transactions: systemState.transactions,
                requiresSupplierMaterial: false,
                weightThreshold: 15000,
                defaultCharge: 100,
                historyPin: '993996'
            };
            
            // Reset UI
            document.getElementById('timer').style.display = 'none';
            document.getElementById('vehicleNumber').value = '';
            document.getElementById('weightInfo').textContent = '';
            document.getElementById('weightDisplay').textContent = '0 KG';
            document.getElementById('weightStatus').textContent = 'Please wait for weight measurement...';
            document.getElementById('processVoiceBtn').style.display = 'none';
            
            // Return to language selection
            showScreen('languageScreen');
        }

        function showPasswordScreen() {
            document.getElementById('passwordInput').value = '';
            showScreen('passwordScreen');
        }

        function checkPassword() {
            const password = document.getElementById('passwordInput').value;
            
            if (password === systemState.historyPin) {
                showScreen('historyScreen');
            } else {
                alert('Incorrect password. Please try again.');
            }
        }

        function showScreen(screenId) {
            // Hide all screens
            const screens = document.querySelectorAll('.screen');
            screens.forEach(screen => {
                screen.classList.remove('active');
            });
            
            // Show selected screen
            document.getElementById(screenId).classList.add('active');
            
            // Show back button on all screens except language and splash screens
            if (screenId === 'languageScreen' || screenId === 'splashScreen') {
                document.getElementById('backBtn').style.display = 'none';
            } else {
                document.getElementById('backBtn').style.display = 'flex';
            }
        }

        function goBack() {
            const currentScreen = document.querySelector('.screen.active').id;
            
            if (currentScreen === 'directionScreen') {
                showScreen('languageScreen');
            } else if (currentScreen === 'purposeScreen') {
                showScreen('directionScreen');
            } else if (currentScreen === 'vehicleScreen') {
                showScreen('purposeScreen');
            } else if (currentScreen === 'weightScreen') {
                showScreen('vehicleScreen');
            } else if (currentScreen === 'inputMethodScreen') {
                showScreen('weightScreen');
            } else if (currentScreen === 'voiceInputScreen' || currentScreen === 'billRecognitionScreen' || currentScreen === 'aiInteractionScreen') {
                showScreen('inputMethodScreen');
            } else if (currentScreen === 'paymentScreen') {
                showScreen('inputMethodScreen');
            } else if (currentScreen === 'calculationScreen') {
                showScreen('weightScreen');
            } else if (currentScreen === 'slipScreen') {
                showScreen('weightScreen');
            } else if (currentScreen === 'passwordScreen') {
                showScreen('languageScreen');
            } else if (currentScreen === 'historyScreen') {
                showScreen('languageScreen');
            }
        }

        // Initialize the application when the page loads
        window.onload = init;
    </script>
</body>
</html>
