# Live-Simulation-Sandbox-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rocket Science & Orbital Mechanics - Webinar Companion</title>
    <style>
        :root {
            --bg-color: #060913;
            --card-bg: #0f1524;
            --accent-blue: #00d2ff;
            --accent-purple: #7000ff;
            --accent-geo: #ff9f43;
            --text-main: #f0f4f8;
            --text-muted: #8da2bb;
            --border-color: #1e293b;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.6;
        }

        header {
            position: relative;
            background: linear-gradient(180deg, rgba(0,210,255,0.1) 0%, rgba(6,9,19,1) 100%);
            padding: 80px 20px;
            text-align: center;
            border-bottom: 1px solid var(--border-color);
        }

        .hero-badge {
            background: rgba(0, 210, 255, 0.1);
            border: 1px solid var(--accent-blue);
            color: var(--accent-blue);
            padding: 6px 16px;
            border-radius: 20px;
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            display: inline-block;
            margin-bottom: 20px;
        }

        h1 {
            font-size: 3rem;
            font-weight: 800;
            letter-spacing: -1px;
            margin-bottom: 10px;
            background: linear-gradient(to right, #fff, var(--accent-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            color: var(--text-muted);
            font-size: 1.25rem;
            max-width: 600px;
            margin: 0auto 30px auto;
        }

        .meta-info {
            font-size: 0.95rem;
            color: #fff;
        }

        .meta-info span {
            color: var(--accent-blue);
        }

        main {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
            display: grid;
            grid-template-columns: 1fr;
            gap: 60px;
        }

        @media (min-width: 992px) {
            main {
                grid-template-columns: 7fr 5fr;
            }
        }

        section h2 {
            font-size: 1.75rem;
            margin-bottom: 25px;
            border-left: 4px solid var(--accent-blue);
            padding-left: 15px;
        }

        /* Speaker Card */
        .bio-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 30px;
            position: sticky;
            top: 20px;
            height: fit-content;
        }

        .bio-title {
            font-size: 1.3rem;
            margin-bottom: 5px;
        }

        .bio-subtitle {
            color: var(--accent-blue);
            font-size: 0.9rem;
            margin-bottom: 20px;
            text-transform: uppercase;
        }

        .bio-list {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .bio-list li strong {
            color: #fff;
        }

        /* Presentation Timeline */
        .timeline {
            display: flex;
            flex-direction: column;
            gap: 24px;
        }

        .slide-node {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 24px;
            transition: transform 0.2s ease;
        }

        .slide-node:hover {
            transform: translateY(-2px);
            border-color: #2e3d56;
        }

        .slide-num {
            font-size: 0.8rem;
            font-weight: bold;
            color: var(--accent-blue);
            text-transform: uppercase;
            margin-bottom: 5px;
        }

        .slide-title {
            font-size: 1.25rem;
            margin-bottom: 12px;
        }

        .slide-bullets {
            padding-left: 20px;
            color: var(--text-muted);
            font-size: 0.95rem;
        }

        .slide-bullets li {
            margin-bottom: 8px;
        }

        /* Embedded Interactive Simulator layout updates */
        .sim-container {
            grid-column: 1 / -1;
            background: #0b0f19;
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 24px;
        }

        .sim-layout {
            display: grid;
            grid-template-columns: 1fr;
            gap: 24px;
        }

        @media (min-width: 768px) {
            .sim-layout {
                grid-template-columns: 1fr 1fr;
            }
        }

        .control-group {
            background: rgba(255, 255, 255, 0.02);
            padding: 16px;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            margin-bottom: 20px;
        }

        .slider-wrapper {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        input[type="range"] {
            flex: 1;
            accent-color: var(--accent-blue);
        }

        .value-display {
            font-family: monospace;
            color: var(--accent-blue);
            font-weight: bold;
            min-width: 90px;
            text-align: right;
        }

        .preset-buttons {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-top: 10px;
        }

        .preset-btn {
            background: #1b263b;
            border: 1px solid var(--border-color);
            color: var(--text-main);
            padding: 10px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.85rem;
        }

        .preset-btn:hover {
            background: #2c3e50;
            border-color: var(--accent-blue);
        }

        .telemetry-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }

        .telemetry-card {
            background: rgba(0, 0, 0, 0.2);
            border: 1px solid var(--border-color);
            padding: 12px;
            border-radius: 6px;
            text-align: center;
        }

        .telemetry-label {
            font-size: 0.75rem;
            color: var(--text-muted);
            text-transform: uppercase;
        }

        .telemetry-value {
            font-size: 1.2rem;
            font-weight: bold;
            font-family: monospace;
            color: var(--accent-blue);
        }

        .canvas-container {
            background: #05070c;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            position: relative;
            aspect-ratio: 1;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        canvas {
            width: 100%;
            height: 100%;
        }

        footer {
            text-align: center;
            padding: 60px 20px;
            color: var(--text-muted);
            font-size: 0.9rem;
            border-top: 1px solid var(--border-color);
            background: #04060d;
        }
    </style>
</head>
<body>

    <header>
        <div class="hero-badge">Live Interactive Session</div>
        <h1>Rocket Science & Orbital Mechanics</h1>
        <p class="subtitle">How Rockets Reach Space and Stay in Orbit</p>
        <div class="meta-info">Presented by: <span>Katie Carlson</span> | Command & Data Handling Engineer</div>
    </header>

    <main>
        <!-- Left Column: Presentation Outline -->
        <section>
            <h2>Webinar Modules</h2>
            <div class="timeline">
                <div class="slide-node">
                    <div class="slide-num">Slide 3</div>
                    <div class="slide-title">The Big Question: What is "Space"?</div>
                    <ul class="slide-bullets">
                        <li>Space is closer than you think (only a 1-hour drive straight up!).</li>
                        <li>Getting there is easy; staying there is the hard part.</li>
                        <li>The Paradox: Space isn't tough because it's high up; it's tough because it's empty.</li>
                    </ul>
                </div>
                
                <div class="slide-node">
                    <div class="slide-num">Slide 4</div>
                    <div class="slide-title">Part 1: Leaving Earth (Action & Reaction)</div>
                    <ul class="slide-bullets">
                        <li>Newton’s Third Law: Every action has an equal and opposite reaction.</li>
                        <li>Momentum conservation: Throwing mass backward pushes the vehicle forward.</li>
                        <li>The challenge: Fighting atmospheric thickness and Earth's heavy gravitational pull.</li>
                    </ul>
                </div>

                <div class="slide-node">
                    <div class="slide-num">Slide 5</div>
                    <div class="slide-title">The Tyranny of the Rocket Equation</div>
                    <ul class="slide-bullets">
                        <li>Tsiolkovsky’s Equation: To push fuel, you need more fuel to push that fuel.</li>
                        <li>Staging: Dropping massive empty metal tanks into the ocean to shed dead weight.</li>
                        <li>Max Q: The point of maximum aerodynamic stress closest to Earth.</li>
                    </ul>
                </div>

                <div class="slide-node">
