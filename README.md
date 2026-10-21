<!DOCTYPE html>
<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hybrid Powerbuilding & 4x4 OS</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        zinc: {
                            950: '#09090b',
                            900: '#18181b',
                            800: '#27272a',
                            700: '#3f3f46',
                        }
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&family=JetBrains+Mono:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
        .font-mono { font-family: 'JetBrains Mono', monospace; }
        ::-webkit-scrollbar { width: 6px; height: 6px; }
        ::-webkit-scrollbar-track { background: #09090b; }
        ::-webkit-scrollbar-thumb { background: #27272a; border-radius: 3px; }
        ::-webkit-scrollbar-thumb:hover { background: #3f3f46; }
    </style>
</head>
<body class="bg-zinc-950 text-zinc-100 min-h-screen flex flex-col selection:bg-amber-500 selection:text-zinc-950">

    <!-- TOP HEADER -->
    <header class="sticky top-0 z-40 bg-zinc-950/95 backdrop-blur-md border-b border-zinc-800 px-4 py-3">
        <div class="max-w-[1600px] mx-auto flex flex-wrap items-center justify-between gap-3">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-amber-500 to-orange-600 flex items-center justify-center shadow-lg shadow-amber-500/20 font-black text-zinc-950">
                    345
                </div>
                <div>
                    <div class="flex items-center gap-2">
                        <h1 class="text-base sm:text-lg font-black tracking-tight uppercase text-white">
                            ARGON // 3-4-5 HYBRID OS
                        </h1>
                        <span id="guardrailStatusBadge" class="hidden sm:inline-flex items-center gap-1 px-2 py-0.5 text-[11px] font-mono font-semibold uppercase rounded-full bg-emerald-500/15 text-emerald-400 border border-emerald-500/30">
                            <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-pulse"></span>
                            Lumbar Guard Active
                        </span>
                    </div>
                    <p class="text-xs text-zinc-400 font-mono">
                        315 BENCH • 405 SQUAT (70LB SSB) • 495 DEADLIFT + 4×/WK NORWEGIAN 4×4
                    </p>
                </div>
            </div>

            <!-- REST TIMER WIDGET -->
            <div class="flex items-center gap-2 bg-zinc-900 border border-zinc-800 rounded-xl px-3 py-1.5">
                <span id="restTimerIcon" class="text-zinc-400 font-bold">⏱</span>
                <span id="restTimerDisplay" class="font-mono text-sm font-bold text-white min-w-[46px]">REST</span>
                <div class="flex items-center gap-1">
                    <button onclick="startRest(60)" class="px-2 py-1 text-[11px] font-mono rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-zinc-300 transition">60s</button>
                    <button onclick="startRest(90)" class="px-2 py-1 text-[11px] font-mono rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-zinc-300 transition">90s</button>
                    <button onclick="startRest(120)" class="px-2 py-1 text-[11px] font-mono rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-zinc-300 transition">2m</button>
                    <button onclick="startRest(180)" class="px-2 py-1 text-[11px] font-mono rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-zinc-300 transition">3m</button>
                    <button onclick="startRest(210)" class="px-2 py-1 text-[11px] font-mono rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-zinc-300 transition">3.5m</button>
                    <button onclick="startRest(240)" class="px-2 py-1 text-[11px] font-mono rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-zinc-300 transition">4m</button>
                    <button onclick="resetRest()" class="p-1 text-zinc-400 hover:text-rose-400" title="Reset">↺</button>
                </div>
            </div>

            <button onclick="toggleMobileChat()" class="xl:hidden flex items-center gap-2 px-3 py-2 rounded-xl bg-amber-500 text-zinc-950 font-bold text-xs uppercase tracking-wider">
                ✨ AI Coach
            </button>
        </div>
    </header>

    <!-- TOAST BANNER -->
    <div id="toast" class="fixed bottom-5 left-1/2 -translate-x-1/2 z-50 hidden items-center gap-2.5 bg-amber-500 text-zinc-950 font-bold text-xs sm:text-sm px-4 py-3 rounded-xl shadow-2xl border border-amber-300 transition-all">
        <span id="toastText">Action Successful</span>
    </div>

    <!-- MAIN APP CONTAINER -->
    <div class="flex-1 max-w-[1600px] w-full mx-auto flex flex-col xl:flex-row overflow-hidden">
        
        <!-- MAIN WORKSPACE -->
        <main class="flex-1 overflow-y-auto p-4 sm:p-6 space-y-6">
            
            <!-- 3-4-5 CLUB METRICS CARDS -->
            <section class="grid grid-cols-1 md:grid-cols-4 gap-3">
                <div class="bg-zinc-900/90 border border-zinc-800/90 rounded-2xl p-4 flex flex-col justify-between">
                    <div class="flex items-center justify-between"><span class="text-[11px] font-mono uppercase text-zinc-400">FLAT BENCH (315 GOAL)</span>🏋️‍♂️</div>
                    <div class="my-2 flex items-baseline justify-between">
                        <div><span id="metricBenchVal" class="text-2xl font-black font-mono text-white">306</span><span class="text-xs font-mono text-zinc-400 ml-1">lbs e1RM</span></div>
                        <span class="text-xs font-mono text-amber-400 font-bold">TARGET: 315</span>
                    </div>
                    <div class="w-full h-2 bg-zinc-800 rounded-full overflow-hidden"><div id="metricBenchBar" class="h-full bg-gradient-to-r from-amber-500 to-emerald-400 rounded-full" style="width: 97%;"></div></div>
                    <div class="mt-2 text-[11px] font-mono text-zinc-400 flex justify-between"><span>255 lbs × 5 @ RPE 8</span><span>97%</span></div>
                </div>

                <div class="bg-zinc-900/90 border border-zinc-800/90 rounded-2xl p-4 flex flex-col justify-between">
                    <div class="flex items-center justify-between"><span class="text-[11px] font-mono uppercase text-zinc-400">SQUAT / 70LB SSB (405)</span>🛡️</div>
                    <div class="my-2 flex items-baseline justify-between">
                        <div><span id="metricSquatVal" class="text-2xl font-black font-mono text-white">333</span><span class="text-xs font-mono text-zinc-400 ml-1">lbs e1RM</span></div>
                        <span class="text-xs font-mono text-amber-400 font-bold">TARGET: 405</span>
                    </div>
                    <div class="w-full h-2 bg-zinc-800 rounded-full overflow-hidden"><div id="metricSquatBar" class="h-full bg-gradient-to-r from-amber-500 to-emerald-400 rounded-full" style="width: 82%;"></div></div>
                    <div class="mt-2 text-[11px] font-mono text-zinc-400 flex justify-between"><span>270 lbs × 5 (SSB)</span><span>82%</span></div>
                </div>

                <div class="bg-zinc-900/90 border border-zinc-800/90 rounded-2xl p-4 flex flex-col justify-between">
                    <div class="flex items-center justify-between"><span class="text-[11px] font-mono uppercase text-zinc-400">DEAD-STOP DL (495 GOAL)</span>🔥</div>
                    <div class="my-2 flex items-baseline justify-between">
                        <div><span id="metricDlVal" class="text-2xl font-black font-mono text-white">451</span><span class="text-xs font-mono text-zinc-400 ml-1">lbs e1RM</span></div>
                        <span class="text-xs font-mono text-amber-400 font-bold">TARGET: 495</span>
                    </div>
                    <div class="w-full h-2 bg-zinc-800 rounded-full overflow-hidden"><div id="metricDlBar" class="h-full bg-gradient-to-r from-amber-500 to-emerald-400 rounded-full" style="width: 91%;"></div></div>
                    <div class="mt-2 text-[11px] font-mono text-zinc-400 flex justify-between"><span>385 lbs × 3 @ RPE 7.5</span><span>91%</span></div>
                </div>

                <div class="bg-zinc-900/90 border border-zinc-800/90 rounded-2xl p-4 flex flex-col justify-between">
                    <div class="flex items-center justify-between"><span class="text-[11px] font-mono uppercase text-zinc-400">WORKING TOTAL & 4×4</span>❤️</div>
                    <div class="my-2 flex items-baseline justify-between">
                        <div><span id="metricTotalVal" class="text-2xl font-black font-mono text-white">1,090</span><span class="text-xs font-mono text-zinc-400 ml-1">/ 1,215</span></div>
                        <span class="px-2 py-0.5 rounded bg-emerald-500/15 text-emerald-400 font-mono text-[11px] font-bold">ACTIVE</span>
                    </div>
                    <div class="text-[11px] font-mono text-zinc-400 space-y-1">
                        <div class="flex justify-between"><span>4x4 HR Zone:</span><span class="text-zinc-200">160–175 BPM</span></div>
                        <div class="flex justify-between"><span>Cadence Target:</span><span class="text-amber-400">165+ SPM Run</span></div>
                    </div>
                </div>
            </section>

            <!-- NAVIGATION TABS -->
            <nav class="flex flex-wrap items-center gap-2 border-b border-zinc-800 pb-3">
                <button onclick="switchTab('logger')" id="tabBtn-logger" class="flex items-center gap-2 px-4 py-2.5 rounded-xl text-xs sm:text-sm font-bold bg-amber-500 text-zinc-950 shadow-lg shadow-amber-500/20 transition">🏋️ Workout Logger (Days 1–5)</button>
                <button onclick="switchTab('plates')" id="tabBtn-plates" class="flex items-center gap-2 px-4 py-2.5 rounded-xl text-xs sm:text-sm font-bold bg-zinc-900 text-zinc-400 hover:bg-zinc-800 hover:text-zinc-200 border border-zinc-800 transition">📐 45lb vs 70lb SSB Plate Calc</button>
                <button onclick="switchTab('timers')" id="tabBtn-timers" class="flex items-center gap-2 px-4 py-2.5 rounded-xl text-xs sm:text-sm font-bold bg-zinc-900 text-zinc-400 hover:bg-zinc-800 hover:text-zinc-200 border border-zinc-800 transition">⏱️ Norwegian 4x4 Timer & Cardio</button>
                <button onclick="switchTab('schedule')" id="tabBtn-schedule" class="flex items-center gap-2 px-4 py-2.5 rounded-xl text-xs sm:text-sm font-bold bg-zinc-900 text-zinc-400 hover:bg-zinc-800 hover:text-zinc-200 border border-zinc-800 transition">📅 Weekly Schedule</button>
            </nav>

            <!-- DYNAMIC LUMBAR ERECTOR GUARDRAIL BANNER -->
            <div id="lumbarGuardrailBanner" class="hidden bg-rose-950/90 border-2 border-rose-500 rounded-2xl p-4 flex flex-col lg:flex-row items-start lg:items-center justify-between gap-4 shadow-2xl">
                <div class="flex items-start gap-3">
                    <span class="text-2xl">🚨</span>
                    <div>
                        <h3 class="text-sm font-black uppercase tracking-wider text-rose-200">LUMBAR ERECTOR GUARDRAIL ALERT — HIGH RPE LOGGED ON AXIAL LIFT</h3>
                        <p class="text-xs text-rose-300 mt-1">Hitting RPE ≥ 9.5 on squats or deadlifts signals spinal stabilizer fatigue. Click below to automatically strip remaining back-off sets by 10% and remove unsupported hinges.</p>
                    </div>
                </div>
                <button onclick="executeLumbarGuardrail()" class="px-4 py-2.5 rounded-xl bg-rose-500 hover:bg-rose-400 text-zinc-950 font-black text-xs uppercase tracking-wider transition shrink-0 shadow-lg">
                    ⚡ 1-Click: Strip Back-Offs by 10% & Clear Hinges
                </button>
            </div>

            <!-- ================= TAB 1: WORKOUT LOGGER ================= -->
            <div id="tabContent-logger" class="space-y-6">
                <!-- Day Selector & Header -->
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-4 sm:p-5 space-y-4">
                    <div class="flex flex-wrap items-center justify-between gap-3">
                        <div id="daySelectorBtns" class="flex flex-wrap items-center gap-2">
                            <!-- Populated via JS -->
                        </div>
                        <div class="flex items-center gap-3">
                            <span class="text-xs font-mono text-zinc-400">Completed: <strong id="completedCount" class="text-amber-400">0/0</strong></span>
                            <button onclick="saveFinishedWorkout()" class="flex items-center gap-1.5 px-4 py-2 rounded-xl bg-emerald-500 hover:bg-emerald-400 text-zinc-950 font-black text-xs uppercase tracking-wider transition shadow-lg shadow-emerald-500/20">
                                ✓ Save Session
                            </button>
                        </div>
                    </div>
                    <div class="border-t border-zinc-800 pt-4 flex flex-col md:flex-row md:items-center justify-between gap-3">
                        <div>
                            <h2 id="activeWorkoutTitle" class="text-xl font-black text-white">Day 1: Upper Push (Bench 315 Focus)</h2>
                            <p id="activeWorkoutSubtitle" class="text-xs sm:text-sm text-zinc-400 mt-0.5">Top Set 255×5 + Back-Offs 235×4×5, Calibrated 115 lb OHP & Parallel Dips</p>
                        </div>
                        <div id="activeWorkoutNotes" class="bg-amber-500/10 border border-amber-500/30 rounded-xl px-3.5 py-2.5 max-w-xl text-xs text-amber-200/90 leading-relaxed">
                            Generate bench arch through your thoracic spine, not lumbar hyperextension. Fasten lifting belt tight on Standing OHP at 115 lbs.
                        </div>
                    </div>
                </div>

                <!-- Exercise List Container -->
                <div id="exerciseContainer" class="space-y-4">
                    <!-- Populated via JS -->
                </div>
            </div>

            <!-- ================= TAB 2: PLATE CALCULATOR ================= -->
            <div id="tabContent-plates" class="hidden bg-zinc-900 border border-zinc-800 rounded-2xl p-6 space-y-6">
                <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                    <div>
                        <h2 class="text-xl font-black text-white">Smart Plate Loader Calculator</h2>
                        <p class="text-xs sm:text-sm text-zinc-400">Toggle between your 45 lb Barbell and 70 lb Safety Squat Bar for exact per-side plate math.</p>
                    </div>
                    <div class="inline-flex rounded-xl bg-zinc-950 p-1 border border-zinc-800">
                        <button onclick="setBarType(45)" id="btnBar45" class="px-4 py-2 rounded-lg text-xs font-mono font-bold bg-amber-500 text-zinc-950 transition">Standard Bar (45 lbs)</button>
                        <button onclick="setBarType(70)" id="btnBar70" class="px-4 py-2 rounded-lg text-xs font-mono font-bold text-zinc-400 hover:text-white transition">Rogue SSB (70 lbs)</button>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-center">
                    <div class="space-y-4">
                        <div>
                            <label class="block text-xs font-mono uppercase text-zinc-400 mb-2">Target Total Load (lbs)</label>
                            <input type="number" id="calcInputWeight" value="270" oninput="updatePlateCalc()" class="w-full bg-zinc-950 border-2 border-zinc-700 focus:border-amber-400 rounded-2xl px-4 py-3 text-3xl font-black font-mono text-white outline-none">
                        </div>
                        <div class="space-y-2">
                            <span class="text-xs font-mono uppercase text-zinc-400">Quick Working Loads:</span>
                            <div class="flex flex-wrap gap-2">
                                <button onclick="quickLoad(115, 45)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">OHP 115</button>
                                <button onclick="quickLoad(130, 70)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">Hatfield 130 (SSB)</button>
                                <button onclick="quickLoad(205, 70)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">SSB Day 4 205</button>
                                <button onclick="quickLoad(235, 45)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">Bench BO 235</button>
                                <button onclick="quickLoad(255, 45)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">Bench Top 255</button>
                                <button onclick="quickLoad(270, 70)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">SSB Top 270</button>
                                <button onclick="quickLoad(315, 45)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">Bench Goal 315</button>
                                <button onclick="quickLoad(385, 45)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">DL Top 385</button>
                                <button onclick="quickLoad(405, 45)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">Squat Goal 405</button>
                                <button onclick="quickLoad(495, 45)" class="px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-xs font-mono font-bold text-zinc-200">DL Goal 495</button>
                            </div>
                        </div>
                    </div>

                    <div class="bg-zinc-950 border border-zinc-800 rounded-2xl p-6 space-y-5">
                        <div class="flex items-center justify-between border-b border-zinc-800 pb-3">
                            <div><span class="text-xs font-mono text-zinc-400 block">BAR WEIGHT</span><span id="calcBarDisplay" class="text-lg font-black font-mono text-white">70 LBS</span></div>
                            <div><span class="text-xs font-mono text-zinc-400 block">PER SIDE</span><span id="calcPerSideDisplay" class="text-lg font-black font-mono text-amber-400">100 LBS</span></div>
                        </div>
                        <div id="calcVisualSleeve" class="py-6 flex items-center justify-start gap-1.5 overflow-x-auto min-h-[140px]">
                            <!-- Visual sleeves populated via JS -->
                        </div>
                        <div id="calcTextSummary" class="text-xs font-mono text-zinc-300 bg-zinc-900 rounded-xl p-3">
                            Load Per Side: 45 lb + 45 lb + 10 lb
                        </div>
                    </div>
                </div>
            </div>

            <!-- ================= TAB 3: NORWEGIAN 4X4 TIMER & CARDIO ================= -->
            <div id="tabContent-timers" class="hidden grid grid-cols-1 lg:grid-cols-2 gap-6">
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-5 flex flex-col justify-between space-y-5">
                    <div>
                        <div class="flex items-center justify-between">
                            <span class="px-2.5 py-1 rounded-full text-xs font-mono uppercase font-bold bg-amber-500/15 text-amber-400 border border-amber-500/30">35-Min Norwegian 4×4 Timer</span>
                            <span class="text-xs font-mono text-emerald-400 font-bold">160–175 BPM Target</span>
                        </div>
                        <div class="mt-4 bg-zinc-950 border border-zinc-800 rounded-2xl p-6 text-center space-y-2">
                            <span id="timerPhaseName" class="text-xs font-mono uppercase tracking-widest text-amber-400">Progressive Warm-Up (6:00)</span>
                            <div id="timerCountdown" class="text-6xl font-black font-mono text-white tracking-tight">06:00</div>
                            <div id="timerZoneBadge" class="inline-block px-3 py-1 rounded-lg bg-emerald-500/15 text-emerald-300 font-mono text-xs font-bold">Zone 1 → 2 (120–135 BPM)</div>
                            <p id="timerCue" class="text-xs text-zinc-400 pt-2 max-w-md mx-auto">Build rhythm smoothly; nasal breathing; establish light mid-foot turnover.</p>
                        </div>
                        <div class="mt-4 flex items-center justify-center gap-3">
                            <button onclick="toggleFourByFour()" id="btn4x4Toggle" class="flex items-center gap-2 px-6 py-3 rounded-xl bg-amber-500 hover:bg-amber-400 text-zinc-950 font-black text-sm uppercase tracking-wider transition">▶ Start 4x4 Timer</button>
                            <button onclick="resetFourByFour()" class="p-3 rounded-xl bg-zinc-800 hover:bg-zinc-700 text-zinc-400">🔄</button>
                        </div>
                    </div>
                </div>

                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-5 space-y-4">
                    <h3 class="text-lg font-black text-white">Log Norwegian 4×4 or Zone 1/2 Flush</h3>
                    <form onsubmit="submitCardioLog(event)" class="space-y-3">
                        <div>
                            <label class="block text-[11px] font-mono uppercase text-zinc-400 mb-1">Modality</label>
                            <select id="cardioModality" class="w-full bg-zinc-950 border border-zinc-700 rounded-xl px-3 py-2 text-sm text-white">
                                <option>Norwegian 4x4: Incline Treadmill (1.5%)</option>
                                <option>Norwegian 4x4: Incline Treadmill (2.0%)</option>
                                <option>Norwegian 4x4: Concept2 Rower</option>
                                <option>Norwegian 4x4: Schwinn Spin Bike</option>
                            </select>
                        </div>
                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <label class="block text-[11px] font-mono uppercase text-zinc-400 mb-1">Avg HR (BPM)</label>
                                <input type="number" id="cardioAvgHr" value="146" class="w-full bg-zinc-950 border border-zinc-700 rounded-xl px-3 py-2 text-sm font-mono text-white">
                            </div>
                            <div>
                                <label class="block text-[11px] font-mono uppercase text-zinc-400 mb-1">Peak HR (BPM)</label>
                                <input type="number" id="cardioPeakHr" value="175" class="w-full bg-zinc-950 border border-zinc-700 rounded-xl px-3 py-2 text-sm font-mono text-emerald-400 font-bold">
                            </div>
                        </div>
                        <button type="submit" class="w-full py-3 rounded-xl bg-emerald-500 hover:bg-emerald-400 text-zinc-950 font-black text-xs uppercase tracking-wider transition">Save Cardio Log</button>
                    </form>
                </div>
            </div>

            <!-- ================= TAB 4: SCHEDULE ================= -->
            <div id="tabContent-schedule" class="hidden space-y-3">
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-4 flex items-center justify-between">
                    <div><span class="text-sm font-black text-amber-400 font-mono">MONDAY</span><p class="text-sm font-bold text-white mt-1">AM: Norwegian 4x4 #1 | PM: Day 1 Upper Push (Bench 315)</p></div>
                    <button onclick="loadDayTemplate('day1_upper_push'); switchTab('logger');" class="px-3 py-1.5 rounded-xl bg-amber-500 text-zinc-950 font-black text-xs">Load Workout</button>
                </div>
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-4 flex items-center justify-between">
                    <div><span class="text-sm font-black text-amber-400 font-mono">TUESDAY</span><p class="text-sm font-bold text-white mt-1">AM: Off Running | PM: Day 2 Lower Power (70lb SSB Squat Focus)</p></div>
                    <button onclick="loadDayTemplate('day2_lower_squat'); switchTab('logger');" class="px-3 py-1.5 rounded-xl bg-amber-500 text-zinc-950 font-black text-xs">Load Workout</button>
                </div>
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-4 flex items-center justify-between">
                    <div><span class="text-sm font-black text-amber-400 font-mono">WEDNESDAY</span><p class="text-sm font-bold text-white mt-1">AM: Norwegian 4x4 #2 | PM: Day 3 Upper Pull (+35 Weighted Pull-Ups)</p></div>
                    <button onclick="loadDayTemplate('day3_upper_pull'); switchTab('logger');" class="px-3 py-1.5 rounded-xl bg-amber-500 text-zinc-950 font-black text-xs">Load Workout</button>
                </div>
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-4 flex items-center justify-between">
                    <div><span class="text-sm font-black text-amber-400 font-mono">THURSDAY</span><p class="text-sm font-bold text-white mt-1">AM: Norwegian 4x4 #3 | PM: Active Recovery Flush & Core Armor</p></div>
                    <button onclick="loadDayTemplate('day5_upper_pump'); switchTab('logger');" class="px-3 py-1.5 rounded-xl bg-amber-500 text-zinc-950 font-black text-xs">Load Workout</button>
                </div>
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-4 flex items-center justify-between">
                    <div><span class="text-sm font-black text-amber-400 font-mono">FRIDAY</span><p class="text-sm font-bold text-white mt-1">AM: Off Running | PM: Day 4 Lower Deadlift (385×3 Top Set + SSB)</p></div>
                    <button onclick="loadDayTemplate('day4_lower_deadlift'); switchTab('logger');" class="px-3 py-1.5 rounded-xl bg-amber-500 text-zinc-950 font-black text-xs">Load Workout</button>
                </div>
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-4 flex items-center justify-between">
                    <div><span class="text-sm font-black text-amber-400 font-mono">SATURDAY</span><p class="text-sm font-bold text-white mt-1">AM: Norwegian 4x4 #4 | PM: Day 5 Zero-Axial Upper Body Pump</p></div>
                    <button onclick="loadDayTemplate('day5_upper_pump'); switchTab('logger');" class="px-3 py-1.5 rounded-xl bg-amber-500 text-zinc-950 font-black text-xs">Load Workout</button>
                </div>
                <div class="bg-zinc-900 border border-zinc-800 rounded-2xl p-4 flex items-center justify-between">
                    <div><span class="text-sm font-black text-amber-400 font-mono">SUNDAY</span><p class="text-sm font-bold text-white mt-1">AM: Full Systemic CNS Recovery | PM: Rest & Nutrition (~200g Protein)</p></div>
                </div>
            </div>

        </main>

        <!-- GEMINI AI COACH SIDEBAR -->
        <aside id="aiCoachSidebar" class="hidden xl:flex w-full xl:w-[430px] shrink-0 bg-zinc-900 border-l border-zinc-800 flex-col h-[calc(100vh-65px)]">
            <div class="p-4 border-b border-zinc-800 flex items-center justify-between bg-zinc-950/60">
                <div class="flex items-center gap-2.5">
                    <div class="w-8 h-8 rounded-lg bg-amber-500/20 border border-amber-500/40 flex items-center justify-center text-amber-400">✨</div>
                    <div>
                        <h2 class="text-sm font-black uppercase tracking-wider text-white">GEMINI AI COACH</h2>
                        <p class="text-[11px] font-mono text-emerald-400">Real-Time Workout Plan Mutator</p>
                    </div>
                </div>
                <button onclick="toggleMobileChat()" class="xl:hidden px-3 py-1 rounded-lg bg-zinc-800 text-xs text-zinc-300">Close</button>
            </div>

            <div class="p-3 bg-zinc-950/40 border-b border-zinc-800 space-y-1.5">
                <span class="text-[10px] font-mono uppercase text-zinc-400 block">Quick Live Audibles:</span>
                <div class="flex flex-wrap gap-1.5">
                    <button onclick="sendQuickAudible('RPE 9.5 Audible')" class="px-2.5 py-1 rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-[11px] font-mono text-zinc-300 transition border border-zinc-700">RPE 9.5 Audible (-10%)</button>
                    <button onclick="sendQuickAudible('Load Day 2')" class="px-2.5 py-1 rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-[11px] font-mono text-zinc-300 transition border border-zinc-700">Load Day 2: 70lb SSB</button>
                    <button onclick="sendQuickAudible('Load Day 5')" class="px-2.5 py-1 rounded-lg bg-zinc-800 hover:bg-amber-500 hover:text-zinc-950 text-[11px] font-mono text-zinc-300 transition border border-zinc-700">Load Day 5: Upper Pump</button>
                </div>
            </div>

            <div id="chatMessages" class="flex-1 overflow-y-auto p-4 space-y-3">
                <div class="flex flex-col items-start">
                    <div class="max-w-[90%] rounded-2xl px-4 py-3 text-xs sm:text-sm bg-zinc-950 border border-zinc-800 text-zinc-200 leading-relaxed">
                        Ready on the platform. Your 315 Bench / 405 Squat / 495 Deadlift progression and 4×/wk Norwegian 4x4 schedule are pre-loaded. Tell me how your sets felt or ask to modify your workout plan in real time!
                    </div>
                </div>
            </div>

            <form onsubmit="handleChatSubmit(event)" class="p-3 border-t border-zinc-800 bg-zinc-950 flex items-center gap-2">
                <input type="text" id="chatInputBox" placeholder="Tell Coach how a set felt or ask to modify workout..." class="flex-1 bg-zinc-900 border border-zinc-700 focus:border-amber-400 rounded-xl px-3.5 py-2.5 text-xs sm:text-sm text-white outline-none">
                <button type="submit" class="p-2.5 rounded-xl bg-amber-500 hover:bg-amber-400 text-zinc-950 transition font-bold">➤</button>
            </form>
        </aside>

    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // --- RTS / EPLEY-RPE e1RM TABLE ---
        const RTS_PERCENT = {
            1:1.0, 1.5:0.978, 2:0.955, 2.5:0.939, 3:0.922, 3.5:0.907, 4:0.892, 4.5:0.878, 5:0.863, 5.5:0.85,
            6:0.837, 6.5:0.824, 7:0.811, 7.5:0.799, 8:0.786, 8.5:0.774, 9:0.762, 9.5:0.751, 10:0.739, 10.5:0.723, 11:0.707, 11.5:0.694, 12:0.68
        };

        function calculateE1RM(weight, reps, rpe) {
            const w = parseFloat(weight) || 0;
            const r = parseInt(reps, 10) || 0;
            const clampedRpe = Math.min(10, Math.max(6, parseFloat(rpe) || 8));
            if (w <= 0 || r <= 0) return 0;
            const rir = Math.max(0, 10 - clampedRpe);
            const eff = Math.round((r + rir) * 2) / 2;
            if (RTS_PERCENT[eff]) return Math.round(w / RTS_PERCENT[eff]);
            return Math.round(w * (1 + eff / 30));
        }

        // --- WORKOUT TEMPLATES ---
        const TEMPLATES = {
            day1_upper_push: {
                id: 'day1_upper_push',
                title: 'Day 1: Upper Push (Bench 315 Focus)',
                subtitle: 'Top Set 255×5 + Back-Offs 235×4×5, Calibrated 115 lb OHP & Parallel Dips',
                notes: 'Generate bench arch through your thoracic spine, not lumbar hyperextension. Fasten lifting belt tight on Standing OHP at 115 lbs.',
                exercises: [
                    {
                        id: 'd1_bench', name: 'Flat Barbell Bench Press', barType: '45lb', liftKey: 'bench', isAxial: false, restSeconds: 210,
                        cue: 'Screw scapulae into pad, drive heels horizontally, touch lower sternum under control.',
                        sets: [
                            { id: 'b1', type: 'WARMUP', weight: 135, reps: 5, rpe: 6.0, completed: true },
                            { id: 'b2', type: 'WARMUP', weight: 185, reps: 3, rpe: 6.5, completed: true },
                            { id: 'b3', type: 'WARMUP', weight: 225, reps: 2, rpe: 7.0, completed: true },
                            { id: 'b4', type: 'TOP SET', weight: 255, reps: 5, rpe: 8.0, completed: false },
                            { id: 'b5', type: 'BACK-OFF', weight: 235, reps: 5, rpe: 7.5, completed: false },
                            { id: 'b6', type: 'BACK-OFF', weight: 235, reps: 5, rpe: 7.5, completed: false },
                            { id: 'b7', type: 'BACK-OFF', weight: 235, reps: 5, rpe: 7.5, completed: false },
                            { id: 'b8', type: 'BACK-OFF', weight: 235, reps: 5, rpe: 7.5, completed: false }
                        ]
                    },
                    {
                        id: 'd1_ohp', name: 'Standing Barbell OHP', barType: '45lb', isAxial: true, restSeconds: 150,
                        cue: 'Calibrated at 115 lbs. Belt tight; squeeze glutes and quads rigid—zero layback.',
                        sets: [
                            { id: 'o1', type: 'WORKING', weight: 115, reps: 6, rpe: 8.0, completed: false },
                            { id: 'o2', type: 'WORKING', weight: 115, reps: 6, rpe: 8.0, completed: false },
                            { id: 'o3', type: 'WORKING', weight: 115, reps: 6, rpe: 8.0, completed: false },
                            { id: 'o4', type: 'WORKING', weight: 115, reps: 6, rpe: 8.0, completed: false }
                        ]
                    },
                    {
                        id: 'd1_dips', name: 'Parallel Bar Dips', barType: 'BW', isAxial: false, restSeconds: 120,
                        cue: '15–20° forward torso lean; let legs hang slack to naturally traction the lumbar spine.',
                        sets: [
                            { id: 'dp1', type: 'WORKING', weight: 200, reps: 10, rpe: 8.0, completed: false },
                            { id: 'dp2', type: 'WORKING', weight: 200, reps: 10, rpe: 8.0, completed: false },
                            { id: 'dp3', type: 'WORKING', weight: 200, reps: 9, rpe: 8.0, completed: false }
                        ]
                    }
                ]
            },
            day2_lower_squat: {
                id: 'day2_lower_squat',
                title: 'Day 2: Lower Power (SSB Squat Focus)',
                subtitle: '70 lb Safety Squat Bar Top Set 270×5 + Back-Offs 235×3×5 & Hatfield Split Squats',
                notes: 'Rogue Safety Squat Bar weighs 70 lbs empty. Top-Set + Back-Off structure prevents Set 3/4 RPE 10 spinal stabilizer fatigue.',
                exercises: [
                    {
                        id: 'd2_ssb', name: 'Safety Squat Bar (SSB) Squat [70 lb Bar]', barType: '70lb_SSB', liftKey: 'squat', isAxial: true, restSeconds: 210,
                        cue: 'Relax hands on handles; push neck and upper traps UP and BACK into the yoke pad out of the hole.',
                        sets: [
                            { id: 's1', type: 'WARMUP', weight: 160, reps: 5, rpe: 6.0, completed: true },
                            { id: 's2', type: 'WARMUP', weight: 210, reps: 3, rpe: 6.5, completed: true },
                            { id: 's3', type: 'TOP SET', weight: 270, reps: 5, rpe: 8.0, completed: false },
                            { id: 's4', type: 'BACK-OFF', weight: 235, reps: 5, rpe: 7.5, completed: false },
                            { id: 's5', type: 'BACK-OFF', weight: 235, reps: 5, rpe: 7.5, completed: false },
                            { id: 's6', type: 'BACK-OFF', weight: 235, reps: 5, rpe: 7.5, completed: false }
                        ]
                    },
                    {
                        id: 'd2_hatfield', name: 'Hatfield SSB Bulgarian Split Squats', barType: '70lb_SSB', isAxial: false, restSeconds: 90,
                        cue: 'Hold Rogue rack uprights at chest height for balance; drop straight down with a vertical spine.',
                        sets: [
                            { id: 'h1', type: 'WORKING', weight: 130, reps: 8, rpe: 8.0, completed: false },
                            { id: 'h2', type: 'WORKING', weight: 130, reps: 8, rpe: 8.0, completed: false },
                            { id: 'h3', type: 'WORKING', weight: 130, reps: 8, rpe: 8.0, completed: false }
                        ]
                    }
                ]
            },
            day3_upper_pull: {
                id: 'day3_upper_pull',
                title: 'Day 3: Upper Pull (Zero Lumbar Shear)',
                subtitle: 'Weighted Pull-Ups (+35 lbs), Chest-Supported DB Rows (85s) & Arms',
                notes: '100% spinal traction or chest-supported pulling. Zero unsupported bent-over barbell rows.',
                exercises: [
                    {
                        id: 'd3_pu', name: 'Weighted Pull-Ups (+35 lbs Dip Belt)', barType: 'DipBelt', isAxial: false, restSeconds: 180,
                        cue: 'Full dead hang at bottom; pull scapulae down and drive elbows to back pockets. Zero kipping.',
                        sets: [
                            { id: 'p1', type: 'WORKING', weight: 35, reps: 5, rpe: 8.0, completed: false },
                            { id: 'p2', type: 'WORKING', weight: 35, reps: 5, rpe: 8.0, completed: false },
                            { id: 'p3', type: 'WORKING', weight: 35, reps: 5, rpe: 8.0, completed: false }
                        ]
                    },
                    {
                        id: 'd3_csr', name: 'Chest-Supported DB Rows (30–45° Incline)', barType: 'DB', isAxial: false, restSeconds: 120,
                        cue: 'Anchor sternum flat to pad; row dumbbells into hip crease with a 1-second peak squeeze.',
                        sets: [
                            { id: 'c1', type: 'WORKING', weight: 85, reps: 10, rpe: 8.0, completed: false },
                            { id: 'c2', type: 'WORKING', weight: 85, reps: 10, rpe: 8.0, completed: false },
                            { id: 'c3', type: 'WORKING', weight: 85, reps: 9, rpe: 8.0, completed: false }
                        ]
                    }
                ]
            },
            day4_lower_deadlift: {
                id: 'day4_lower_deadlift',
                title: 'Day 4: Lower Deadlift & SSB',
                subtitle: 'Dead-Stop Conventional Deadlift (385×3 Top Set, 355×3×4 Back-Offs) & 205 lb SSB Squats',
                notes: 'Pull every rep from a complete dead stop—zero touch-and-go bouncing. Reset 360° diaphragmatic breath on the floor.',
                exercises: [
                    {
                        id: 'd4_dl', name: 'Conventional Barbell Deadlift (Dead-Stop)', barType: '45lb', liftKey: 'deadlift', isAxial: true, restSeconds: 240,
                        cue: 'Pull slack out of bar, wedge hips, leg-press floor away. Halt immediately if any lumbar pinch.',
                        sets: [
                            { id: 'dl1', type: 'WARMUP', weight: 135, reps: 5, rpe: 6.0, completed: true },
                            { id: 'dl2', type: 'WARMUP', weight: 225, reps: 3, rpe: 6.0, completed: true },
                            { id: 'dl3', type: 'WARMUP', weight: 315, reps: 2, rpe: 6.5, completed: true },
                            { id: 'dl4', type: 'TOP SET', weight: 385, reps: 3, rpe: 7.5, completed: false },
                            { id: 'dl5', type: 'BACK-OFF', weight: 355, reps: 4, rpe: 7.5, completed: false },
                            { id: 'dl6', type: 'BACK-OFF', weight: 355, reps: 4, rpe: 7.5, completed: false },
                            { id: 'dl7', type: 'BACK-OFF', weight: 355, reps: 4, rpe: 7.5, completed: false }
                        ]
                    }
                ]
            },
            day5_upper_pump: {
                id: 'day5_upper_pump',
                title: 'Day 5: Zero-Axial Upper Body Pump',
                subtitle: 'Seated 75° DB Press (55s), 30° Incline Bench & CS Rows (70s), 20 lb Laterals',
                notes: '100% chest- and back-supported upper hypertrophy. Zero compressive shear on the lumbar spine.',
                exercises: [
                    {
                        id: 'd5_sdbo', name: 'Seated DB Shoulder Press (75° Incline)', barType: 'DB', isAxial: false, restSeconds: 120,
                        cue: 'Calibrated at 55 lbs. Keep upper back and head glued to pad.',
                        sets: [
                            { id: 'sd1', type: 'WORKING', weight: 55, reps: 9, rpe: 8.0, completed: false },
                            { id: 'sd2', type: 'WORKING', weight: 55, reps: 9, rpe: 8.0, completed: false },
                            { id: 'sd3', type: 'WORKING', weight: 55, reps: 8, rpe: 8.0, completed: false }
                        ]
                    }
                ]
            }
        };

        let currentActiveDayId = 'day1_upper_push';
        let currentWorkout = JSON.parse(JSON.stringify(TEMPLATES.day1_upper_push));
        let activeBarType = 70; // 70lb SSB by default for powerbuilding baseline

        // --- APP INITIALIZATION ---
        window.addEventListener('DOMContentLoaded', () => {
            renderDaySelector();
            renderActiveWorkout();
            updatePlateCalc();
            initFourByFourTimer();
        });

        function switchTab(tabId) {
            ['logger', 'plates', 'timers', 'schedule'].forEach(id => {
                document.getElementById('tabContent-' + id).classList.add('hidden');
                document.getElementById('tabBtn-' + id).className = "flex items-center gap-2 px-4 py-2.5 rounded-xl text-xs sm:text-sm font-bold bg-zinc-900 text-zinc-400 hover:bg-zinc-800 hover:text-zinc-200 border border-zinc-800 transition";
            });
            document.getElementById('tabContent-' + tabId).classList.remove('hidden');
            document.getElementById('tabBtn-' + tabId).className = "flex items-center gap-2 px-4 py-2.5 rounded-xl text-xs sm:text-sm font-bold bg-amber-500 text-zinc-950 shadow-lg shadow-amber-500/20 transition";
        }

        function triggerToast(msg) {
            const t = document.getElementById('toast');
            document.getElementById('toastText').innerText = msg;
            t.classList.remove('hidden');
            t.classList.add('flex');
            setTimeout(() => {
                t.classList.remove('flex');
                t.classList.add('hidden');
            }, 3500);
        }

        // --- REST TIMER ---
        let restInterval = null;
        let restSecondsLeft = 0;
        function startRest(sec) {
            clearInterval(restInterval);
            restSecondsLeft = sec;
            updateRestDisplay();
            document.getElementById('restTimerIcon').classList.add('text-amber-400', 'animate-spin');
            restInterval = setInterval(() => {
                restSecondsLeft--;
                if (restSecondsLeft <= 0) {
                    clearInterval(restInterval);
                    document.getElementById('restTimerIcon').classList.remove('text-amber-400', 'animate-spin');
                    document.getElementById('restTimerDisplay').innerText = '0:00';
                    triggerToast('Rest Complete — Brace 360° & Approach Bar');
                } else {
                    updateRestDisplay();
                }
            }, 1000);
        }
        function updateRestDisplay() {
            const m = Math.floor(restSecondsLeft / 60);
            const s = restSecondsLeft % 60;
            document.getElementById('restTimerDisplay').innerText = `${m}:${s < 10 ? '0' : ''}${s}`;
        }
        function resetRest() {
            clearInterval(restInterval);
            document.getElementById('restTimerIcon').classList.remove('text-amber-400', 'animate-spin');
            document.getElementById('restTimerDisplay').innerText = 'REST';
        }

        // --- RENDER WORKOUT LOGGER ---
        function renderDaySelector() {
            const container = document.getElementById('daySelectorBtns');
            container.innerHTML = '';
            Object.values(TEMPLATES).forEach(tpl => {
                const btn = document.createElement('button');
                btn.className = `px-3.5 py-2 rounded-xl text-xs font-mono font-bold transition ${currentActiveDayId === tpl.id ? 'bg-amber-500 text-zinc-950 shadow-md shadow-amber-500/20' : 'bg-zinc-800/80 text-zinc-300 hover:bg-zinc-700'}`;
                btn.innerText = tpl.title.split(':')[0] + ': ' + tpl.title.split('(')[0].split(':')[1];
                btn.onclick = () => loadDayTemplate(tpl.id);
                container.appendChild(btn);
            });
        }

        function loadDayTemplate(dayId) {
            currentActiveDayId = dayId;
            currentWorkout = JSON.parse(JSON.stringify(TEMPLATES[dayId]));
            renderDaySelector();
            renderActiveWorkout();
            document.getElementById('lumbarGuardrailBanner').classList.add('hidden');
        }

        function renderActiveWorkout() {
            document.getElementById('activeWorkoutTitle').innerText = currentWorkout.title;
            document.getElementById('activeWorkoutSubtitle').innerText = currentWorkout.subtitle;
            document.getElementById('activeWorkoutNotes').innerText = currentWorkout.notes || '';

            let doneCount = 0;
            let totalCount = 0;
            currentWorkout.exercises.forEach(ex => ex.sets.forEach(s => {
                totalCount++;
                if (s.completed) doneCount++;
            }));
            document.getElementById('completedCount').innerText = `${doneCount}/${totalCount}`;

            const container = document.getElementById('exerciseContainer');
            container.innerHTML = '';

            currentWorkout.exercises.forEach((ex, idx) => {
                const isSSB = ex.barType === '70lb_SSB';
                const isStandard = ex.barType === '45lb';

                const card = document.createElement('div');
                card.className = "bg-zinc-900/95 border border-zinc-800 rounded-2xl overflow-hidden";
                
                let setsHtml = '';
                ex.sets.forEach((s, sIdx) => {
                    const e1rm = (s.type === 'WARMUP' || s.unit === 'sec') ? '—' : calculateE1RM(s.weight, s.reps, s.rpe) + ' lbs';
                    const isHighRpe = parseFloat(s.rpe) >= 9.5 && ex.isAxial;

                    setsHtml += `
                        <tr class="transition ${s.completed ? 'bg-emerald-950/20 text-zinc-300' : isHighRpe ? 'bg-rose-950/35' : 'hover:bg-zinc-800/40'}">
                            <td class="py-2.5 px-4 font-mono text-xs text-zinc-400">${sIdx + 1}</td>
                            <td class="py-2.5 px-3"><span class="px-2 py-0.5 rounded text-[10px] font-mono font-bold uppercase ${s.type==='TOP SET'?'bg-amber-500 text-zinc-950':s.type==='BACK-OFF'?'bg-sky-500/20 text-sky-300 border border-sky-500/30':'bg-zinc-800 text-zinc-300'}">${s.type}</span></td>
                            <td class="py-2.5 px-3"><input type="number" step="5" value="${s.weight}" onchange="updateSetVal('${ex.id}','${s.id}','weight',this.value)" class="w-20 bg-zinc-950 border border-zinc-700 focus:border-amber-400 rounded-lg px-2.5 py-1 font-mono text-sm font-bold text-white outline-none"></td>
                            <td class="py-2.5 px-3">
                                <input type="number" value="${s.reps}" onchange="updateSetVal('${ex.id}','${s.id}','reps',this.value)" class="w-16 bg-zinc-950 border border-zinc-700 focus:border-amber-400 rounded-lg px-2.5 py-1 font-mono text-sm font-bold text-white outline-none">
                                ${s.unit ? '<span class="text-xs font-mono text-zinc-400">'+s.unit+'</span>' : ''}
                            </td>
                            <td class="py-2.5 px-3">
                                <select onchange="updateSetVal('${ex.id}','${s.id}','rpe',this.value)" class="bg-zinc-950 border ${isHighRpe ? 'border-rose-500 text-rose-400' : 'border-zinc-700 text-amber-400'} rounded-lg px-2 py-1 font-mono text-sm font-bold outline-none">
                                    ${[6.0, 6.5, 7.0, 7.5, 8.0, 8.5, 9.0, 9.5, 10.0].map(v => `<option value="${v}" ${parseFloat(s.rpe)===v?'selected':''}>RPE ${v.toFixed(1)}</option>`).join('')}
                                </select>
                            </td>
                            <td class="py-2.5 px-3 font-mono text-xs text-emerald-400 font-bold">${e1rm}</td>
                            <td class="py-2.5 px-4 text-right">
                                <button onclick="toggleSetComplete('${ex.id}','${s.id}')" class="w-7 h-7 rounded-lg inline-flex items-center justify-center font-bold transition ${s.completed ? 'bg-emerald-500 text-zinc-950' : 'bg-zinc-800 text-zinc-400 hover:bg-zinc-700'}">✓</button>
                            </td>
                        </tr>
                    `;
                });

                card.innerHTML = `
                    <div class="p-4 bg-zinc-900 border-b border-zinc-800 flex flex-wrap items-center justify-between gap-3">
                        <div class="space-y-1">
                            <div class="flex items-center gap-2">
                                <span class="px-2 py-0.5 rounded bg-zinc-800 text-amber-400 font-mono text-xs font-bold">#${idx+1}</span>
                                <h3 class="text-base sm:text-lg font-extrabold text-white">${ex.name}</h3>
                                <span class="px-2 py-0.5 rounded text-[11px] font-mono font-bold uppercase ${isSSB?'bg-emerald-500/20 text-emerald-300 border border-emerald-500/30':isStandard?'bg-amber-500/20 text-amber-300 border border-amber-500/30':'bg-zinc-800 text-zinc-300'}">
                                    ${isSSB?'70 LB ROGUE SSB':isStandard?'45 LB BARBELL':ex.barType}
                                </span>
                            </div>
                            <p class="text-xs text-zinc-400">${ex.cue}</p>
                        </div>
                        <button onclick="startRest(${ex.restSeconds || 120})" class="flex items-center gap-1.5 px-3 py-1.5 rounded-xl bg-zinc-800 hover:bg-zinc-700 text-xs font-mono text-zinc-200 transition">⏱ Rest ${formatSec(ex.restSeconds || 120)}</button>
                    </div>
                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="border-b border-zinc-800/80 text-[11px] font-mono uppercase text-zinc-400 bg-zinc-950/40">
                                    <th class="py-2.5 px-4">Set</th>
                                    <th class="py-2.5 px-3">Type</th>
                                    <th class="py-2.5 px-3">Weight</th>
                                    <th class="py-2.5 px-3">Reps</th>
                                    <th class="py-2.5 px-3">RPE</th>
                                    <th class="py-2.5 px-3">e1RM</th>
                                    <th class="py-2.5 px-4 text-right">Complete</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-zinc-800/60 text-sm">${setsHtml}</tbody>
                        </table>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        function formatSec(sec) {
            const m = Math.floor(sec / 60);
            const r = sec % 60;
            return `${m}:${r < 10 ? '0' : ''}${r}`;
        }

        function updateSetVal(exId, setId, field, val) {
            currentWorkout.exercises.forEach(ex => {
                if (ex.id === exId) {
                    ex.sets.forEach(s => {
                        if (s.id === setId) {
                            s[field] = (field === 'weight' || field === 'reps' || field === 'rpe') ? parseFloat(val) : val;
                            if (ex.isAxial && parseFloat(s.rpe) >= 9.5 && (field === 'rpe' || s.completed)) {
                                document.getElementById('lumbarGuardrailBanner').classList.remove('hidden');
                            }
                        }
                    });
                }
            });
            renderActiveWorkout();
        }

        function toggleSetComplete(exId, setId) {
            currentWorkout.exercises.forEach(ex => {
                if (ex.id === exId) {
                    ex.sets.forEach(s => {
                        if (s.id === setId) {
                            s.completed = !s.completed;
                            if (s.completed && ex.restSeconds) startRest(ex.restSeconds);
                            if (s.completed && ex.isAxial && parseFloat(s.rpe) >= 9.5) {
                                document.getElementById('lumbarGuardrailBanner').classList.remove('hidden');
                            }
                        }
                    });
                }
            });
            renderActiveWorkout();
        }

        function executeLumbarGuardrail() {
            currentWorkout.exercises.forEach(ex => {
                if (ex.isAxial) {
                    ex.sets.forEach(s => {
                        if (!s.completed && (s.type === 'BACK-OFF' || s.type === 'WORKING')) {
                            s.weight = Math.round((s.weight * 0.9) / 5) * 5;
                            s.rpe = 7.5;
                        }
                    });
                }
            });
            document.getElementById('lumbarGuardrailBanner').classList.add('hidden');
            renderActiveWorkout();
            triggerToast('Remaining Back-Off Sets Stripped by 10% (Lumbar Guardrail Active)');
        }

        function saveFinishedWorkout() {
            triggerToast('Workout Successfully Saved to Performance Log!');
        }

        // --- PLATE CALCULATOR ---
        function setBarType(bW) {
            activeBarType = bW;
            document.getElementById('btnBar45').className = bW === 45 ? "px-4 py-2 rounded-lg text-xs font-mono font-bold bg-amber-500 text-zinc-950 transition" : "px-4 py-2 rounded-lg text-xs font-mono font-bold text-zinc-400 hover:text-white transition";
            document.getElementById('btnBar70').className = bW === 70 ? "px-4 py-2 rounded-lg text-xs font-mono font-bold bg-emerald-500 text-zinc-950 transition" : "px-4 py-2 rounded-lg text-xs font-mono font-bold text-zinc-400 hover:text-white transition";
            updatePlateCalc();
        }

        function quickLoad(w, b) {
            document.getElementById('calcInputWeight').value = w;
            setBarType(b);
        }

        function updatePlateCalc() {
            const target = parseFloat(document.getElementById('calcInputWeight').value) || 0;
            document.getElementById('calcBarDisplay').innerText = activeBarType + ' LBS';
            if (target <= activeBarType) {
                document.getElementById('calcPerSideDisplay').innerText = '0 LBS';
                document.getElementById('calcVisualSleeve').innerHTML = '<span class="text-xs font-mono text-zinc-500">Empty Bar</span>';
                document.getElementById('calcTextSummary').innerText = 'Empty bar.';
                return;
            }
            const perSide = (target - activeBarType) / 2;
            document.getElementById('calcPerSideDisplay').innerText = perSide + ' LBS';

            const available = [45, 35, 25, 10, 5, 2.5];
            let rem = perSide;
            const plates = [];
            for (const p of available) {
                while (rem >= p - 0.001) {
                    plates.push(p);
                    rem = Math.round((rem - p) * 100) / 100;
                }
            }

            const sleeveContainer = document.getElementById('calcVisualSleeve');
            let html = `<div class="h-5 w-16 bg-zinc-600 rounded-l-md flex items-center justify-center text-[10px] font-mono font-bold text-zinc-950 shrink-0">${activeBarType}LB</div><div class="h-8 w-3 bg-zinc-400 rounded-sm shrink-0"></div>`;
            
            const heightMap = {
                45: 'h-28 bg-blue-600 border-blue-400 text-white',
                35: 'h-24 bg-amber-500 border-amber-300 text-zinc-950',
                25: 'h-20 bg-emerald-600 border-emerald-400 text-white',
                10: 'h-16 bg-zinc-200 border-white text-zinc-950',
                5: 'h-12 bg-rose-600 border-rose-400 text-white',
                2.5: 'h-10 bg-purple-600 border-purple-400 text-white'
            };

            plates.forEach(p => {
                html += `<div class="w-8 rounded-md border flex items-center justify-center font-mono text-xs font-black shadow-md shrink-0 ${heightMap[p]||'h-14 bg-zinc-700'}">${p}</div>`;
            });
            html += '<div class="h-4 w-12 bg-zinc-700 rounded-r-md shrink-0"></div>';
            sleeveContainer.innerHTML = html;
            document.getElementById('calcTextSummary').innerText = `Load Per Side: ${plates.length ? plates.join(' lb + ') + ' lb' : 'None'}`;
        }

        // --- NORWEGIAN 4X4 TIMER ---
        const PHASES = [
            { name: 'Progressive Warm-Up (6:00)', duration: 360, zone: 'Zone 1 → 2 (120–135 BPM)', cue: 'Build rhythm smoothly; nasal breathing; establish light mid-foot turnover.' },
            { name: 'Interval 1 / 4 — VO2 Max Work (4:00)', duration: 240, zone: '85–95% HRmax (160–175 BPM)', cue: 'Cross 160 BPM by the 90-second mark. Cadence 165–170 SPM.' },
            { name: 'Active Recovery 1 / 3 (3:00)', duration: 180, zone: '70% HRmax (125–135 BPM)', cue: 'Brisk walk or easy spin. Keep moving to flush lactate.' },
            { name: 'Interval 2 / 4 — VO2 Max Work (4:00)', duration: 240, zone: '85–95% HRmax (160–175 BPM)', cue: 'Compact stride under center of mass.' },
            { name: 'Active Recovery 2 / 3 (3:00)', duration: 180, zone: '70% HRmax (125–135 BPM)', cue: 'Control breathing; bring HR back into pocket.' },
            { name: 'Interval 3 / 4 — VO2 Max Work (4:00)', duration: 240, zone: '85–95% HRmax (160–175 BPM)', cue: 'Maintain tall posture and 165+ SPM turnover.' },
            { name: 'Active Recovery 3 / 3 (3:00)', duration: 180, zone: '70% HRmax (125–135 BPM)', cue: 'Final recovery valley before 4th interval.' },
            { name: 'Interval 4 / 4 — Final VO2 Push (4:00)', duration: 240, zone: '85–95% HRmax (160–175 BPM)', cue: 'Hold 160–175 BPM zone through final bell.' },
            { name: 'Cool-Down & Decompression (4:00)', duration: 240, zone: 'Zone 1 (<120 BPM)', cue: 'Easy walk + nasal diaphragmatic breathing.' }
        ];
        let timerRunning = false;
        let phaseIdx = 0;
        let secLeft = 360;
        let tInterval = null;

        function initFourByFourTimer() {
            updateTimerUI();
        }
        function updateTimerUI() {
            const p = PHASES[phaseIdx];
            document.getElementById('timerPhaseName').innerText = p.name;
            document.getElementById('timerZoneBadge').innerText = p.zone;
            document.getElementById('timerCue').innerText = p.cue;
            const m = Math.floor(secLeft / 60);
            const s = secLeft % 60;
            document.getElementById('timerCountdown').innerText = `${m < 10 ? '0' : ''}${m}:${s < 10 ? '0' : ''}${s}`;
        }
        function toggleFourByFour() {
            timerRunning = !timerRunning;
            const btn = document.getElementById('btn4x4Toggle');
            if (timerRunning) {
                btn.innerText = '⏸ Pause 4x4';
                tInterval = setInterval(() => {
                    secLeft--;
                    if (secLeft <= 0) {
                        phaseIdx++;
                        if (phaseIdx < PHASES.length) {
                            secLeft = PHASES[phaseIdx].duration;
                            triggerToast(`Phase: ${PHASES[phaseIdx].name}`);
                        } else {
                            timerRunning = false;
                            clearInterval(tInterval);
                            triggerToast('35-Minute Norwegian 4x4 Complete!');
                        }
                    }
                    updateTimerUI();
                }, 1000);
            } else {
                btn.innerText = '▶ Resume 4x4';
                clearInterval(tInterval);
            }
        }
        function resetFourByFour() {
            timerRunning = false;
            clearInterval(tInterval);
            phaseIdx = 0;
            secLeft = PHASES[0].duration;
            document.getElementById('btn4x4Toggle').innerText = '▶ Start 4x4 Timer';
            updateTimerUI();
        }
        function submitCardioLog(e) {
            e.preventDefault();
            triggerToast('Norwegian 4x4 Session Logged Successfully');
        }

        // --- GEMINI AI COACH SIDEBAR & MOCK LLM INTEGRATION ---
        function toggleMobileChat() {
            const sidebar = document.getElementById('aiCoachSidebar');
            sidebar.classList.toggle('hidden');
            sidebar.classList.toggle('fixed');
            sidebar.classList.toggle('inset-0');
            sidebar.classList.toggle('z-50');
        }

        function sendQuickAudible(type) {
            if (type === 'RPE 9.5 Audible') {
                appendChatMessage('user', 'My top set felt like RPE 9.5. Strip my remaining back-off sets by 10%.');
                setTimeout(() => {
                    executeLumbarGuardrail();
                    appendChatMessage('assistant', '**Lumbar Erector Guardrail Executed:** Because your set hit RPE 9.5, I automatically stripped all remaining back-off sets by 10% and capped target RPE at 7.5 to preserve your recovery.');
                }, 600);
            } else if (type === 'Load Day 2') {
                loadDayTemplate('day2_lower_squat');
                appendChatMessage('user', 'Load Day 2 Lower Power with the 70 lb Safety Squat Bar.');
                setTimeout(() => {
                    appendChatMessage('assistant', 'Loaded **Day 2: Lower Power (70 lb SSB Squat Focus)** with your 270 lb × 5 Top Set, 235 lb × 3×5 Back-Offs, and 130 lb Hatfield SSB Split Squats.');
                }, 600);
            } else if (type === 'Load Day 5') {
                loadDayTemplate('day5_upper_pump');
                appendChatMessage('user', 'Switch my active workout to Day 5 Zero-Axial Upper Body Pump.');
                setTimeout(() => {
                    appendChatMessage('assistant', 'Switched to **Day 5: Zero-Axial Upper Body Pump** (55 lb Seated 75° DB Press, Incline DB Press, and CS Rows).');
                }, 600);
            }
        }

        function handleChatSubmit(e) {
            e.preventDefault();
            const input = document.getElementById('chatInputBox');
            const txt = input.value.trim();
            if (!txt) return;
            appendChatMessage('user', txt);
            input.value = '';

            setTimeout(() => {
                const lower = txt.toLowerCase();
                if (lower.includes('squat') || lower.includes('day 2')) {
                    loadDayTemplate('day2_lower_squat');
                    appendChatMessage('assistant', 'Loaded Day 2 Lower Power with 70 lb SSB squats and Hatfield split squats.');
                } else if (lower.includes('bench') || lower.includes('push')) {
                    loadDayTemplate('day1_upper_push');
                    appendChatMessage('assistant', 'Loaded Day 1 Upper Push with your 255 lb Bench top set and 115 lb OHP.');
                } else {
                    appendChatMessage('assistant', `**Coach Verified:** Staying locked on crisp bar speed (RPE 7.5–8 ceiling on primary lifts) and 360° belt bracing. Your current progression on ${currentWorkout.title} is dialed in.`);
                }
            }, 800);
        }

        function appendChatMessage(role, text) {
            const box = document.getElementById('chatMessages');
            const div = document.createElement('div');
            div.className = `flex flex-col ${role === 'user' ? 'items-end' : 'items-start'}`;
            div.innerHTML = `<div class="max-w-[90%] rounded-2xl px-4 py-3 text-xs sm:text-sm ${role === 'user' ? 'bg-amber-500 text-zinc-950 font-semibold' : 'bg-zinc-950 border border-zinc-800 text-zinc-200'} leading-relaxed">${text}</div>`;
            box.appendChild(div);
            box.scrollTop = box.scrollHeight;
        }
    </script>
</body>
</html>
