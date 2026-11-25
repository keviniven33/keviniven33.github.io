<html lang="en" class="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nexus University | Student Portal</title>
    <!-- Google Fonts: Plus Jakarta Sans & Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Plus+Jakarta+Sans:wght@600;700;800&display=swap" rel="stylesheet">
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Tailwind Configuration -->
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        display: ['Plus Jakarta Sans', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#eef2ff',
                            100: '#e0e7ff',
                            200: '#c7d2fe',
                            300: '#a5b4fc',
                            400: '#818cf8',
                            500: '#6366f1',
                            600: '#4f46e5',
                            700: '#4338ca',
                            800: '#3730a3',
                            900: '#312e81',
                        }
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-slate-50 text-slate-800 dark:bg-slate-950 dark:text-slate-100 transition-colors duration-300 antialiased selection:bg-brand-500 selection:text-white overflow-x-hidden">

    <!-- Toast Notification Container (Replaces alert) -->
    <div id="toast-container" class="fixed bottom-5 right-5 z-50 flex flex-col gap-2 pointer-events-none"></div>

    <!-- Mobile Navigation Overlay -->
    <div id="mobile-overlay" class="fixed inset-0 bg-slate-900/50 backdrop-blur-sm z-30 hidden lg:hidden transition-opacity"></div>

    <!-- Main Layout Wrapper -->
    <div class="flex min-h-screen">
        
        <!-- Sidebar Navigation -->
        <aside id="sidebar" class="fixed inset-y-0 left-0 z-40 w-64 transform -translate-x-full lg:translate-x-0 lg:static lg:inset-0 bg-white/90 dark:bg-slate-900/90 backdrop-blur-xl border-r border-slate-200/80 dark:border-slate-800/80 flex flex-col justify-between transition-transform duration-300 ease-in-out shadow-xl lg:shadow-none">
            <div>
                <!-- Brand Logo -->
                <div class="h-16 flex items-center justify-between px-6 border-b border-slate-200/80 dark:border-slate-800/80">
                    <div class="flex items-center gap-3">
                        <div class="w-9 h-9 rounded-xl bg-gradient-to-tr from-brand-600 to-indigo-400 flex items-center justify-center text-white font-display font-bold text-lg shadow-md shadow-brand-500/20">
                            N
                        </div>
                        <div>
                            <span class="font-display font-bold text-lg tracking-tight text-slate-900 dark:text-white">Nexus<span class="text-brand-600 dark:text-brand-400">Portal</span></span>
                        </div>
                    </div>
                    <button id="close-sidebar-btn" class="lg:hidden p-2 rounded-lg text-slate-500 hover:bg-slate-100 dark:hover:bg-slate-800">
                        <i class="fa-solid fa-xmark text-lg"></i>
                    </button>
                </div>

                <!-- Navigation Links -->
                <nav class="p-4 space-y-1.5" aria-label="Main Navigation">
                    <button data-target="dashboard" class="nav-btn w-full flex items-center gap-3.5 px-4 py-3 rounded-xl text-sm font-medium transition-all duration-200 bg-brand-50 text-brand-700 dark:bg-brand-500/15 dark:text-brand-300 shadow-sm">
                        <i class="fa-solid fa-grid-2 w-5 text-center"></i>
                        <span>Dashboard</span>
                    </button>
                    <button data-target="schedule" class="nav-btn w-full flex items-center gap-3.5 px-4 py-3 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-800/60 hover:text-slate-900 dark:hover:text-slate-200 transition-all duration-200">
                        <i class="fa-regular fa-calendar-days w-5 text-center"></i>
                        <span>Class Schedule</span>
                    </button>
                    <button data-target="grades" class="nav-btn w-full flex items-center gap-3.5 px-4 py-3 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-800/60 hover:text-slate-900 dark:hover:text-slate-200 transition-all duration-200">
                        <i class="fa-solid fa-graduation-cap w-5 text-center"></i>
                        <span>Grades & GPA</span>
                    </button>
                    <button data-target="announcements" class="nav-btn w-full flex items-center justify-between px-4 py-3 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-800/60 hover:text-slate-900 dark:hover:text-slate-200 transition-all duration-200">
                        <div class="flex items-center gap-3.5">
                            <i class="fa-regular fa-bell w-5 text-center"></i>
                            <span>Announcements</span>
                        </div>
                        <span class="px-2 py-0.5 text-xs font-semibold rounded-full bg-rose-100 text-rose-600 dark:bg-rose-500/20 dark:text-rose-300">2</span>
                    </button>
                    <button data-target="profile" class="nav-btn w-full flex items-center gap-3.5 px-4 py-3 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-800/60 hover:text-slate-900 dark:hover:text-slate-200 transition-all duration-200">
                        <i class="fa-regular fa-user w-5 text-center"></i>
                        <span>Student Profile</span>
                    </button>
                </nav>
            </div>

            <!-- Sidebar Footer / Mini Profile & Theme -->
            <div class="p-4 border-t border-slate-200/80 dark:border-slate-800/80 space-y-3">
                <div class="p-3 rounded-2xl bg-slate-100/80 dark:bg-slate-800/60 flex items-center gap-3">
                    <div id="sidebar-avatar" class="w-10 h-10 rounded-xl bg-brand-600 text-white flex items-center justify-center font-display font-bold text-sm shrink-0 shadow-sm">
                        AR
                    </div>
                    <div class="min-w-0 flex-1">
                        <p id="sidebar-name" class="text-sm font-semibold text-slate-900 dark:text-white truncate">Alex Rivera</p>
                        <p id="sidebar-major" class="text-xs text-slate-500 dark:text-slate-400 truncate">B.S. Computer Science</p>
                    </div>
                </div>
                <button id="reset-demo-btn" class="w-full py-2 px-3 rounded-xl text-xs font-medium text-slate-500 hover:text-slate-800 dark:text-slate-400 dark:hover:text-slate-200 hover:bg-slate-100 dark:hover:bg-slate-800 transition-colors flex items-center justify-center gap-2">
                    <i class="fa-solid fa-rotate-left"></i> Reset Demo Data
                </button>
            </div>
        </aside>

        <!-- Main Content Area -->
        <div class="flex-1 flex flex-col min-w-0">
            
            <!-- Top Header Bar -->
            <header class="sticky top-0 z-20 h-16 bg-white/80 dark:bg-slate-900/80 backdrop-blur-md border-b border-slate-200/80 dark:border-slate-800/80 px-4 sm:px-8 flex items-center justify-between">
                <div class="flex items-center gap-3">
                    <button id="open-sidebar-btn" class="lg:hidden p-2.5 rounded-xl text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-800 transition-colors" aria-label="Open menu">
                        <i class="fa-solid fa-bars text-lg"></i>
                    </button>
                    <h1 id="page-title" class="font-display font-bold text-lg sm:text-xl text-slate-900 dark:text-white">Dashboard</h1>
                </div>

                <div class="flex items-center gap-2 sm:gap-4">
                    <!-- Term Badge -->
                    <span class="hidden sm:inline-flex items-center gap-1.5 px-3 py-1.5 rounded-xl text-xs font-semibold bg-emerald-50 text-emerald-700 dark:bg-emerald-500/15 dark:text-emerald-300 border border-emerald-200/60 dark:border-emerald-500/20">
                        <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                        Fall Semester 2026
                    </span>

                    <!-- Dark/Light Theme Toggle -->
                    <button id="theme-toggle" class="p-2.5 rounded-xl bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-amber-400 hover:bg-slate-200 dark:hover:bg-slate-700 transition-all duration-200" aria-label="Toggle Theme">
                        <i id="theme-icon" class="fa-solid fa-moon text-base"></i>
                    </button>
                </div>
            </header>

            <!-- Dynamic Views Container -->
            <main class="flex-1 p-4 sm:p-6 lg:p-8 max-w-7xl w-full mx-auto space-y-6">

                <!-- ========================================== -->
                <!-- SECTION 1: DASHBOARD                       -->
                <!-- ========================================== -->
                <section id="view-dashboard" class="view-section space-y-6">
                    
                    <!-- Welcome Banner -->
                    <div class="relative overflow-hidden rounded-3xl bg-gradient-to-r from-brand-600 via-indigo-600 to-violet-600 p-6 sm:p-8 text-white shadow-lg shadow-brand-500/20">
                        <div class="relative z-10 flex flex-col md:flex-row md:items-center justify-between gap-4">
                            <div>
                                <p id="current-date-display" class="text-indigo-100 text-xs sm:text-sm font-medium uppercase tracking-wider mb-1">Wednesday, November 25, 2026</p>
                                <h2 class="font-display font-bold text-2xl sm:text-3xl tracking-tight">Welcome back, <span id="dash-welcome-name">Alex</span>! 👋</h2>
                                <p class="text-indigo-100/90 text-sm sm:text-base mt-1.5 max-w-xl">You have <span class="font-semibold text-white">3 classes</span> scheduled today and <span id="dash-pending-count" class="font-semibold text-white">3 pending tasks</span> due this week.</p>
                            </div>
                            <div class="flex flex-wrap gap-2.5">
                                <button onclick="switchView('schedule')" class="px-4 py-2.5 rounded-xl bg-white text-brand-700 font-semibold text-sm shadow-sm hover:bg-indigo-50 transition-colors">
                                    View Timetable
                                </button>
                                <button onclick="switchView('grades')" class="px-4 py-2.5 rounded-xl bg-white/15 hover:bg-white/25 backdrop-blur-sm text-white font-semibold text-sm border border-white/20 transition-colors">
                                    Check Grades
                                </button>
                            </div>
                        </div>
                        <!-- Decorative shapes -->
                        <div class="absolute -right-10 -top-10 w-48 h-48 rounded-full bg-white/10 blur-2xl pointer-events-none"></div>
                        <div class="absolute right-24 -bottom-16 w-40 h-40 rounded-full bg-indigo-400/20 blur-xl pointer-events-none"></div>
                    </div>

                    <!-- Quick Stats Grid -->
                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-5">
                        <div class="p-5 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800/80 shadow-sm hover:shadow-md transition-shadow">
                            <div class="flex items-center justify-between mb-3">
                                <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-slate-400">Current GPA</span>
                                <div class="w-9 h-9 rounded-xl bg-brand-50 dark:bg-brand-500/15 text-brand-600 dark:text-brand-400 flex items-center justify-center">
                                    <i class="fa-solid fa-chart-line"></i>
                                </div>
                            </div>
                            <div class="flex items-baseline gap-2">
                                <span class="font-display font-bold text-2xl sm:text-3xl text-slate-900 dark:text-white">3.86</span>
                                <span class="text-xs font-semibold text-emerald-600 dark:text-emerald-400 bg-emerald-50 dark:bg-emerald-500/15 px-2 py-0.5 rounded-full">+0.08</span>
                            </div>
                            <p class="text-xs text-slate-500 dark:text-slate-400 mt-1">Dean's Honors List</p>
                        </div>

                        <div class="p-5 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800/80 shadow-sm hover:shadow-md transition-shadow">
                            <div class="flex items-center justify-between mb-3">
                                <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-slate-400">Completed Credits</span>
                                <div class="w-9 h-9 rounded-xl bg-emerald-50 dark:bg-emerald-500/15 text-emerald-600 dark:text-emerald-400 flex items-center justify-center">
                                    <i class="fa-solid fa-award"></i>
                                </div>
                            </div>
                            <div class="flex items-baseline gap-2">
                                <span class="font-display font-bold text-2xl sm:text-3xl text-slate-900 dark:text-white">84</span>
                                <span class="text-xs font-medium text-slate-500 dark:text-slate-400">/ 120 req</span>
                            </div>
                            <div class="w-full bg-slate-100 dark:bg-slate-800 h-1.5 rounded-full mt-2 overflow-hidden">
                                <div class="bg-emerald-500 h-full rounded-full" style="width: 70%"></div>
                            </div>
                        </div>

                        <div class="p-5 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800/80 shadow-sm hover:shadow-md transition-shadow">
                            <div class="flex items-center justify-between mb-3">
                                <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-slate-400">Attendance Rate</span>
                                <div class="w-9 h-9 rounded-xl bg-sky-50 dark:bg-sky-500/15 text-sky-600 dark:text-sky-400 flex items-center justify-center">
                                    <i class="fa-solid fa-user-check"></i>
                                </div>
                            </div>
                            <div class="flex items-baseline gap-2">
                                <span class="font-display font-bold text-2xl sm:text-3xl text-slate-900 dark:text-white">96.4%</span>
                                <span class="text-xs font-semibold text-sky-600 dark:text-sky-400">Excellent</span>
                            </div>
                            <p class="text-xs text-slate-500 dark:text-slate-400 mt-1">54 of 56 sessions attended</p>
                        </div>

                        <div class="p-5 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800/80 shadow-sm hover:shadow-md transition-shadow">
                            <div class="flex items-center justify-between mb-3">
                                <span class="text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-slate-400">Pending Tasks</span>
                                <div class="w-9 h-9 rounded-xl bg-amber-50 dark:bg-amber-500/15 text-amber-600 dark:text-amber-400 flex items-center justify-center">
                                    <i class="fa-solid fa-list-check"></i>
                                </div>
                            </div>
                            <div class="flex items-baseline gap-2">
                                <span id="stat-pending-tasks" class="font-display font-bold text-2xl sm:text-3xl text-slate-900 dark:text-white">3</span>
                                <span class="text-xs font-medium text-amber-600 dark:text-amber-400">Due soon</span>
                            </div>
                            <p class="text-xs text-slate-500 dark:text-slate-400 mt-1">Check list below to update</p>
                        </div>
                    </div>

                    <!-- Main Dashboard Grid: Today's Classes + Deadlines + Announcements -->
                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                        
                        <!-- Today's Classes Timeline -->
                        <div class="lg:col-span-1 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800/80 p-5 sm:p-6 shadow-sm flex flex-col">
                            <div class="flex items-center justify-between mb-5">
                                <h3 class="font-display font-bold text-base sm:text-lg text-slate-900 dark:text-white">Today's Classes</h3>
                                <span class="text-xs font-semibold px-2.5 py-1 rounded-lg bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300">Wednesday</span>
                            </div>
                            <div id="dashboard-timeline" class="space-y-4 flex-1">
                                <!-- Populated via JS -->
                            </div>
                        </div>

                        <!-- Interactive Deadlines Checklist -->
                        <div class="lg:col-span-1 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800/80 p-5 sm:p-6 shadow-sm flex flex-col">
                            <div class="flex items-center justify-between mb-4">
                                <h3 class="font-display font-bold text-base sm:text-lg text-slate-900 dark:text-white">Upcoming Deadlines</h3>
                                <span class="text-xs text-slate-500 dark:text-slate-400">Auto-saved</span>
                            </div>
                            
                            <!-- Quick Add Deadline Form -->
                            <form id="add-task-form" class="flex gap-2 mb-4">
                                <input type="text" id="new-task-input" placeholder="Add a reminder..." class="flex-1 px-3 py-2 text-sm rounded-xl bg-slate-50 dark:bg-slate-800/80 border border-slate-200 dark:border-slate-700 focus:outline-none focus:ring-2 focus:ring-brand-500 text-slate-800 dark:text-slate-100">
                                <button type="submit" class="px-3.5 py-2 rounded-xl bg-brand-600 hover:bg-brand-700 text-white text-sm font-medium transition-colors" aria-label="Add task">
                                    <i class="fa-solid fa-plus"></i>
                                </button>
                            </form>

                            <div id="deadlines-list" class="space-y-2.5 flex-1 overflow-y-auto max-h-80 pr-1">
                                <!-- Populated via JS -->
                            </div>
                        </div>

                        <!-- Recent Announcements Preview -->
                        <div class="lg:col-span-1 rounded-2xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-800/80 p-5 sm:p-6 shadow-sm flex flex-col">
                            <div class="flex items-center justify-between mb-5">
                                <h3 class="font-display font-bold text-base sm:text-lg text-slate-900 dark:text-white">Campus Updates</h3>
                                <button onclick="switchView('announcements')" class="text-xs font-semibold text-brand-600 dark:text-brand-400 hover:underline">View All</button>
                            </div>
                            <div id="dashboard-announcements" class="space-y-3.5 flex-1">
                                <!-- Populated via JS -->
                            </div>
                        </div>

                    </div>
                </section>

                <!-- ========================================== -->
                <!-- SECTION 2: CLASS SCHEDULE                  -->
                <!-- ========================================== -->
                <section id="view-schedule" class="view-section hidden space-y-6">
                    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 bg-white dark:bg-slate-900 p-5 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 shadow-sm">
                        <div>
                            <h2 class="font-display font-bold text-xl text-slate-900 dark:text-white">Weekly Class Timetable</h2>
                            <p class="text-sm text-slate-500 dark:text-slate-400">Fall 2026 Enrolled Courses (16 Credit Hours)</p>
                        </div>

                        <!-- Day Filter Pills -->
                        <div class="flex flex-wrap items-center gap-1.5 bg-slate-100 dark:bg-slate-800 p-1.5 rounded-xl">
                            <button data-day="ALL" class="day-filter-btn px-3 py-1.5 rounded-lg text-xs font-semibold bg-white dark:bg-slate-700 text-slate-900 dark:text-white shadow-sm transition-all">Full Week</button>
                            <button data-day="Monday" class="day-filter-btn px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition-all">Mon</button>
                            <button data-day="Tuesday" class="day-filter-btn px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition-all">Tue</button>
                            <button data-day="Wednesday" class="day-filter-btn px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition-all">Wed</button>
                            <button data-day="Thursday" class="day-filter-btn px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition-all">Thu</button>
                            <button data-day="Friday" class="day-filter-btn px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition-all">Fri</button>
                        </div>
                    </div>

                    <!-- Color-Coded Category Legend -->
                    <div class="flex flex-wrap items-center gap-4 px-2 text-xs font-medium text-slate-600 dark:text-slate-400">
                        <span class="flex items-center gap-2"><span class="w-3 h-3 rounded-full bg-indigo-500"></span> Core Computer Science</span>
                        <span class="flex items-center gap-2"><span class="w-3 h-3 rounded-full bg-emerald-500"></span> Mathematics & Logic</span>
                        <span class="flex items-center gap-2"><span class="w-3 h-3 rounded-full bg-amber-500"></span> Laboratory / Practical</span>
                        <span class="flex items-center gap-2"><span class="w-3 h-3 rounded-full bg-rose-500"></span> General Elective</span>
                    </div>

                    <!-- Schedule Grid Container -->
                    <div id="schedule-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-4">
                        <!-- Populated dynamically via JS -->
                    </div>
                </section>

                <!-- ========================================== -->
                <!-- SECTION 3: GRADES & GPA                    -->
                <!-- ========================================== -->
                <section id="view-grades" class="view-section hidden space-y-6">
                    
                    <!-- Top Controls & Summary Cards -->
                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                        <div class="lg:col-span-2 bg-white dark:bg-slate-900 p-6 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 shadow-sm flex flex-col justify-between">
                            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-6">
                                <div>
                                    <h2 class="font-display font-bold text-xl text-slate-900 dark:text-white">Academic Performance</h2>
                                    <p class="text-sm text-slate-500 dark:text-slate-400">Click any course row to inspect assignment & exam scores</p>
                                </div>
                                <select id="semester-selector" class="px-4 py-2.5 rounded-xl bg-slate-100 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm font-semibold text-slate-800 dark:text-white focus:outline-none focus:ring-2 focus:ring-brand-500">
                                    <option value="fall2026">Fall Semester 2026 (Current)</option>
                                    <option value="spring2026">Spring Semester 2026</option>
                                    <option value="fall2025">Fall Semester 2025</option>
                                </select>
                            </div>

                            <div class="grid grid-cols-3 gap-4">
                                <div class="p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/60 border border-slate-200/60 dark:border-slate-700/60">
                                    <p class="text-xs font-semibold text-slate-500 dark:text-slate-400">Term GPA</p>
                                    <p id="term-gpa-val" class="font-display font-bold text-2xl sm:text-3xl text-brand-600 dark:text-brand-400 mt-1">3.90</p>
                                </div>
                                <div class="p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/60 border border-slate-200/60 dark:border-slate-700/60">
                                    <p class="text-xs font-semibold text-slate-500 dark:text-slate-400">Cumulative GPA</p>
                                    <p class="font-display font-bold text-2xl sm:text-3xl text-slate-900 dark:text-white mt-1">3.86</p>
                                </div>
                                <div class="p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/60 border border-slate-200/60 dark:border-slate-700/60">
                                    <p class="text-xs font-semibold text-slate-500 dark:text-slate-400">Term Credits</p>
                                    <p id="term-credits-val" class="font-display font-bold text-2xl sm:text-3xl text-emerald-600 dark:text-emerald-400 mt-1">16.0</p>
                                </div>
                            </div>
                        </div>

                        <!-- GPA & Course Grade Visual Chart -->
                        <div class="bg-white dark:bg-slate-900 p-6 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 shadow-sm flex flex-col justify-between">
                            <div>
                                <h3 class="font-display font-bold text-base text-slate-900 dark:text-white">Score Distribution</h3>
                                <p class="text-xs text-slate-500 dark:text-slate-400 mb-4">Percentage performance by course</p>
                            </div>
                            <div id="grades-bar-chart" class="space-y-3 my-auto">
                                <!-- Visual CSS Bar Chart populated via JS -->
                            </div>
                        </div>
                    </div>

                    <!-- Interactive Course Grades Table -->
                    <div class="bg-white dark:bg-slate-900 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 shadow-sm overflow-hidden">
                        <div class="overflow-x-auto">
                            <table class="w-full text-left border-collapse">
                                <thead>
                                    <tr class="border-b border-slate-200 dark:border-slate-800 bg-slate-50/80 dark:bg-slate-800/40 text-xs font-semibold uppercase tracking-wider text-slate-500 dark:text-slate-400">
                                        <th class="py-4 px-6">Course</th>
                                        <th class="py-4 px-4">Instructor</th>
                                        <th class="py-4 px-4 text-center">Credits</th>
                                        <th class="py-4 px-4 text-center">Percentage</th>
                                        <th class="py-4 px-4 text-center">Letter</th>
                                        <th class="py-4 px-6 text-right">Breakdown</th>
                                    </tr>
                                </thead>
                                <tbody id="grades-table-body" class="divide-y divide-slate-200/80 dark:divide-slate-800/80 text-sm">
                                    <!-- Populated via JS -->
                                </tbody>
                            </table>
                        </div>
                    </div>
                </section>

                <!-- ========================================== -->
                <!-- SECTION 4: ANNOUNCEMENTS                   -->
                <!-- ========================================== -->
                <section id="view-announcements" class="view-section hidden space-y-6">
                    
                    <!-- Search and Category Filter Header -->
                    <div class="bg-white dark:bg-slate-900 p-5 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 shadow-sm flex flex-col md:flex-row md:items-center justify-between gap-4">
                        <div class="flex flex-wrap gap-2">
                            <button data-cat="All" class="ann-filter-btn px-4 py-2 rounded-xl text-xs font-semibold bg-brand-600 text-white shadow-sm transition-all">All</button>
                            <button data-cat="Academic" class="ann-filter-btn px-4 py-2 rounded-xl text-xs font-semibold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 transition-all">Academic</button>
                            <button data-cat="Events" class="ann-filter-btn px-4 py-2 rounded-xl text-xs font-semibold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 transition-all">Events</button>
                            <button data-cat="Campus" class="ann-filter-btn px-4 py-2 rounded-xl text-xs font-semibold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 transition-all">Campus</button>
                        </div>

                        <div class="relative w-full md:w-72">
                            <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                            <input type="text" id="announcement-search" placeholder="Search announcements..." class="w-full pl-10 pr-4 py-2 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm focus:outline-none focus:ring-2 focus:ring-brand-500 text-slate-800 dark:text-white">
                        </div>
                    </div>

                    <!-- Announcements Feed Grid -->
                    <div id="announcements-feed" class="grid grid-cols-1 md:grid-cols-2 gap-5">
                        <!-- Populated via JS -->
                    </div>
                </section>

                <!-- ========================================== -->
                <!-- SECTION 5: STUDENT PROFILE                 -->
                <!-- ========================================== -->
                <section id="view-profile" class="view-section hidden space-y-6">
                    <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                        
                        <!-- Profile Summary Card & Unofficial Transcript Trigger -->
                        <div class="lg:col-span-1 space-y-6">
                            <div class="bg-white dark:bg-slate-900 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 p-6 shadow-sm text-center">
                                <div id="profile-avatar-large" class="w-24 h-24 mx-auto rounded-2xl bg-gradient-to-tr from-brand-600 to-indigo-400 text-white font-display font-bold text-3xl flex items-center justify-center shadow-lg shadow-brand-500/25 mb-4">
                                    AR
                                </div>
                                <h2 id="profile-card-name" class="font-display font-bold text-xl text-slate-900 dark:text-white">Alex Rivera</h2>
                                <p id="profile-card-id" class="text-xs font-mono font-semibold text-brand-600 dark:text-brand-400 mt-1">ID: NX-2026-8492</p>
                                <p id="profile-card-major" class="text-sm text-slate-600 dark:text-slate-300 mt-2">B.S. Computer Science • Junior</p>
                                
                                <div class="mt-5 pt-5 border-t border-slate-200/80 dark:border-slate-800/80 flex justify-around text-center">
                                    <div>
                                        <p class="text-xs text-slate-500 dark:text-slate-400">Standing</p>
                                        <p class="text-sm font-bold text-emerald-600 dark:text-emerald-400 mt-0.5">Good Standing</p>
                                    </div>
                                    <div class="w-px bg-slate-200 dark:bg-slate-800"></div>
                                    <div>
                                        <p class="text-xs text-slate-500 dark:text-slate-400">Honors</p>
                                        <p class="text-sm font-bold text-slate-900 dark:text-white mt-0.5">Dean's List</p>
                                    </div>
                                </div>

                                <button id="open-transcript-btn" class="mt-6 w-full py-2.5 px-4 rounded-xl bg-slate-900 dark:bg-slate-800 hover:bg-slate-800 dark:hover:bg-slate-700 text-white text-sm font-semibold transition-colors flex items-center justify-center gap-2 shadow-sm">
                                    <i class="fa-solid fa-file-lines"></i> Unofficial Transcript
                                </button>
                            </div>
                        </div>

                        <!-- Editable Student Information Form -->
                        <div class="lg:col-span-2 bg-white dark:bg-slate-900 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 p-6 sm:p-8 shadow-sm">
                            <div class="flex items-center justify-between mb-6">
                                <div>
                                    <h3 class="font-display font-bold text-xl text-slate-900 dark:text-white">Personal & Academic Details</h3>
                                    <p class="text-sm text-slate-500 dark:text-slate-400">Update your directory information (saved locally in your browser)</p>
                                </div>
                            </div>

                            <form id="profile-form" class="space-y-5" novalidate>
                                <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
                                    <div>
                                        <label for="prof-name" class="block text-xs font-semibold uppercase tracking-wider text-slate-600 dark:text-slate-400 mb-1.5">Full Name *</label>
                                        <input type="text" id="prof-name" required class="w-full px-4 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm text-slate-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-brand-500">
                                    </div>
                                    <div>
                                        <label for="prof-id" class="block text-xs font-semibold uppercase tracking-wider text-slate-600 dark:text-slate-400 mb-1.5">Student ID *</label>
                                        <input type="text" id="prof-id" required class="w-full px-4 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm font-mono text-slate-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-brand-500">
                                    </div>
                                    <div>
                                        <label for="prof-major" class="block text-xs font-semibold uppercase tracking-wider text-slate-600 dark:text-slate-400 mb-1.5">Degree Major *</label>
                                        <input type="text" id="prof-major" required class="w-full px-4 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm text-slate-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-brand-500">
                                    </div>
                                    <div>
                                        <label for="prof-year" class="block text-xs font-semibold uppercase tracking-wider text-slate-600 dark:text-slate-400 mb-1.5">Class Standing</label>
                                        <select id="prof-year" class="w-full px-4 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm text-slate-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-brand-500">
                                            <option value="Freshman">Freshman (Year 1)</option>
                                            <option value="Sophomore">Sophomore (Year 2)</option>
                                            <option value="Junior">Junior (Year 3)</option>
                                            <option value="Senior">Senior (Year 4)</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label for="prof-email" class="block text-xs font-semibold uppercase tracking-wider text-slate-600 dark:text-slate-400 mb-1.5">University Email *</label>
                                        <input type="email" id="prof-email" required class="w-full px-4 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm text-slate-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-brand-500">
                                    </div>
                                    <div>
                                        <label for="prof-advisor" class="block text-xs font-semibold uppercase tracking-wider text-slate-600 dark:text-slate-400 mb-1.5">Faculty Advisor</label>
                                        <input type="text" id="prof-advisor" class="w-full px-4 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm text-slate-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-brand-500">
                                    </div>
                                </div>

                                <div>
                                    <label for="prof-bio" class="block text-xs font-semibold uppercase tracking-wider text-slate-600 dark:text-slate-400 mb-1.5">Academic Bio & Research Interests</label>
                                    <textarea id="prof-bio" rows="3" class="w-full px-4 py-2.5 rounded-xl bg-slate-50 dark:bg-slate-800 border border-slate-200 dark:border-slate-700 text-sm text-slate-900 dark:text-white focus:outline-none focus:ring-2 focus:ring-brand-500"></textarea>
                                </div>

                                <div class="flex items-center justify-end gap-3 pt-2">
                                    <button type="submit" class="px-6 py-2.5 rounded-xl bg-brand-600 hover:bg-brand-700 text-white font-semibold text-sm shadow-md shadow-brand-500/20 transition-all flex items-center gap-2">
                                        <i class="fa-solid fa-floppy-disk"></i> Save Changes
                                    </button>
                                </div>
                            </form>
                        </div>

                    </div>
                </section>

            </main>
        </div>
    </div>

    <!-- ========================================== -->
    <!-- MODAL: ANNOUNCEMENT ARTICLE READER         -->
    <!-- ========================================== -->
    <div id="article-modal" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-slate-900/60 backdrop-blur-sm">
        <div class="bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 rounded-3xl max-w-xl w-full p-6 sm:p-8 shadow-2xl transform transition-all">
            <div class="flex items-center justify-between gap-4 mb-4">
                <span id="modal-ann-badge" class="px-3 py-1 rounded-full text-xs font-semibold bg-brand-50 text-brand-700 dark:bg-brand-500/20 dark:text-brand-300">Academic</span>
                <button onclick="closeModal('article-modal')" class="p-2 rounded-xl text-slate-400 hover:text-slate-700 dark:hover:text-white hover:bg-slate-100 dark:hover:bg-slate-800">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>
            <h3 id="modal-ann-title" class="font-display font-bold text-xl sm:text-2xl text-slate-900 dark:text-white mb-2">Announcement Title</h3>
            <p id="modal-ann-meta" class="text-xs text-slate-500 dark:text-slate-400 mb-5">Posted Nov 24, 2026 • Office of the Registrar</p>
            <div id="modal-ann-body" class="text-sm sm:text-base text-slate-600 dark:text-slate-300 leading-relaxed space-y-3">
                <!-- Full content -->
            </div>
            <div class="mt-6 pt-4 border-t border-slate-200 dark:border-slate-800 flex justify-end">
                <button onclick="closeModal('article-modal')" class="px-5 py-2 rounded-xl bg-slate-100 dark:bg-slate-800 hover:bg-slate-200 dark:hover:bg-slate-700 text-sm font-semibold text-slate-800 dark:text-white transition-colors">Close</button>
            </div>
        </div>
    </div>

    <!-- ========================================== -->
    <!-- MODAL: UNOFFICIAL TRANSCRIPT SUMMARY       -->
    <!-- ========================================== -->
    <div id="transcript-modal" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-slate-900/60 backdrop-blur-sm">
        <div class="bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 rounded-3xl max-w-2xl w-full p-6 sm:p-8 shadow-2xl max-h-[90vh] overflow-y-auto">
            <div class="flex items-center justify-between border-b border-slate-200 dark:border-slate-800 pb-4 mb-5">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-brand-600 text-white font-display font-bold flex items-center justify-center">N</div>
                    <div>
                        <h3 class="font-display font-bold text-lg text-slate-900 dark:text-white">Nexus University</h3>
                        <p class="text-xs text-slate-500 dark:text-slate-400">Unofficial Academic Record Summary</p>
                    </div>
                </div>
                <button onclick="closeModal('transcript-modal')" class="p-2 rounded-xl text-slate-400 hover:text-slate-700 dark:hover:text-white hover:bg-slate-100 dark:hover:bg-slate-800">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <div id="transcript-content" class="space-y-5 text-sm">
                <!-- Populated dynamically from profile & grades state -->
            </div>

            <div class="mt-6 pt-4 border-t border-slate-200 dark:border-slate-800 flex flex-wrap justify-end gap-3">
                <button onclick="window.print()" class="px-4 py-2 rounded-xl bg-brand-600 hover:bg-brand-700 text-white text-sm font-semibold flex items-center gap-2 transition-colors">
                    <i class="fa-solid fa-print"></i> Print / Save PDF
                </button>
                <button onclick="closeModal('transcript-modal')" class="px-4 py-2 rounded-xl bg-slate-100 dark:bg-slate-800 text-slate-800 dark:text-white text-sm font-semibold hover:bg-slate-200 dark:hover:bg-slate-700 transition-colors">
                    Close
                </button>
            </div>
        </div>
    </div>

    <!-- Application Logic -->
    <script>
        // ==========================================
        // 1. DEFAULT DATA & LOCALSTORAGE STATE
        // ==========================================
        const DEFAULT_DATA = {
            profile: {
                name: "Alex Rivera",
                id: "NX-2026-8492",
                major: "B.S. Computer Science",
                year: "Junior",
                email: "alex.rivera@nexus.edu",
                advisor: "Dr. Elena Vance",
                bio: "Focused on distributed systems, human-computer interaction, and applied machine learning. Undergraduate teaching assistant for Intro to Algorithms."
            },
            deadlines: [
                { id: 1, title: "CS-304 Distributed Systems Lab 4", course: "CS-304", due: "Tomorrow, 11:59 PM", completed: false },
                { id: 2, title: "MATH-240 Linear Algebra Problem Set 8", course: "MATH-240", due: "Fri, Nov 27", completed: false },
                { id: 3, title: "CS-320 UI/UX Interactive Prototype", course: "CS-320", due: "Mon, Nov 30", completed: false },
                { id: 4, title: "PHIL-210 Ethics Midterm Reflection", course: "PHIL-210", due: "Completed", completed: true }
            ],
            schedule: [
                { day: "Monday", code: "CS-304", title: "Distributed Systems", time: "09:00 - 10:30", room: "Turing Hall 204", instructor: "Dr. M. Chen", category: "core" },
                { day: "Monday", code: "MATH-240", title: "Linear Algebra II", time: "13:00 - 14:30", room: "Euler Bldg 108", instructor: "Prof. S. Patel", category: "math" },
                { day: "Tuesday", code: "CS-320", title: "Human-Computer Interaction", time: "10:00 - 11:30", room: "Design Studio B", instructor: "Dr. E. Vance", category: "core" },
                { day: "Tuesday", code: "PHIL-210", title: "Ethics in Technology", time: "14:00 - 15:30", room: "Humanities 301", instructor: "Dr. R. Sterling", category: "elective" },
                { day: "Wednesday", code: "CS-304", title: "Distributed Systems", time: "09:00 - 10:30", room: "Turing Hall 204", instructor: "Dr. M. Chen", category: "core" },
                { day: "Wednesday", code: "CS-304L", title: "Systems Architecture Lab", time: "11:00 - 12:30", room: "CompLab 4B", instructor: "TA J. Kim", category: "lab" },
                { day: "Wednesday", code: "MATH-240", title: "Linear Algebra II", time: "13:00 - 14:30", room: "Euler Bldg 108", instructor: "Prof. S. Patel", category: "math" },
                { day: "Thursday", code: "CS-320", title: "Human-Computer Interaction", time: "10:00 - 11:30", room: "Design Studio B", instructor: "Dr. E. Vance", category: "core" },
                { day: "Thursday", code: "PHIL-210", title: "Ethics in Technology", time: "14:00 - 15:30", room: "Humanities 301", instructor: "Dr. R. Sterling", category: "elective" },
                { day: "Friday", code: "CS-320L", title: "Usability Testing Workshop", time: "10:00 - 12:00", room: "Design Studio B", instructor: "Dr. E. Vance", category: "lab" }
            ],
            grades: {
                fall2026: {
                    termGpa: "3.90",
                    credits: "16.0",
                    courses: [
                        {
                            code: "CS-304", name: "Distributed Systems", instructor: "Dr. M. Chen", credits: 4, score: 94, letter: "A",
                            breakdown: [
                                { item: "Midterm Exam", weight: "30%", score: "92 / 100" },
                                { item: "Raft Consensus Lab", weight: "25%", score: "98 / 100" },
                                { item: "Problem Sets (1-3)", weight: "25%", score: "93 / 100" },
                                { item: "Participation & Quizzes", weight: "20%", score: "94 / 100" }
                            ]
                        },
                        {
                            code: "CS-320", name: "Human-Computer Interaction", instructor: "Dr. E. Vance", credits: 4, score: 96, letter: "A",
                            breakdown: [
                                { item: "User Research Report", weight: "30%", score: "97 / 100" },
                                { item: "Wireframe Critique", weight: "20%", score: "95 / 100" },
                                { item: "Interactive Prototype", weight: "35%", score: "96 / 100" },
                                { item: "Studio Attendance", weight: "15%", score: "96 / 100" }
                            ]
                        },
                        {
                            code: "MATH-240", name: "Linear Algebra II", instructor: "Prof. S. Patel", credits: 4, score: 89, letter: "B+",
                            breakdown: [
                                { item: "Midterm I", weight: "25%", score: "86 / 100" },
                                { item: "Midterm II", weight: "25%", score: "91 / 100" },
                                { item: "Weekly Proofs", weight: "30%", score: "90 / 100" },
                                { item: "MATLAB Exercises", weight: "20%", score: "89 / 100" }
                            ]
                        },
                        {
                            code: "PHIL-210", name: "Ethics in Technology", instructor: "Dr. R. Sterling", credits: 4, score: 93, letter: "A",
                            breakdown: [
                                { item: "AI Policy Essay", weight: "40%", score: "94 / 100" },
                                { item: "Case Study Debate", weight: "30%", score: "92 / 100" },
                                { item: "Seminar Reflections", weight: "30%", score: "93 / 100" }
                            ]
                        }
                    ]
                },
                spring2026: {
                    termGpa: "3.82",
                    credits: "16.0",
                    courses: [
                        {
                            code: "CS-250", name: "Data Structures & Algorithms", instructor: "Dr. A. Turing", credits: 4, score: 91, letter: "A-",
                            breakdown: [
                                { item: "Graph Algorithms Exam", weight: "40%", score: "90 / 100" },
                                { item: "Dynamic Programming Lab", weight: "35%", score: "93 / 100" },
                                { item: "Weekly Quests", weight: "25%", score: "90 / 100" }
                            ]
                        },
                        {
                            code: "CS-210", name: "Computer Organization", instructor: "Prof. K. Liu", credits: 4, score: 95, letter: "A",
                            breakdown: [
                                { item: "RISC-V Simulator", weight: "45%", score: "96 / 100" },
                                { item: "Memory Hierarchy Exam", weight: "35%", score: "94 / 100" },
                                { item: "Assembly Labs", weight: "20%", score: "95 / 100" }
                            ]
                        },
                        {
                            code: "STAT-200", name: "Probability & Statistics", instructor: "Dr. H. Ramos", credits: 4, score: 88, letter: "B+",
                            breakdown: [
                                { item: "Midterm Exam", weight: "40%", score: "85 / 100" },
                                { item: "R Data Analysis Project", weight: "35%", score: "92 / 100" },
                                { item: "Homework Sets", weight: "25%", score: "87 / 100" }
                            ]
                        },
                        {
                            code: "ENG-105", name: "Technical Communication", instructor: "Prof. L. Vance", credits: 4, score: 94, letter: "A",
                            breakdown: [
                                { item: "Whitepaper Draft", weight: "50%", score: "94 / 100" },
                                { item: "Lightning Talk", weight: "50%", score: "94 / 100" }
                            ]
                        }
                    ]
                },
                fall2025: {
                    termGpa: "3.85",
                    credits: "15.0",
                    courses: [
                        {
                            code: "CS-102", name: "Object-Oriented Programming", instructor: "Dr. M. Chen", credits: 4, score: 95, letter: "A",
                            breakdown: [
                                { item: "Final Software Project", weight: "50%", score: "96 / 100" },
                                { item: "Midterm Practical", weight: "30%", score: "94 / 100" },
                                { item: "Code Reviews", weight: "20%", score: "95 / 100" }
                            ]
                        },
                        {
                            code: "MATH-150", name: "Multivariable Calculus", instructor: "Prof. S. Patel", credits: 4, score: 90, letter: "A-",
                            breakdown: [
                                { item: "Exam 1 & 2", weight: "60%", score: "89 / 100" },
                                { item: "Vector Calculus Labs", weight: "40%", score: "92 / 100" }
                            ]
                        },
                        {
                            code: "PHYS-180", name: "Electromagnetism", instructor: "Dr. N. Tesla", credits: 4, score: 89, letter: "B+",
                            breakdown: [
                                { item: "Lab Experiments", weight: "30%", score: "94 / 100" },
                                { item: "Written Exams", weight: "70%", score: "87 / 100" }
                            ]
                        },
                        {
                            code: "HIST-112", name: "History of Science", instructor: "Dr. C. Sagan", credits: 3, score: 96, letter: "A",
                            breakdown: [
                                { item: "Research Paper", weight: "60%", score: "96 / 100" },
                                { item: "Book Review", weight: "40%", score: "96 / 100" }
                            ]
                        }
                    ]
                }
            },
            announcements: [
                {
                    id: 101,
                    title: "Spring 2027 Course Registration Window Opens Monday",
                    category: "Academic",
                    pinned: true,
                    urgent: true,
                    date: "Nov 25, 2026 • 09:00 AM",
                    author: "Office of the University Registrar",
                    summary: "Priority registration for Juniors and Seniors begins November 30 at 8:00 AM. Ensure advisor holds are cleared.",
                    content: "Priority registration for the Spring 2027 semester opens next Monday, November 30, 2026 at 8:00 AM EST. Students with 60 or more earned credit hours are eligible for Phase 1 enrollment.\n\nPlease log in to verify that you have met with your faculty advisor and have no outstanding financial or administrative holds. Course catalogs and updated lab schedules are available in the academic directory."
                },
                {
                    id: 102,
                    title: "Extended 24/7 Study Hours at Main Science Library",
                    category: "Campus",
                    pinned: true,
                    urgent: false,
                    date: "Nov 24, 2026 • 02:15 PM",
                    author: "Campus Library Services",
                    summary: "Starting December 1, all floors of the Turing Science Library will remain open 24/7 through finals week.",
                    content: "To support students preparing for final examinations and capstone presentations, the Turing Science Library will transition to 24/7 operations starting December 1 through December 18.\n\nValid student ID cards are required for building entry after 10:00 PM. Quiet zones on the 3rd and 4th floors will be strictly enforced, and complimentary coffee/tea stations will be available nightly at midnight."
                },
                {
                    id: 103,
                    title: "Annual Winter Hackathon & Tech Career Expo",
                    category: "Events",
                    pinned: false,
                    urgent: false,
                    date: "Nov 22, 2026 • 11:30 AM",
                    author: "ACM Student Chapter",
                    summary: "Join 300+ student builders for a 36-hour innovation sprint with mentors from top engineering teams.",
                    content: "Registration is officially open for NexusHacks Winter 2026! Form teams of up to 4 students and build hardware or software prototypes across tracks in AI, Sustainability, and FinTech.\n\nOver $10,000 in prizes and direct internship interviews will be awarded. Meals, workshops, and hardware kits are provided free of charge to all registered participants."
                },
                {
                    id: 104,
                    title: "Undergraduate Research Fellowship Applications Due",
                    category: "Academic",
                    pinned: false,
                    urgent: false,
                    date: "Nov 20, 2026 • 04:00 PM",
                    author: "Dean of Undergraduate Studies",
                    summary: "Apply for paid Spring/Summer faculty-mentored research stipends across all STEM and Humanities departments.",
                    content: "The Undergraduate Research Office is accepting proposals for the 2027 Honors Research Fellowship. Selected students receive a $3,500 stipend and dedicated lab space to pursue independent inquiry alongside a faculty mentor.\n\nSubmit a 2-page project abstract and a letter of endorsement from your faculty advisor by December 10."
                }
            ]
        };

        // Load or Initialize State
        let appState = {
            profile: JSON.parse(localStorage.getItem('nexus_profile')) || { ...DEFAULT_DATA.profile },
            deadlines: JSON.parse(localStorage.getItem('nexus_deadlines')) || [ ...DEFAULT_DATA.deadlines ],
            theme: localStorage.getItem('nexus_theme') || 'light',
            activeView: 'dashboard',
            scheduleFilter: 'ALL',
            announcementFilter: 'All',
            announcementSearch: ''
        };

        function saveState() {
            localStorage.setItem('nexus_profile', JSON.stringify(appState.profile));
            localStorage.setItem('nexus_deadlines', JSON.stringify(appState.deadlines));
            localStorage.setItem('nexus_theme', appState.theme);
        }

        // ==========================================
        // 2. TOAST NOTIFICATION HELPER (No alert())
        // ==========================================
        function showToast(message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            const bgClass = type === 'success' 
                ? 'bg-slate-900 dark:bg-white text-white dark:text-slate-900' 
                : 'bg-rose-600 text-white';
            const icon = type === 'success' ? 'fa-circle-check text-emerald-400 dark:text-emerald-600' : 'fa-circle-exclamation';
            
            toast.className = `pointer-events-auto flex items-center gap-3 px-4 py-3 rounded-2xl shadow-xl text-sm font-medium transform transition-all duration-300 translate-y-4 opacity-0 ${bgClass}`;
            toast.innerHTML = `<i class="fa-solid ${icon}"></i><span>${message}</span>`;
            
            container.appendChild(toast);
            requestAnimationFrame(() => {
                toast.classList.remove('translate-y-4', 'opacity-0');
            });

            setTimeout(() => {
                toast.classList.add('translate-y-4', 'opacity-0');
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // ==========================================
        // 3. THEME & NAVIGATION MANAGEMENT
        // ==========================================
        function applyTheme() {
            const html = document.documentElement;
            const icon = document.getElementById('theme-icon');
            if (appState.theme === 'dark') {
                html.classList.add('dark');
                icon.className = 'fa-solid fa-sun text-base';
            } else {
                html.classList.remove('dark');
                icon.className = 'fa-solid fa-moon text-base';
            }
        }

        document.getElementById('theme-toggle').addEventListener('click', () => {
            appState.theme = appState.theme === 'light' ? 'dark' : 'light';
            saveState();
            applyTheme();
        });

        function switchView(viewName) {
            appState.activeView = viewName;
            
            // Update Sections
            document.querySelectorAll('.view-section').forEach(sec => sec.classList.add('hidden'));
            const activeSec = document.getElementById(`view-${viewName}`);
            if (activeSec) activeSec.classList.remove('hidden');

            // Update Nav Buttons
            const titles = {
                dashboard: 'Dashboard',
                schedule: 'Class Schedule',
                grades: 'Grades & GPA',
                announcements: 'Announcements',
                profile: 'Student Profile'
            };
            document.getElementById('page-title').textContent = titles[viewName] || 'Dashboard';

            document.querySelectorAll('.nav-btn').forEach(btn => {
                if (btn.dataset.target === viewName) {
                    btn.className = 'nav-btn w-full flex items-center justify-between px-4 py-3 rounded-xl text-sm font-semibold transition-all duration-200 bg-brand-50 text-brand-700 dark:bg-brand-500/15 dark:text-brand-300 shadow-sm';
                } else {
                    btn.className = 'nav-btn w-full flex items-center justify-between px-4 py-3 rounded-xl text-sm font-medium text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-800/60 hover:text-slate-900 dark:hover:text-slate-200 transition-all duration-200';
                }
            });

            // Close mobile sidebar if open
            closeMobileSidebar();
        }

        document.querySelectorAll('.nav-btn').forEach(btn => {
            btn.addEventListener('click', () => switchView(btn.dataset.target));
        });

        // Mobile Sidebar Handlers
        const sidebar = document.getElementById('sidebar');
        const overlay = document.getElementById('mobile-overlay');
        function openMobileSidebar() {
            sidebar.classList.remove('-translate-x-full');
            overlay.classList.remove('hidden');
        }
        function closeMobileSidebar() {
            sidebar.classList.add('-translate-x-full');
            overlay.classList.add('hidden');
        }
        document.getElementById('open-sidebar-btn').addEventListener('click', openMobileSidebar);
        document.getElementById('close-sidebar-btn').addEventListener('click', closeMobileSidebar);
        overlay.addEventListener('click', closeMobileSidebar);

        // ==========================================
        // 4. DASHBOARD RENDERING & INTERACTIVITY
        // ==========================================
        function renderDashboard() {
            // Set formatted current date
            const now = new Date();
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            document.getElementById('current-date-display').textContent = now.toLocaleDateString('en-US', options);

            // Welcome Name
            const firstName = appState.profile.name.split(' ')[0] || 'Student';
            document.getElementById('dash-welcome-name').textContent = firstName;

            // Today's Classes (Wednesday default showcase)
            const todaysClasses = DEFAULT_DATA.schedule.filter(c => c.day === 'Wednesday');
            const timelineEl = document.getElementById('dashboard-timeline');
            timelineEl.innerHTML = todaysClasses.map((cls, idx) => `
                <div class="relative pl-6 pb-4 ${idx !== todaysClasses.length - 1 ? 'border-l-2 border-slate-200 dark:border-slate-800' : ''}">
                    <span class="absolute -left-[7px] top-1 w-3 h-3 rounded-full bg-brand-600 ring-4 ring-white dark:ring-slate-900"></span>
                    <div class="p-3.5 rounded-xl bg-slate-50 dark:bg-slate-800/60 border border-slate-200/60 dark:border-slate-700/60">
                        <div class="flex items-center justify-between text-xs font-semibold text-brand-600 dark:text-brand-400 mb-1">
                            <span>${cls.code}</span>
                            <span>${cls.time}</span>
                        </div>
                        <p class="font-semibold text-sm text-slate-900 dark:text-white">${cls.title}</p>
                        <p class="text-xs text-slate-500 dark:text-slate-400 mt-1"><i class="fa-solid fa-location-dot mr-1"></i>${cls.room}</p>
                    </div>
                </div>
            `).join('');

            // Render Deadlines Checklist
            renderDeadlines();

            // Render Campus Updates Preview (Top 2 pinned/recent)
            const annPreviewEl = document.getElementById('dashboard-announcements');
            annPreviewEl.innerHTML = DEFAULT_DATA.announcements.slice(0, 2).map(ann => `
                <div onclick="openArticleModal(${ann.id})" class="cursor-pointer p-4 rounded-xl bg-slate-50 dark:bg-slate-800/60 hover:bg-slate-100 dark:hover:bg-slate-800 border border-slate-200/60 dark:border-slate-700/60 transition-colors">
                    <div class="flex items-center gap-2 mb-1.5">
                        <span class="px-2 py-0.5 text-[11px] font-semibold rounded-md bg-brand-100 text-brand-700 dark:bg-brand-500/20 dark:text-brand-300">${ann.category}</span>
                        ${ann.urgent ? '<span class="px-2 py-0.5 text-[11px] font-semibold rounded-md bg-rose-100 text-rose-700 dark:bg-rose-500/20 dark:text-rose-300">Urgent</span>' : ''}
                    </div>
                    <h4 class="font-semibold text-sm text-slate-900 dark:text-white line-clamp-1">${ann.title}</h4>
                    <p class="text-xs text-slate-500 dark:text-slate-400 mt-1 line-clamp-2">${ann.summary}</p>
                </div>
            `).join('');
        }

        function renderDeadlines() {
            const listEl = document.getElementById('deadlines-list');
            const pendingCount = appState.deadlines.filter(t => !t.completed).length;
            
            document.getElementById('stat-pending-tasks').textContent = pendingCount;
            document.getElementById('dash-pending-count').textContent = `${pendingCount} pending ${pendingCount === 1 ? 'task' : 'tasks'}`;

            if (appState.deadlines.length === 0) {
                listEl.innerHTML = `<p class="text-xs text-slate-400 text-center py-6">No tasks yet. Add one above!</p>`;
                return;
            }

            listEl.innerHTML = appState.deadlines.map(task => `
                <div class="flex items-center justify-between gap-3 p-3 rounded-xl bg-slate-50 dark:bg-slate-800/50 border border-slate-200/60 dark:border-slate-700/60 group">
                    <label class="flex items-start gap-3 cursor-pointer flex-1 min-w-0">
                        <input type="checkbox" ${task.completed ? 'checked' : ''} onchange="toggleDeadline(${task.id})" class="mt-0.5 w-4 h-4 rounded border-slate-300 text-brand-600 focus:ring-brand-500 cursor-pointer">
                        <div class="min-w-0 flex-1">
                            <p class="text-sm font-medium truncate transition-all ${task.completed ? 'line-through text-slate-400 dark:text-slate-500' : 'text-slate-800 dark:text-slate-200'}">${task.title}</p>
                            <p class="text-[11px] text-slate-500 dark:text-slate-400">${task.course} • ${task.due}</p>
                        </div>
                    </label>
                    <button onclick="deleteDeadline(${task.id})" class="opacity-0 group-hover:opacity-100 p-1.5 text-slate-400 hover:text-rose-500 transition-opacity" aria-label="Delete task">
                        <i class="fa-solid fa-trash-can text-xs"></i>
                    </button>
                </div>
            `).join('');
        }

        window.toggleDeadline = function(id) {
            const task = appState.deadlines.find(t => t.id === id);
            if (task) {
                task.completed = !task.completed;
                saveState();
                renderDeadlines();
            }
        };

        window.deleteDeadline = function(id) {
            appState.deadlines = appState.deadlines.filter(t => t.id !== id);
            saveState();
            renderDeadlines();
            showToast('Task removed');
        };

        document.getElementById('add-task-form').addEventListener('submit', (e) => {
            e.preventDefault();
            const input = document.getElementById('new-task-input');
            const val = input.value.trim();
            if (!val) return;

            appState.deadlines.unshift({
                id: Date.now(),
                title: val,
                course: "Personal",
                due: "Upcoming",
                completed: false
            });
            input.value = '';
            saveState();
            renderDeadlines();
            showToast('Deadline added to checklist');
        });

        // ==========================================
        // 5. CLASS SCHEDULE RENDERING
        // ==========================================
        function renderSchedule() {
            const days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'];
            const filteredDays = appState.scheduleFilter === 'ALL' ? days : [appState.scheduleFilter];
            const grid = document.getElementById('schedule-grid');

            // Adjust grid columns based on filter
            grid.className = appState.scheduleFilter === 'ALL' 
                ? 'grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-4' 
                : 'grid grid-cols-1 max-w-2xl mx-auto gap-4';

            const catColors = {
                core: 'border-l-4 border-l-indigo-500 bg-indigo-50/40 dark:bg-indigo-500/10',
                math: 'border-l-4 border-l-emerald-500 bg-emerald-50/40 dark:bg-emerald-500/10',
                lab: 'border-l-4 border-l-amber-500 bg-amber-50/40 dark:bg-amber-500/10',
                elective: 'border-l-4 border-l-rose-500 bg-rose-50/40 dark:bg-rose-500/10'
            };

            grid.innerHTML = filteredDays.map(day => {
                const classes = DEFAULT_DATA.schedule.filter(c => c.day === day);
                return `
                    <div class="bg-white dark:bg-slate-900 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 p-4 shadow-sm flex flex-col">
                        <div class="flex items-center justify-between pb-3 mb-3 border-b border-slate-100 dark:border-slate-800">
                            <h3 class="font-display font-bold text-base text-slate-900 dark:text-white">${day}</h3>
                            <span class="text-xs font-semibold px-2 py-0.5 rounded-md bg-slate-100 dark:bg-slate-800 text-slate-500 dark:text-slate-400">${classes.length} ${classes.length === 1 ? 'class' : 'classes'}</span>
                        </div>
                        <div class="space-y-3 flex-1">
                            ${classes.map(cls => `
                                <div class="p-3.5 rounded-xl border border-slate-200/60 dark:border-slate-700/60 ${catColors[cls.category] || ''}">
                                    <div class="flex items-center justify-between text-xs font-bold text-slate-700 dark:text-slate-200 mb-1">
                                        <span>${cls.code}</span>
                                        <span class="font-mono text-[11px] text-slate-500 dark:text-slate-400">${cls.time}</span>
                                    </div>
                                    <p class="font-semibold text-sm text-slate-900 dark:text-white leading-snug">${cls.title}</p>
                                    <div class="mt-2.5 pt-2 border-t border-slate-200/50 dark:border-slate-700/50 text-xs text-slate-500 dark:text-slate-400 space-y-1">
                                        <p><i class="fa-solid fa-location-dot w-4 text-center"></i> ${cls.room}</p>
                                        <p><i class="fa-solid fa-chalkboard-user w-4 text-center"></i> ${cls.instructor}</p>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                `;
            }).join('');
        }

        document.querySelectorAll('.day-filter-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                appState.scheduleFilter = btn.dataset.day;
                document.querySelectorAll('.day-filter-btn').forEach(b => {
                    b.className = b.dataset.day === appState.scheduleFilter
                        ? 'day-filter-btn px-3 py-1.5 rounded-lg text-xs font-semibold bg-white dark:bg-slate-700 text-slate-900 dark:text-white shadow-sm transition-all'
                        : 'day-filter-btn px-3 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 hover:text-slate-900 dark:hover:text-white transition-all';
                });
                renderSchedule();
            });
        });

        // ==========================================
        // 6. GRADES & GPA RENDERING
        // ==========================================
        function renderGrades(semesterKey = 'fall2026') {
            const semData = DEFAULT_DATA.grades[semesterKey];
            if (!semData) return;

            document.getElementById('term-gpa-val').textContent = semData.termGpa;
            document.getElementById('term-credits-val').textContent = semData.credits;

            // Render Bar Chart
            const chartEl = document.getElementById('grades-bar-chart');
            chartEl.innerHTML = semData.courses.map(c => `
                <div>
                    <div class="flex justify-between text-xs font-semibold mb-1">
                        <span class="text-slate-700 dark:text-slate-300">${c.code}</span>
                        <span class="text-brand-600 dark:text-brand-400">${c.score}% (${c.letter})</span>
                    </div>
                    <div class="w-full h-2.5 bg-slate-100 dark:bg-slate-800 rounded-full overflow-hidden">
                        <div class="h-full bg-gradient-to-r from-brand-600 to-indigo-400 rounded-full transition-all duration-500" style="width: ${c.score}%"></div>
                    </div>
                </div>
            `).join('');

            // Render Interactive Table
            const tbody = document.getElementById('grades-table-body');
            tbody.innerHTML = semData.courses.map((c, idx) => `
                <tr onclick="toggleGradeRow('breakdown-${idx}')" class="cursor-pointer hover:bg-slate-50 dark:hover:bg-slate-800/50 transition-colors">
                    <td class="py-4 px-6">
                        <p class="font-bold text-slate-900 dark:text-white">${c.code}</p>
                        <p class="text-xs text-slate-500 dark:text-slate-400">${c.name}</p>
                    </td>
                    <td class="py-4 px-4 text-slate-600 dark:text-slate-300">${c.instructor}</td>
                    <td class="py-4 px-4 text-center font-medium">${c.credits}.0</td>
                    <td class="py-4 px-4 text-center font-semibold text-slate-900 dark:text-white">${c.score}%</td>
                    <td class="py-4 px-4 text-center">
                        <span class="px-2.5 py-1 rounded-lg text-xs font-bold ${c.letter.startsWith('A') ? 'bg-emerald-50 text-emerald-700 dark:bg-emerald-500/20 dark:text-emerald-300' : 'bg-sky-50 text-sky-700 dark:bg-sky-500/20 dark:text-sky-300'}">${c.letter}</span>
                    </td>
                    <td class="py-4 px-6 text-right text-brand-600 dark:text-brand-400 font-semibold text-xs">
                        Details <i class="fa-solid fa-chevron-down ml-1"></i>
                    </td>
                </tr>
                <tr id="breakdown-${idx}" class="hidden bg-slate-50/70 dark:bg-slate-800/30">
                    <td colspan="6" class="px-6 py-4">
                        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-3">
                            ${c.breakdown.map(b => `
                                <div class="p-3 rounded-xl bg-white dark:bg-slate-900 border border-slate-200/80 dark:border-slate-700/80">
                                    <p class="text-xs font-semibold text-slate-800 dark:text-slate-200">${b.item}</p>
                                    <div class="flex items-center justify-between mt-1.5 text-xs">
                                        <span class="text-slate-400">Weight: ${b.weight}</span>
                                        <span class="font-bold text-brand-600 dark:text-brand-400">${b.score}</span>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                    </td>
                </tr>
            `).join('');
        }

        window.toggleGradeRow = function(rowId) {
            const row = document.getElementById(rowId);
            if (row) row.classList.toggle('hidden');
        };

        document.getElementById('semester-selector').addEventListener('change', (e) => {
            renderGrades(e.target.value);
        });

        // ==========================================
        // 7. ANNOUNCEMENTS RENDERING & MODAL
        // ==========================================
        function renderAnnouncements() {
            const feed = document.getElementById('announcements-feed');
            const query = appState.announcementSearch.toLowerCase();
            
            const filtered = DEFAULT_DATA.announcements.filter(ann => {
                const matchesCat = appState.announcementFilter === 'All' || ann.category === appState.announcementFilter;
                const matchesQuery = ann.title.toLowerCase().includes(query) || ann.summary.toLowerCase().includes(query);
                return matchesCat && matchesQuery;
            });

            if (filtered.length === 0) {
                feed.innerHTML = `<div class="col-span-full text-center py-12 text-slate-400">No announcements match your filter criteria.</div>`;
                return;
            }

            feed.innerHTML = filtered.map(ann => `
                <article class="bg-white dark:bg-slate-900 rounded-2xl border border-slate-200/80 dark:border-slate-800/80 p-6 shadow-sm hover:shadow-md transition-all flex flex-col justify-between">
                    <div>
                        <div class="flex flex-wrap items-center justify-between gap-2 mb-3">
                            <div class="flex items-center gap-2">
                                <span class="px-2.5 py-1 rounded-lg text-xs font-semibold bg-brand-50 text-brand-700 dark:bg-brand-500/20 dark:text-brand-300">${ann.category}</span>
                                ${ann.pinned ? '<span class="px-2 py-0.5 rounded-md text-xs font-semibold bg-amber-50 text-amber-700 dark:bg-amber-500/20 dark:text-amber-300"><i class="fa-solid fa-thumbtack mr-1"></i>Pinned</span>' : ''}
                                ${ann.urgent ? '<span class="px-2 py-0.5 rounded-md text-xs font-semibold bg-rose-50 text-rose-700 dark:bg-rose-500/20 dark:text-rose-300">Urgent</span>' : ''}
                            </div>
                            <span class="text-xs text-slate-400">${ann.date.split('•')[0]}</span>
                        </div>
                        <h3 class="font-display font-bold text-lg text-slate-900 dark:text-white mb-2">${ann.title}</h3>
                        <p class="text-sm text-slate-600 dark:text-slate-300 leading-relaxed mb-4">${ann.summary}</p>
                    </div>
                    <div class="pt-4 border-t border-slate-100 dark:border-slate-800 flex items-center justify-between">
                        <span class="text-xs font-medium text-slate-500 dark:text-slate-400">${ann.author}</span>
                        <button onclick="openArticleModal(${ann.id})" class="text-xs font-semibold text-brand-600 dark:text-brand-400 hover:underline flex items-center gap-1">
                            Read Full Notice <i class="fa-solid fa-arrow-right"></i>
                        </button>
                    </div>
                </article>
            `).join('');
        }

        document.querySelectorAll('.ann-filter-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                appState.announcementFilter = btn.dataset.cat;
                document.querySelectorAll('.ann-filter-btn').forEach(b => {
                    b.className = b.dataset.cat === appState.announcementFilter
                        ? 'ann-filter-btn px-4 py-2 rounded-xl text-xs font-semibold bg-brand-600 text-white shadow-sm transition-all'
                        : 'ann-filter-btn px-4 py-2 rounded-xl text-xs font-semibold bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-300 hover:bg-slate-200 dark:hover:bg-slate-700 transition-all';
                });
                renderAnnouncements();
            });
        });

        document.getElementById('announcement-search').addEventListener('input', (e) => {
            appState.announcementSearch = e.target.value;
            renderAnnouncements();
        });

        window.openArticleModal = function(id) {
            const ann = DEFAULT_DATA.announcements.find(a => a.id === id);
            if (!ann) return;
            document.getElementById('modal-ann-badge').textContent = ann.category;
            document.getElementById('modal-ann-title').textContent = ann.title;
            document.getElementById('modal-ann-meta').textContent = `${ann.date} • ${ann.author}`;
            document.getElementById('modal-ann-body').innerHTML = ann.content.split('\n\n').map(p => `<p>${p}</p>`).join('');
            
            const modal = document.getElementById('article-modal');
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        };

        window.closeModal = function(modalId) {
            const modal = document.getElementById(modalId);
            modal.classList.add('hidden');
            modal.classList.remove('flex');
        };

        // ==========================================
        // 8. STUDENT PROFILE & TRANSCRIPT MODAL
        // ==========================================
        function syncProfileUI() {
            const p = appState.profile;
            const initials = p.name.split(' ').map(n => n[0]).join('').substring(0, 2).toUpperCase() || 'ST';

            // Sidebar & Cards
            document.getElementById('sidebar-avatar').textContent = initials;
            document.getElementById('sidebar-name').textContent = p.name;
            document.getElementById('sidebar-major').textContent = p.major;

            document.getElementById('profile-avatar-large').textContent = initials;
            document.getElementById('profile-card-name').textContent = p.name;
            document.getElementById('profile-card-id').textContent = `ID: ${p.id}`;
            document.getElementById('profile-card-major').textContent = `${p.major} • ${p.year}`;

            // Form inputs
            document.getElementById('prof-name').value = p.name;
            document.getElementById('prof-id').value = p.id;
            document.getElementById('prof-major').value = p.major;
            document.getElementById('prof-year').value = p.year;
            document.getElementById('prof-email').value = p.email;
            document.getElementById('prof-advisor').value = p.advisor;
            document.getElementById('prof-bio').value = p.bio;
        }

        document.getElementById('profile-form').addEventListener('submit', (e) => {
            e.preventDefault();
            const name = document.getElementById('prof-name').value.trim();
            const id = document.getElementById('prof-id').value.trim();
            const major = document.getElementById('prof-major').value.trim();
            const email = document.getElementById('prof-email').value.trim();

            if (!name || !id || !major || !email || !email.includes('@')) {
                showToast('Please fill in all required fields with a valid email.', 'error');
                return;
            }

            appState.profile = {
                name,
                id,
                major,
                year: document.getElementById('prof-year').value,
                email,
                advisor: document.getElementById('prof-advisor').value.trim(),
                bio: document.getElementById('prof-bio').value.trim()
            };

            saveState();
            syncProfileUI();
            renderDashboard();
            showToast('Profile updated and saved locally!');
        });

        // Unofficial Transcript Modal
        document.getElementById('open-transcript-btn').addEventListener('click', () => {
            const p = appState.profile;
            const content = document.getElementById('transcript-content');
            
            content.innerHTML = `
                <div class="grid grid-cols-2 gap-4 p-4 rounded-2xl bg-slate-50 dark:bg-slate-800/60 border border-slate-200/80 dark:border-slate-700/80">
                    <div>
                        <p class="text-xs text-slate-500">Student Name</p>
                        <p class="font-bold text-slate-900 dark:text-white">${p.name}</p>
                    </div>
                    <div>
                        <p class="text-xs text-slate-500">Student ID</p>
                        <p class="font-mono font-bold text-slate-900 dark:text-white">${p.id}</p>
                    </div>
                    <div>
                        <p class="text-xs text-slate-500">Program / Major</p>
                        <p class="font-semibold text-slate-900 dark:text-white">${p.major}</p>
                    </div>
                    <div>
                        <p class="text-xs text-slate-500">Cumulative GPA</p>
                        <p class="font-bold text-brand-600 dark:text-brand-400">3.86 / 4.00</p>
                    </div>
                </div>
                <div class="space-y-4">
                    ${Object.entries(DEFAULT_DATA.grades).map(([key, sem]) => `
                        <div>
                            <div class="flex justify-between items-center font-bold text-slate-800 dark:text-slate-200 border-b border-slate-200 dark:border-slate-700 pb-1 mb-2">
                                <span class="uppercase text-xs tracking-wider">${key.replace('20', ' 20')}</span>
                                <span class="text-xs">Term GPA: ${sem.termGpa}</span>
                            </div>
                            <div class="space-y-1 text-xs">
                                ${sem.courses.map(c => `
                                    <div class="flex justify-between py-1">
                                        <span><strong>${c.code}</strong> - ${c.name}</span>
                                        <span class="font-mono font-semibold">${c.credits}.0 cr | ${c.letter}</span>
                                    </div>
                                `).join('')}
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;

            const modal = document.getElementById('transcript-modal');
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        });

        // Reset Demo Data Button
        document.getElementById('reset-demo-btn').addEventListener('click', () => {
            localStorage.removeItem('nexus_profile');
            localStorage.removeItem('nexus_deadlines');
            appState.profile = { ...DEFAULT_DATA.profile };
            appState.deadlines = [ ...DEFAULT_DATA.deadlines ];
            saveState();
            syncProfileUI();
            renderDashboard();
            showToast('Demo data restored to defaults');
        });

        // ==========================================
        // 9. INITIALIZE APPLICATION
        // ==========================================
        window.addEventListener('DOMContentLoaded', () => {
            applyTheme();
            syncProfileUI();
            renderDashboard();
            renderSchedule();
            renderGrades('fall2026');
            renderAnnouncements();
        });
    </script>
</body>
</html>
