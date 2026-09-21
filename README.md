# Game-coding-Ai<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI & Coding Quiz Master - 15 Tantangan Profesional</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-in {
            animation: fadeIn 0.4s ease-out forwards;
        }
        /* Custom scrollbar untuk review list */
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: rgba(15, 23, 42, 0.6);
            border-radius: 4px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: rgba(99, 102, 241, 0.5);
            border-radius: 4px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover {
            background: rgba(99, 102, 241, 0.8);
        }
    </style>
</head>
<body class="bg-gradient-to-br from-slate-950 via-indigo-950 to-slate-900 min-h-screen text-slate-100 flex flex-col items-center justify-center p-4">

    <div class="w-full max-w-2xl bg-slate-900/90 backdrop-blur-xl rounded-2xl shadow-2xl border border-indigo-500/20 overflow-hidden">
        
        <!-- Header -->
        <header class="bg-slate-900/80 p-5 sm:p-6 border-b border-indigo-500/20 flex justify-between items-center">
            <div class="flex items-center space-x-3">
                <span class="text-3xl">🤖</span>
                <div>
                    <h1 class="text-lg sm:text-xl font-bold tracking-wide text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-indigo-400 to-pink-400">AI & Coding Quiz</h1>
                    <p class="text-xs text-slate-400">15 Tantangan Teknologi & Pemrograman</p>
                </div>
            </div>
            <div id="quiz-header-stats" class="hidden flex items-center space-x-3 text-sm font-medium">
                <div class="bg-slate-800/80 px-3 py-1.5 rounded-lg border border-slate-700/80 flex items-center space-x-1.5 shadow-sm">
                    <span class="text-cyan-400">⏱️</span>
                    <span id="timer-display" class="font-bold text-cyan-200">25s</span>
                </div>
                <div class="bg-slate-800/80 px-3 py-1.5 rounded-lg border border-slate-700/80 shadow-sm">
                    Skor: <span id="score-display" class="text-emerald-400 font-bold">0</span>
                </div>
            </div>
        </header>

        <!-- Main Content Area -->
        <main class="p-6 sm:p-8">

            <!-- SCREEN 1: Setup / Home -->
            <section id="screen-setup" class="space-y-6 animate-fade-in">
                <div>
                    <h2 class="text-2xl font-bold text-slate-100 mb-1">Uji Keahlian AI & Coding Kamu!</h2>
                    <p class="text-slate-400 text-sm">Kuis interaktif ini dirancang khusus untuk menguji wawasanmu seputar Artificial Intelligence, Machine Learning, algoritma, serta konsep dasar hingga lanjutan pemrograman.</p>
                </div>

                <div class="bg-cyan-950/30 border border-cyan-500/30 p-4 rounded-xl space-y-2 text-sm text-cyan-200">
                    <div class="font-semibold flex items-center space-x-2">
                        <span>⚡</span>
                        <span>Ketentuan Kuis:</span>
                    </div>
                    <ul class="list-disc list-inside space-y-1 text-slate-300 text-xs sm:text-sm pl-1">
                        <li>Total 15 pertanyaan pilihan ganda berkualitas tinggi.</li>
                        <li>Durasi 25 detik per pertanyaan.</li>
                        <li>Setiap jawaban benar bernilai +10 poin.</li>
                        <li>Disertai pembahasan mendalam serta rekap hasil lengkap di akhir.</li>
                    </ul>
                </div>

                <button onclick="startQuiz()" class="w-full py-4 px-4 bg-gradient-to-r from-cyan-500 via-indigo-600 to-purple-600 hover:opacity-95 text-white font-semibold rounded-xl shadow-xl transition transform active:scale-95 flex items-center justify-center space-x-2 text-base">
                    <span>Mulai Kuis Sekarang</span>
                    <span>🚀</span>
                </button>
            </section>

            <!-- SCREEN 2: Quiz Active -->
            <section id="screen-quiz" class="hidden space-y-6 animate-fade-in">
                <div class="flex justify-between items-center text-xs font-semibold text-slate-400 uppercase tracking-wider">
                    <span id="question-progress">Pertanyaan 1 dari 15</span>
                    <span class="bg-cyan-500/15 text-cyan-300 px-2.5 py-1 rounded-full border border-cyan-500/30">AI & Programming</span>
                </div>

                <!-- Progress Bar -->
                <div class="w-full bg-slate-800 h-2.5 rounded-full overflow-hidden shadow-inner">
                    <div id="progress-bar-fill" class="bg-gradient-to-r from-cyan-400 to-indigo-500 h-full w-0 transition-all duration-300"></div>
                </div>

                <h3 id="question-text" class="text-lg sm:text-xl font-semibold text-slate-100 leading-relaxed min-h-[60px]">
                    Pertanyaan akan muncul di sini...
                </h3>

                <!-- Options -->
                <div id="options-container" class="space-y-3">
                    <!-- Dinamis dimasukkan oleh JS -->
                </div>

                <div id="feedback-container" class="hidden p-4 rounded-xl text-sm animate-fade-in space-y-2">
                    <!-- Feedback jawaban benar/salah & penjelasan -->
                </div>

                <div class="flex justify-end pt-2">
                    <button id="next-btn" onclick="nextQuestion()" class="hidden py-3 px-6 bg-indigo-600 hover:bg-indigo-500 text-white font-medium rounded-xl transition shadow-lg active:scale-95 flex items-center space-x-2">
                        <span>Lanjut Soal</span>
                        <span>➡️</span>
                    </button>
                </div>
            </section>

            <!-- SCREEN 3: Result & Review Summary -->
            <section id="screen-result" class="hidden space-y-6 animate-fade-in text-center">
                <div class="inline-flex p-4 bg-indigo-600/20 border border-indigo-500/30 rounded-full text-4xl mb-1 shadow-lg">
                    🏆
                </div>
                <div>
                    <h2 class="text-2xl font-bold text-slate-100">Kuis Selesai!</h2>
                    <p class="text-slate-400 text-sm mt-1">Berikut adalah laporan performa kamu dalam dunia AI dan Coding.</p>
                </div>

                <div class="bg-slate-900/80 p-6 rounded-2xl border border-slate-800 flex justify-around items-center shadow-inner">
                    <div>
                        <div class="text-3xl font-extrabold text-cyan-400" id="final-score">0</div>
                        <div class="text-xs text-slate-400 mt-1 uppercase tracking-wider font-semibold">Skor Akhir</div>
                    </div>
                    <div class="h-10 w-px bg-slate-800"></div>
                    <div>
                        <div class="text-3xl font-extrabold text-indigo-400" id="final-correct">0/15</div>
                        <div class="text-xs text-slate-400 mt-1 uppercase tracking-wider font-semibold">Jawaban Benar</div>
                    </div>
                </div>

                <div class="space-y-3 text-left">
                    <h4 class="text-sm font-semibold text-slate-300 uppercase tracking-wider">Review 15 Pertanyaan & Pembahasan:</h4>
                    <div id="review-list" class="space-y-3 max-h-72 overflow-y-auto pr-2 custom-scrollbar">
                        <!-- Dinamis dimasukkan oleh JS -->
                    </div>
                </div>

                <button onclick="restartQuiz()" class="w-full py-3.5 px-4 bg-gradient-to-r from-cyan-500 via-indigo-600 to-purple-600 hover:opacity-95 text-white font-semibold rounded-xl shadow-xl transition transform active:scale-95">
                    🔄 Mainkan Ulang Kuis
                </button>
            </section>

        </main>
    </div>

    <script>
        // Database 15 Soal AI dan Coding Beserta Pembahasan
        const aiCodingQuizData = [
            {
                q: "Apa nama cabang ilmu Artificial Intelligence yang memungkinkan komputer belajar dari data tanpa diprogram secara eksplisit?",
                options: ["Deep Learning", "Machine Learning", "Quantum Computing", "Natural Language Processing"],
                answer: 1,
                explanation: "Machine Learning adalah subset dari AI yang berfokus pada pengembangan algoritma agar sistem dapat belajar dari data."
            },
            {
                q: "Dalam pemrograman, apa fungsi utama dari struktur data 'Stack'?",
                options: ["First In, First Out (FIFO)", "Last In, First Out (LIFO)", "Random Access", "Key-Value Pairing"],
                answer: 1,
                explanation: "Stack menggunakan prinsip LIFO (Last In, First Out), di mana elemen terakhir yang dimasukkan akan menjadi yang pertama keluar."
            },
            {
                q: "Model bahasa besar (LLM) seperti ChatGPT didasarkan pada arsitektur jaringan saraf tiruan yang disebut...",
                options: ["Convolutional Neural Network (CNN)", "Recurrent Neural Network (RNN)", "Transformer", "Perceptron"],
                answer: 2,
                explanation: "Arsitektur Transformer yang diperkenalkan pada tahun 2017 menjadi fondasi utama bagi sebagian besar model LLM modern."
            },
            {
                q: "Manakah dari bahasa pemrograman berikut yang paling dominan digunakan dalam pengembangan Data Science dan AI?",
                options: ["Java", "Python", "C++", "HTML"],
                answer: 1,
                explanation: "Python sangat mendominasi AI & Data Science karena ekosistem pustakanya yang kaya seperti TensorFlow, PyTorch, dan Pandas."
            },
            {
                q: "Apa yang dimaksud dengan 'Overfitting' dalam konteks Machine Learning?",
                options: ["Model terlalu sederhana sehingga gagal mengenali pola data", "Model menghafal data pelatihan terlalu baik sehingga buruk pada data baru", "Proses pelatihan berjalan terlalu lambat", "Kekurangan jumlah data latih"],
                answer: 1,
                explanation: "Overfitting terjadi ketika model Machine Learning terlalu menyesuaikan diri dengan data latih, termasuk noise di dalamnya, sehingga generalisasinya buruk."
            },
            {
                q: "Di dalam pemrogaman web, bahasa apa yang berjalan di sisi browser (client-side) untuk membuat halaman menjadi interaktif?",
                options: ["Python", "PHP", "JavaScript", "SQL"],
                answer: 2,
                explanation: "JavaScript adalah bahasa utama standar web yang dieksekusi di sisi klien (browser) untuk interaktivitas."
            },
            {
                q: "Apa kepanjangan dari singkatan NLP dalam bidang Artificial Intelligence?",
                options: ["Natural Logic Programming", "Neural Language Process", "Natural Language Processing", "Network Layer Protocol"],
                answer: 2,
                explanation: "NLP (Natural Language Processing) adalah cabang AI yang berfokus pada interaksi antara komputer dan bahasa manusia."
            },
            {
                q: "Manakah struktur kontrol perulangan (looping) yang umumnya digunakan ketika jumlah iterasi belum diketahui pasti di awal?",
                options: ["for loop", "while loop", "foreach loop", "range loop"],
                answer: 1,
                explanation: "'While loop' mengeksekusi blok kode selama kondisi tertentu bernilai benar, cocok untuk perulangan dengan batas dinamis."
            },
            {
                q: "Apa fungsi utama dari version control system seperti Git?",
                options: ["Mengompilasi kode program agar berjalan lebih cepat", "Melacak perubahan kode dan memfasilitasi kolaborasi tim pengembang", "Mendeteksi virus pada direktori proyek", "Menghapus file cache otomatis"],
                answer: 1,
                explanation: "Git membantu pengembang melacak riwayat perubahan source code serta mempermudah kerja tim secara kolaboratif."
            },
            {
                q: "Apa perbedaan utama antara supervised learning dan unsupervised learning?",
                options: ["Supervised menggunakan data berlabel, unsupervised menggunakan data tidak berlabel", "Supervised lebih lambat daripada unsupervised", "Supervised hanya untuk gambar, unsupervised untuk teks", "Tidak ada perbedaan mendasar"],
                answer: 0,
                explanation: "Supervised learning dilatih menggunakan dataset yang memiliki label jawaban, sedangkan unsupervised mencari pola tersembunyi pada data tanpa label."
            },
            {
                q: "Di dalam pemrograman berorientasi objek (OOP), pilar yang menyembunyikan detail implementasi internal dari suatu objek disebut...",
                options: ["Inheritance", "Polymorphism", "Encapsulation", "Abstraction"],
                answer: 2,
                explanation: "Encapsulation (enkapsulasi) membungkus data dan metode dalam satu unit serta membatasi akses langsung dari luar."
            },
            {
                q: "Apa istilah untuk teknik di mana AI menghasilkan teks, gambar, atau media baru berdasarkan prompt pengguna?",
                options: ["Analytical AI", "Generative AI", "Predictive AI", "Descriptive AI"],
                answer: 1,
                explanation: "Generative AI merujuk pada sistem kecerdasan buatan yang mampu membuat konten baru yang menyerupai buatan manusia."
            },
            {
                q: "Kompleksitas waktu (Time Complexity) dari algoritma Binary Search pada array yang terurut dinyatakan sebagai...",
                options: ["O(n)", "O(n^2)", "O(log n)", "O(1)"],
                answer: 2,
                explanation: "Binary Search membagi ruang pencarian menjadi separuh pada setiap langkahnya, sehingga kompleksitas waktunya adalah O(log n)."
            },
            {
                q: "Apa kegunaan utama dari fungsi 'API' (Application Programming Interface)?",
                options: ["Menyimpan database di cloud", "Menghubungkan dan memungkinkan komunikasi antar perangkat lunak yang berbeda", "Mengamankan jaringan dari serangan DDoS", "Mendesain antarmuka pengguna grafis (GUI)"],
                answer: 1,
                explanation: "API berfungsi sebagai jembatan bagi berbagai aplikasi atau sistem yang berbeda untuk saling bertukar data dan fungsionalitas."
            },
            {
                q: "Algoritma pencarian jalur terpendek dalam graf yang sangat populer digunakan pada peta digital adalah...",
                options: ["Bubble Sort", "Dijkstra's Algorithm", "K-Means Clustering", "Linear Regression"],
                answer: 1,
                explanation: "Algoritma Dijkstra digunakan untuk menemukan jalur terpendek dari satu titik awal ke semua titik lainnya dalam sebuah graf berbobot."
            }
        ];

        // State Variabel Game
        let currentQuestions = [];
        let currentIndex = 0;
        let score = 0;
        let correctCount = 0;
        let timer = null;
        let timeLeft = 25;
        let userAnswersHistory = [];
        let isAnswerLocked = false;

        function startQuiz() {
            currentQuestions = [...aiCodingQuizData];
            currentIndex = 0;
            score = 0;
            correctCount = 0;
            userAnswersHistory = [];

            document.getElementById('screen-setup').classList.add('hidden');
            document.getElementById('screen-result').classList.add('hidden');
            document.getElementById('screen-quiz').classList.remove('hidden');
            document.getElementById('quiz-header-stats').classList.remove('hidden');
            document.getElementById('score-display').innerText = score;

            loadQuestion();
        }

        function loadQuestion() {
            if (currentIndex >= currentQuestions.length) {
                endQuiz();
                return;
            }

            isAnswerLocked = false;
            clearInterval(timer);
            timeLeft = 25;
            document.getElementById('timer-display').innerText = timeLeft + 's';
            startTimer();

            const qObj = currentQuestions[currentIndex];
            document.getElementById('question-progress').innerText = `Pertanyaan ${currentIndex + 1} dari ${currentQuestions.length}`;
            
            // Update Progress Bar
            const progressPercent = ((currentIndex) / currentQuestions.length) * 100;
            document.getElementById('progress-bar-fill').style.width = progressPercent + '%';

            document.getElementById('question-text').innerText = qObj.q;

            const optionsContainer = document.getElementById('options-container');
            optionsContainer.innerHTML = '';

            qObj.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.className = "w-full p-4 rounded-xl border border-slate-800 bg-slate-900/80 hover:bg-slate-800/80 text-left font-medium transition flex items-center justify-between group active:scale-[0.99] shadow-sm";
                btn.innerHTML = `
                    <span class="flex items-center space-x-3">
                        <span class="w-7 h-7 rounded-lg bg-slate-800 border border-slate-700 flex items-center justify-center text-xs font-bold text-slate-300 group-hover:bg-cyan-600 group-hover:border-cyan-500 group-hover:text-white transition">${String.fromCharCode(65 + idx)}</span>
                        <span class="text-sm sm:text-base">${opt}</span>
                    </span>
                `;
                btn.onclick = () => selectAnswer(idx);
                optionsContainer.appendChild(btn);
            });

            document.getElementById('feedback-container').classList.add('hidden');
            document.getElementById('next-btn').classList.add('hidden');
        }

        function startTimer() {
            timer = setInterval(() => {
                timeLeft--;
                document.getElementById('timer-display').innerText = timeLeft + 's';
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    handleTimeOut();
                }
            }, 1000);
        }

        function handleTimeOut() {
            if (isAnswerLocked) return;
            isAnswerLocked = true;
            clearInterval(timer);

            const qObj = currentQuestions[currentIndex];
            userAnswersHistory.push({
                question: qObj.q,
                selected: -1,
                correct: qObj.answer,
                options: qObj.options,
                explanation: qObj.explanation
            });

            const buttons = document.getElementById('options-container').children;
            buttons[qObj.answer].className = "w-full p-4 rounded-xl border border-emerald-500/80 bg-emerald-950/40 text-left font-medium flex items-center justify-between shadow-md";

            showFeedback(false, "Waktu habis! Kamu tidak sempat memilih jawaban.", qObj.explanation);
        }

        function selectAnswer(selectedIndex) {
            if (isAnswerLocked) return;
            isAnswerLocked = true;
            clearInterval(timer);

            const qObj = currentQuestions[currentIndex];
            const isCorrect = selectedIndex === qObj.answer;
            const buttons = document.getElementById('options-container').children;

            if (isCorrect) {
                score += 10;
                correctCount++;
                document.getElementById('score-display').innerText = score;
                buttons[selectedIndex].className = "w-full p-4 rounded-xl border border-emerald-500/80 bg-emerald-950/50 text-left font-medium flex items-center justify-between transition shadow-md";
                showFeedback(true, "Luar biasa! Jawaban kamu benar! 🎉", qObj.explanation);
            } else {
                buttons[selectedIndex].className = "w-full p-4 rounded-xl border border-rose-500/80 bg-rose-950/50 text-left font-medium flex items-center justify-between transition shadow-md";
                buttons[qObj.answer].className = "w-full p-4 rounded-xl border border-emerald-500/80 bg-emerald-950/50 text-left font-medium flex items-center justify-between transition shadow-md";
                showFeedback(false, `Kurang tepat. Jawaban yang benar adalah: ${qObj.options[qObj.answer]}`, qObj.explanation);
            }

            userAnswersHistory.push({
                question: qObj.q,
                selected: selectedIndex,
                correct: qObj.answer,
                options: qObj.options,
                explanation: qObj.explanation
            });
        }

        function showFeedback(isCorrect, message, explanation) {
            const feedbackEl = document.getElementById('feedback-container');
            feedbackEl.classList.remove('hidden');
            if (isCorrect) {
                feedbackEl.className = "p-4 rounded-xl text-sm bg-emerald-950/80 border border-emerald-500/40 text-emerald-200 animate-fade-in shadow-inner space-y-1.5";
            } else {
                feedbackEl.className = "p-4 rounded-xl text-sm bg-rose-950/80 border border-rose-500/40 text-rose-200 animate-fade-in shadow-inner space-y-1.5";
            }
            feedbackEl.innerHTML = `
                <div class="font-semibold">${message}</div>
                <div class="text-xs opacity-90 text-slate-300">💡 <strong>Pembahasan:</strong> ${explanation}</div>
            `;
            document.getElementById('next-btn').classList.remove('hidden');
        }

        function nextQuestion() {
            currentIndex++;
            loadQuestion();
        }

        function endQuiz() {
            clearInterval(timer);
            document.getElementById('screen-quiz').classList.add('hidden');
            document.getElementById('quiz-header-stats').classList.add('hidden');
            document.getElementById('screen-result').classList.remove('hidden');

            document.getElementById('final-score').innerText = score;
            document.getElementById('final-correct').innerText = `${correctCount}/${currentQuestions.length}`;

            const reviewList = document.getElementById('review-list');
            reviewList.innerHTML = '';

            userAnswersHistory.forEach((item, index) => {
                const isCorrect = item.selected === item.correct;
                const card = document.createElement('div');
                card.className = `p-3.5 rounded-xl border text-xs sm:text-sm ${isCorrect ? 'bg-emerald-950/20 border-emerald-500/30' : 'bg-rose-950/20 border-rose-500/30'}`;
                
                let selectedText = item.selected >= 0 ? item.options[item.selected] : "Tidak dijawab";
                let correctText = item.options[item.correct];

                card.innerHTML = `
                    <div class="font-semibold text-slate-200 mb-1">P.${index + 1} - ${item.question}</div>
                    <div class="space-y-1 mt-2 text-slate-400">
                        <div>Jawabanmu: <span class="${isCorrect ? 'text-emerald-400 font-medium' : 'text-rose-400 font-medium'}">${selectedText}</span></div>
                        ${!isCorrect ? `<div>Jawaban Benar: <span class="text-emerald-400 font-medium">${correctText}</span></div>` : ''}
                        <div class="text-slate-300 text-xs italic mt-1">💡 ${item.explanation}</div>
                    </div>
                `;
                reviewList.appendChild(card);
            });
        }

        function restartQuiz() {
            document.getElementById('screen-result').classList.add('hidden');
            document.getElementById('screen-setup').classList.remove('hidden');
        }
    </script>
</body>
</html>
