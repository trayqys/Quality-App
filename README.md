<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Quality Yacht Service</title>
    <!-- Tailwind CSS for modern mobile styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
</head>
<body class="bg-gray-900 text-gray-100 font-sans antialiased pb-28">

    <!-- TOP GLOBAL HEADER -->
    <header class="bg-gray-800 border-b border-gray-700 sticky top-0 z-50 px-4 py-3 flex justify-between items-center shadow-lg">
        <div>
            <h1 class="text-xl font-bold text-white tracking-wide">Quality Yacht Service</h1>
            <p class="text-xs text-blue-400 font-medium">Unified Operations Hub</p>
        </div>
        <div class="flex space-x-2">
            <button onclick="toggleModal('clientModal')" class="bg-gray-700 text-white p-2.5 rounded-xl transition active:scale-95 flex items-center justify-center" title="Add Client">
                <i data-lucide="user-plus" class="w-5 h-5"></i>
            </button>
            <button onclick="toggleModal('inventoryModal')" class="bg-gray-700 text-white p-2.5 rounded-xl transition active:scale-95 flex items-center justify-center" title="Manage Inventory">
                <i data-lucide="package" class="w-5 h-5"></i>
            </button>
            <button onclick="toggleModal('expenseModal')" class="bg-gray-700 text-amber-400 p-2.5 rounded-xl transition active:scale-95 flex items-center justify-center" title="Log Expense">
                <i data-lucide="trending-down" class="w-5 h-5"></i>
            </button>
        </div>
    </header>

    <!-- GROSS EARNINGS DASHBOARD -->
    <div class="p-4 space-y-3">
        <div class="bg-gradient-to-r from-blue-900/30 via-indigo-900/20 to-emerald-900/30 border border-gray-700/60 p-5 rounded-2xl shadow-xl flex justify-between items-center">
            <div>
                <p class="text-[10px] font-bold text-gray-400 uppercase tracking-wider">Gross Income</p>
                <h3 id="grossRevenueBox" class="text-2xl font-black text-white mt-1">$0.00</h3>
            </div>
            <div class="text-right space-y-1 text-xs">
                <p class="text-blue-400 font-medium" id="yachtSplit">Yacht: $0.00</p>
                <p class="text-emerald-400 font-medium" id="supSplit">SUP: $0.00</p>
            </div>
        </div>
    </div>

    <!-- SEGMENTED NAVIGATION SWITCHER -->
    <div class="p-4 pt-0">
        <div class="bg-gray-800 p-1 rounded-2xl flex border border-gray-700">
            <button id="yachtTabBtn" onclick="switchTab('yacht')" class="w-1/3 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 bg-blue-600 text-white shadow">
                <i data-lucide="anchor" class="w-4 h-4"></i> Yacht Ops
            </button>
            <button id="supTabBtn" onclick="switchTab('sup')" class="w-1/3 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 text-gray-400 hover:text-white">
                <i data-lucide="waves" class="w-4 h-4"></i> SUP Fleet
            </button>
            <button id="expenseTabBtn" onclick="switchTab('expense')" class="w-1/3 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 text-gray-400 hover:text-white">
                <i data-lucide="receipt" class="w-4 h-4"></i> Expenses
            </button>
            <button id="settingsTabBtn" onclick="switchTab('settings')" class="w-1/4 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 text-gray-400 hover:text-white">
    <i data-lucide="settings" class="w-4 h-4"></i> Settings
</button
        </div>
    </div>

    <!-- MAIN VIEWPORTS -->
    <main class="px-4">
        
        <!-- ================= YACHT MANAGEMENT VIEW ================= -->
        <section id="yachtView" class="space-y-5">
            <div class="flex justify-between items-center">
                <h2 class="text-base font-bold text-gray-200 flex items-center gap-2">
                    <i data-lucide="wrench" class="w-5 h-5 text-blue-500"></i> Cleaning Jobs
                </h2>
                <button onclick="toggleModal('jobModal')" class="bg-blue-600 text-xs font-semibold px-3 py-2 rounded-xl flex items-center gap-1 active:scale-95 transition">
                    <i data-lucide="plus" class="w-3.5 h-3.5"></i> Add Job
                </button>
            </div>
            <div class="space-y-5">
                <div>
                    <h3 class="text-xs font-bold text-amber-400 uppercase tracking-wider mb-2 flex items-center gap-1.5">
                        <span class="w-1.5 h-1.5 rounded-full bg-amber-400 animate-pulse"></span> Today's Active Tasks
                    </h3>
                    <div id="yachtTodayList" class="space-y-3"></div>
                </div>
                <div>
                    <h3 class="text-xs font-bold text-blue-400 uppercase tracking-wider mb-2 flex items-center gap-1.5">
                        <span class="w-1.5 h-1.5 rounded-full bg-blue-50"></span> Upcoming Service Log
                    </h3>
                    <div id="yachtUpcomingList" class="space-y-3"></div>
                </div>
                <div>
                    <h3 class="text-xs font-bold text-emerald-400 uppercase tracking-wider mb-2 flex items-center gap-1.5">
                        <span class="w-1.5 h-1.5 rounded-full bg-emerald-400"></span> Completed Assignments
                    </h3>
                    <div id="yachtCompletedList" class="space-y-3"></div>
                </div>
            </div>
        </section>

        <!-- ================= SUP RENTAL VIEW ================= -->
        <section id="supView" class="space-y-4 hidden">
            <div class="flex justify-between items-center">
                <h2 class="text-base font-bold text-gray-200 flex items-center gap-2">
                    <i data-lucide="calendar-range" class="w-5 h-5 text-emerald-500"></i> Rental Traffic Control
                </h2>
                <button onclick="toggleModal('rentalModal')" class="bg-emerald-600 text-xs font-semibold px-3 py-2 rounded-xl flex items-center gap-1 active:scale-95 transition">
                    <i data-lucide="plus" class="w-3.5 h-3.5"></i> Book Rental
                </button>
            </div>
            <div class="space-y-5">
                <div>
                    <h3 class="text-xs font-bold text-amber-400 uppercase tracking-wider mb-2 flex items-center gap-1.5">
                        <span class="w-1.5 h-1.5 rounded-full bg-amber-400 animate-pulse"></span> Upcoming Departures
                    </h3>
                    <div id="supUpcomingList" class="space-y-2"></div>
                </div>
                <div>
                    <h3 class="text-xs font-bold text-blue-400 uppercase tracking-wider mb-2 flex items-center gap-1.5">
                        <span class="w-1.5 h-1.5 rounded-full bg-blue-400"></span> Active Rentals Out (Chartered)
                    </h3>
                    <div id="supActiveList" class="space-y-2"></div>
                </div>
                <div>
                    <h3 class="text-xs font-bold text-emerald-400 uppercase tracking-wider mb-2 flex items-center gap-1.5">
                        <span class="w-1.5 h-1.5 rounded-full bg-emerald-400"></span> Returned / Closed Files
                    </h3>
                    <div id="supCompletedList" class="space-y-2"></div>
                </div>
            </div>
        </section>

        <!-- ================= EXPENSES VIEW ================= -->
        <section id="expenseView" class="space-y-4 hidden">
            <div class="flex justify-between items-center">
                <h2 class="text-base font-bold text-gray-200 flex items-center gap-2">
                    <i data-lucide="receipt" class="w-5 h-5 text-rose-500"></i> Corporate Expense Ledger
                </h2>
                <button onclick="toggleModal('expenseModal')" class="bg-rose-600 text-xs font-semibold px-3 py-2 rounded-xl flex items-center gap-1 active:scale-95 transition">
                    <i data-lucide="plus" class="w-3.5 h-3.5"></i> Log Outlay
                </button>
            </div>
            <div class="bg-gray-800 rounded-2xl border border-gray-700 overflow-hidden">
                <div class="p-4 border-b border-gray-700 bg-gray-800/50">
                    <h3 class="text-xs font-bold text-gray-400 uppercase tracking-wider">Transaction Records</h3>
                </div>
                <div id="expenseLedgerList" class="divide-y divide-gray-700 max-h-96 overflow-y-auto">
                    <!-- Expenses fall here dynamically -->
                </div>
            </div>
        </section>
    </main>

    <!-- ================= SETTINGS VIEW ================= -->
