<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Everybody Networks - Executive Workshop</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            overflow: hidden;
            height: 100vh;
        }
        
        .presentation-container {
            width: 100vw;
            height: 100vh;
            display: flex;
            flex-direction: column;
        }
        
        .slide {
            display: none;
            width: 100%;
            height: calc(100vh - 80px);
            padding: 60px 80px;
            animation: fadeIn 0.4s ease-in;
        }
        
        .slide.active {
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .slide-content {
            background: white;
            border-radius: 20px;
            padding: 60px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            max-width: 1200px;
            margin: 0 auto;
            width: 100%;
        }
        
        h1 {
            font-size: 3.5em;
            color: #FF6B35;
            margin-bottom: 20px;
            line-height: 1.2;
        }
        
        h2 {
            font-size: 2.5em;
            color: #2EC4B6;
            margin-bottom: 30px;
            line-height: 1.3;
        }
        
        h3 {
            font-size: 1.8em;
            color: #FF6B35;
            margin-bottom: 20px;
        }
        
        p, li {
            font-size: 1.4em;
            line-height: 1.6;
            color: #333;
            margin-bottom: 15px;
        }
        
        .subtitle {
            font-size: 1.8em;
            color: #666;
            font-style: italic;
            margin-top: 10px;
        }
        
        .presenter {
            font-size: 1.3em;
            color: #2EC4B6;
            margin-top: 40px;
        }
        
        ul {
            list-style: none;
            margin-left: 0;
        }
        
        ul li {
            padding-left: 40px;
            position: relative;
            margin-bottom: 20px;
        }
        
        ul li:before {
            content: "→";
            position: absolute;
            left: 0;
            color: #FF6B35;
            font-weight: bold;
            font-size: 1.5em;
        }
        
        .two-column {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            margin-top: 30px;
        }
        
        .three-column {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 30px;
            margin-top: 30px;
        }
        
        .highlight-box {
            background: linear-gradient(135deg, #FFE66D 0%, #FF6B35 100%);
            padding: 30px;
            border-radius: 15px;
            color: white;
            margin: 20px 0;
        }
        
        .highlight-box p, .highlight-box li {
            color: white;
            font-weight: 500;
        }
        
        .insight-box {
            background: linear-gradient(135deg, #2EC4B6 0%, #20B2AA 100%);
            padding: 35px;
            border-radius: 15px;
            color: white;
            margin: 25px 0;
            border-left: 6px solid #FFE66D;
        }
        
        .insight-box p, .insight-box li {
            color: white;
        }
        
        .insight-box h3 {
            color: white;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        
        th, td {
            padding: 20px;
            text-align: left;
            border-bottom: 2px solid #2EC4B6;
        }
        
        th {
            background: #2EC4B6;
            color: white;
            font-size: 1.5em;
        }
        
        td {
            font-size: 1.3em;
        }
        
        .emphasis {
            color: #FF6B35;
            font-weight: bold;
        }
        
        .big-stat {
            font-size: 3.5em;
            color: #FF6B35;
            font-weight: bold;
            text-align: center;
            margin: 30px 0;
        }
        
        .framework-box {
            background: #F8F9FA;
            padding: 30px;
            border-radius: 15px;
            border-left: 6px solid #2EC4B6;
            margin: 25px 0;
        }
        
        .framework-box h3 {
            color: #2EC4B6;
            margin-bottom: 15px;
        }
        
        .controls {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            height: 80px;
            background: rgba(255,255,255,0.95);
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 40px;
            box-shadow: 0 -5px 20px rgba(0,0,0,0.1);
        }
        
        .nav-buttons {
            display: flex;
            gap: 20px;
        }
        
        button {
            padding: 15px 30px;
            font-size: 1.1em;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: 600;
        }
        
        .prev-btn {
            background: #2EC4B6;
            color: white;
        }
        
        .next-btn {
            background: #FF6B35;
            color: white;
        }
        
        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        button:disabled {
            opacity: 0.3;
            cursor: not-allowed;
        }
        
        .slide-counter {
            font-size: 1.2em;
            color: #666;
            font-weight: 500;
        }
        
        .timer {
            font-size: 1.2em;
            color: #FF6B35;
            font-weight: 600;
            font-family: 'Courier New', monospace;
        }
        
        .chat-prompt {
            background: #FFF9E6;
            border-left: 5px solid #FFE66D;
            padding: 20px;
            margin: 20px 0;
            font-style: italic;
            border-radius: 5px;
        }
        
        .activity-box {
            background: linear-gradient(135deg, #2EC4B6 0%, #20B2AA 100%);
            padding: 40px;
            border-radius: 15px;
            color: white;
            margin: 30px 0;
            text-align: center;
        }
        
        .activity-box h3 {
            color: white;
            font-size: 2em;
        }
        
        .activity-box p, .activity-box li {
            color: white;
        }
        
        .activity-box ul li:before {
            color: #FFE66D;
        }
        
        .quote {
            font-size: 1.6em;
            font-style: italic;
            color: #555;
            text-align: center;
            margin: 30px 0;
            padding: 30px;
            border-left: 5px solid #2EC4B6;
            background: #F8F9FA;
        }
    </style>
</head>
<body>
    <div class="presentation-container">
        <!-- Slide 1: Title -->
        <div class="slide active">
            <div class="slide-content">
                <h1>EVERYBODY NETWORKS</h1>
                <p class="subtitle">The Art of Connection You're Already Doing</p>
                <p class="presenter">Presented by Kristen Hoover</p>
            </div>
        </div>

        <!-- Slide 2: The Uncomfortable Truth -->
        <div class="slide">
            <div class="slide-content">
                <h2>Let me tell you something that might make you uncomfortable...</h2>
                <p style="font-size: 1.6em; margin: 40px 0; color: #666;">Your job search strategy is probably backwards.</p>
                <div class="two-column" style="margin: 50px 0;">
                    <div>
                        <h3>Most People:</h3>
                        <p style="font-size: 1.5em;">80% applying online<br>20% talking to humans</p>
                    </div>
                    <div>
                        <h3>What Works:</h3>
                        <p style="font-size: 1.5em;">20% applying online<br>80% talking to humans</p>
                    </div>
                </div>
                <div class="highlight-box" style="margin-top: 50px;">
                    <p style="font-size: 1.6em; text-align: center; margin: 0;"><strong>The hidden job market—roles that never get posted—accounts for 70-85% of all hires.</strong></p>
                </div>
                <p style="font-size: 1.5em; text-align: center; margin-top: 30px; color: #FF6B35; font-weight: bold;">You can't apply your way into the hidden job market.<br>You can only talk your way in.</p>
            </div>
        </div>

        <!-- Slide 3: Today's Plan -->
        <div class="slide">
            <div class="slide-content">
                <h2>What We're Covering Today</h2>
                <ul style="font-size: 1.6em;">
                    <li>The Relationship ROI Model (your strategic framework)</li>
                    <li>Your networking audit (where are you now?)</li>
                    <li>Questions that create real connection</li>
                    <li>The follow-up that actually works</li>
                    <li>Your 20-year network strategy</li>
                </ul>
                <p style="margin-top: 60px; font-size: 1.6em; color: #2EC4B6; text-align: center; font-weight: bold;">60 minutes. Live practice. Strategic thinking.</p>
            </div>
        </div>

        <!-- Slide 4: The Relationship ROI Model -->
        <div class="slide">
            <div class="slide-content">
                <h2>The Relationship ROI Model™</h2>
                <p style="font-size: 1.5em; margin-bottom: 30px;">Your strategic networking framework:</p>
                <div class="framework-box">
                    <h3>R — Reconnect</h3>
                    <p>Reactivate dormant ties (people you knew but fell out of touch with)</p>
                </div>
                <div class="framework-box">
                    <h3>O — Outreach</h3>
                    <p>Build new connections in target companies and roles</p>
                </div>
                <div class="framework-box">
                    <h3>I — Invest</h3>
                    <p>Nurture relationships before you need them (not transactional)</p>
                </div>
            </div>
        </div>

        <!-- Slide 5: Networking Myths -->
        <div class="slide">
            <div class="slide-content">
                <h2>Networking Myths vs Reality</h2>
                <table>
                    <tr>
                        <th>MYTH</th>
                        <th>REALITY</th>
                    </tr>
                    <tr>
                        <td>I have to sell myself</td>
                        <td>You're sharing who you are</td>
                    </tr>
                    <tr>
                        <td>It's fake and transactional</td>
                        <td>It's relationship-building</td>
                    </tr>
                    <tr>
                        <td>I need to know important people</td>
                        <td>Everyone knows someone</td>
                    </tr>
                    <tr>
                        <td>I'm bad at small talk</td>
                        <td>Real talk beats small talk</td>
                    </tr>
                </table>
                <div class="chat-prompt">
                    <p><strong>Chat:</strong> What's YOUR networking myth?</p>
                </div>
            </div>
        </div>

        <!-- Slide 6: Your Networking Audit -->
        <div class="slide">
            <div class="slide-content">
                <h2>Your Networking Audit</h2>
                <p style="font-size: 1.4em; margin-bottom: 30px;">Rate yourself 1-5 on each (1 = never, 5 = always):</p>
                <ul style="font-size: 1.3em;">
                    <li>I have regular conversations with people outside my immediate circle</li>
                    <li>I follow up within 48 hours after meeting someone new</li>
                    <li>I offer value (resources, introductions, insights) without being asked</li>
                    <li>I maintain relationships even when I don't need anything</li>
                    <li>I'm visible in my professional community</li>
                </ul>
                <div class="highlight-box" style="margin-top: 40px;">
                    <p style="font-size: 1.4em;"><strong>Your Score:</strong></p>
                    <p>20-25: Strategic networker | 15-19: On the right track<br>10-14: Huge opportunity | 5-9: Leaving opportunity on the table</p>
                </div>
                <div class="chat-prompt">
                    <p><strong>Put your score in chat if comfortable—or just note it for yourself. This is your baseline.</strong></p>
                </div>
            </div>
        </div>

        <!-- Slide 7: Where Networking Happens -->
        <div class="slide">
            <div class="slide-content">
                <h2>Where Networking Actually Happens</h2>
                <div class="two-column">
                    <ul>
                        <li>At the gym</li>
                        <li>School pickup/drop-off</li>
                        <li>Coffee shops</li>
                        <li>Running errands</li>
                    </ul>
                    <ul>
                        <li>LinkedIn comments</li>
                        <li>Volunteer events</li>
                        <li>Zoom waiting rooms</li>
                        <li>Community gatherings</li>
                    </ul>
                </div>
                <p style="margin-top: 60px; font-size: 1.8em; color: #FF6B35; text-align: center; font-weight: bold;">You're already doing this. Let's make it intentional.</p>
            </div>
        </div>

        <!-- Slide 8: Live Practice -->
        <div class="slide">
            <div class="slide-content">
                <div class="activity-box">
                    <h3>LIVE PRACTICE — The Question Swap</h3>
                    <div style="margin: 30px 0;">
                        <p style="font-size: 1.5em;"><strong>Old way:</strong> "What do you do?"</p>
                        <p style="font-size: 1.5em;"><strong>New way:</strong> "What's something you're excited about right now?"</p>
                    </div>
                    <h3 style="margin-top: 40px;">YOUR TURN:</h3>
                    <ul style="text-align: left; max-width: 600px; margin: 20px auto;">
                        <li>Pick someone in the Zoom chat</li>
                        <li>DM them</li>
                        <li>Try both questions (1 min each)</li>
                        <li>Notice which one feels better</li>
                    </ul>
                    <p style="font-size: 2em; margin-top: 40px; font-weight: bold;">GO. 3 minutes total.</p>
                </div>
            </div>
        </div>

        <!-- Slide 9: Debrief -->
        <div class="slide">
            <div class="slide-content">
                <h2>What Did You Notice?</h2>
                <p style="font-size: 1.5em; margin: 40px 0;">The new question:</p>
                <ul style="font-size: 1.5em;">
                    <li>Felt more human</li>
                    <li>Was easier to answer</li>
                    <li>Led somewhere interesting</li>
                    <li>Made you want to keep talking</li>
                </ul>
                <p style="margin-top: 60px; font-size: 2em; color: #2EC4B6; text-align: center; font-weight: bold;">That's the shift.</p>
            </div>
        </div>

        <!-- Slide 10: Questions That Build Connection -->
        <div class="slide">
            <div class="slide-content">
                <h2>10 Strategic Connection Questions</h2>
                <table>
                    <tr>
                        <th>Instead of this</th>
                        <th>Try this →</th>
                    </tr>
                    <tr>
                        <td>"What do you do?"</td>
                        <td>"What are you working on that excites you?"</td>
                    </tr>
                    <tr>
                        <td>"How are you?"</td>
                        <td>"What's giving you energy these days?"</td>
                    </tr>
                    <tr>
                        <td>"Busy lately?"</td>
                        <td>"What's been the highlight of your week?"</td>
                    </tr>
                    <tr>
                        <td>At events</td>
                        <td>"What brought you here today?"</td>
                    </tr>
                    <tr>
                        <td>For depth</td>
                        <td>"What's a challenge you're working through?"</td>
                    </tr>
                </table>
            </div>
        </div>

        <!-- Slide 11: Build the List -->
        <div class="slide">
            <div class="slide-content">
                <h2>YOUR Turn to Build the List</h2>
                <div class="chat-prompt" style="font-size: 1.4em; padding: 40px; margin: 60px 0;">
                    <p><strong>In chat: What's a question YOU'VE been asked that made you feel seen or heard?</strong></p>
                </div>
                <p style="margin-top: 60px; font-size: 1.6em; text-align: center; color: #FF6B35; font-weight: bold;">Remember: The goal is to make people feel seen, not interviewed.</p>
            </div>
        </div>

        <!-- Slide 12: Research Insight - Weak Ties -->
        <div class="slide">
            <div class="slide-content">
                <h2>Research Insight: Weak Ties</h2>
                <div class="insight-box">
                    <h3>Stanford Research Shows:</h3>
                    <p style="font-size: 1.5em;"><strong>Weak ties</strong> (people you don't know well) are MORE valuable for job searches than close friends.</p>
                </div>
                <p style="font-size: 1.5em; margin: 40px 0;"><strong>Why?</strong> Your close friends know the same people you know. Weak ties access different networks.</p>
                <div class="highlight-box">
                    <p style="font-size: 1.5em; text-align: center; margin: 0;">That person you chatted with once at the gym?<br><strong>More valuable than you think.</strong></p>
                </div>
            </div>
        </div>

        <!-- Slide 13: Follow-Up Framework -->
        <div class="slide">
            <div class="slide-content">
                <h2>The Follow-Up Framework</h2>
                <p style="font-size: 1.6em; color: #666; margin: 30px 0;">Most people think networking happens at the event.</p>
                <p style="font-size: 2em; color: #FF6B35; font-weight: bold; margin: 20px 0;">Wrong. It happens in the follow-up.</p>
                <div class="highlight-box" style="margin-top: 40px;">
                    <h3 style="color: white;">The 3-Part Formula:</h3>
                    <ul style="font-size: 1.4em;">
                        <li>Reference something specific you discussed</li>
                        <li>Share something useful (article, resource, connection)</li>
                        <li>Suggest a next step (coffee, staying in touch)</li>
                    </ul>
                </div>
                <p style="margin-top: 30px; font-size: 1.5em; text-align: center; font-weight: bold;">Do it within 24-48 hours.</p>
            </div>
        </div>

        <!-- Slide 14: Real Example -->
        <div class="slide">
            <div class="slide-content">
                <h2>Real Example</h2>
                <div style="background: #F5F5F5; padding: 40px; border-radius: 15px; margin: 30px 0;">
                    <p style="font-size: 1.4em; margin-bottom: 30px;"><strong>Met someone at the gym. Talked about job searching.</strong></p>
                    <div style="background: white; padding: 30px; border-radius: 10px; border-left: 5px solid #2EC4B6;">
                        <p style="font-size: 1.3em; font-style: italic; color: #555;">"Hey! Still thinking about what you said about informational interviews. Here's an article I found helpful. Would love to grab coffee if you're up for it."</p>
                    </div>
                    <p style="font-size: 1.4em; margin-top: 30px; color: #FF6B35;"><strong>Result:</strong> Coffee happened. She introduced me to someone. That led to an interview.</p>
                </div>
            </div>
        </div>

        <!-- Slide 15: Practice Follow-Up -->
        <div class="slide">
            <div class="slide-content">
                <h2>PRACTICE — Write Your Follow-Up</h2>
                <div class="activity-box">
                    <p style="font-size: 1.5em; margin-bottom: 30px;"><strong>Scenario:</strong> You just had a great conversation with someone about [pick something].</p>
                    <h3 style="color: white;">In chat: Draft your follow-up message.</h3>
                </div>
                <p style="margin-top: 40px; font-size: 1.3em; text-align: center; color: #666;">We'll call out 2-3 strong examples and explain why they work</p>
            </div>
        </div>

        <!-- Slide 16: Career Asset Reframe -->
        <div class="slide">
            <div class="slide-content">
                <h2>Your Most Valuable Career Asset</h2>
                <p style="font-size: 1.5em; margin: 30px 0;">Think about your career assets:</p>
                <div class="three-column">
                    <div style="text-align: center; padding: 20px;">
                        <p style="font-size: 1.6em; color: #2EC4B6;">✓ Your resume</p>
                    </div>
                    <div style="text-align: center; padding: 20px;">
                        <p style="font-size: 1.6em; color: #2EC4B6;">✓ Your skills</p>
                    </div>
                    <div style="text-align: center; padding: 20px;">
                        <p style="font-size: 1.6em; color: #2EC4B6;">✓ Your experience</p>
                    </div>
                </div>
                <div class="highlight-box" style="margin-top: 50px;">
                    <p style="font-size: 2em; text-align: center; margin: 0;"><strong>Your Network</strong></p>
                    <p style="font-size: 1.5em; text-align: center; margin-top: 20px;">The only asset that <strong>appreciates over time</strong></p>
                </div>
                <p style="font-size: 1.4em; margin-top: 40px; text-align: center; color: #666;">Your resume gets stale. Your skills get outdated.<br>But relationships compound.</p>
            </div>
        </div>

        <!-- Slide 17: Research Insight - Visibility -->
        <div class="slide">
            <div class="slide-content">
                <h2>Research Insight: Visibility = Opportunity</h2>
                <div class="insight-box">
                    <h3>LinkedIn Data Shows:</h3>
                    <p style="font-size: 1.5em;">People who engage with others' content (commenting, sharing) are <strong>5x more likely</strong> to hear about opportunities than people who just scroll.</p>
                </div>
                <div class="highlight-box" style="margin-top: 50px;">
                    <p style="font-size: 1.5em; text-align: center; margin: 0;"><strong>Action:</strong> Comment on 3 LinkedIn posts per week.<br>Show up visibly.</p>
                </div>
            </div>
        </div>

        <!-- Slide 18: The Fear -->
        <div class="slide">
            <div class="slide-content">
                <h2>Let's Talk About the Fear</h2>
                <div class="chat-prompt" style="font-size: 1.4em; padding: 40px; margin: 40px 0;">
                    <p><strong>In chat: What's your biggest networking fear?</strong></p>
                </div>
                <div class="two-column">
                    <div>
                        <h3 style="font-size: 1.3em;">Common ones:</h3>
                        <ul style="font-size: 1.2em;">
                            <li>"I don't know what to say"</li>
                            <li>"I'm afraid of rejection"</li>
                            <li>"I feel like I'm bothering people"</li>
                        </ul>
                    </div>
                    <div>
                        <h3 style="font-size: 1.3em;">The truth:</h3>
                        <ul style="font-size: 1.2em;">
                            <li>Curiosity is your guide</li>
                            <li>You're looking for YOUR people</li>
                            <li>Most people love talking about themselves</li>
                        </ul>
                    </div>
                </div>
                <p style="margin-top: 50px; font-size: 1.6em; text-align: center; color: #FF6B35; font-weight: bold;">If it was easy, everybody would do it. You're being brave.</p>
            </div>
        </div>

        <!-- Slide 19: The Real Cost -->
        <div class="slide">
            <div class="slide-content">
                <h2>The Real Cost</h2>
                <p style="font-size: 1.8em; color: #FF6B35; margin: 30px 0; font-weight: bold;">If you're NOT networking...</p>
                <div class="highlight-box">
                    <p style="font-size: 1.5em; margin-bottom: 20px;">You're robbing yourself of:</p>
                    <ul style="font-size: 1.3em;">
                        <li>Opportunities that exist right now</li>
                        <li>Information that could help you</li>
                        <li>Connections that open doors</li>
                        <li><strong>Energy</strong> from human interaction</li>
                        <li>Tools that speed up your search</li>
                    </ul>
                </div>
                <p style="margin-top: 50px; font-size: 1.8em; text-align: center; color: #2EC4B6; font-weight: bold;">Networking doesn't drain you. It fuels you.</p>
            </div>
        </div>

        <!-- Slide 20: 20-Year Network Strategy -->
        <div class="slide">
            <div class="slide-content">
                <h2>The 20-Year Network Strategy</h2>
                <p style="font-size: 1.5em; margin: 30px 0; color: #666;">Most people network when they need a job. That's reactive.<br>Here's what proactive looks like:</p>
                <div class="framework-box">
                    <p><strong>Today:</strong> Build relationships with peers</p>
                </div>
                <div class="framework-box">
                    <p><strong>5 years:</strong> Those peers become managers, directors, VPs</p>
                </div>
                <div class="framework-box">
                    <p><strong>10 years:</strong> Some become C-suite, founders, decision-makers</p>
                </div>
                <div class="framework-box">
                    <p><strong>20 years:</strong> Your network is filled with people who can open any door</p>
                </div>
                <div class="highlight-box" style="margin-top: 40px;">
                    <p style="font-size: 1.4em; text-align: center; margin: 0;">The person you have coffee with today might be the CEO who hires you in 15 years.</p>
                </div>
            </div>
        </div>

        <!-- Slide 21: Your Strategic Challenge -->
        <div class="slide">
            <div class="slide-content">
                <h2>Your Strategic Challenge</h2>
                <p style="font-size: 1.6em; margin: 40px 0; color: #FF6B35; font-weight: bold;">Pick ONE strategic move for the next 30 days:</p>
                <div class="framework-box">
                    <h3>Option 1: Reconnect with 5 Dormant Ties</h3>
                    <p>People you knew but fell out of touch with. Use the reactivation script.</p>
                </div>
                <div class="framework-box">
                    <h3>Option 2: Become Visible in Your Industry</h3>
                    <p>Comment thoughtfully on 3 LinkedIn posts per week for 4 weeks.</p>
                </div>
                <div class="framework-box">
                    <h3>Option 3: Build Your Target 20 List</h3>
                    <p>20 people you want to know. Reach out to 5 this month.</p>
                </div>
                <div class="chat-prompt" style="margin-top: 40px;">
                    <p><strong>Post your commitment in Slack. We'll check in.</strong></p>
                </div>
            </div>
        </div>

        <!-- Slide 22: The Lasting Truth -->
        <div class="slide">
            <div class="slide-content">
                <h2>The Lasting Truth</h2>
                <div class="highlight-box" style="margin: 40px 0;">
                    <p style="font-size: 1.8em; text-align: center; margin: 0;">Opportunities don't find you because you're qualified.</p>
                    <p style="font-size: 1.8em; text-align: center; margin-top: 20px;"><strong>Opportunities find you because someone thought of you.</strong></p>
                </div>
                <p style="font-size: 1.4em; margin: 40px 0;">Your job—starting today—is to become the person people think of.</p>
                <p style="font-size: 1.3em; line-height: 1.8;">That doesn't happen by sending great resumes. It happens by having great conversations. By asking questions that make people think. By following up when others ghost. By showing up consistently, visibly, and generously.</p>
            </div>
        </div>

        <!-- Slide 23: Final Truth -->
        <div class="slide">
            <div class="slide-content">
                <h2>Remember This</h2>
                <p style="font-size: 2em; color: #2EC4B6; font-weight: bold; text-align: center; margin: 40px 0;">The most successful people you know didn't get there alone.</p>
                <ul style="font-size: 1.5em; margin: 40px 0;">
                    <li>They built relationships</li>
                    <li>They invested in people</li>
                    <li>They showed up</li>
                </ul>
                <p style="font-size: 1.8em; color: #FF6B35; font-weight: bold; text-align: center; margin: 60px 0;">And so will you.</p>
                <p style="margin-top: 60px; font-size: 1.3em; text-align: center; color: #666;">Questions? Drop them in chat.</p>
            </div>
        </div>

        <div class="controls">
            <div class="timer" id="timer">00:00</div>
            <div class="nav-buttons">
                <button class="prev-btn" onclick="prevSlide()">← Previous</button>
                <span class="slide-counter"><span id="current">1</span> / <span id="total">23</span></span>
                <button class="next-btn" onclick="nextSlide()">Next →</button>
            </div>
            <div style="width: 80px;"></div>
        </div>
    </div>

    <script>
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        const totalSlides = slides.length;
        let startTime = Date.now();

        document.getElementById('total').textContent = totalSlides;

        function showSlide(n) {
            slides[currentSlide].classList.remove('active');
            currentSlide = (n + totalSlides) % totalSlides;
            slides[currentSlide].classList.add('active');
            document.getElementById('current').textContent = currentSlide + 1;
            
            document.querySelector('.prev-btn').disabled = currentSlide === 0;
            document.querySelector('.next-btn').disabled = currentSlide === totalSlides - 1;
        }

        function nextSlide() {
            if (currentSlide < totalSlides - 1) {
                showSlide(currentSlide + 1);
            }
        }

        function prevSlide() {
            if (currentSlide > 0) {
                showSlide(currentSlide - 1);
            }
        }

        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight') nextSlide();
            if (e.key === 'ArrowLeft') prevSlide();
        });

        function updateTimer() {
            const elapsed = Date.now() - startTime;
            const minutes = Math.floor(elapsed / 60000);
            const seconds = Math.floor((elapsed % 60000) / 1000);
            document.getElementById('timer').textContent = 
                String(minutes).padStart(2, '0') + ':' + String(seconds).padStart(2, '0');
        }

        setInterval(updateTimer, 1000);
        showSlide(0);
    </script>
</body>
</html
