<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VBGRAMG - Gram Panchayat Level Monitoring</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f4f7fb;
            color: #263238;
        }

        /* Header */
        .header {
            background: linear-gradient(135deg, #064e3b, #0f766e);
            color: white;
            padding: 18px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 3px 10px rgba(0,0,0,0.15);
        }

        .header h1 {
            font-size: 24px;
        }

        .header p {
            font-size: 13px;
            margin-top: 4px;
            opacity: 0.9;
        }

        .user {
            text-align: right;
        }

        /* Layout */
        .layout {
            display: flex;
            min-height: calc(100vh - 75px);
        }

        /* Sidebar */
        .sidebar {
            width: 240px;
            background: #ffffff;
            border-right: 1px solid #ddd;
            padding: 20px 10px;
        }

        .sidebar h3 {
            padding: 10px 15px;
            color: #0f766e;
            font-size: 14px;
            text-transform: uppercase;
        }

        .menu {
            list-style: none;
        }

        .menu li {
            margin: 5px 0;
        }

        .menu a {
            display: block;
            text-decoration: none;
            color: #374151;
            padding: 12px 15px;
            border-radius: 7px;
            transition: 0.2s;
        }

        .menu a:hover,
        .menu a.active {
            background: #dff7f2;
            color: #047857;
            font-weight: bold;
        }

        /* Main */
        .main {
            flex: 1;
            padding: 25px;
            overflow-x: auto;
        }

        .page-title {
            margin-bottom: 20px;
        }

        .page-title h2 {
            color: #064e3b;
            margin-bottom: 5px;
        }

        .page-title p {
            color: #6b7280;
            font-size: 14px;
        }

        /* Filter */
        .filter-box {
            background: white;
            padding: 18px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.06);
        }

        .filters {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
        }

        label {
            font-size: 13px;
            color: #4b5563;
            display: block;
            margin-bottom: 6px;
        }

        select,
        input {
            width: 100%;
            padding: 10px;
            border: 1px solid #d1d5db;
            border-radius: 6px;
            background: white;
        }

        button {
            background: #047857;
            color: white;
            border: none;
            padding: 10px 18px;
            border-radius: 6px;
            cursor: pointer;
            margin-top: 20px;
        }

        button:hover {
            background: #065f46;
        }

        /* Cards */
        .cards {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-bottom: 20px;
        }

        .card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.06);
            border-left: 5px solid #10b981;
        }

        .card h4 {
            color: #6b7280;
            font-size: 13px;
            margin-bottom: 10px;
        }

        .card .number {
            font-size: 28px;
            font-weight: bold;
            color: #064e3b;
        }

        .success {
            color: #059669 !important;
        }

        .warning {
            color: #d97706 !important;
        }

        .danger {
            color: #dc2626 !important;
        }

        /* Content grid */
        .content-grid {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 20px;
        }

        .panel {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.06);
            margin-bottom: 20px;
        }

        .panel h3 {
            color: #064e3b;
            margin-bottom: 15px;
        }

        /* Progress */
        .progress-item {
            margin-bottom: 18px;
        }

        .progress-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 6px;
            font-size: 13px;
        }

        .progress {
            height: 10px;
            background: #e5e7eb;
            border-radius: 10px;
            overflow: hidden;
        }

        .progress-bar {
            height: 100%;
            border-radius: 10px;
            background: #10b981;
        }

        /* Table */
        table {
            width: 100%;
            border-collapse: collapse;
        }

        th,
        td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #e5e7eb;
            font-size: 13px;
        }

        th {
            background: #f0fdf4;
            color: #065f46;
        }

        .badge {
            padding: 5px 9px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: bold;
        }

        .badge-green {
            background: #dcfce7;
            color: #166534;
        }

        .badge-yellow {
            background: #fef3c7;
            color: #92400e;
        }

        .badge-red {
            background: #fee2e2;
            color: #991b1b;
        }

        /* Alert */
        .alert {
            padding: 12px;
            border-radius: 7px;
            margin-bottom: 10px;
            font-size: 13px;
        }

        .alert-warning {
            background: #fff7ed;
            border-left: 4px solid #f97316;
        }

        .alert-danger {
            background: #fef2f2;
            border-left: 4px solid #ef4444;
        }

        .alert-success {
            background: #ecfdf5;
            border-left: 4px solid #10b981;
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 15px;
            color: #6b7280;
            font-size: 12px;
        }

        /* Responsive */
        @media (max-width: 1000px) {
            .cards {
                grid-template-columns: repeat(2, 1fr);
            }

            .filters {
                grid-template-columns: repeat(2, 1fr);
            }

            .content-grid {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 650px) {
            .sidebar {
                display: none;
            }

            .header {
                padding: 15px;
            }

            .main {
                padding: 15px;
            }

            .cards,
            .filters {
                grid-template-columns: 1fr;
            }

            .user {
                display: none;
            }
        }
    </style>
</head>

<body>

<header class="header">
    <div>
        <h1>VBGRAMG</h1>
        <p>Gram Panchayat Level Monitoring System</p>
    </div>

    <div class="user">
        <strong>Administrator</strong><br>
        <small>Gram Panchayat Monitoring</small>
    </div>
</header>

<div class="layout">

    <!-- Sidebar -->
    <aside class="sidebar">

        <h3>Monitoring Menu</h3>

        <ul class="menu">
            <li><a href="#" class="active">📊 Dashboard</a></li>
            <li><a href="#">🏘️ Panchayat Details</a></li>
            <li><a href="#">📋 Works & Projects</a></li>
            <li><a href="#">👥 Beneficiaries</a></li>
            <li><a href="#">💰 Financial Progress</a></li>
            <li><a href="#">📈 Physical Progress</a></li>
            <li><a href="#">📝 Inspections</a></li>
            <li><a href="#">⚠️ Issues & Alerts</a></li>
            <li><a href="#">📑 Reports</a></li>
            <li><a href="#">⚙️ Settings</a></li>
        </ul>

    </aside>

    <!-- Main Content -->
    <main class="main">

        <div class="page-title">
            <h2>Gram Panchayat Monitoring Dashboard</h2>
            <p>Monitor scheme implementation, projects, beneficiaries and financial progress.</p>
        </div>

        <!-- Filters -->
        <section class="filter-box">

            <div class="filters">

                <div>
                    <label>District</label>
                    <select id="district">
                        <option>Select District</option>
                        <option>Thrissur</option>
                        <option>Ernakulam</option>
                        <option>Palakkad</option>
                        <option>Malappuram</option>
                    </select>
                </div>

                <div>
                    <label>Block Panchayat</label>
                    <select>
                        <option>Select Block</option>
                        <option>Block Panchayat 1</option>
                        <option>Block Panchayat 2</option>
                    </select>
                </div>

                <div>
                    <label>Gram Panchayat</label>
                    <select>
                        <option>Select Panchayat</option>
                        <option>Gram Panchayat A</option>
                        <option>Gram Panchayat B</option>
                    </select>
                </div>

                <div>
                    <label>Financial Year</label>
                    <select>
                        <option>2026-27</option>
                        <option>2025-26</option>
                        <option>2024-25</option>
                    </select>
                </div>

            </div>

            <button onclick="applyFilter()">Apply Filter</button>

        </section>

        <!-- Summary Cards -->
        <section class="cards">

            <div class="card">
                <h4>Total Projects</h4>
                <div class="number">128</div>
            </div>

            <div class="card">
                <h4>Completed Projects</h4>
                <div class="number success">82</div>
            </div>

            <div class="card">
                <h4>Projects In Progress</h4>
                <div class="number warning">34</div>
            </div>

            <div class="card">
                <h4>Delayed Projects</h4>
                <div class="number danger">12</div>
            </div>

        </section>

        <div class="content-grid">

            <!-- Left -->
            <div>

                <!-- Progress -->
                <section class="panel">

                    <h3>Scheme / Project Progress</h3>

                    <div class="progress-item">
                        <div class="progress-header">
                            <span>Infrastructure Development</span>
                            <strong>78%</strong>
                        </div>
                        <div class="progress">
                            <div class="progress-bar" style="width:78%"></div>
                        </div>
                    </div>

                    <div class="progress-item">
                        <div class="progress-header">
                            <span>Water & Sanitation</span>
                            <strong>65%</strong>
                        </div>
                        <div class="progress">
                            <div class="progress-bar" style="width:65%"></div>
                        </div>
                    </div>

                    <div class="progress-item">
                        <div class="progress-header">
                            <span>Livelihood Projects</span>
                            <strong>84%</strong>
                        </div>
                        <div class="progress">
                            <div class="progress-bar" style="width:84%"></div>
                        </div>
                    </div>

                    <div class="progress-item">
                        <div class="progress-header">
                            <span>Social Development</span>
                            <strong>72%</strong>
                        </div>
                        <div class="progress">
                            <div class="progress-bar" style="width:72%"></div>
                        </div>
                    </div>

                </section>

                <!-- Project Table -->
                <section class="panel">

                    <h3>Recent Projects</h3>

                    <table>

                        <thead>
                            <tr>
                                <th>Project</th>
                                <th>Category</th>
                                <th>Progress</th>
                                <th>Status</th>
                            </tr>
                        </thead>

                        <tbody>

                            <tr>
                                <td>Road Development</td>
                                <td>Infrastructure</td>
                                <td>92%</td>
                                <td>
                                    <span class="badge badge-green">
                                        On Track
                                    </span>
                                </td>
                            </tr>

                            <tr>
                                <td>Drinking Water Project</td>
                                <td>Water</td>
                                <td>61%</td>
                                <td>
                                    <span class="badge badge-yellow">
                                        In Progress
                                    </span>
                                </td>
                            </tr>

                            <tr>
                                <td>Community Hall</td>
                                <td>Building</td>
                                <td>45%</td>
                                <td>
                                    <span class="badge badge-red">
                                        Delayed
                                    </span>
                                </td>
                            </tr>

                            <tr>
                                <td>Skill Development Centre</td>
                                <td>Livelihood</td>
                                <td>88%</td>
                                <td>
                                    <span class="badge badge-green">
                                        On Track
                                    </span>
                                </td>
                            </tr>

                        </tbody>

                    </table>

                </section>

            </div>

            <!-- Right -->
            <div>

                <!-- Financial -->
                <section class="panel">

                    <h3>Financial Progress</h3>

                    <div class="progress-item">
                        <div class="progress-header">
                            <span>Allocated</span>
                            <strong>₹2.50 Cr</strong>
                        </div>

                        <div class="progress">
                            <div class="progress-bar" style="width:100%"></div>
                        </div>
                    </div>

                    <div class="progress-item">
                        <div class="progress-header">
                            <span>Expenditure</span>
                            <strong>₹1.78 Cr</strong>
                        </div>

                        <div class="progress">
                            <div class="progress-bar"
                                 style="width:71%">
                            </div>
                        </div>
                    </div>

                </section>

                <!-- Alerts -->
                <section class="panel">

                    <h3>Alerts & Notifications</h3>

                    <div class="alert alert-danger">
                        <strong>3 Projects Delayed</strong><br>
                        Immediate monitoring required.
                    </div>

                    <div class="alert alert-warning">
                        <strong>5 Projects Near Deadline</strong><br>
                        Review expected completion dates.
                    </div>

                    <div class="alert alert-success">
                        <strong>Monthly Report Updated</strong><br>
                        Data successfully submitted.
                    </div>

                </section>

                <!-- Quick Stats -->
                <section class="panel">

                    <h3>Beneficiary Statistics</h3>

                    <p style="margin:12px 0;">
                        👨‍👩‍👧 Total Beneficiaries:
                        <strong>4,825</strong>
                    </p>

                    <p style="margin:12px 0;">
                        👩 Women Beneficiaries:
                        <strong>2,460</strong>
                    </p>

                    <p style="margin:12px 0;">
                        👴 Senior Citizens:
                        <strong>815</strong>
                    </p>

                    <p style="margin:12px 0;">
                        ♿ Persons with Disabilities:
                        <strong>172</strong>
                    </p>

                </section>

            </div>

        </div>

        <footer>
            VBGRAMG Gram Panchayat Level Monitoring System © 2026
        </footer>

    </main>

</div>

<script>

    function applyFilter() {

        const district =
            document.getElementById("district").value;

        if (district === "Select District") {
            alert("Please select a district.");
            return;
        }

        alert(
            "Dashboard filtered for: " + district
        );
    }

</script>

</body>
</html>