<div id="settingsView" class="hidden space-y-6 max-w-md mx-auto pt-4 px-2">
    <div class="bg-gray-800 border border-gray-700/70 rounded-2xl p-6 shadow-xl space-y-4">
        <div class="flex items-center gap-3 border-b border-gray-700 pb-3">
            <div class="p-2 bg-rose-500/10 text-rose-400 rounded-xl">
                <i data-lucide="shield-alert" class="w-6 h-6"></i>
            </div>
            <div>
                <h3 class="text-base font-bold text-white">System Security & Maintenance</h3>
                <p class="text-xs text-gray-400">Manage local device application parameters.</p>
            </div>
        </div>

        <div class="space-y-3 pt-2">
            <h4 class="text-xs font-black text-rose-400 tracking-wider uppercase">Danger Zone</h4>
            <p class="text-xs text-gray-300 leading-normal">
                Executing a data purge will permanently destroy all registered client indices, workflow logs, active deployment rentals, and structural ledgers stored in this mobile unit's local memory.
            </p>
            
            <button onclick="systemResetData()" class="w-full mt-2 py-3 bg-rose-600 hover:bg-rose-700 active:scale-[0.99] text-white font-bold text-sm rounded-xl transition shadow-lg flex items-center justify-center gap-2 border border-rose-500/30">
                <i data-lucide="trash-2" class="w-4 h-4"></i> Execute Master Factory Reset
            </button>
        </div>
    </div>
