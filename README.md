# LCA_Modul_26<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Life Cycle Assessment (LCA) Interactive Module</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6;
        }
        /* Custom scrollbar for better aesthetics */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; }
        ::-webkit-scrollbar-thumb { background: #888; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #555; }
        
        .fade-in {
            animation: fadeIn 0.5s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        tuGreen: {
                            50: '#f4f8ec',
                            100: '#e5f0d3',
                            500: '#84B819',
                            600: '#699912',
                            700: '#537a0c',
                            800: '#3e5c09',
                        }
                    }
                }
            }
        }
    </script>
</head>
<body class="text-gray-800 antialiased">

    <header class="bg-tuGreen-700 text-white shadow-md sticky top-0 z-50">
        <div class="max-w-6xl mx-auto px-4 py-4 flex flex-col md:flex-row justify-between items-center">
            <div class="flex items-center gap-3">
                <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                <h1 class="text-xl font-bold">LCA Basics</h1>
            </div>
            <div class="text-sm mt-2 md:mt-0 font-medium opacity-90">
                Prof. Dr.-Ing. Daniela Kattwinkel | TU Dortmund
            </div>
        </div>
    </header>

    <main class="max-w-6xl mx-auto px-4 py-8 space-y-12">
        
        <!-- Hero Introduction -->
        <section class="bg-white rounded-2xl shadow-sm p-6 md:p-10 text-center border-t-4 border-tuGreen-500">
            <h2 class="text-3xl md:text-4xl font-bold text-gray-900 mb-4">Basics of Life Cycle Assessment</h2>
            <p class="text-lg text-gray-600 max-w-3xl mx-auto">
                Welcome to the interactive learning module! Based on the recent lecture, this tool will help you understand the four iterative phases of LCA (ISO 14040/14044) and test your knowledge.
            </p>
        </section>

        <!-- Interactive Calculator Section -->
        <section class="bg-white rounded-2xl shadow-sm overflow-hidden flex flex-col md:flex-row">
            <div class="bg-tuGreen-50 p-6 md:p-10 md:w-1/3 flex flex-col justify-center border-r border-tuGreen-100">
                <h3 class="text-2xl font-bold text-tuGreen-800 mb-2">Interactive Impact Calculator</h3>
                <p class="text-gray-600 text-sm mb-6">
                    Adjust the wattage and hours of use to see how the energy efficiency and lifespan of a lightbulb impact kg of CO<sub>2</sub>-Eq. emissions.
                </p>
                <div class="bg-white p-4 rounded-xl shadow-inner border border-gray-100">
                    <p class="text-xs text-gray-500 uppercase font-semibold mb-1">Functional Unit</p>
                    <p class="text-gray-800 font-medium">Providing light over a set time</p>
                </div>
            </div>
            
            <div class="p-6 md:p-10 md:w-2/3">
                <div class="mb-6">
                    <div class="flex justify-between items-end mb-2">
                        <label for="wattage" class="font-semibold text-gray-700">Bulb Wattage</label>
                        <span id="watt-output" class="text-2xl font-bold text-tuGreen-600">8 W</span>
                    </div>
                    <input type="range" id="wattage" min="1" max="100" value="8" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer accent-tuGreen-600">
                    <div class="flex justify-between text-xs text-gray-400 mt-2">
                        <span>1W (Ultra LED)</span>
                        <span>60W (Incandescent)</span>
                        <span>100W</span>
                    </div>
                </div>

                <div class="mb-8">
                    <div class="flex justify-between items-end mb-2">
                        <label for="hours" class="font-semibold text-gray-700">Hours of Usage</label>
                        <span id="hours-output" class="text-2xl font-bold text-tuGreen-600">25,000 h</span>
                    </div>
                    <input type="range" id="hours" min="1000" max="50000" step="1000" value="25000" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer accent-tuGreen-600">
                    <div class="flex justify-between text-xs text-gray-400 mt-2">
                        <span>1,000 h</span>
                        <span>50,000 h</span>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- Energy Consumption Card -->
                    <div class="bg-gray-50 rounded-xl p-5 border border-gray-100 relative overflow-hidden group hover:shadow-md transition-shadow">
                        <div class="absolute top-0 right-0 p-4 opacity-10">
                            <svg class="w-16 h-16" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M11.3 1.046A1 1 0 0112 2v5h4a1 1 0 01.82 1.573l-7 10A1 1 0 018 18v-5H4a1 1 0 01-.82-1.573l7-10a1 1 0 011.12-.381z" clip-rule="evenodd"></path></svg>
                        </div>
                        <h4 class="text-sm font-semibold text-gray-500 uppercase mb-1">Energy Use (over 25k hrs)</h4>
                        <p class="text-3xl font-bold text-gray-800" id="kwh-output">200 <span class="text-lg font-medium text-gray-500">kWh</span></p>
                    </div>

                    <!-- CO2 Emissions Card -->
                    <div class="bg-gray-50 rounded-xl p-5 border border-gray-100 relative overflow-hidden group hover:shadow-md transition-shadow">
                        <div class="absolute top-0 right-0 p-4 opacity-10">
                            <svg class="w-16 h-16" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M3.172 5.172a4 4 0 015.656 0L10 6.343l1.172-1.171a4 4 0 115.656 5.656L10 17.657l-6.828-6.829a4 4 0 010-5.656z" clip-rule="evenodd"></path></svg>
                        </div>
                        <h4 class="text-sm font-semibold text-gray-500 uppercase mb-1">Global Warming Potential</h4>
                        <p class="text-3xl font-bold text-gray-800" id="co2-output">96.80 <span class="text-lg font-medium text-gray-500">kg CO₂-Eq</span></p>
                    </div>
                </div>

                <!-- Bulb Count Info -->
                <div class="mt-6 bg-blue-50 border border-blue-100 p-4 rounded-xl flex items-center gap-4">
                    <svg class="w-8 h-8 text-blue-500 flex-shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"></path></svg>
                    <p class="text-sm text-gray-700" id="bulb-info">You will need <strong>1</strong> bulb(s) for this duration.</p>
                </div>

                <!-- Visual Bar -->
                <div class="mt-6">
                    <p class="text-sm font-medium text-gray-600 mb-2">Total Emissions Relative to Max Potential</p>
                    <div class="w-full bg-gray-200 rounded-full h-4 relative">
                        <div id="co2-bar" class="bg-amber-500 h-4 rounded-full transition-all duration-300 ease-out" style="width: 13.3%"></div>
                    </div>
                </div>
                <p class="text-xs text-gray-400 mt-4 text-center">
                    * Calculation uses grid emission factor ~0.484 kg CO₂e / kWh and includes material/manufacturing footprint from the lecture. Incandescent bulbs assume 1000h lifespan.
                </p>
            </div>
        </section>

        <!-- Quiz Section -->
        <section id="quiz-section" class="bg-white rounded-2xl shadow-sm p-6 md:p-10">
            <div class="text-center mb-8">
                <h3 class="text-3xl font-bold text-gray-900">Knowledge Check</h3>
                <p class="text-gray-600 mt-2">Test your understanding of the LCA Basics lecture.</p>
            </div>

            <!-- Quiz Container -->
            <div id="quiz-container" class="max-w-3xl mx-auto space-y-8">
                <!-- Questions will be injected here via JS -->
            </div>

            <!-- Quiz Results / Submit -->
            <div class="max-w-3xl mx-auto mt-8 pt-8 border-t border-gray-100 text-center">
                <button id="submit-quiz" class="bg-tuGreen-600 hover:bg-tuGreen-700 text-white font-bold py-3 px-8 rounded-full shadow-lg transition-transform transform hover:scale-105">
                    Submit Answers
                </button>
                <div id="quiz-results" class="hidden mt-6 p-4 rounded-xl font-medium text-lg fade-in">
                    <!-- Results injected here -->
                </div>
            </div>
        </section>

    </main>

    <footer class="bg-gray-800 text-gray-400 py-8 text-center text-sm mt-12">
        <p>&copy; 2026 Life Cycle Assessment Interactive Module.</p>
        <p class="mt-1">Based on "Basics of Life Cycle Assessment of technical products" by Prof. Dr.-Ing. Daniela Kattwinkel.</p>
    </footer>

    <script>
        // --- Calculator Logic ---
        const wattageInput = document.getElementById('wattage');
        const hoursInput = document.getElementById('hours');
        const wattOutput = document.getElementById('watt-output');
        const hoursOutput = document.getElementById('hours-output');
        const kwhOutput = document.getElementById('kwh-output');
        const co2Output = document.getElementById('co2-output');
        const co2Bar = document.getElementById('co2-bar');
        const bulbInfo = document.getElementById('bulb-info');

        const EMISSION_FACTOR = 0.48396; 
        const MAX_CO2_REFERENCE = 2500; // Updated max scale for visualization

        function updateCalculator() {
            const watts = parseInt(wattageInput.value);
            const hours = parseInt(hoursInput.value);
            
            wattOutput.textContent = `${watts} W`;
            hoursOutput.textContent = `${hours.toLocaleString()} h`;

            // Calculate kWh ( W * h / 1000 )
            const kwh = (watts * hours) / 1000;
            kwhOutput.innerHTML = `${kwh.toFixed(0)} <span class="text-lg font-medium text-gray-500">kWh</span>`;

            // Logic from lecture: > 15W usually assumed Incandescent (1000h), else LED (50000h)
            const isIncandescent = watts > 15;
            const lifespan = isIncandescent ? 1000 : 50000;
            const bulbsNeeded = Math.ceil(hours / lifespan);
            
            // Material + EoL CO2 per bulb (from lecture: Incandescent = (6.69+0.03)/25 = 0.2688 kg, LED = 8.04+0.01 = 8.05 kg)
            const footprintPerBulb = isIncandescent ? 0.2688 : 8.05;
            const manufacturingEoL_CO2 = bulbsNeeded * footprintPerBulb;
            
            // Use phase CO2
            const usePhaseCO2 = kwh * EMISSION_FACTOR;
            
            const totalCO2 = usePhaseCO2 + manufacturingEoL_CO2;

            co2Output.innerHTML = `${totalCO2.toFixed(2)} <span class="text-lg font-medium text-gray-500">kg CO₂-Eq</span>`;
            
            // Update Info
            bulbInfo.innerHTML = `You will need <strong>${bulbsNeeded}</strong> bulb(s) for this duration. (Assumes ${lifespan}h lifespan for ${watts}W bulb).`;

            // Update bar width (capped at 100%)
            const percentage = Math.min((totalCO2 / MAX_CO2_REFERENCE) * 100, 100);
            co2Bar.style.width = `${percentage}%`;

            // Change color based on efficiency
            if (percentage < 20) {
                co2Bar.className = 'bg-tuGreen-500 h-4 rounded-full transition-all duration-300 ease-out';
            } else if (percentage < 60) {
                co2Bar.className = 'bg-yellow-500 h-4 rounded-full transition-all duration-300 ease-out';
            } else {
                co2Bar.className = 'bg-red-500 h-4 rounded-full transition-all duration-300 ease-out';
            }
        }

        wattageInput.addEventListener('input', updateCalculator);
        hoursInput.addEventListener('input', updateCalculator);
        // Initialize
        updateCalculator();

        // --- STREAMING_CHUNK: JavaScript for the Quiz logic ---
        // --- Quiz Logic ---
        const questions = [
            {
                question: "What does the abbreviation 'LCA' stand for?",
                options: [
                    "Low Carbon Analysis",
                    "Life Cycle Assessment",
                    "Long-term Climate Action",
                    "Linear Consumption Assessment"
                ],
                correctAnswer: 1,
                hint: "It looks at the entire span of a product's life from raw material to disposal."
            },
            {
                question: "What are the four iterative phases of an LCA?",
                options: [
                    "Planning, Execution, Review, Reporting",
                    "Goal and scope, Inventory (LCI), Impact assessment (LCIA), Interpretation",
                    "Design, Manufacturing, Use phase, Recycling",
                    "Classification, Characterisation, Normalisation, Weighting"
                ],
                correctAnswer: 1,
                hint: "Think about the ISO 14040/14044 framework which starts with defining the goal."
            },
            {
                question: "In the 'Goal and Scope' phase, what is the purpose of defining a 'Functional Unit'?",
                options: [
                    "To determine the monetary cost of a product",
                    "To make product systems comparable (e.g., providing 25,000 h of light)",
                    "To calculate the total weight of the product",
                    "To list all the raw materials used"
                ],
                correctAnswer: 1,
                hint: "It provides a clear reference point so you can compare apples to apples (or LED to Incandescent)."
            },
            {
                question: "What happens during the 'Characterisation' step in the Impact Assessment (LCIA) phase?",
                options: [
                    "Data is collected from manufacturing plants",
                    "The system boundaries are defined",
                    "Different inventory flows (like CH₄) are converted into one common indicator (like kg CO₂e)",
                    "The final report is written for stakeholders"
                ],
                correctAnswer: 2,
                hint: "We use characterisation factors to translate various emissions into a shared unit."
            },
            {
                question: "In the lecture's comparison of LED vs. Incandescent bulbs, which life cycle phase dominated the CO₂-Eq emissions for BOTH bulbs?",
                options: [
                    "Material and Manufacturing",
                    "Transport",
                    "Use Phase",
                    "End-of-Life"
                ],
                correctAnswer: 2,
                hint: "Look at the orange bars in the slide's bar chart - they tower over the others!"
            },
            {
                question: "Why might the famous 'Centennial Light Bulb' (running since 1901) NOT be the most sustainable light bulb?",
                options: [
                    "Because it is made of toxic materials.",
                    "Because its energy consumption during its extremely long use phase far outweighs the emissions saved by not manufacturing replacements.",
                    "Because it requires constant maintenance and repair.",
                    "Because it doesn't emit enough light to be measured."
                ],
                correctAnswer: 1,
                hint: "Efficiency matters! An old bulb uses vastly more electricity per hour than modern ones."
            }
        ];

        const quizContainer = document.getElementById('quiz-container');
        const submitBtn = document.getElementById('submit-quiz');
        const resultsDiv = document.getElementById('quiz-results');

        // Render Questions
        questions.forEach((q, index) => {
            const questionCard = document.createElement('div');
            questionCard.className = 'bg-gray-50 border border-gray-100 p-6 rounded-xl relative';
            questionCard.id = `question-${index}`;
            
            const questionHeader = document.createElement('div');
            questionHeader.className = 'flex justify-between items-start mb-4 gap-4';
            
            const questionTitle = document.createElement('h4');
            questionTitle.className = 'font-bold text-lg text-gray-800';
            questionTitle.innerHTML = `<span class="text-tuGreen-600 mr-2">Q${index + 1}.</span> ${q.question}`;
            
            const hintContainer = document.createElement('div');
            hintContainer.className = 'relative group';
            
            const hintIcon = document.createElement('div');
            hintIcon.className = 'cursor-pointer text-amber-400 hover:text-amber-500 transition-colors p-1';
            hintIcon.innerHTML = `<svg class="w-7 h-7" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path d="M11 3a1 1 0 10-2 0v1a1 1 0 102 0V3zM15.657 5.757a1 1 0 00-1.414-1.414l-.707.707a1 1 0 001.414 1.414l.707-.707zM18 10a1 1 0 01-1 1h-1a1 1 0 110-2h1a1 1 0 011 1zM5.05 6.464A1 1 0 106.464 5.05l-.707-.707a1 1 0 00-1.414 1.414l.707.707zM5 10a1 1 0 01-1 1H3a1 1 0 110-2h1a1 1 0 011 1zM8 16v-1h4v1a2 2 0 11-4 0zM12 14c.015-.34.208-.646.477-.859a4 4 0 10-4.954 0c.27.213.462.519.476.859h4z"></path></svg>`;
            
            const hintTooltip = document.createElement('div');
            hintTooltip.className = 'absolute right-0 top-full mt-2 w-56 bg-gray-800 text-white text-xs rounded-lg p-3 opacity-0 group-hover:opacity-100 pointer-events-none transition-opacity z-10 shadow-lg';
            hintTooltip.textContent = "Hint: " + q.hint;

            hintContainer.appendChild(hintIcon);
            hintContainer.appendChild(hintTooltip);
            
            questionHeader.appendChild(questionTitle);
            questionHeader.appendChild(hintContainer);
            questionCard.appendChild(questionHeader);

            const optionsGrid = document.createElement('div');
            optionsGrid.className = 'grid grid-cols-1 md:grid-cols-2 gap-3';

            q.options.forEach((opt, optIndex) => {
                const label = document.createElement('label');
                label.className = 'flex items-start p-3 bg-white border border-gray-200 rounded-lg cursor-pointer hover:bg-gray-50 transition-colors option-label';
                
                const input = document.createElement('input');
                input.type = 'radio';
                input.name = `q${index}`;
                input.value = optIndex;
                input.className = 'mt-1 mr-3 w-4 h-4 text-tuGreen-600 focus:ring-tuGreen-500 border-gray-300';
                
                const span = document.createElement('span');
                span.className = 'text-gray-700 text-sm';
                span.textContent = opt;

                label.appendChild(input);
                label.appendChild(span);
                optionsGrid.appendChild(label);
            });

            questionCard.appendChild(optionsGrid);
            
            // Add feedback container
            const feedback = document.createElement('div');
            feedback.id = `feedback-${index}`;
            feedback.className = 'hidden mt-4 text-sm font-medium p-3 rounded-lg';
            questionCard.appendChild(feedback);

            quizContainer.appendChild(questionCard);
        });

        // Handle Submission
        submitBtn.addEventListener('click', () => {
            let score = 0;
            let allAnswered = true;

            questions.forEach((q, index) => {
                const selected = document.querySelector(`input[name="q${index}"]:checked`);
                const feedbackDiv = document.getElementById(`feedback-${index}`);
                const questionCard = document.getElementById(`question-${index}`);
                
                if (!selected) {
                    allAnswered = false;
                    questionCard.classList.add('border-red-300');
                    return;
                } else {
                    questionCard.classList.remove('border-red-300');
                }

                const answerVal = parseInt(selected.value);
                feedbackDiv.classList.remove('hidden');

                // Disable inputs after submit
                const inputs = document.querySelectorAll(`input[name="q${index}"]`);
                inputs.forEach(inp => inp.disabled = true);

                if (answerVal === q.correctAnswer) {
                    score++;
                    feedbackDiv.className = 'mt-4 text-sm font-medium p-3 rounded-lg bg-green-100 text-green-800 fade-in';
                    feedbackDiv.innerHTML = `✓ Correct!`;
                } else {
                    feedbackDiv.className = 'mt-4 text-sm font-medium p-3 rounded-lg bg-red-100 text-red-800 fade-in';
                    feedbackDiv.innerHTML = `✗ Incorrect. The correct answer is: <strong>${q.options[q.correctAnswer]}</strong>`;
                }
            });

            if (!allAnswered) {
                // We show an inline message instead of alert()
                resultsDiv.classList.remove('hidden', 'bg-green-100', 'text-green-800');
                resultsDiv.classList.add('bg-amber-100', 'text-amber-800');
                resultsDiv.textContent = 'Please answer all questions before submitting.';
                return;
            }

            // Hide submit button
            submitBtn.style.display = 'none';

            // Show results
            resultsDiv.classList.remove('hidden', 'bg-amber-100', 'text-amber-800');
            
            const percentage = (score / questions.length) * 100;
            if (percentage >= 80) {
                resultsDiv.classList.add('bg-green-100', 'text-green-800');
            } else if (percentage >= 50) {
                resultsDiv.classList.add('bg-yellow-100', 'text-yellow-800');
            } else {
                resultsDiv.classList.add('bg-gray-200', 'text-gray-800');
            }
            
            resultsDiv.innerHTML = `Quiz Completed! You scored <strong>${score} out of ${questions.length}</strong> (${percentage}%).`;
        });
    </script>
</body>
</html>
