<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Acid-Base Chemistry Learning Platform</title>
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #2ecc71;
            --warning: #f39c12;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 2rem 0;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        .topics-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }
        
        .topic-card {
            background: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
            border-left: 4px solid var(--secondary);
        }
        
        .topic-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
        }
        
        .topic-card h3 {
            color: var(--primary);
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
        }
        
        .topic-card h3 i {
            margin-right: 0.5rem;
            color: var(--secondary);
        }
        
        .topic-card p {
            color: #666;
            font-size: 0.9rem;
        }
        
        .content-section {
            background: white;
            border-radius: 8px;
            padding: 2rem;
            margin-top: 2rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            display: none;
        }
        
        .active-section {
            display: block;
        }
        
        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid #eee;
        }
        
        .section-header h2 {
            color: var(--primary);
        }
        
        .back-btn {
            background: var(--light);
            color: var(--dark);
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            display: flex;
            align-items: center;
            transition: background 0.3s ease;
        }
        
        .back-btn:hover {
            background: #dfe6e9;
        }
        
        .theory-content {
            margin-bottom: 2rem;
        }
        
        .practice-problems {
            background: #f8f9fa;
            border-radius: 8px;
            padding: 1.5rem;
            margin-top: 2rem;
        }
        
        .problem {
            margin-bottom: 2rem;
            padding-bottom: 1.5rem;
            border-bottom: 1px dashed #ddd;
        }
        
        .problem:last-child {
            border-bottom: none;
        }
        
        .problem h4 {
            color: var(--primary);
            margin-bottom: 1rem;
        }
        
        .options {
            margin: 1rem 0;
        }
        
        .option {
            margin-bottom: 0.5rem;
        }
        
        .option input {
            margin-right: 0.5rem;
        }
        
        .submit-btn {
            background: var(--secondary);
            color: white;
            border: none;
            padding: 0.7rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s ease;
        }
        
        .submit-btn:hover {
            background: #2980b9;
        }
        
        .result {
            margin-top: 1rem;
            padding: 1rem;
            border-radius: 4px;
            display: none;
        }
        
        .correct {
            background: #d5f4e6;
            color: #27ae60;
            border-left: 4px solid var(--success);
        }
        
        .incorrect {
            background: #fdeaea;
            color: #e74c3c;
            border-left: 4px solid var(--accent);
        }
        
        .explanation {
            margin-top: 0.5rem;
            font-size: 0.9rem;
        }
        
        footer {
            background: var(--dark);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }
        
        .formula {
            background: #f8f9fa;
            padding: 1rem;
            border-radius: 4px;
            margin: 1rem 0;
            font-family: 'Courier New', monospace;
            border-left: 4px solid var(--secondary);
        }
        
        .example {
            background: #e8f4fc;
            padding: 1rem;
            border-radius: 4px;
            margin: 1rem 0;
            border-left: 4px solid var(--secondary);
        }
        
        .nav-buttons {
            display: flex;
            justify-content: space-between;
            margin-top: 2rem;
        }
        
        .nav-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 0.7rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s ease;
        }
        
        .nav-btn:hover {
            background: #1a252f;
        }
        
        .nav-btn:disabled {
            background: #95a5a6;
            cursor: not-allowed;
        }
        
        @media (max-width: 768px) {
            .topics-grid {
                grid-template-columns: 1fr;
            }
            
            .container {
                padding: 1rem;
            }
            
            h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1>Acid-Base Chemistry</h1>
            <p class="subtitle">A Comprehensive Learning Platform</p>
        </div>
    </header>
    
    <div class="container">
        <div class="topics-grid" id="topicsGrid">
            <!-- Topic cards will be generated by JavaScript -->
        </div>
        
        <div class="content-section" id="contentSection">
            <!-- Content will be loaded here by JavaScript -->
        </div>
    </div>
    
    <footer>
        <div class="container">
            <p>Acid-Base Chemistry Learning Platform &copy; 2023</p>
        </div>
    </footer>

    <script>
        // Topic data structure
        const topics = [
            {
                id: 'ka-expressions',
                title: 'Ka Expressions for Weak Acids',
                theory: `
                    <h3>Understanding Ka Expressions</h3>
                    <p>The acid dissociation constant (K<sub>a</sub>) is a quantitative measure of the strength of a weak acid in solution. It is the equilibrium constant for the dissociation reaction of the acid.</p>
                    
                    <div class="formula">
                        <strong>Generic Weak Acid:</strong> HA ⇌ H⁺ + A⁻<br>
                        <strong>K<sub>a</sub> Expression:</strong> K<sub>a</sub> = [H⁺][A⁻] / [HA]
                    </div>
                    
                    <div class="example">
                        <strong>Example (Acetic Acid):</strong><br>
                        CH<sub>3</sub>COOH ⇌ H⁺ + CH<sub>3</sub>COO⁻<br>
                        K<sub>a</sub> = [H⁺][CH<sub>3</sub>COO⁻] / [CH<sub>3</sub>COOH]
                    </div>
                    
                    <p>Key points about K<sub>a</sub>:</p>
                    <ul>
                        <li>Larger K<sub>a</sub> values indicate stronger acids</li>
                        <li>K<sub>a</sub> is constant for a given acid at a specific temperature</li>
                        <li>pK<sub>a</sub> = -log(K<sub>a</sub>) - smaller pK<sub>a</sub> values indicate stronger acids</li>
                    </ul>
                `,
                problems: [
                    {
                        question: "Write the K<sub>a</sub> expression for hydrofluoric acid (HF).",
                        options: [
                            "K<sub>a</sub> = [H⁺][F⁻] / [HF]",
                            "K<sub>a</sub> = [HF] / [H⁺][F⁻]",
                            "K<sub>a</sub> = [H⁺]²[F⁻] / [HF]",
                            "K<sub>a</sub> = [H⁺][F⁻]² / [HF]"
                        ],
                        correct: 0,
                        explanation: "For HF ⇌ H⁺ + F⁻, the K<sub>a</sub> expression follows the general form K<sub>a</sub> = [H⁺][A⁻] / [HA]."
                    },
                    {
                        question: "Which K<sub>a</sub> expression is correct for carbonic acid (H₂CO₃) considering only its first dissociation?",
                        options: [
                            "K<sub>a</sub> = [H⁺][HCO₃⁻] / [H₂CO₃]",
                            "K<sub>a</sub> = [H⁺]²[CO₃²⁻] / [H₂CO₃]",
                            "K<sub>a</sub> = [H⁺][CO₃²⁻] / [HCO₃⁻]",
                            "K<sub>a</sub> = [H⁺][HCO₃⁻]² / [H₂CO₃]"
                        ],
                        correct: 0,
                        explanation: "For the first dissociation: H₂CO₃ ⇌ H⁺ + HCO₃⁻, so K<sub>a</sub> = [H⁺][HCO₃⁻] / [H₂CO₃]."
                    },
                    {
                        question: "What is the K<sub>a</sub> expression for the generic weak acid HX?",
                        options: [
                            "K<sub>a</sub> = [H⁺][X⁻] / [HX]",
                            "K<sub>a</sub> = [HX] / [H⁺][X⁻]",
                            "K<sub>a</sub> = [H⁺]²[X⁻] / [HX]",
                            "K<sub>a</sub> = [H⁺][X⁻]² / [HX]"
                        ],
                        correct: 0,
                        explanation: "For a generic weak acid HX ⇌ H⁺ + X⁻, the K<sub>a</sub> expression is K<sub>a</sub> = [H⁺][X⁻] / [HX]."
                    }
                ]
            },
            {
                id: 'strong-acid-ph',
                title: 'pH of Strong Acid Solutions',
                theory: `
                    <h3>Calculating [H⁺] and pH for Strong Acids</h3>
                    <p>Strong acids completely dissociate in water, meaning [H⁺] equals the initial concentration of the acid.</p>
                    
                    <div class="formula">
                        <strong>For monoprotic strong acids:</strong> [H⁺] = [HA]<sub>initial</sub><br>
                        <strong>pH = -log[H⁺]</strong>
                    </div>
                    
                    <div class="example">
                        <strong>Example:</strong> Calculate the pH of 0.025 M HCl<br>
                        [H⁺] = 0.025 M<br>
                        pH = -log(0.025) = 1.60
                    </div>
                    
                    <p>Common strong acids include: HCl, HBr, HI, HNO₃, H₂SO₄ (first proton), HClO₄</p>
                    
                    <p>For diprotic strong acids like H₂SO₄, the first proton dissociates completely, while the second proton is weak (K<sub>a₂</sub> ≈ 0.012).</p>
                `,
                problems: [
                    {
                        question: "What is the pH of a 0.005 M HNO₃ solution?",
                        options: [
                            "2.30",
                            "2.70",
                            "3.00",
                            "3.30"
                        ],
                        correct: 0,
                        explanation: "[H⁺] = 0.005 M, pH = -log(0.005) = 2.30"
                    },
                    {
                        question: "Calculate [H⁺] for a solution with pH = 1.80.",
                        options: [
                            "0.0158 M",
                            "0.0200 M",
                            "0.0251 M",
                            "0.0316 M"
                        ],
                        correct: 0,
                        explanation: "[H⁺] = 10^(-pH) = 10^(-1.80) = 0.0158 M"
                    },
                    {
                        question: "What is the pH of a 0.10 M HCl solution?",
                        options: [
                            "1.00",
                            "1.10",
                            "1.20",
                            "1.30"
                        ],
                        correct: 0,
                        explanation: "[H⁺] = 0.10 M, pH = -log(0.10) = 1.00"
                    }
                ]
            },
            {
                id: 'weak-acid-ph',
                title: 'pH of Weak Acid Solutions',
                theory: `
                    <h3>Calculating [H⁺] and pH for Weak Acids</h3>
                    <p>Weak acids only partially dissociate in water. We use an ICE table and the K<sub>a</sub> expression to find [H⁺].</p>
                    
                    <div class="formula">
                        <strong>General approach:</strong><br>
                        1. Set up ICE table: HA ⇌ H⁺ + A⁻<br>
                        2. Apply K<sub>a</sub> = [H⁺][A⁻] / [HA]<br>
                        3. Solve for x = [H⁺]<br>
                        4. pH = -log[H⁺]
                    </div>
                    
                    <div class="example">
                        <strong>Example:</strong> Calculate the pH of 0.10 M acetic acid (K<sub>a</sub> = 1.8 × 10⁻⁵)<br>
                        CH₃COOH ⇌ H⁺ + CH₃COO⁻<br>
                        K<sub>a</sub> = x² / (0.10 - x) ≈ x² / 0.10 = 1.8 × 10⁻⁵<br>
                        x² = 1.8 × 10⁻⁶<br>
                        x = √(1.8 × 10⁻⁶) = 1.34 × 10⁻³ M<br>
                        pH = -log(1.34 × 10⁻³) = 2.87
                    </div>
                    
                    <p>The "x is small" approximation is valid when [HA]₀ >> K<sub>a</sub> (typically when [HA]₀/K<sub>a</sub> > 100).</p>
                `,
                problems: [
                    {
                        question: "What is the [H⁺] in a 0.50 M HF solution? (K<sub>a</sub> = 6.8 × 10⁻⁴)",
                        options: [
                            "0.018 M",
                            "0.025 M",
                            "0.032 M",
                            "0.041 M"
                        ],
                        correct: 0,
                        explanation: "K<sub>a</sub> = x² / (0.50 - x) ≈ x² / 0.50 = 6.8 × 10⁻⁴, x² = 3.4 × 10⁻⁴, x = 0.018 M"
                    },
                    {
                        question: "Calculate the pH of 0.20 M formic acid (HCOOH) with K<sub>a</sub> = 1.8 × 10⁻⁴.",
                        options: [
                            "2.22",
                            "2.42",
                            "2.62",
                            "2.82"
                        ],
                        correct: 0,
                        explanation: "K<sub>a</sub> = x² / 0.20 = 1.8 × 10⁻⁴, x² = 3.6 × 10⁻⁵, x = 0.0060 M, pH = -log(0.0060) = 2.22"
                    },
                    {
                        question: "What is the percent dissociation of 0.10 M acetic acid (K<sub>a</sub> = 1.8 × 10⁻⁵)?",
                        options: [
                            "1.34%",
                            "2.15%",
                            "3.42%",
                            "4.25%"
                        ],
                        correct: 0,
                        explanation: "[H⁺] = √(K<sub>a</sub> × C) = √(1.8 × 10⁻⁵ × 0.10) = 1.34 × 10⁻³ M, % dissociation = (1.34 × 10⁻³ / 0.10) × 100% = 1.34%"
                    }
                ]
            },
            // More topics would follow the same pattern...
            {
                id: 'buffer-solutions',
                title: 'Buffer Solutions',
                theory: `
                    <h3>Understanding and Calculating Buffer pH</h3>
                    <p>Buffer solutions resist pH changes when small amounts of acid or base are added. They contain a weak acid and its conjugate base (or weak base and its conjugate acid).</p>
                    
                    <div class="formula">
                        <strong>Henderson-Hasselbalch Equation:</strong><br>
                        pH = pK<sub>a</sub> + log([A⁻]/[HA])
                    </div>
                    
                    <div class="example">
                        <strong>Example:</strong> Calculate the pH of a buffer with 0.10 M CH₃COOH and 0.15 M CH₃COONa (K<sub>a</sub> = 1.8 × 10⁻⁵)<br>
                        pK<sub>a</sub> = -log(1.8 × 10⁻⁵) = 4.74<br>
                        pH = 4.74 + log(0.15/0.10) = 4.74 + 0.18 = 4.92
                    </div>
                    
                    <p>Key properties of buffers:</p>
                    <ul>
                        <li>Maximum buffer capacity when [HA] = [A⁻] (pH = pK<sub>a</sub>)</li>
                        <li>Buffer range is typically pK<sub>a</sub> ± 1</li>
                        <li>Can be prepared by mixing a weak acid with its salt, or by partial neutralization of a weak acid</li>
                    </ul>
                `,
                problems: [
                    {
                        question: "What is the pH of a buffer containing 0.20 M NH₃ and 0.30 M NH₄Cl? (K<sub>b</sub> for NH₃ = 1.8 × 10⁻⁵)",
                        options: [
                            "9.08",
                            "9.25",
                            "9.43",
                            "9.56"
                        ],
                        correct: 1,
                        explanation: "pK<sub>a</sub> for NH₄⁺ = 14 - pK<sub>b</sub> = 14 - (-log(1.8 × 10⁻⁵)) = 14 - 4.74 = 9.26, pH = pK<sub>a</sub> + log([NH₃]/[NH₄⁺]) = 9.26 + log(0.20/0.30) = 9.26 - 0.18 = 9.08"
                    },
                    {
                        question: "How would you prepare 1 L of a pH 4.50 acetate buffer? (pK<sub>a</sub> of acetic acid = 4.74)",
                        options: [
                            "[CH₃COOH] = 0.36 M, [CH₃COONa] = 0.64 M",
                            "[CH₃COOH] = 0.64 M, [CH₃COONa] = 0.36 M",
                            "[CH₃COOH] = 0.50 M, [CH₃COONa] = 0.50 M",
                            "[CH₃COOH] = 0.25 M, [CH₃COONa] = 0.75 M"
                        ],
                        correct: 1,
                        explanation: "pH = pK<sub>a</sub> + log([A⁻]/[HA]), 4.50 = 4.74 + log([A⁻]/[HA]), log([A⁻]/[HA]) = -0.24, [A⁻]/[HA] = 10^(-0.24) = 0.575, so [HA] = 0.64 M and [A⁻] = 0.36 M (approximately)"
                    },
                    {
                        question: "Which combination would make an effective buffer?",
                        options: [
                            "HCl and NaCl",
                            "CH₃COOH and CH₃COONa",
                            "NaOH and NaCl",
                            "HNO₃ and KNO₃"
                        ],
                        correct: 1,
                        explanation: "An effective buffer requires a weak acid/base pair. CH₃COOH (weak acid) and CH₃COONa (its conjugate base) form a buffer system."
                    }
                ]
            }
        ];

        // Initialize the page
        document.addEventListener('DOMContentLoaded', function() {
            const topicsGrid = document.getElementById('topicsGrid');
            const contentSection = document.getElementById('contentSection');
            
            // Generate topic cards
            topics.forEach(topic => {
                const card = document.createElement('div');
                card.className = 'topic-card';
                card.innerHTML = `
                    <h3><i>📚</i> ${topic.title}</h3>
                    <p>Click to learn about ${topic.title.toLowerCase()} and practice with problems.</p>
                `;
                card.addEventListener('click', () => showTopic(topic.id));
                topicsGrid.appendChild(card);
            });
            
            // Function to show a specific topic
            function showTopic(topicId) {
                const topic = topics.find(t => t.id === topicId);
                if (!topic) return;
                
                contentSection.innerHTML = `
                    <div class="section-header">
                        <h2>${topic.title}</h2>
                        <button class="back-btn" id="backBtn">← Back to Topics</button>
                    </div>
                    <div class="theory-content">
                        ${topic.theory}
                    </div>
                    <div class="practice-problems">
                        <h3>Practice Problems</h3>
                        ${topic.problems.map((problem, index) => `
                            <div class="problem" id="problem-${index}">
                                <h4>Problem ${index + 1}</h4>
                                <p>${problem.question}</p>
                                <div class="options">
                                    ${problem.options.map((option, optIndex) => `
                                        <div class="option">
                                            <input type="radio" id="prob-${index}-opt-${optIndex}" name="problem-${index}" value="${optIndex}">
                                            <label for="prob-${index}-opt-${optIndex}">${option}</label>
                                        </div>
                                    `).join('')}
                                </div>
                                <button class="submit-btn" onclick="checkAnswer(${index}, '${topicId}')">Check Answer</button>
                                <div class="result" id="result-${index}"></div>
                            </div>
                        `).join('')}
                    </div>
                    <div class="nav-buttons">
                        <button class="nav-btn" id="prevBtn" disabled>Previous Topic</button>
                        <button class="nav-btn" id="nextBtn">Next Topic</button>
                    </div>
                `;
                
                contentSection.classList.add('active-section');
                
                // Add event listeners
                document.getElementById('backBtn').addEventListener('click', () => {
                    contentSection.classList.remove('active-section');
                });
                
                // Navigation buttons
                const currentIndex = topics.findIndex(t => t.id === topicId);
                const prevBtn = document.getElementById('prevBtn');
                const nextBtn = document.getElementById('nextBtn');
                
                if (currentIndex > 0) {
                    prevBtn.disabled = false;
                    prevBtn.addEventListener('click', () => showTopic(topics[currentIndex - 1].id));
                } else {
                    prevBtn.disabled = true;
                }
                
                if (currentIndex < topics.length - 1) {
                    nextBtn.disabled = false;
                    nextBtn.addEventListener('click', () => showTopic(topics[currentIndex + 1].id));
                } else {
                    nextBtn.disabled = true;
                }
                
                // Scroll to top of content
                contentSection.scrollIntoView({ behavior: 'smooth' });
            }
            
            // Make checkAnswer function globally available
            window.checkAnswer = function(problemIndex, topicId) {
                const topic = topics.find(t => t.id === topicId);
                const problem = topic.problems[problemIndex];
                const selectedOption = document.querySelector(`input[name="problem-${problemIndex}"]:checked`);
                
                const resultDiv = document.getElementById(`result-${problemIndex}`);
                
                if (!selectedOption) {
                    resultDiv.innerHTML = '<div class="result incorrect">Please select an answer.</div>';
                    resultDiv.style.display = 'block';
                    return;
                }
                
                const selectedValue = parseInt(selectedOption.value);
                
                if (selectedValue === problem.correct) {
                    resultDiv.innerHTML = `
                        <div class="result correct">
                            <strong>Correct!</strong>
                            <div class="explanation">${problem.explanation}</div>
                        </div>
                    `;
                } else {
                    resultDiv.innerHTML = `
                        <div class="result incorrect">
                            <strong>Incorrect.</strong>
                            <div class="explanation">${problem.explanation}</div>
                        </div>
                    `;
                }
                
                resultDiv.style.display = 'block';
            };
        });
    </script>
</body>
</html>
