
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ICON PUBLIC SCHOOL AHILYANAGAR - CCA SYSTEM</title>
    <!-- Chart.js CDN -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;800&display=swap');

        :root {
            --phoenix: #3b82f6;
            /* Blue */
            --titan: #22c55e;
            /* Green */
            --trojan: #ef4444;
            /* Red */
            --unicorn: #eab308;
            /* Yellow */
            --bg-gradient: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            --card-bg: rgba(255, 255, 255, 0.95);
            --text-dark: #1f2937;
        }

        body {
            font-family: 'Outfit', sans-serif;
            margin: 0;
            padding: 0;
            background: var(--bg-gradient);
            background-attachment: fixed;
            color: var(--text-dark);
            min-height: 100vh;
        }

        /* --- LOGIN PAGE --- */
        #login-page {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            width: 100%;
            position: absolute;
            top: 0;
            left: 0;
            background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
            z-index: 1000;
        }

        .login-card {
            background: var(--card-bg);
            padding: 3rem 2.5rem;
            border-radius: 1.5rem;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
            width: 90%;
            max-width: 420px;
            text-align: center;
            backdrop-filter: blur(10px);
        }

        .login-card h2 {
            margin-top: 0;
            color: #1e3c72;
            font-weight: 800;
            font-size: 2rem;
            letter-spacing: 1px;
        }

        .login-card p {
            color: #6b7280;
            margin-bottom: 2rem;
            font-size: 1.1rem;
        }

        /* --- GLOBAL INPUTS & BUTTONS --- */
        input[type="text"],
        input[type="password"],
        input[type="number"],
        select,
        textarea {
            width: 100%;
            padding: 1.2rem;
            margin-bottom: 1.2rem;
            border: 2px solid #e5e7eb;
            border-radius: 0.75rem;
            box-sizing: border-box;
            font-size: 1.1rem;
            font-family: 'Outfit', sans-serif;
            transition: all 0.3s ease;
            background: #f9fafb;
        }

        input:focus,
        textarea:focus {
            outline: none;
            border-color: #3b82f6;
            background: white;
            box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.1);
        }

        button.primary-btn {
            background: linear-gradient(to right, #1e3c72, #2a5298);
            color: white;
            padding: 1.2rem;
            border: none;
            border-radius: 0.75rem;
            font-size: 1.2rem;
            cursor: pointer;
            width: 100%;
            transition: transform 0.2s, box-shadow 0.2s;
            font-weight: 600;
            font-family: 'Outfit', sans-serif;
        }

        button.primary-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(30, 60, 114, 0.3);
        }

        /* --- MAIN APP CONTAINER --- */
        #main-app {
            display: none;
            /* Hidden until login */
            max-width: 1100px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        /* --- HEADER --- */
        header {
            text-align: center;
            padding: 2.5rem 1rem;
            margin-bottom: 2.5rem;
            background: var(--card-bg);
            border-radius: 1.5rem;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            backdrop-filter: blur(10px);
        }

        h1.glowing {
            color: #1e3c72;
            margin: 0 0 0.5rem 0;
            font-size: 2.5rem;
            font-weight: 800;
            letter-spacing: 2px;
            text-transform: uppercase;
            text-shadow: 0 0 10px rgba(42, 82, 152, 0.3);
            animation: glowPulse 2s infinite alternate;
        }

        header h3 {
            color: #4b5563;
            margin: 0;
            font-weight: 400;
            font-size: 1.2rem;
        }

        @keyframes glowPulse {
            from {
                text-shadow: 0 0 10px rgba(30, 60, 114, 0.4);
            }

            to {
                text-shadow: 0 0 25px rgba(30, 60, 114, 0.8), 0 0 35px rgba(59, 130, 246, 0.6);
            }
        }

        /* --- NAVIGATION --- */
        nav {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 2.5rem;
            flex-wrap: wrap;
        }

        .nav-tab {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            padding: 0.8rem 2rem;
            border-radius: 2rem;
            font-weight: 600;
            font-size: 1.1rem;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.3);
            backdrop-filter: blur(5px);
        }

        .nav-tab.active,
        .nav-tab:hover {
            background: white;
            color: #1e3c72;
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }

        /* --- SECTIONS --- */
        .section {
            display: none;
            background: var(--card-bg);
            padding: 2.5rem;
            border-radius: 1.5rem;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
            animation: slideUp 0.4s ease-out;
            backdrop-filter: blur(10px);
        }

        .section.active {
            display: block;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        h2.section-title {
            color: #1e3c72;
            margin-top: 0;
            font-size: 2rem;
            border-bottom: 3px solid #e5e7eb;
            padding-bottom: 0.5rem;
            margin-bottom: 2rem;
        }

        /* --- HOMEPAGE --- */
        .info-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1.5rem;
            font-size: 1.1rem;
            line-height: 1.8;
            margin-bottom: 2rem;
            background: #f9fafb;
            padding: 2rem;
            border-radius: 1rem;
            border: 1px solid #e5e7eb;
        }

        .info-item strong {
            color: #1e3c72;
        }

        .website-link {
            text-align: center;
            margin: 2.5rem 0;
        }

        .website-link button {
            background: linear-gradient(135deg, #f59e0b, #d97706);
            width: auto;
            padding: 1rem 3rem;
            border-radius: 3rem;
        }

        .map-container {
            width: 100%;
            height: 350px;
            border-radius: 1.2rem;
            overflow: hidden;
            margin-bottom: 2.5rem;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            border: 4px solid white;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-top: 1.5rem;
            flex-wrap: wrap;
        }

        .social-btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 0.8rem 2rem;
            border-radius: 3rem;
            text-decoration: none;
            font-weight: 600;
            color: white;
            transition: all 0.3s;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
        }

        .social-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
        }

        .instagram {
            background: linear-gradient(45deg, #f09433 0%, #e6683c 25%, #dc2743 50%, #cc2366 75%, #bc1888 100%);
        }

        .youtube {
            background: #ff0000;
        }

        .facebook {
            background: #1877f2;
        }

        .twitter {
            background: #000000;
        }

        /* --- STUDENT MANAGEMENT --- */
        .house-selector {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .house-btn {
            padding: 1.5rem 1rem;
            border-radius: 1rem;
            border: 3px solid transparent;
            cursor: pointer;
            text-align: center;
            font-weight: 800;
            font-size: 1.2rem;
            color: white;
            opacity: 0.5;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        .house-btn.active {
            opacity: 1;
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            border-color: white;
        }

        .btn-phoenix {
            background-color: var(--phoenix);
        }

        .btn-titan {
            background-color: var(--titan);
        }

        .btn-trojan {
            background-color: var(--trojan);
        }

        .btn-unicorn {
            background-color: var(--unicorn);
            color: #333;
            text-shadow: none;
        }

        /* --- TABLE --- */
        .table-responsive {
            overflow-x: auto;
            border-radius: 1rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            border: 1px solid #e5e7eb;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            background: white;
        }

        th,
        td {
            padding: 1.2rem 1rem;
            text-align: left;
            border-bottom: 1px solid #f3f4f6;
        }

        th {
            background-color: #f9fafb;
            font-weight: 800;
            color: #4b5563;
            text-transform: uppercase;
            font-size: 0.9rem;
            letter-spacing: 0.5px;
        }

        tr:last-child td {
            border-bottom: none;
        }

        tr:hover {
            background-color: #f8fafc;
        }

        .house-badge {
            padding: 0.4rem 1rem;
            border-radius: 2rem;
            font-weight: 800;
            font-size: 0.85rem;
            display: inline-block;
            text-transform: uppercase;
        }

        .delete-btn {
            background: #ef4444;
            color: white;
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 0.5rem;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.2s;
        }

        .delete-btn:hover {
            background: #dc2626;
        }

        /* --- COMMUNITY WALL --- */
        .post-input-area {
            background: #f9fafb;
            padding: 2rem;
            border-radius: 1.2rem;
            margin-bottom: 3rem;
            border: 1px solid #e5e7eb;
            box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.02);
        }

        .post-card {
            background: white;
            border-left: 6px solid #1e3c72;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border-radius: 0 1rem 1rem 0;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: transform 0.2s;
        }

        .post-card:hover {
            transform: translateX(5px);
        }

        .post-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
            border-bottom: 1px solid #f3f4f6;
            padding-bottom: 0.5rem;
        }

        .post-author {
            font-weight: 800;
            color: #1e3c72;
            font-size: 1.1rem;
        }

        .post-date {
            font-size: 0.85rem;
            color: #9ca3af;
        }

        .post-message {
            color: #4b5563;
            line-height: 1.6;
            font-size: 1.1rem;
            white-space: pre-wrap;
        }

        /* --- CHART --- */
        .chart-container-wrapper {
            background: white;
            border-radius: 1.5rem;
            padding: 2rem;
            box-shadow: inset 0 2px 10px rgba(0, 0, 0, 0.02);
            border: 1px solid #e5e7eb;
        }

        .chart-container {
            position: relative;
            height: 450px;
            width: 100%;
            display: flex;
            justify-content: center;
        }

        /* --- RESPONSIVE --- */
        @media (max-width: 768px) {
            h1.glowing {
                font-size: 1.8rem;
            }

            .section {
                padding: 1.5rem;
            }

            .login-card {
                padding: 2rem 1.5rem;
            }

            .nav-tab {
                padding: 0.6rem 1.2rem;
                font-size: 1rem;
            }

            .house-selector {
                grid-template-columns: repeat(2, 1fr);
            }

            header {
                padding: 1.5rem 1rem;
            }
        }
    </style>
</head>

<body>

    <!-- ==================== LOGIN SECTION ==================== -->
    <div id="login-page">
        <div class="login-card">
            <h2>ICON PUBLIC SCHOOL</h2>
            <p>CCA System Administration</p>

            <input type="text" id="username" placeholder="Username" autocomplete="off">
            <input type="password" id="password" placeholder="Password">

            <p id="login-error" style="color: #ef4444; display: none; margin-bottom: 1rem; font-weight: 600;">⚠️ Invalid
                Username or Password</p>

            <button class="primary-btn" onclick="login()">Access System</button>
            <p style="margin-top: 1.5rem; font-size: 0.85rem; color: #9ca3af;">Secured Portal</p>
        </div>
    </div>

    <!-- ==================== MAIN APPLICATION ==================== -->
    <div id="main-app">
        <header>
            <h1 class="glowing">ICON PUBLIC SCHOOL AHILYANAGAR</h1>
            <h3>Co-Curricular Activities (CCA) Management</h3>
        </header>

        <!-- Navigation Tabs -->
        <nav>
            <div class="nav-tab active" onclick="switchTab('home')">Home</div>
            <div class="nav-tab" onclick="switchTab('students')">Students</div>
            <div class="nav-tab" onclick="switchTab('chart')">House Chart</div>
            <div class="nav-tab" onclick="switchTab('community')">Community</div>
        </nav>

        <!-- ==================== HOME TAB ==================== -->
        <div id="home" class="section active">
            <h2 class="section-title">Welcome to CCA System</h2>

            <div class="info-grid">
                <div class="info-item">
                    <strong>📍 Address:</strong> 46/2 Station Road Near Railway Station, Ahilyanagar, Maharashtra, India
                </div>
                <div class="info-item">
                    <strong>📞 Phone:</strong> 7249657337 / 7756994850
                </div>
                <div class="info-item">
                    <strong>👩‍🏫 Principal:</strong> Mrs. Deepika Nagarwala
                </div>
            </div>

            <div class="website-link">
                <a href="https://iconpublicschools.org" target="_blank" style="text-decoration: none;">
                    <button class="primary-btn">🌐 Visit Official School Website</button>
                </a>
            </div>

            <h3 style="color: #1e3c72; margin-top: 3rem;">Location Map</h3>
            <div class="map-container">
                <!-- Using an embedded Google map for Ahilyanagar Railway Station -->
                <iframe
                    src="https://maps.google.com/maps?q=Ahmednagar%20Railway%20Station&t=&z=14&ie=UTF8&iwloc=&output=embed"
                    width="100%" height="100%" style="border:0;" allowfullscreen="" loading="lazy">
                </iframe>
            </div>

            <h3 style="color: #1e3c72; text-align: center; margin-top: 3rem;">Connect With Us</h3>
            <div class="social-links">
                <a href="#" class="social-btn instagram">Instagram</a>
                <a href="#" class="social-btn youtube">YouTube</a>
                <a href="#" class="social-btn facebook">Facebook</a>
                <a href="#" class="social-btn twitter">Twitter</a>
            </div>
        </div>

        <!-- ==================== STUDENTS TAB ==================== -->
        <div id="students" class="section">
            <h2 class="section-title">Add Student Record</h2>

            <input type="text" id="student-name" placeholder="Enter full student name">
            <input type="number" id="student-points" placeholder="Enter points awarded">

            <p style="font-weight: 800; color: #4b5563; margin: 1.5rem 0 1rem 0; font-size: 1.1rem;">Assign House:</p>
            <div class="house-selector">
                <div class="house-btn btn-phoenix" onclick="selectHouse('Phoenix')">Phoenix</div>
                <div class="house-btn btn-titan" onclick="selectHouse('Titan')">Titan</div>
                <div class="house-btn btn-trojan" onclick="selectHouse('Trojan')">Trojan</div>
                <div class="house-btn btn-unicorn" onclick="selectHouse('Unicorn')">Unicorn</div>
            </div>

            <button class="primary-btn" onclick="addStudent()">➕ Add Student to Records</button>

            <h2 class="section-title" style="margin-top: 4rem;">Student Database</h2>

            <input type="text" id="search-student" placeholder="🔍 Search student by name..." onkeyup="searchStudent()"
                style="margin-bottom: 1.5rem; max-width: 400px; display: block;">

            <div class="table-responsive">
                <table id="student-table">
                    <thead>
                        <tr>
                            <th>Student Name</th>
                            <th>House</th>
                            <th>Points</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody id="student-list">
                        <!-- Javascript will populate rows here -->
                    </tbody>
                </table>
            </div>
        </div>

        <!-- ==================== CHART TAB ==================== -->
        <div id="chart" class="section">
            <h2 class="section-title">House Point Standings</h2>
            <div class="chart-container-wrapper">
                <div class="chart-container">
                    <canvas id="pointChart"></canvas>
                </div>
            </div>
        </div>

        <!-- ==================== COMMUNITY TAB ==================== -->
        <div id="community" class="section">
            <h2 class="section-title">Community Wall</h2>

            <div class="post-input-area">
                <input type="text" id="post-name" placeholder="Your Name">
                <textarea id="post-message" rows="4"
                    placeholder="Share your message or announcement globally..."></textarea>
                <button class="primary-btn" onclick="addPost()">📢 Post to Community Wall</button>
            </div>

            <h3 style="color: #1e3c72; margin-bottom: 1.5rem;">Recent Announcements</h3>
            <div id="post-list">
                <!-- Javascript will populate posts here -->
            </div>
        </div>
    </div>

    <!-- ==================== JAVASCRIPT LOGIC ==================== -->
    <script>
        // Global State & Data
        let selectedHouse = '';
        let myChart = null;

        // Load data from LocalStorage or initialize empties
        let students = JSON.parse(localStorage.getItem('icon_cca_students')) || [];
        let posts = JSON.parse(localStorage.getItem('icon_cca_posts')) || [];

        // --- 1. LOGIN LOGIC ---
        function login() {
            const user = document.getElementById('username').value.trim();
            const pass = document.getElementById('password').value;

            // Check credentials based on requirements
            if (user === 'admin' && pass === 'icon123') {
                // Success
                document.getElementById('login-page').style.display = 'none';
                document.getElementById('main-app').style.display = 'block';

                // Render initial data
                renderStudents();
                renderPosts();
                initChart();
            } else {
                // Failure
                document.getElementById('login-error').style.display = 'block';
                // Add a shake animation effect (optional visual feedback)
                const card = document.querySelector('.login-card');
                card.style.transform = 'translate(-5px, 0)';
                setTimeout(() => card.style.transform = 'translate(5px, 0)', 100);
                setTimeout(() => card.style.transform = 'translate(-5px, 0)', 200);
                setTimeout(() => card.style.transform = 'translate(0, 0)', 300);
            }
        }

        // Allow pressing Enter key to login
        document.getElementById('password').addEventListener('keypress', function (e) {
            if (e.key === 'Enter') login();
        });

        // --- 2. NAVIGATION LOGIC ---
        function switchTab(tabId) {
            // Update Active Tab Button
            document.querySelectorAll('.nav-tab').forEach(tab => tab.classList.remove('active'));
            event.currentTarget.classList.add('active'); // event.currentTarget ensures we get the nav-tab div

            // Handle Sections 
            document.querySelectorAll('.section').forEach(sec => {
                sec.classList.remove('active');
            });

            const targetSec = document.getElementById(tabId);
            targetSec.classList.add('active');

            // Force update chart to render correctly when its section becomes visible
            if (tabId === 'chart') {
                updateChart();
            }
        }

        // --- 3. STUDENT MANAGEMENT LOGIC ---
        function selectHouse(house) {
            selectedHouse = house;
            document.querySelectorAll('.house-btn').forEach(btn => btn.classList.remove('active'));
            event.currentTarget.classList.add('active');
        }

        function addStudent() {
            const name = document.getElementById('student-name').value.trim();
            const pointsValue = document.getElementById('student-points').value;
            const points = parseInt(pointsValue);

            // Validation
            if (!name || isNaN(points) || !selectedHouse) {
                alert('Oops! Please enter student name, points, and select a house before saving.');
                return;
            }

            // Create record
            const student = {
                id: Date.now(), // Generate a unique ID timestamp
                name: name,
                points: points,
                house: selectedHouse
            };

            // Save and update UI
            students.push(student);
            saveStudents();
            renderStudents();
            updateChart();

            // Reset inputs
            document.getElementById('student-name').value = '';
            document.getElementById('student-points').value = '';
            selectedHouse = '';
            document.querySelectorAll('.house-btn').forEach(btn => btn.classList.remove('active'));

            alert('Student record added successfully!');
        }

        function deleteStudent(id) {
            if (confirm('Are you sure you want to delete this student record?')) {
                students = students.filter(s => s.id !== id);
                saveStudents();
                renderStudents();
                updateChart();
            }
        }

        function editStudent(id) {
            const student = students.find(s => s.id === id);
            if (!student) return;

            const newName = prompt(`Edit name for student:`, student.name);
            if (newName === null) return;

            const newPts = prompt(`Edit points for ${newName}:`, student.points);

            if (newPts !== null && newName.trim() !== '') {
                const parsed = parseInt(newPts);
                if (!isNaN(parsed)) {
                    student.name = newName.trim();
                    student.points = parsed;
                    saveStudents();
                    renderStudents();
                    updateChart();
                } else {
                    alert('Invalid points format. Please enter a number.');
                }
            }
        }

        function searchStudent() {
            const input = document.getElementById('search-student').value.toLowerCase();
            const rows = document.getElementById('student-list').getElementsByTagName('tr');

            for (let i = 0; i < rows.length; i++) {
                const nameCell = rows[i].getElementsByTagName('td')[0];
                if (nameCell && !nameCell.hasAttribute('colspan')) {
                    const txtValue = nameCell.textContent || nameCell.innerText;
                    if (txtValue.toLowerCase().indexOf(input) > -1) {
                        rows[i].style.display = "";
                    } else {
                        rows[i].style.display = "none";
                    }
                }
            }
        }

        function saveStudents() {
            localStorage.setItem('icon_cca_students', JSON.stringify(students));
        }

        function renderStudents() {
            const tbody = document.getElementById('student-list');
            tbody.innerHTML = ''; // Clear table

            if (students.length === 0) {
                tbody.innerHTML = `<tr><td colspan="4" style="text-align:center; color:#6b7280; padding:2rem;">No student records found. Add students above.</td></tr>`;
                return;
            }

            students.forEach(student => {
                // Determine styling based on house
                let bgPrimary = '';
                let textPrimary = 'white';

                switch (student.house) {
                    case 'Phoenix': bgPrimary = 'var(--phoenix)'; break;
                    case 'Titan': bgPrimary = 'var(--titan)'; break;
                    case 'Trojan': bgPrimary = 'var(--trojan)'; break;
                    case 'Unicorn': bgPrimary = 'var(--unicorn)'; textPrimary = '#333'; break;
                }

                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td style="font-weight: 600; color: #1f2937;">${student.name}</td>
                    <td>
                        <span class="house-badge" style="background-color: ${bgPrimary}; color: ${textPrimary};">
                            ${student.house}
                        </span>
                    </td>
                    <td style="font-weight: 800; font-size: 1.1rem; color: #1e3c72;">${student.points}</td>
                    <td style="display: flex; gap: 0.5rem; border-bottom: none; align-items: center;">
                        <button class="delete-btn" style="background: #eab308; color: #1f2937;" onclick="editStudent(${student.id})">Edit</button>
                        <button class="delete-btn" onclick="deleteStudent(${student.id})">Delete</button>
                    </td>
                `;
                tbody.appendChild(tr);
            });
        }

        // --- 4. CHART.JS LOGIC ---
        function getHousePoints() {
            // Aggregate points per house
            let totals = { Phoenix: 0, Titan: 0, Trojan: 0, Unicorn: 0 };
            students.forEach(s => {
                if (totals[s.house] !== undefined) {
                    totals[s.house] += s.points;
                }
            });
            return totals;
        }

        function initChart() {
            const ctx = document.getElementById('pointChart').getContext('2d');
            const data = getHousePoints();

            // Re-create chart if exists to avoid ghosts
            if (myChart) {
                myChart.destroy();
            }

            myChart = new Chart(ctx, {
                type: 'pie', // Explicitly requested Pie Chart
                data: {
                    labels: ['Phoenix', 'Titan', 'Trojan', 'Unicorn'],
                    datasets: [{
                        data: [data.Phoenix, data.Titan, data.Trojan, data.Unicorn],
                        backgroundColor: [
                            '#3b82f6', // Phoenix
                            '#22c55e', // Titan
                            '#ef4444', // Trojan
                            '#eab308'  // Unicorn
                        ],
                        borderWidth: 3,
                        borderColor: '#ffffff',
                        hoverOffset: 15
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                padding: 25,
                                font: {
                                    size: 15,
                                    family: "'Outfit', sans-serif",
                                    weight: 'bold'
                                },
                                usePointStyle: true
                            }
                        },
                        tooltip: {
                            padding: 15,
                            titleFont: { size: 16, family: "'Outfit', sans-serif" },
                            bodyFont: { size: 16, family: "'Outfit', sans-serif" },
                            callbacks: {
                                label: function (context) {
                                    return ` Total Points: ${context.parsed}`;
                                }
                            }
                        }
                    }
                }
            });
        }

        function updateChart() {
            if (myChart) {
                const data = getHousePoints();
                myChart.data.datasets[0].data = [data.Phoenix, data.Titan, data.Trojan, data.Unicorn];
                myChart.update();
            }
        }

        // --- 5. COMMUNITY WALL LOGIC ---
        function addPost() {
            const name = document.getElementById('post-name').value.trim();
            const message = document.getElementById('post-message').value.trim();

            if (!name || !message) {
                alert('Please provide your name and message to post!');
                return;
            }

            const post = {
                id: Date.now(),
                name: name,
                message: message,
                date: new Date().toLocaleDateString('en-US', {
                    year: 'numeric', month: 'short', day: 'numeric',
                    hour: '2-digit', minute: '2-digit'
                })
            };

            posts.unshift(post); // Add newest post to the top
            savePosts();
            renderPosts();

            // Clear inputs
            document.getElementById('post-name').value = '';
            document.getElementById('post-message').value = '';
        }

        function savePosts() {
            localStorage.setItem('icon_cca_posts', JSON.stringify(posts));
        }

        function renderPosts() {
            const list = document.getElementById('post-list');
            list.innerHTML = '';

            if (posts.length === 0) {
                list.innerHTML = `
                    <div style="text-align:center; padding: 3rem; background: white; border-radius: 1rem; color: #9ca3af; border: 1px dashed #e5e7eb;">
                        <i>The community wall is quiet. Be the first to start the conversation!</i>
                    </div>`;
                return;
            }

            posts.forEach(post => {
                const div = document.createElement('div');
                div.className = 'post-card';
                div.innerHTML = `
                    <div class="post-header">
                        <div class="post-author">${post.name}</div>
                        <div class="post-date">${post.date}</div>
                    </div>
                    <div class="post-message">${post.message}</div>
                `;
                list.appendChild(div);
            });
        }
    </script>
</body>

</html>