</div>

    <!-- ================= SYSTEM OPERATION MODALS ================= -->
    
    <!-- 1. ADD CLIENT MODAL -->
    <div id="clientModal" class="fixed inset-0 bg-black/70 z-50 flex items-end sm:items-center justify-center p-0 sm:p-4 hidden">
        <div class="bg-gray-800 w-full sm:max-w-md rounded-t-3xl sm:rounded-2xl p-6 border-t border-gray-700 max-h-[85vh] overflow-y-auto">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg font-bold">Add Client Profile</h3>
                <button onclick="toggleModal('clientModal')" class="text-gray-400"><i data-lucide="x"></i></button>
            </div>
            <form id="clientForm" onsubmit="saveClient(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Full Name</label>
                    <input type="text" id="clientName" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-blue-500">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-gray-400 mb-1">Phone Number</label>
                        <input type="tel" id="clientPhone" placeholder="(555) 000-0000" class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-sm text-white focus:outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-gray-400 mb-1">Email Address</label>
                        <input type="email" id="clientEmail" placeholder="captain@yacht.com" class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-sm text-white focus:outline-none focus:border-blue-500">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Vessel Name & Details</label>
                    <input type="text" id="clientYacht" class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-blue-500" placeholder="e.g., Lady Grace (42' Boston Whaler)">
                </div>
                <button type="submit" class="w-full bg-blue-600 py-3 rounded-xl font-bold text-white shadow-lg transition active:scale-95">Save Client Profile</button>
            </form>
        </div>
    </div>

    <!-- 2. SUP INVENTORY MANAGEMENT MODAL -->
    <div id="inventoryModal" class="fixed inset-0 bg-black/70 z-50 flex items-end sm:items-center justify-center p-0 sm:p-4 hidden">
        <div class="bg-gray-800 w-full sm:max-w-md rounded-t-3xl sm:rounded-2xl p-6 border-t border-gray-700 max-h-[85vh] overflow-y-auto">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg font-bold">SUP Fleet Management</h3>
                <button onclick="toggleModal('inventoryModal')" class="text-gray-400"><i data-lucide="x"></i></button>
            </div>
            <form id="inventoryForm" onsubmit="saveInventoryItem(event)" class="space-y-3 mb-6">
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Add Equipment Asset Name</label>
                    <div class="flex gap-2">
                        <input type="text" id="newBoardName" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-2.5 text-sm text-white focus:outline-none focus:border-emerald-500" placeholder="e.g., Red Paddle Co 10'6 #2">
                        <button type="submit" class="bg-emerald-600 font-bold text-xs px-4 rounded-xl text-white whitespace-nowrap">Add Asset</button>
                    </div>
                </div>
            </form>
            <div>
                <h4 class="text-xs font-bold text-gray-400 uppercase tracking-wider mb-2">Current Active Fleet List</h4>
                <div id="fleetInventoryContainer" class="space-y-2 max-h-48 overflow-y-auto pr-1"></div>
            </div>
        </div>
    </div>

    <!-- 3. NEW YACHT MAINTENANCE JOB MODAL -->
    <div id="jobModal" class="fixed inset-0 bg-black/70 z-50 flex items-end sm:items-center justify-center p-0 sm:p-4 hidden">
        <div class="bg-gray-800 w-full sm:max-w-md rounded-t-3xl sm:rounded-2xl p-6 border-t border-gray-700 max-h-[85vh] overflow-y-auto">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg font-bold">New Service Job</h3>
                <button onclick="toggleModal('jobModal')" class="text-gray-400"><i data-lucide="x"></i></button>
            </div>
            <form id="jobForm" onsubmit="saveJob(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Select Client Profile</label>
                    <select id="jobClientSelect" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-blue-500 text-sm"></select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Job Execution Date</label>
                    <input type="date" id="jobDate" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-blue-500 text-sm">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Scope of Maintenance</label>
                    <textarea id="jobDesc" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-blue-500 text-sm h-20" placeholder="e.g., Monthly hull scrub, zinc replacement, fluid diagnostics..."></textarea>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Fixed Service Flat Rate ($)</label>
                    <input type="number" id="jobCost" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-blue-500">
                </div>
                <button type="submit" class="w-full bg-blue-600 py-3 rounded-xl font-bold text-white shadow-lg transition active:scale-95">File Active Job</button>
            </form>
        </div>
    </div>

    <!-- 4. NEW MULTI-DAY SUP RENTAL MODAL -->
    <div id="rentalModal" class="fixed inset-0 bg-black/70 z-50 flex items-end sm:items-center justify-center p-0 sm:p-4 hidden">
        <div class="bg-gray-800 w-full sm:max-w-md rounded-t-3xl sm:rounded-2xl p-6 border-t border-gray-700 max-h-[85vh] overflow-y-auto">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg font-bold">Book SUP Rental</h3>
                <button onclick="toggleModal('rentalModal')" class="text-gray-400"><i data-lucide="x"></i></button>
            </div>
            <form id="rentalForm" onsubmit="saveRental(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Select Client</label>
                    <select id="rentalClientSelect" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-emerald-500 text-sm"></select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Select Fleet Assets</label>
                    <div id="rentalAssetCheckboxGroup" class="bg-gray-900 border border-gray-700 rounded-xl p-3 space-y-2 max-h-36 overflow-y-auto text-sm"></div>
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-gray-400 mb-1">Pickup Date</label>
                        <input type="date" id="rentalStartDate" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-emerald-500 text-sm">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-gray-400 mb-1">Expected Return</label>
                        <input type="date" id="rentalEndDate" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-emerald-500 text-sm">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Rental Cost per Board / Day ($)</label>
                    <input type="number" id="rentalCost" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-emerald-500" placeholder="e.g. 50">
                </div>
                <button type="submit" class="w-full bg-emerald-600 py-3 rounded-xl font-bold text-white shadow-lg transition active:scale-95">Book Operational Period</button>
            </form>
        </div>
    </div>

    <!-- 5. NEW EXPENSE OUTLAY MODAL -->
    <div id="expenseModal" class="fixed inset-0 bg-black/70 z-50 flex items-end sm:items-center justify-center p-0 sm:p-4 hidden">
        <div class="bg-gray-800 w-full sm:max-w-md rounded-t-3xl sm:rounded-2xl p-6 border-t border-gray-700 max-h-[85vh] overflow-y-auto">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg font-bold text-rose-400">Operating Expense</h3>
                <button onclick="toggleModal('expenseModal')" class="text-gray-400"><i data-lucide="x"></i></button>
            </div>
            <form id="expenseForm" onsubmit="saveExpense(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Expenses</label>
                    <select id="expenseCategory" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-rose-500 text-sm">
                        <option value="Yacht Supplies">Yacht Cleaning Supplies</option>
                        <option value="SUP Maintenance">SUP Equipment Repair & Parts</option>
                        <option value="Commission">Commission</option>
                        <option value="Miscellaneous">Miscellaneous Overhead</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Transaction Date</label>
                    <input type="date" id="expenseDate" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-rose-500 text-sm">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Description / Vendor Notes</label>
                    <input type="text" id="expenseDesc" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-rose-500 text-sm" placeholder="e.g., Nassau Marine Supply - 4x Zinc Anodes">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-gray-400 mb-1">Total Net Cost ($)</label>
                    <input type="number" step="0.01" id="expenseAmount" required class="w-full bg-gray-900 border border-gray-700 rounded-xl p-3 text-white focus:outline-none focus:border-rose-500">
                </div>
                <button type="submit" class="w-full bg-rose-600 py-3 rounded-xl font-bold text-white shadow-lg transition active:scale-95">Record Outlay</button>
            </form>
        </div>
    </div>

    <!-- ================= DOCUMENT DISPLAY ENGINE ================= -->
    <div id="invoiceModal" class="fixed inset-0 bg-black/90 z-50 overflow-y-auto p-4 hidden flex items-center justify-center">
        <div class="bg-white text-gray-800 w-full max-w-2xl rounded-2xl p-8 my-8 shadow-2xl relative">
            <button onclick="toggleModal('invoiceModal')" class="absolute top-4 right-4 text-gray-400 hover:text-gray-600 print-hidden">
                <i data-lucide="x" class="w-6 h-6"></i>
            </button>
            <div id="invoiceContent"></div>
            <div class="mt-6 flex justify-end gap-3 border-t border-gray-200 pt-4 print-hidden">
                <button onclick="window.print()" class="bg-gray-900 hover:bg-black text-white font-bold px-5 py-2.5 rounded-xl flex items-center gap-2 text-sm transition">
                    <i data-lucide="printer" class="w-4 h-4"></i> Print Statement
                </button>
            </div>
        </div>
    </div>

  <!-- ================= ARCHITECTURAL LOGIC ENGINE ================= -->
    <script>
        // Clean system template boundaries
        const blankState = {
            clients: [],
            jobs: [],
            rentals: [],
            expenses: [],
            fleet: ['Inflatable SUP #1', 'Inflatable SUP #2', 'Rigid Epoxy Board #1']
        };

        let appData = JSON.parse(localStorage.getItem('qualityYachtServiceData')) || { ...blankState };

        if(!appData.expenses) { appData.expenses = []; }

        function commitStorage() {
            localStorage.setItem('qualityYachtServiceData', JSON.stringify(appData));
            renderAll();
        }

        // MASTER FACTORY RESET CONTROLLER
        function systemResetData() {
            if (confirm("⚠️ SYSTEM DESTRUCTION ALERT:\n\nThis action will completely erase all Clients, Yacht Jobs, Rental Histories, and Corporate Expenses from this mobile interface. Continue?")) {
                if (confirm("FINAL VALIDATION:\n\nAre you absolutely positive you want to clear your production data back to zero? This process is structurally irreversible.")) {
                    appData = {
                        clients: [],
                        jobs: [],
                        rentals: [],
                        expenses: [],
                        fleet: [] // Completely clean slate for local setup
                    };
                    commitStorage();
                    switchTab('yacht'); // Bounce safety back to core monitor
                    alert("System cache cleared. Interface ready for customized entry production.");
                }
            }
        }

        function switchTab(viewTarget) {
            const views = {
                yacht: document.getElementById('yachtView'),
                sup: document.getElementById('supView'),
                expense: document.getElementById('expenseView'),
                settings: document.getElementById('settingsView')
            };
            
            const btns = {
                yacht: document.getElementById('yachtTabBtn'),
                sup: document.getElementById('supTabBtn'),
                expense: document.getElementById('expenseTabBtn'),
                settings: document.getElementById('settingsTabBtn')
            };

            // Hide all structural views
            Object.values(views).forEach(v => { if(v) v.classList.add('hidden'); });
            
            // Clean dynamic base classes across headers
            const generalBtnStyle = "w-1/4 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 text-gray-400 hover:text-white";
            Object.values(btns).forEach(b => { if(b) b.className = generalBtnStyle; });

            // Activate specific channel parameters
            if (viewTarget === 'yacht') {
                if(views.yacht) views.yacht.classList.remove('hidden');
                if(btns.yacht) btns.yacht.className = "w-1/4 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 bg-blue-600 text-white shadow";
            } else if (viewTarget === 'sup') {
                if(views.sup) views.sup.classList.remove('hidden');
                if(btns.sup) btns.sup.className = "w-1/4 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 bg-emerald-600 text-white shadow";
            } else if (viewTarget === 'expense') {
                if(views.expense) views.expense.classList.remove('hidden');
                if(btns.expense) btns.expense.className = "w-1/4 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 bg-rose-600 text-white shadow";
            } else if (viewTarget === 'settings') {
                if(views.settings) views.settings.classList.remove('hidden');
                if(btns.settings) btns.settings.className = "w-1/4 py-2.5 text-xs sm:text-sm font-semibold rounded-xl transition duration-200 flex justify-center items-center gap-1.5 bg-gray-700 text-white shadow ring-1 ring-gray-600";
            }
        }

        function toggleModal(modalId) {
            const el = document.getElementById(modalId);
            if(!el) return;
            el.classList.toggle('hidden');
            if(!el.classList.contains('hidden')) {
                populateDropdownStructures();
                renderInventoryList();
            }
        }

        function saveClient(e) {
            e.preventDefault();
            appData.clients.push({
                id: Date.now().toString(),
                name: document.getElementById('clientName').value,
                phone: document.getElementById('clientPhone').value || 'No Phone',
                email: document.getElementById('clientEmail').value || 'No Email',
                yacht: document.getElementById('clientYacht').value || 'Shoreline Base Client'
            });
            document.getElementById('clientForm').reset();
            toggleModal('clientModal');
            commitStorage();
        }

        function saveInventoryItem(e) {
            e.preventDefault();
            const nameField = document.getElementById('newBoardName');
            if(!nameField.value.trim()) return;
            appData.fleet.push(nameField.value.trim());
            nameField.value = '';
            renderInventoryList();
            commitStorage();
        }

        function removeInventoryItem(index) {
            appData.fleet.splice(index, 1);
            renderInventoryList();
            commitStorage();
        }

        function saveJob(e) {
            e.preventDefault();
            appData.jobs.push({
                id: Date.now().toString(),
                clientId: document.getElementById('jobClientSelect').value,
                desc: document.getElementById('jobDesc').value,
                cost: parseFloat(document.getElementById('jobCost').value),
                date: document.getElementById('jobDate').value,
                status: 'Active'
            });
            document.getElementById('jobForm').reset();
            toggleModal('jobModal');
            commitStorage();
        }

        function completeJob(id) {
            const job = appData.jobs.find(j => j.id === id);
            if(job) {
                job.status = 'Completed';
                commitStorage();
            }
        }

        function cancelJob(id) {
            if(confirm("Are you sure you want to cancel this yacht maintenance task?")) {
                const job = appData.jobs.find(j => j.id === id);
                if(job) {
                    job.status = 'Canceled';
                    commitStorage();
                }
            }
        }

        function saveRental(e) {
            e.preventDefault();
            const checkedBoxes = document.querySelectorAll('.asset-checkbox:checked');
            if (checkedBoxes.length === 0) {
                alert('Please check at least one fleet asset to book.');
                return;
            }
            
            const costPerBoardPerDay = parseFloat(document.getElementById('rentalCost').value);
            const clientId = document.getElementById('rentalClientSelect').value;
            const startDateStr = document.getElementById('rentalStartDate').value;
            const endDateStr = document.getElementById('rentalEndDate').value;
            
            if (!startDateStr || !endDateStr) {
                alert('Please select both a Start Date and an End Date.');
                return;
            }

            const start = new Date(startDateStr);
            const end = new Date(endDateStr);
            
            if (end < start) {
                alert('Error: End date cannot be prior to start date.');
                return;
            }

            const dayDiff = Math.max(1, Math.round((end - start) / (1000 * 60 * 60 * 24)));

            // === RENTAL OVERLAP GUARD ===
            const proposedStart = new Date(startDateStr + "T00:00:00").getTime();
            const proposedEnd = new Date(endDateStr + "T00:00:00").getTime();
            let overlapErrorMsg = "";

            for (let box of checkedBoxes) {
                const boardName = box.value;
                
                const conflict = appData.rentals.find(r => {
                    if (r.item !== boardName) return false;
                    if (r.status === 'Canceled' || r.status === 'Returned') return false;

                    const existStart = new Date(r.startDate + "T00:00:00").getTime();
                    const existEnd = new Date(r.endDate + "T00:00:00").getTime();

                    return (proposedStart <= existEnd && proposedEnd >= existStart);
                });

                if (conflict) {
                    overlapErrorMsg += `• "${boardName}" is already booked from ${conflict.startDate} to ${conflict.endDate}.\n`;
                }
            }

            if (overlapErrorMsg) {
                alert(`Rental Conflict Detected:\n\n${overlapErrorMsg}\nPlease adjust dates or choose alternative boards.`);
                return;
            }
            // ============================
            
            const calculatedTotalCostPerAsset = costPerBoardPerDay * dayDiff;
            const groupId = "GRP-" + Date.now().toString().slice(-6);

            checkedBoxes.forEach((box) => {
                appData.rentals.push({
                    id: Date.now().toString() + "-" + Math.random().toString(36).slice(2, 5),
                    groupId: groupId,
                    clientId: clientId,
                    item: box.value,
                    startDate: startDateStr,
                    endDate: endDateStr,
                    cost: calculatedTotalCostPerAsset, 
                    status: 'Upcoming'
                });
            });

            document.getElementById('rentalForm').reset();
            toggleModal('rentalModal');
            commitStorage();
        }

        function alterGroupRentalWorkflow(groupId, targetState) {
            if(targetState === 'Canceled' && !confirm("Are you sure you want to cancel this rental session?")) {
                return;
            }
            appData.rentals.forEach(r => {
                if(r.groupId === groupId) { r.status = targetState; }
            });
            commitStorage();
        }

        function saveExpense(e) {
            e.preventDefault();
            appData.expenses.push({
                id: Date.now().toString(),
                category: document.getElementById('expenseCategory').value,
                date: document.getElementById('expenseDate').value,
                desc: document.getElementById('expenseDesc').value,
                amount: parseFloat(document.getElementById('expenseAmount').value)
            });
            document.getElementById('expenseForm').reset();
            toggleModal('expenseModal');
            commitStorage();
        }

        function purgeExpense(id) {
            if(confirm("Confirm deletion of this expense record?")) {
                appData.expenses = appData.expenses.filter(exp => exp.id !== id);
                commitStorage();
            }
        }

        function populateDropdownStructures() {
            const jobClient = document.getElementById('jobClientSelect');
            const rentalClient = document.getElementById('rentalClientSelect');
            const assetCheckboxGroup = document.getElementById('rentalAssetCheckboxGroup');
            
            if(!jobClient || !rentalClient || !assetCheckboxGroup) return;

            let clientOptions = appData.clients.length === 0
                ? `<option value="" disabled>No profiles. Please add a client.</option>`
                : appData.clients.map(c => `<option value="${c.id}">${c.name} (${c.yacht})</option>`).join('');
            
            jobClient.innerHTML = clientOptions;
            rentalClient.innerHTML = clientOptions;

            if(appData.fleet.length === 0) {
                assetCheckboxGroup.innerHTML = `<p class="text-xs text-gray-500 italic">Fleet list empty. Add assets first.</p>`;
            } else {
                assetCheckboxGroup.innerHTML = appData.fleet.map((board, idx) => `
                    <label class="flex items-center gap-3 py-1 cursor-pointer select-none">
                        <input type="checkbox" value="${board}" class="asset-checkbox w-4 h-4 rounded text-emerald-600 bg-gray-800 border-gray-700 focus:ring-emerald-500">
                        <span class="text-gray-200 font-medium">${board}</span>
                    </label>
                `).join('');
            }
        }

        function renderInventoryList() {
            const container = document.getElementById('fleetInventoryContainer');
            if(!container) return;
            if(appData.fleet.length === 0) {
                container.innerHTML = `<p class="text-xs text-gray-500 italic">No assets indexed.</p>`;
                return;
            }
            container.innerHTML = appData.fleet.map((item, index) => `
                <div class="bg-gray-900 px-3 py-2 rounded-xl flex justify-between items-center border border-gray-700/50">
                    <span class="text-xs font-medium text-gray-200">${item}</span>
                    <button onclick="removeInventoryItem(${index})" class="text-red-400 hover:text-red-500"><i data-lucide="trash-2" class="w-4 h-4"></i></button>
                </div>
            `).join('');
            lucide.createIcons();
        }

        function showInvoiceDisplay(mode, recordId) {
            let clientRef;
            let invoiceItemsHTML = '';
            let subtotal = 0;
            let displayDate = '';
            let footerTimelineStr = '';
            let invoiceNumber = recordId.slice(-4);

            if(mode === 'job') {
                const job = appData.jobs.find(j => j.id === recordId);
                clientRef = appData.clients.find(c => c.id === job.clientId);
                subtotal = job.cost;
                displayDate = job.date;
                
                invoiceItemsHTML = `
                    <tr class="border-b border-gray-200 text-gray-800 text-sm">
                        <td class="py-3 font-semibold text-left text-gray-900">${job.desc}</td>
                        <td class="py-3 text-center text-gray-600">1</td>
                        <td class="py-3 text-right text-gray-600">$${job.cost.toFixed(2)}</td>
                        <td class="py-3 text-right font-semibold text-gray-900">$${job.cost.toFixed(2)}</td>
                    </tr>
                `;
            } else {
                const baseRental = appData.rentals.find(r => r.id === recordId);
                const relatedGroupItems = appData.rentals.filter(r => r.groupId === baseRental.groupId);
                clientRef = appData.clients.find(c => c.id === baseRental.clientId);
                displayDate = baseRental.startDate;

                const start = new Date(baseRental.startDate);
                const end = new Date(baseRental.endDate);
                const dayDiff = Math.max(1, Math.round((end - start) / (1000 * 60 * 60 * 24)));
                
                footerTimelineStr = `Rental Duration Balance: ${baseRental.startDate} to ${baseRental.endDate}`;

                relatedGroupItems.forEach(item => {
                    const pricePerDayMetric = item.cost / dayDiff;
                    subtotal += item.cost;
                    invoiceItemsHTML += `
                        <tr class="border-b border-gray-200 text-gray-800 text-sm">
                            <td class="py-4 font-semibold text-left text-gray-900">Paddle board (${item.item})</td>
                            <td class="py-4 text-center text-gray-900">${dayDiff}</td>
                            <td class="py-4 text-right text-gray-600">$${pricePerDayMetric.toFixed(2)}</td>
                            <td class="py-4 text-right font-semibold text-gray-900">$${item.cost.toFixed(2)}</td>
                        </tr>
                    `;
                });
            }

            const formatDateString = (dateStr) => {
                if(!dateStr) return '';
                const options = { day: 'numeric', month: 'short', year: 'numeric' };
                return new Date(dateStr + "T00:00:00").toLocaleDateString('en-US', options);
            };

            document.getElementById('invoiceContent').innerHTML = `
                <div class="flex justify-between items-start pb-8">
                    <div class="flex flex-col items-center">
                        <div class="w-44 h-12 bg-blue-600 text-white font-bold rounded-xl flex items-center justify-center tracking-wider text-sm shadow-md">
                            QUALITY YACHT
                        </div>
                    </div>
                    <div class="text-right flex flex-col justify-end">
                        <h1 class="text-3xl font-normal tracking-tight text-gray-900 mb-1">Invoice</h1>
                        <p class="text-base font-bold text-gray-900 leading-tight">Quality Yacht Service</p>
                        <p class="text-xs text-gray-600">Nassau</p>
                        <p class="text-xs text-gray-600">The Bahamas</p>
                        <p class="text-xs text-gray-600 mt-1">1(242)551-4171</p>
                        <p class="text-xs text-gray-600">Qualityyacht@hotmail.com</p>
                    </div>
                </div>

                <div class="bg-gray-100/80 rounded-xl p-5 grid grid-cols-2 gap-4 items-start mb-8">
                    <div>
                        <h4 class="text-xs font-black text-gray-900 uppercase tracking-wider mb-1">BILL TO</h4>
                        <p class="text-base font-bold text-gray-900 leading-snug">${clientRef ? clientRef.name : 'Vessel Account'}</p>
                        <p class="text-xs text-gray-700 mt-0.5">${clientRef ? clientRef.phone : ''}</p>
                        <p class="text-[11px] text-gray-500 italic">${clientRef ? clientRef.yacht : ''}</p>
                    </div>
                    <div class="text-right grid grid-cols-2 gap-y-1 text-xs">
                        <span class="font-bold text-gray-900 text-left pl-6">Invoice #</span>
                        <span class="text-gray-900 font-medium">${invoiceNumber}</span>
                        <span class="font-bold text-gray-900 text-left pl-6">Date</span>
                        <span class="text-gray-900 font-medium">${formatDateString(displayDate)}</span>
                    </div>
                </div>

                <table class="w-full text-left mb-6">
                    <thead>
                        <tr class="border-b-2 border-gray-300 text-xs font-black text-gray-900">
                            <th class="py-2 text-left w-1/2">Item</th>
                            <th class="py-2 text-center">Days</th>
                            <th class="py-2 text-right">Price</th>
                            <th class="py-2 text-right">Amount</th>
                        </tr>
                    </thead>
                    <tbody>
                        ${invoiceItemsHTML}
                    </tbody>
                </table>

                <div class="flex flex-col items-end space-y-1.5 text-sm pr-1 mb-8">
                    <div class="w-64 flex justify-between">
                        <span class="text-gray-600 font-medium">Subtotal</span>
                        <span class="text-gray-900 font-semibold">$${subtotal.toFixed(2)}</span>
                    </div>
                    <div class="w-64 flex justify-between border-b border-gray-200 pb-4">
                        <span class="text-gray-600 font-medium">Total</span>
                        <span class="text-gray-900 font-semibold">$${subtotal.toFixed(2)}</span>
                    </div>
                </div>

                <div class="flex justify-end mt-4">
                    <div class="bg-gray-100 rounded-lg p-4 w-64 text-right">
                        <p class="text-xs font-bold text-gray-700 uppercase tracking-wider mb-1">Amount due</p>
                        <p class="text-3xl font-black text-gray-900">$${subtotal.toFixed(2)}</p>
                    </div>
                </div>

                ${footerTimelineStr ? `
                    <div class="mt-16 pt-4 border-t border-gray-100 text-[11px] font-medium text-gray-600">
                        ${footerTimelineStr}
                    </div>
                ` : ''}
            `;
            
            const modal = document.getElementById('invoiceModal');
            if(modal) modal.classList.remove('hidden');
            lucide.createIcons();
        }

        function getCountdownBadge(endDateStr) {
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            
            const end = new Date(endDateStr + "T00:00:00");
            end.setHours(0, 0, 0, 0);
            
            const diffTime = end - today;
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));

            if (diffDays < 0) {
                return `<span class="text-[10px] font-black px-2 py-0.5 rounded bg-rose-500/20 text-rose-400 animate-pulse border border-rose-500/30">OVERDUE</span>`;
            } else if (diffDays === 0) {
                return `<span class="text-[10px] font-black px-2 py-0.5 rounded bg-amber-500/20 text-amber-400 animate-pulse border border-amber-500/30">DUE TODAY</span>`;
            } else if (diffDays === 1) {
                return `<span class="text-[10px] font-bold px-2 py-0.5 rounded bg-amber-500/10 text-amber-400 border border-amber-500/20">1 DAY LEFT</span>`;
            } else {
                return `<span class="text-[10px] font-bold px-2 py-0.5 rounded bg-emerald-500/10 text-emerald-400 border border-emerald-500/20">${diffDays} DAYS LEFT</span>`;
            }
        }

        function renderAll() {
            const localDate = new Date();
            const year = localDate.getFullYear();
            const month = String(localDate.getMonth() + 1).padStart(2, '0');
            const day = String(localDate.getDate()).padStart(2, '0');
            const todayStr = `${year}-${month}-${day}`;

            // 1. FINANCIAL CALCULATION LAYER
            let yachtEarningsTotal = 0;
            let supEarningsTotal = 0;

            appData.jobs.forEach(j => {
                if (j.status === 'Completed') yachtEarningsTotal += j.cost;
            });

            appData.rentals.forEach(r => {
                if (r.status === 'Active' || r.status === 'Returned') supEarningsTotal += r.cost;
            });

            const grossRevenue = yachtEarningsTotal + supEarningsTotal;
            
            const grossEl = document.getElementById('grossRevenueBox');
            if (grossEl) grossEl.innerText = `$${grossRevenue.toLocaleString('en-US', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}`;
            
            const yachtSplitEl = document.getElementById('yachtSplit');
            if (yachtSplitEl) yachtSplitEl.innerText = `Yacht (Completed): $${yachtEarningsTotal.toLocaleString('en-US', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}`;
            
            const supSplitEl = document.getElementById('supSplit');
            if (supSplitEl) supSplitEl.innerText = `SUP (Deployed/Returned): $${supEarningsTotal.toLocaleString('en-US', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}`;

            const findClient = (id) => appData.clients.find(c => c.id === id) || { name: 'Unknown Client', yacht: 'N/A' };

            // 2. YACHT MAINTENANCE LOGS
            let yachtTodayHTML = '';
            let yachtUpcomingHTML = '';
            let yachtCompletedHTML = '';

            appData.jobs.forEach(job => {
                if (job.status === 'Canceled') return; // Soft-hidden filter rule active

                const client = findClient(job.clientId);
                const isToday = job.date === todayStr;

                const baseCard = `
                    <div class="bg-gray-800 border border-gray-700/80 p-4 rounded-xl flex justify-between items-center shadow-md">
                        <div class="space-y-1">
                            <div class="flex items-center gap-2">
                                <h4 class="text-sm font-bold text-white leading-tight">${client.name}</h4>
                                <span class="text-[10px] bg-gray-700 text-gray-300 font-medium px-2 py-0.5 rounded-md border border-gray-600/50">${client.yacht}</span>
                            </div>
                            <p class="text-xs text-gray-300 font-medium">${job.desc}</p>
                            <p class="text-[10px] text-gray-500 font-bold tracking-wide">${new Date(job.date + "T00:00:00").toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' })}</p>
                        </div>
                        <div class="flex flex-col items-end gap-2 shrink-0 pl-3">
                            <span class="text-sm font-black text-white">$${job.cost.toFixed(2)}</span>
                            <div class="flex items-center gap-1.5">
                                <button onclick="showInvoiceDisplay('job', '${job.id}')" class="bg-gray-700 text-gray-300 p-1.5 rounded-lg active:scale-95 transition" title="View Statement">
                                    <i data-lucide="file-text" class="w-3.5 h-3.5"></i>
                                </button>
                                ${job.status === 'Active' ? `
                                    <button onclick="cancelJob('${job.id}')" class="bg-red-500/10 hover:bg-red-500/20 text-red-400 p-1.5 rounded-lg active:scale-95 transition" title="Cancel Job">
                                        <i data-lucide="x" class="w-3.5 h-3.5"></i>
                                    </button>
                                    <button onclick="completeJob('${job.id}')" class="bg-blue-600 text-white p-1.5 rounded-lg active:scale-95 transition" title="Complete Job">
                                        <i data-lucide="check" class="w-3.5 h-3.5"></i>
                                    </button>
                                ` : `
                                    <span class="text-[10px] font-extrabold text-emerald-400 bg-emerald-500/10 px-2 py-1 rounded border border-emerald-500/20 uppercase tracking-wide">Done</span>
                                `}
                            </div>
                        </div>
                    </div>
                `;

                if (job.status === 'Completed') {
                    yachtCompletedHTML += baseCard;
                } else if (isToday) {
                    yachtTodayHTML += baseCard;
                } else {
                    yachtUpcomingHTML += baseCard;
                }
            });

            const ytEl = document.getElementById('yachtTodayList');
            if(ytEl) ytEl.innerHTML = yachtTodayHTML || `<p class="text-xs text-gray-500 italic py-2">No maintenance tasks queued for today.</p>`;
            
            const yuEl = document.getElementById('yachtUpcomingList');
            if(yuEl) yuEl.innerHTML = yachtUpcomingHTML || `<p class="text-xs text-gray-500 italic py-2">No upcoming maintenance operations filed.</p>`;
            
            const ycEl = document.getElementById('yachtCompletedList');
            if(ycEl) ycEl.innerHTML = yachtCompletedHTML || `<p class="text-xs text-gray-500 italic py-2">No finished work orders tracked yet.</p>`;

            // 3. SUP FLEET RENTAL LOGS
            let rentalGroups = {};
            appData.rentals.forEach(r => {
                if (r.status === 'Canceled') return; 
                if(!rentalGroups[r.groupId]) rentalGroups[r.groupId] = [];
                rentalGroups[r.groupId].push(r);
            });

            let supUpcomingHTML = '';
            let supActiveHTML = '';
            let supCompletedHTML = '';

            Object.keys(rentalGroups).forEach(groupId => {
                const groupItems = rentalGroups[groupId];
                const baseItem = groupItems[0];
                const client = findClient(baseItem.clientId);
                const assetNames = groupItems.map(item => item.item).join(', ');
                const totalCost = groupItems.reduce((acc, curr) => acc + curr.cost, 0);
                const statusLabel = baseItem.status;
                const dateBadge = getCountdownBadge(baseItem.endDate);

                const baseGroupCard = `
                    <div class="bg-gray-800 border border-gray-700/80 p-4 rounded-xl flex justify-between items-center shadow-md">
                        <div class="space-y-1.5">
                            <div class="flex items-center flex-wrap gap-2">
                                <h4 class="text-sm font-bold text-white leading-tight">${client.name}</h4>
                                ${statusLabel === 'Active' ? dateBadge : ''}
                            </div>
                            <p class="text-xs text-emerald-400 font-semibold">${assetNames}</p>
                            <div class="text-[10px] text-gray-400 flex items-center gap-1.5 font-medium">
                                <i data-lucide="calendar" class="w-3 h-3 text-gray-500"></i>
                                <span>${new Date(baseItem.startDate + "T00:00:00").toLocaleDateString('en-US', { month: 'short', day: 'numeric' })} – ${new Date(baseItem.endDate + "T00:00:00").toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' })}</span>
                            </div>
                        </div>
                        <div class="flex flex-col items-end gap-2 shrink-0 pl-3">
                            <span class="text-sm font-black text-white">$${totalCost.toFixed(2)}</span>
                            <div class="flex items-center gap-1.5">
                                <button onclick="showInvoiceDisplay('rental', '${baseItem.id}')" class="bg-gray-700 text-gray-300 p-1.5 rounded-lg active:scale-95 transition" title="Print Statement">
                                    <i data-lucide="file-text" class="w-3.5 h-3.5"></i>
                                </button>
                                ${statusLabel === 'Upcoming' ? `
                                    <button onclick="alterGroupRentalWorkflow('${groupId}', 'Canceled')" class="bg-red-500/10 hover:bg-red-500/20 text-red-400 p-1.5 rounded-lg active:scale-95 transition" title="Cancel Booking">
                                        <i data-lucide="x" class="w-3.5 h-3.5"></i>
                                    </button>
                                    <button onclick="alterGroupRentalWorkflow('${groupId}', 'Active')" class="bg-emerald-600 text-white p-1.5 rounded-lg active:scale-95 transition" title="Dispatch Fleet">
                                        <i data-lucide="play" class="w-3.5 h-3.5"></i>
                                    </button>
                                ` : statusLabel === 'Active' ? `
                                    <button onclick="alterGroupRentalWorkflow('${groupId}', 'Canceled')" class="bg-red-500/10 hover:bg-red-500/20 text-red-400 p-1.5 rounded-lg active:scale-95 transition" title="Cancel Booking">
                                        <i data-lucide="x" class="w-3.5 h-3.5"></i>
                                    </button>
                                    <button onclick="alterGroupRentalWorkflow('${groupId}', 'Returned')" class="bg-blue-600 text-white p-1.5 rounded-lg active:scale-95 transition" title="Return Fleet">
                                        <i data-lucide="check" class="w-3.5 h-3.5"></i>
                                    </button>
                                ` : `
                                    <span class="text-[10px] font-extrabold text-emerald-400 bg-emerald-500/10 px-2 py-1 rounded border border-emerald-500/20 uppercase tracking-wide">Returned</span>
                                `}
                            </div>
                        </div>
                    </div>
                `;

                if (statusLabel === 'Upcoming') {
                    supUpcomingHTML += baseGroupCard;
                } else if (statusLabel === 'Active') {
                    supActiveHTML += baseGroupCard;
                } else {
                    supCompletedHTML += baseGroupCard;
                }
            });

            const suEl = document.getElementById('supUpcomingList');
            if(suEl) suEl.innerHTML = supUpcomingHTML || `<p class="text-xs text-gray-500 italic py-2">No pending fleet departures.</p>`;
            
            const saEl = document.getElementById('supActiveList');
            if(saEl) saEl.innerHTML = supActiveHTML || `<p class="text-xs text-gray-500 italic py-2">No active rentals out on charter.</p>`;
            
            const scEl = document.getElementById('supCompletedList');
            if(scEl) scEl.innerHTML = supCompletedHTML || `<p class="text-xs text-gray-500 italic py-2">No closed files tracked in the history ledger.</p>`;

            // 4. OPERATIONAL EXPENSES
            let expenseHTML = '';
            const sortedExpenses = [...appData.expenses].sort((a,b) => new Date(b.date) - new Date(a.date));
            
            sortedExpenses.forEach(exp => {
                expenseHTML += `
                    <div class="p-4 flex justify-between items-center hover:bg-gray-800/40 transition">
                        <div>
                            <div class="flex items-center gap-2">
                                <span class="text-[10px] font-bold px-2 py-0.5 rounded tracking-wide uppercase bg-rose-500/10 text-rose-400 border border-rose-500/20">
                                    ${exp.category}
                                </span>
                                <span class="text-xs text-gray-500 font-semibold">${new Date(exp.date + "T00:00:00").toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' })}</span>
                            </div>
                            <p class="text-sm font-semibold text-gray-200 mt-1">${exp.desc}</p>
                        </div>
                        <div class="flex items-center gap-3 pl-2">
                            <span class="text-sm font-black text-rose-400">-$${exp.amount.toFixed(2)}</span>
                            <button onclick="purgeExpense('${exp.id}')" class="text-gray-500 hover:text-red-400 transition" title="Purge Transaction">
                                <i data-lucide="trash-2" class="w-4 h-4"></i>
                            </button>
                        </div>
                    </div>
                `;
            });

            const exL = document.getElementById('expenseLedgerList');
            if(exL) {
                exL.innerHTML = expenseHTML || `
                    <div class="p-8 text-center text-gray-500">
                        <i data-lucide="receipt" class="w-8 h-8 mx-auto mb-2 text-gray-600"></i>
                        <p class="text-xs italic">No operational expense outlays logged yet.</p>
                    </div>
                `;
            }

            lucide.createIcons();
        }

        window.addEventListener('DOMContentLoaded', () => {
            renderAll();
        });
    </script>
    </body>
</html>
