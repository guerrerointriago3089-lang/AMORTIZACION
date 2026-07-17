<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KRONOS - Simulador de Amortización de Créditos</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts (Plus Jakarta Sans) -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                        code: ['Fira Code', 'monospace'],
                    },
                    colors: {
                        luxury: {
                            bg: '#05060b',
                            card: '#0c0e17',
                            border: 'rgba(16, 185, 129, 0.15)',
                            text: '#e2e8f0',
                            accent: '#10b981', 
                            gold: '#f59e0b',
                        }
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background-color: #05060b;
            font-family: 'Plus Jakarta Sans', sans-serif;
            color: #e2e8f0;
        }
        .glow-emerald {
            box-shadow: 0 0 25px rgba(16, 185, 129, 0.08), inset 0 0 10px rgba(16, 185, 129, 0.01);
        }
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: rgba(12, 14, 23, 0.5);
        }
        ::-webkit-scrollbar-thumb {
            background: rgba(16, 185, 129, 0.25);
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: rgba(16, 185, 129, 0.5);
        }
    </style>
</head>
<body class="relative min-h-screen flex flex-col justify-between overflow-x-hidden antialiased">

    <!-- Grid Background -->
    <div class="absolute inset-0 bg-[linear-gradient(rgba(16,185,129,0.01)_1px,transparent_1px),linear-gradient(90deg,rgba(16,185,129,0.01)_1px,transparent_1px)] bg-[size:40px_40px] pointer-events-none z-0"></div>
    <div class="absolute top-0 left-1/4 w-[500px] h-[500px] bg-emerald-500/5 rounded-full filter blur-[120px] pointer-events-none z-0"></div>
    <div class="absolute bottom-10 right-10 w-[400px] h-[400px] bg-emerald-500/3 rounded-full filter blur-[100px] pointer-events-none z-0"></div>

    <!-- MAIN NAV HEADER -->
    <header class="z-20 w-full bg-[#0c0e17]/90 border-b border-emerald-950/40 px-6 py-4 flex justify-between items-center backdrop-blur-md sticky top-0">
        <div class="flex items-center space-x-3">
            <div class="bg-emerald-950/60 p-2.5 rounded-xl border border-emerald-500/20">
                <i data-lucide="calculator" class="w-6 h-6 text-emerald-400"></i>
            </div>
            <div>
                <h1 class="font-bold text-lg md:text-xl tracking-wider text-emerald-400 font-sans flex items-center gap-2">
                    KRONOS
                    <span class="text-[9px] bg-emerald-950 text-emerald-300 px-2.5 py-0.5 border border-emerald-500/30 rounded-full font-sans tracking-normal">SISTEMA AMORTIZACIÓN</span>
                </h1>
                <p class="text-[10px] text-slate-400 tracking-wider uppercase font-sans">Análisis y proyección detallada de pasivos financieros</p>
            </div>
        </div>

        <div class="hidden lg:flex items-center space-x-6 text-xs font-sans border-l border-emerald-950/50 pl-6">
            <div class="flex flex-col items-end">
                <span class="text-slate-500 text-[9px] uppercase">MODO DE CÁLCULO</span>
                <span class="text-emerald-400 font-bold flex items-center gap-1">
                    CÁLCULO INMEDIATO
                </span>
            </div>
        </div>
    </header>

    <!-- MAIN SYSTEM INTERFACE -->
    <main class="flex-1 z-10 p-4 md:p-6 lg:p-8 max-w-[1600px] w-full mx-auto grid grid-cols-1 lg:grid-cols-12 gap-6 items-start">

        <!-- LEFT COLUMN: Control Panel & Debt Inputs -->
        <section class="lg:col-span-4 space-y-6">
            <div class="bg-[#0c0e17] border border-emerald-950 rounded-2xl p-5 md:p-6 glow-emerald">
                <div class="flex items-center space-x-2.5 border-b border-emerald-950/70 pb-4 mb-5">
                    <i data-lucide="sliders" class="w-4 h-4 text-emerald-400"></i>
                    <h2 class="font-bold text-sm tracking-widest uppercase text-slate-300 font-sans">Condiciones del Crédito</h2>
                </div>

                <!-- Input Controls -->
                <div class="space-y-4 font-sans">
                    <!-- Loan Amount -->
                    <div>
                        <div class="flex justify-between items-center mb-1.5">
                            <label for="loan-amount" class="text-xs text-slate-400 font-semibold uppercase tracking-wider">Monto de Capital</label>
                            <span class="text-xs text-emerald-400 font-bold" id="label-amount">$100,000.00</span>
                        </div>
                        <div class="relative">
                            <span class="absolute left-3 top-2.5 text-slate-500 font-semibold text-sm">$</span>
                            <input type="number" id="loan-amount" value="100000" min="1000" max="100000000" step="5000" class="w-full bg-black/40 border border-emerald-950/70 rounded-xl py-2 pl-7 pr-3 text-slate-200 text-sm focus:outline-none focus:border-emerald-500/80 transition" oninput="calculateAmortization()">
                        </div>
                        <input type="range" id="loan-amount-range" min="5000" max="1000000" step="5000" value="100000" class="w-full h-1 bg-emerald-950 rounded-lg appearance-none cursor-pointer mt-2 accent-emerald-500" oninput="syncRange('amount')">
                    </div>

                    <!-- Interest Rate -->
                    <div>
                        <div class="flex justify-between items-center mb-1.5">
                            <label for="interest-rate" class="text-xs text-slate-400 font-semibold uppercase tracking-wider">Tasa de Interés Anual (T.N.A.)</label>
                            <span class="text-xs text-emerald-400 font-bold" id="label-rate">12.50%</span>
                        </div>
                        <div class="relative">
                            <input type="number" id="interest-rate" value="12.5" min="0.1" max="100" step="0.1" class="w-full bg-black/40 border border-emerald-950/70 rounded-xl py-2 px-3 text-slate-200 text-sm focus:outline-none focus:border-emerald-500/80 transition" oninput="calculateAmortization()">
                            <span class="absolute right-3 top-2.5 text-slate-500 font-semibold text-sm">%</span>
                        </div>
                        <input type="range" id="interest-rate-range" min="1" max="40" step="0.1" value="12.5" class="w-full h-1 bg-emerald-950 rounded-lg appearance-none cursor-pointer mt-2 accent-emerald-500" oninput="syncRange('rate')">
                    </div>

                    <!-- Loan Term -->
                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label for="loan-term" class="text-xs text-slate-400 font-semibold uppercase tracking-wider block mb-1.5">Plazo</label>
                            <input type="number" id="loan-term" value="5" min="1" max="50" class="w-full bg-black/40 border border-emerald-950/70 rounded-xl py-2 px-3 text-slate-200 text-sm focus:outline-none focus:border-emerald-500/80 transition" oninput="calculateAmortization()">
                        </div>
                        <div>
                            <label for="term-type" class="text-xs text-slate-400 font-semibold uppercase tracking-wider block mb-1.5">Frecuencia</label>
                            <select id="term-type" class="w-full bg-[#0c0e17] border border-emerald-950/70 rounded-xl py-2 px-3 text-slate-200 text-sm focus:outline-none focus:border-emerald-500/80 cursor-pointer transition" onchange="calculateAmortization()">
                                <option value="years">Años</option>
                                <option value="months">Meses</option>
                            </select>
                        </div>
                    </div>

                    <!-- Amortization System -->
                    <div>
                        <label for="amortization-type" class="text-xs text-slate-400 font-semibold uppercase tracking-wider block mb-1.5">Sistema de Amortización</label>
                        <select id="amortization-type" class="w-full bg-[#0c0e17] border border-emerald-950/70 rounded-xl py-2.5 px-3 text-slate-200 text-sm focus:outline-none focus:border-emerald-500/80 cursor-pointer transition" onchange="calculateAmortization()">
                            <option value="french">Sistema Francés (Cuotas Constantes)</option>
                            <option value="german">Sistema Alemán (Amortización Constante)</option>
                            <option value="american">Sistema Americano (Interés Solo / Capital Final)</option>
                        </select>
                        <p class="text-[11px] text-slate-400 mt-2 font-sans leading-relaxed" id="system-info-description">
                            * Francés: Al inicio del crédito se abona una mayor proporción de intereses. Las cuotas periódicas se mantienen constantes.
                        </p>
                    </div>
                </div>
            </div>

            <!-- EXTRA PAYMENTS WIDGET -->
            <div class="bg-[#0c0e17] border border-emerald-950 rounded-2xl p-5 md:p-6 glow-emerald relative overflow-hidden">
                <div class="absolute -top-12 -right-12 w-28 h-28 bg-emerald-500/5 rounded-full filter blur-xl pointer-events-none"></div>
                <div class="flex items-center justify-between border-b border-emerald-950/70 pb-4 mb-4">
                    <div class="flex items-center space-x-2.5">
                        <i data-lucide="trending-down" class="w-4 h-4 text-emerald-400"></i>
                        <h2 class="font-bold text-sm tracking-widest uppercase text-slate-300 font-sans">Abonos Extraordinarios</h2>
                    </div>
                    <span class="text-[9px] bg-emerald-950 text-emerald-400 px-2 py-0.5 rounded border border-emerald-500/20 font-sans">OPCIONAL</span>
                </div>
                
                <p class="text-[11px] text-slate-400 mb-4 leading-relaxed font-sans">
                    Permite calcular el impacto de los aportes complementarios para reducir el interés total y acortar el plazo de pago.
                </p>

                <div class="space-y-4 font-sans">
                    <!-- Recurring Extra Payment -->
                    <div>
                        <div class="flex justify-between items-center mb-1">
                            <label for="extra-monthly" class="text-xs text-slate-400 font-semibold tracking-wide">Abono Mensual Recurrente</label>
                            <span class="text-[10px] text-emerald-500 font-bold" id="label-monthly-extra">$0.00 / mes</span>
                        </div>
                        <div class="relative">
                            <span class="absolute left-3 top-2.5 text-slate-500 font-semibold text-sm">$</span>
                            <input type="number" id="extra-monthly" value="0" min="0" step="50" class="w-full bg-black/40 border border-emerald-950/70 rounded-xl py-2 pl-7 pr-3 text-slate-200 text-sm focus:outline-none focus:border-emerald-500/80 transition" oninput="calculateAmortization()">
                        </div>
                    </div>

                    <!-- Single Big Lump Sum Payment -->
                    <div class="grid grid-cols-2 gap-3">
                        <div>
                            <label for="extra-one-time" class="text-xs text-slate-400 font-semibold tracking-wide block mb-1">Abono Único Especial</label>
                            <div class="relative">
                                <span class="absolute left-3 top-2.5 text-slate-500 font-semibold text-sm">$</span>
                                <input type="number" id="extra-one-time" value="0" min="0" step="100" class="w-full bg-black/40 border border-emerald-950/70 rounded-xl py-2 pl-7 pr-3 text-slate-200 text-sm focus:outline-none focus:border-emerald-500/80 transition" oninput="calculateAmortization()">
                            </div>
                        </div>
                        <div>
                            <label for="extra-one-time-month" class="text-xs text-slate-400 font-semibold tracking-wide block mb-1">En el Mes Nº</label>
                            <input type="number" id="extra-one-time-month" value="12" min="1" max="600" class="w-full bg-black/40 border border-emerald-950/70 rounded-xl py-2 px-3 text-slate-200 text-sm focus:outline-none focus:border-emerald-500/80 transition" oninput="calculateAmortization()">
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- RIGHT COLUMN: Dashboard Statistics & Chart Analysis -->
        <section class="lg:col-span-8 space-y-6">
            
            <!-- FINANCIAL STATS (KPIS) -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4 font-sans">
                <!-- KPI 1: Cuota Estimada -->
                <div class="bg-[#0c0e17] border border-emerald-950 rounded-2xl p-4 glow-emerald">
                    <span class="text-[9px] text-slate-500 uppercase tracking-widest font-semibold block mb-1">Cuota Promedio</span>
                    <div class="text-xl md:text-2xl font-bold text-slate-200" id="kpi-monthly-payment">$0.00</div>
                    <span class="text-[9.5px] text-slate-400 mt-1 block" id="kpi-payment-details">Capital + Interés</span>
                </div>

                <!-- KPI 2: Total Intereses -->
                <div class="bg-[#0c0e17] border border-emerald-950 rounded-2xl p-4 glow-emerald">
                    <span class="text-[9px] text-slate-500 uppercase tracking-widest font-semibold block mb-1">Total Intereses</span>
                    <div class="text-xl md:text-2xl font-bold text-emerald-400" id="kpi-total-interest">$0.00</div>
                    <span class="text-[9.5px] text-slate-400 mt-1 block" id="kpi-interest-percentage">0.00% del préstamo</span>
                </div>

                <!-- KPI 3: Total Pagado -->
                <div class="bg-[#0c0e17] border border-emerald-950 rounded-2xl p-4 glow-emerald">
                    <span class="text-[9px] text-slate-500 uppercase tracking-widest font-semibold block mb-1">Costo Total</span>
                    <div class="text-xl md:text-2xl font-bold text-slate-200" id="kpi-total-paid">$0.00</div>
                    <span class="text-[9.5px] text-slate-400 mt-1 block">Préstamo + Intereses</span>
                </div>

                <!-- KPI 4: Ahorro Estimado -->
                <div class="bg-[#0c0e17] border-emerald-950 rounded-2xl p-4 bg-emerald-950/10 border-emerald-500/20 relative overflow-hidden">
                    <span class="text-[9px] text-emerald-400 uppercase tracking-widest font-semibold block mb-1">Ahorro Generado</span>
                    <div class="text-xl md:text-2xl font-bold text-emerald-400" id="kpi-savings">$0.00</div>
                    <span class="text-[9.5px] text-emerald-400/80 mt-1 block" id="kpi-savings-time">Periodos ahorrados: 0</span>
                </div>
            </div>

            <!-- INTERACTIVE ANALYTICAL CHARTS -->
            <div class="grid grid-cols-1 md:grid-cols-12 gap-6 font-sans">
                <!-- Evolution Graph (Line) -->
                <div class="bg-[#0c0e17] border border-emerald-950 rounded-2xl p-4 md:p-5 glow-emerald md:col-span-8 flex flex-col justify-between">
                    <div class="flex items-center justify-between mb-4">
                        <span class="text-xs text-slate-400 font-semibold tracking-wider uppercase">Trayectoria del Saldo Pendiente</span>
                        <div class="flex items-center space-x-1.5">
                            <span class="inline-block w-2.5 h-2.5 rounded-full bg-emerald-500"></span>
                            <span class="text-[10px] text-slate-400">Saldo Restante</span>
                        </div>
                    </div>
                    <div class="h-64 relative w-full flex items-center justify-center">
                        <canvas id="evolutionChart"></canvas>
                    </div>
                </div>

                <!-- Amortization Ratio (Donut) -->
                <div class="bg-[#0c0e17] border border-emerald-950 rounded-2xl p-4 md:p-5 glow-emerald md:col-span-4 flex flex-col justify-between">
                    <span class="text-xs text-slate-400 font-semibold tracking-wider uppercase mb-4">Estructura del Desembolso</span>
                    <div class="h-56 relative w-full flex items-center justify-center">
                        <canvas id="ratioChart"></canvas>
                    </div>
                    <div class="text-center text-[10px] text-slate-500 mt-2">
                        Relación entre capital e interés total.
                    </div>
                </div>
            </div>

            <!-- AMORTIZATION DATA TABLE CARD -->
            <div class="bg-[#0c0e17] border border-emerald-950 rounded-2xl p-5 md:p-6 glow-emerald">
                <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4 border-b border-emerald-950/70 pb-4 mb-4">
                    <div>
                        <h2 class="font-bold text-sm tracking-widest uppercase text-slate-300 font-sans">Tabla de Amortización Mensual</h2>
                        <p class="text-[11px] text-slate-400 mt-1 font-sans">Evolución de cuotas y saldos de conformidad con las variables indicadas.</p>
                    </div>

                    <!-- Actions & Downloads -->
                    <div class="flex flex-wrap items-center gap-2 font-sans">
                        <button onclick="exportCSV()" class="bg-emerald-950/40 hover:bg-emerald-900/40 text-emerald-400 border border-emerald-800/40 px-3 py-1.5 rounded-xl text-xs font-semibold transition flex items-center gap-1.5 shadow-sm">
                            <i data-lucide="download" class="w-3.5 h-3.5"></i> Exportar CSV
                        </button>
                        <button onclick="window.print()" class="bg-slate-900 hover:bg-slate-800 text-slate-300 border border-slate-800 px-3 py-1.5 rounded-xl text-xs font-semibold transition flex items-center gap-1.5">
                            <i data-lucide="printer" class="w-3.5 h-3.5"></i> Imprimir Reporte
                        </button>
                    </div>
                </div>

                <!-- Table Container -->
                <div class="overflow-x-auto border border-emerald-950 rounded-xl bg-black/40 max-h-[420px] relative">
                    <table class="w-full text-left border-collapse text-xs md:text-sm" id="amortization-table">
                        <thead class="sticky top-0 bg-[#0c0e17] border-b border-emerald-950 text-emerald-400 font-sans tracking-wider text-[10px] uppercase">
                            <tr>
                                <th class="p-3 font-semibold text-center w-16">Mes</th>
                                <th class="p-3 font-semibold">Monto de Cuota</th>
                                <th class="p-3 font-semibold">Interés del Período</th>
                                <th class="p-3 font-semibold">Amort. Capital</th>
                                <th class="p-3 font-semibold">Abono Extra</th>
                                <th class="p-3 font-semibold text-right">Saldo Remanente</th>
                            </tr>
                        </thead>
                        <tbody class="divide-y divide-emerald-950/30 text-slate-300 font-sans text-[11px]" id="table-body">
                            <!-- Populated Dynamically via JS -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>
    </main>

    <!-- FOOTER STATEMENTS -->
    <footer class="z-20 w-full bg-[#0c0e17] text-center py-4 border-t border-emerald-950/40 text-[10px] text-slate-500 font-sans uppercase tracking-wider">
        © 2026 Simulador Financiero Premium. Todos los derechos reservados. Uso libre y privado.
    </footer>

    <!-- ADVANCED CALCULATIONS & CHARTS INTERACTION -->
    <script>
        // Global references for Chart.js instances to avoid multiple layout overlaps
        let evolutionChartInst = null;
        let ratioChartInst = null;

        // Custom alert wrapper to replace forbidden native alert()
        function showCustomToast(message, type = 'info') {
            const toast = document.createElement('div');
            toast.className = `fixed bottom-5 right-5 z-50 p-4 rounded-xl border font-sans text-xs flex items-center gap-2 shadow-2xl transition-all duration-300 transform translate-y-10 opacity-0`;
            
            if (type === 'error') {
                toast.className += ' bg-rose-950/90 text-rose-200 border-rose-800';
            } else {
                toast.className += ' bg-emerald-950/90 text-emerald-200 border-emerald-800';
            }
            
            toast.innerHTML = `<i data-lucide="info" class="w-4 h-4"></i> <span>${message}</span>`;
            document.body.appendChild(toast);
            lucide.createIcons();

            // Trigger Animation
            setTimeout(() => {
                toast.classList.remove('translate-y-10', 'opacity-0');
            }, 10);

            // Close Animation
            setTimeout(() => {
                toast.classList.add('translate-y-10', 'opacity-0');
                setTimeout(() => toast.remove(), 300);
            }, 4000);
        }

        // Setup page initialization
        window.onload = function() {
            lucide.createIcons();
            calculateAmortization();
        };

        // Synchronize numeric inputs with visual sliders
        function syncRange(field) {
            if (field === 'amount') {
                const rangeVal = document.getElementById('loan-amount-range').value;
                document.getElementById('loan-amount').value = rangeVal;
            } else if (field === 'rate') {
                const rangeVal = document.getElementById('interest-rate-range').value;
                document.getElementById('interest-rate').value = rangeVal;
            }
            calculateAmortization();
        }

        // Currency and percentage formatter utilities
        function formatMoney(amount) {
            return new Intl.NumberFormat('es-ES', {
                style: 'currency',
                currency: 'EUR',
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            }).format(amount).replace('€', '$'); // standard dollar representation with elegant styling
        }

        function formatPercent(value) {
            return new Intl.NumberFormat('es-ES', {
                style: 'percent',
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            }).format(value);
        }

        // Main algorithm to resolve Amortization schedule dynamically
        function calculateAmortization() {
            // Retrieve values
            let capital = parseFloat(document.getElementById('loan-amount').value);
            let annualRate = parseFloat(document.getElementById('interest-rate').value);
            let termVal = parseInt(document.getElementById('loan-term').value);
            let termType = document.getElementById('term-type').value;
            let amortType = document.getElementById('amortization-type').value;

            // Extra payment simulators
            let extraMonthly = parseFloat(document.getElementById('extra-monthly').value) || 0;
            let extraOneTime = parseFloat(document.getElementById('extra-one-time').value) || 0;
            let extraOneTimeMonth = parseInt(document.getElementById('extra-one-time-month').value) || 0;

            // Validation fallbacks
            if (isNaN(capital) || capital <= 0) capital = 100000;
            if (isNaN(annualRate) || annualRate <= 0) annualRate = 12.5;
            if (isNaN(termVal) || termVal <= 0) termVal = 5;

            // Update UI quick labels
            document.getElementById('label-amount').textContent = formatMoney(capital);
            document.getElementById('label-rate').textContent = `${annualRate.toFixed(2)}%`;
            document.getElementById('label-monthly-extra').textContent = `${formatMoney(extraMonthly)} / mes`;

            // Adjust ranges
            document.getElementById('loan-amount-range').value = capital;
            document.getElementById('interest-rate-range').value = annualRate;

            // Compute total months
            let totalPeriods = termType === 'years' ? termVal * 12 : termVal;
            let monthlyRate = (annualRate / 100) / 12;

            // Generate system detail text
            const descLabel = document.getElementById('system-info-description');
            if (amortType === 'french') {
                descLabel.textContent = "* Francés: Al inicio de la tabla pagas mayor cantidad de intereses, pero tus cuotas mensuales permanecen idénticas (pago constante).";
            } else if (amortType === 'german') {
                descLabel.textContent = "* Alemán: Tu abono a capital es constante en cada mes, reduciendo los intereses de forma acelerada y disminuyendo la cuota final paulatinamente.";
            } else {
                descLabel.textContent = "* Americano: Solo pagas intereses mensuales fijos. La totalidad del capital prestado se abona al final en la última cuota.";
            }

            // Calculation variables
            let schedule = [];
            let totalPaidBase = 0;
            let totalInterestBase = 0;
            
            // To evaluate savings, we compute the base case first (NO extra payments)
            let baseMetrics = computeBaseSchedule(capital, monthlyRate, totalPeriods, amortType);

            // Compute actual schedule incorporating extra payments
            let balance = capital;
            let currentPeriod = 1;
            let runningInterest = 0;
            let runningPrincipal = 0;
            let totalPaidWithExtras = 0;

            while (balance > 0.01 && currentPeriod <= totalPeriods) {
                let interestForMonth = balance * monthlyRate;
                let principalForMonth = 0;
                let actualExtra = extraMonthly;

                if (currentPeriod === extraOneTimeMonth) {
                    actualExtra += extraOneTime;
                }

                if (amortType === 'french') {
                    // Constant theoretical payment (Capital + Interest)
                    let theoreticalCuota = capital * (monthlyRate * Math.pow(1 + monthlyRate, totalPeriods)) / (Math.pow(1 + monthlyRate, totalPeriods) - 1);
                    principalForMonth = theoreticalCuota - interestForMonth;
                } else if (amortType === 'german') {
                    // Constant Capital portion
                    principalForMonth = capital / totalPeriods;
                } else {
                    // American - Interest only, principal paid at final installment
                    principalForMonth = (currentPeriod === totalPeriods) ? capital : 0;
                }

                // Adjustments to avoid negative balances or overpayment on final month
                if (principalForMonth > balance) {
                    principalForMonth = balance;
                }

                let normalCuota = principalForMonth + interestForMonth;
                
                // Incorporate the extra payments
                let maxPossibleExtra = balance - principalForMonth;
                if (actualExtra > maxPossibleExtra) {
                    actualExtra = maxPossibleExtra;
                }

                let totalSubtotalForPeriod = normalCuota + actualExtra;
                balance = balance - (principalForMonth + actualExtra);

                runningInterest += interestForMonth;
                runningPrincipal += (principalForMonth + actualExtra);
                totalPaidWithExtras += totalSubtotalForPeriod;

                schedule.push({
                    period: currentPeriod,
                    payment: normalCuota,
                    interest: interestForMonth,
                    principal: principalForMonth,
                    extra: actualExtra,
                    remaining: Math.max(0, balance)
                });

                if (balance <= 0.01) {
                    break;
                }
                currentPeriod++;
            }

            // Render KPI indicators
            let averagePayment = schedule.reduce((sum, item) => sum + item.payment, 0) / schedule.length;
            document.getElementById('kpi-monthly-payment').textContent = formatMoney(averagePayment);
            document.getElementById('kpi-total-interest').textContent = formatMoney(runningInterest);
            document.getElementById('kpi-total-paid').textContent = formatMoney(totalPaidWithExtras);

            let percentInterestOfLoan = (runningInterest / capital);
            document.getElementById('kpi-interest-percentage').textContent = `${(percentInterestOfLoan * 100).toFixed(2)}% del préstamo`;

            // Compute Savings (Base total paid minus actual with extras paid)
            let totalSaved = Math.max(0, baseMetrics.totalPaid - totalPaidWithExtras);
            let timeSaved = Math.max(0, baseMetrics.periods - schedule.length);

            document.getElementById('kpi-savings').textContent = formatMoney(totalSaved);
            document.getElementById('kpi-savings-time').textContent = `Meses ahorrados: ${timeSaved}`;

            // Handle Savings card glowing style if savings exist
            const savingsCard = document.getElementById('kpi-savings').parentElement;
            if (totalSaved > 0) {
                savingsCard.className = "bg-emerald-950/20 border-emerald-500/40 p-4 rounded-2xl border glow-emerald relative overflow-hidden transition duration-300";
            } else {
                savingsCard.className = "bg-[#0c0e17] border-emerald-950 rounded-2xl p-4 border relative overflow-hidden transition duration-300";
            }

            // Render Amortization Data Table
            const tbody = document.getElementById('table-body');
            tbody.innerHTML = "";

            schedule.forEach(row => {
                const tr = document.createElement('tr');
                tr.className = "hover:bg-emerald-950/10 transition duration-150";
                tr.innerHTML = `
                    <td class="p-3 text-center text-slate-400 font-bold border-r border-emerald-950/20">${row.period}</td>
                    <td class="p-3 font-semibold">${formatMoney(row.payment + row.extra)}</td>
                    <td class="p-3 text-emerald-400/90">${formatMoney(row.interest)}</td>
                    <td class="p-3 text-slate-300">${formatMoney(row.principal)}</td>
                    <td class="p-3 ${row.extra > 0 ? 'text-emerald-400 font-bold bg-emerald-950/10' : 'text-slate-500'}">${row.extra > 0 ? formatMoney(row.extra) : '-'}</td>
                    <td class="p-3 text-right font-semibold text-slate-200">${formatMoney(row.remaining)}</td>
                `;
                tbody.appendChild(tr);
            });

            // Update Analytical charts (Trajectory + Ratio)
            updateAnalyticalCharts(schedule, capital, runningInterest);
        }

        // Helper function to resolve default loan calculations (no extra payments case)
        function computeBaseSchedule(capital, monthlyRate, totalPeriods, amortType) {
            let balance = capital;
            let totalPaid = 0;
            let totalInterest = 0;
            let periodsCount = 0;

            for (let i = 1; i <= totalPeriods; i++) {
                if (balance <= 0) break;
                let interestForMonth = balance * monthlyRate;
                let principalForMonth = 0;

                if (amortType === 'french') {
                    let theoreticalCuota = capital * (monthlyRate * Math.pow(1 + monthlyRate, totalPeriods)) / (Math.pow(1 + monthlyRate, totalPeriods) - 1);
                    principalForMonth = theoreticalCuota - interestForMonth;
                } else if (amortType === 'german') {
                    principalForMonth = capital / totalPeriods;
                } else {
                    principalForMonth = (i === totalPeriods) ? capital : 0;
                }

                if (principalForMonth > balance) {
                    principalForMonth = balance;
                }

                let currentCuota = principalForMonth + interestForMonth;
                balance -= principalForMonth;
                totalInterest += interestForMonth;
                totalPaid += currentCuota;
                periodsCount++;
            }

            return {
                totalPaid: totalPaid,
                totalInterest: totalInterest,
                periods: periodsCount
            };
        }

        // Render or update Chart.js assets
        function updateAnalyticalCharts(schedule, capital, totalInterest) {
            // Evolution chart datasets
            const labels = schedule.map(row => `M${row.period}`);
            const balances = schedule.map(row => row.remaining);
            
            // 1. Line Trajectory Chart
            if (evolutionChartInst) {
                evolutionChartInst.data.labels = labels;
                evolutionChartInst.data.datasets[0].data = balances;
                evolutionChartInst.update();
            } else {
                const ctxLine = document.getElementById('evolutionChart').getContext('2d');
                evolutionChartInst = new Chart(ctxLine, {
                    type: 'line',
                    data: {
                        labels: labels,
                        datasets: [{
                            label: 'Saldo de Capital',
                            data: balances,
                            borderColor: '#10b981',
                            backgroundColor: 'rgba(16, 185, 129, 0.03)',
                            borderWidth: 2,
                            fill: true,
                            tension: 0.35,
                            pointRadius: 0,
                            pointHoverRadius: 5,
                            pointBackgroundColor: '#10b981',
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: { display: false }
                        },
                        scales: {
                            x: {
                                grid: { color: 'rgba(16, 185, 129, 0.02)' },
                                ticks: { color: '#64748b', font: { family: 'Plus Jakarta Sans', size: 9 } }
                            },
                            y: {
                                grid: { color: 'rgba(16, 185, 129, 0.05)' },
                                ticks: { color: '#64748b', font: { family: 'Plus Jakarta Sans', size: 9 } }
                            }
                        }
                    }
                });
            }

            // 2. Donut Ratio Chart (Capital vs Interest ratio)
            if (ratioChartInst) {
                ratioChartInst.data.datasets[0].data = [capital, totalInterest];
                ratioChartInst.update();
            } else {
                const ctxDonut = document.getElementById('ratioChart').getContext('2d');
                ratioChartInst = new Chart(ctxDonut, {
                    type: 'doughnut',
                    data: {
                        labels: ['Préstamo Principal', 'Intereses Totales'],
                        datasets: [{
                            data: [capital, totalInterest],
                            backgroundColor: ['#0f172a', '#10b981'],
                            borderColor: 'rgba(16, 185, 129, 0.15)',
                            borderWidth: 1.5,
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: {
                                position: 'bottom',
                                labels: {
                                    color: '#cbd5e1',
                                    font: { family: 'Plus Jakarta Sans', size: 10 }
                                }
                            }
                        },
                        cutout: '70%'
                    }
                });
            }
        }

        // Export active Amortization schedule to CSV file
        function exportCSV() {
            let csvContent = "data:text/csv;charset=utf-8,";
            csvContent += "Mes,Cuota Mensual,Interes Pagado,Amortizacion de Capital,Abono Extra,Saldo Restante\n";

            // Extract values directly from schedule rows dynamically
            const tbodyRows = document.querySelectorAll("#table-body tr");
            tbodyRows.forEach(row => {
                const cols = row.querySelectorAll("td");
                const rowData = Array.from(cols).map(col => {
                    // Remove currency formatting characters
                    return col.innerText.replace(/[$,\s]/g, '').replace('-', '0');
                }).join(",");
                csvContent += rowData + "\n";
            });

            // Trigger secure local download anchor
            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", "reporte_amortizacion.csv");
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);

            showCustomToast("Reporte exportado exitosamente como archivo CSV.");
        }
    </script>
</body>
</html>
```
eof