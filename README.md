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
            display: https://vbgramg.dord.gov.in/vbgramg/home.aspx grid;
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
        <p>Pattiam Gram Panchayat Level Monitoring System</p>
    </div>

    <div class="user">
        <strong>Administrator</strong><br>
        <small>Pattiam Gram Panchayat Monitoring</small>
    </div>
</header>

<div class="layout">

    <!-- Sidebar -->
    <aside class="sidebar">

        <h3>Monitoring Menu</h3>

        <ul class="menu">
            <li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/vbgramg_ataglance/At_a_glance.aspx>📊 AT A GLANCE </a></li>
            <li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/IndexFrame.aspx?payload=iPj-AzfVDlAjNH7Q6XCteCh-Y51A1WO6n84SL9J1bxYq5nG-668vltW9F6eBHwGIukj0BBHYeHZu-A5SnIAxJ33lhs2pXOxCh3qGCAqs24tQmPmnMBrvETqXydHKgAqN8YbvNhQA2S9d5rgWSe13VG82oy8F-H1kHFqwRjR6uyFaIv9UrSlh4rY5dwVcfpNuvdHAg5ZEblPVQ0HVBiopJQk4RgNrn5wcSpL5cyJ5WdVetsi43dy2w3ZIX2q8Nw_TCfGiE9DZxCCiaOeBGrdmQOd7we9RFj56EiclCUHzNsc>Pattiam Report </a></li>
            <li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/work_register.aspx?payload=p1ay8F5exg6cJaJ4XCAcUlvBLTgACr0yFm1YZ9NmrLZZjGWSDhbEduc5IU4eshDMZPim9AB-ww_vZSR0lsrfWU7_RzprOYcqYaqoRbXjYquQP4AflW1L16Dz6g3MupwoGHAK4cqnQnxcRnTjeVhOdPZgUCJxDUw4VTm3UT7SRUejNLTGjkXRwqAHTc1vjPYEmXTDR3aOi1YKqv2AXullyb4BwAro4u8n2JoSR-rqkg3zKqupvd5k9nDDGGxlHsRH0JRu3vXI_geY-jKVVYfkhlaZhJQ8gHOCCYSgiX-T4qBVERZ-sZrs1tfAlRZrESiE>📋 Works Register </a></li>
            <li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/writereaddata/state_out/jobcardreg_1602006005_eng.html>👥 JOB CARD REGISERED</a></li>
            <li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/state_html/emuster_wagelist_rpt.aspx?payload=PBRkgzOGa-VcRTyVQgTHkwBd4rVf-CTgCjHbYGVS8SBrJvOlj_uO0Y0uhLEUL1woAAiF6oS_8EFzqQxGvwWRHMyJCcT9L8Pu5n3id1Pw_RVQgI7MJ-DYP43pF40EhyUXVT-8otL5-wAhZRYh7If5cpcn1gDHMt-HIA7ab4TCa2YCTRdo7Izk1c5sXFn2mpTHR5AZfJtQnL94AytWu6L0Z3b_CrarqbJPQd0lkIvixzeQbnbdmXrkzUa0ptEKuW04Vrtnun_ZPmc2yWC3RYz-rA>💰E-Mustroll and Wagelist</a></li>
            <li><a href=https://vbgramgrep.dord.gov.in/vbgramg/specific_work_search_rpt.aspx?payload=IUIs-oDgeppQNjfEmEGnJSl0h-NW1UizMC8hJu_B7xx8i5xxkiQnlArPvdz0Z4oIc_Bbtl3wtQLLNVCdM03U5igajiKoaC1jLDHD5-cA2QODwRqbWeDig5ed5tW4NJZiCQw82zvMBIj6IwbOcpHa4TjvpRngruZ2aW674AN1Ad4PSh2ui0SnWVxCV_nXkMiY>📈 E-Work File</a></li>
            <li><b>📝 Dynamic Report</></li><li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/dynamic_work_details.aspx?payload=5Ej2GFsBYVl8xwvMqBLE5TLhFZpcvKTM0OuciIEPt3esYU7Xxpupu1ZnUpC-3MlimaZli0jGlT31JvWffd-ZBpq6I4GEOJ13QZX3rT8qmlvcZblkpgoI6FBC3wANY5s-PlDe4Zd7L038dvus0ZHO1iGGRzvsN9tQhDg7ViKpJ42f-SzuZNKeKB3_zgDf9yGy>❗ Work Report </a></li>
<li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/dynamic_account_sk_ssk.aspx?payload=O7Y1eWDFXqYtMng4O_1I4L9N8SesxGHRtJdSanm_NDUAQFRLSOJj_oCSsWbA6QfPFDZsBiUtHS7sgImksSNKtmAFJZWe3MPKViQbeSotAJamMOAc95khcPu-j99YQ05RmDtCdQCHrVdvfZ_UkiEsNFReK9AAoMmGj3BgHdrQ6gqNK_-qwVm8j_HQtt-1Rrd->❗ Skilled Report </a></li>
            <li> <B>⚠️ Tracking & Alerts</B> </li><li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/dynamic_muster_track.aspx?payload=tX2SfSIxHu_zB9yWSjXfzLsiaIRcQTMlEkKlec2XpZ-MgLZrPxebQNm4PpP62pRqZWeZzmSseFvci5oXDKTT_e-zMKfLY9FpaF2zn3U27eLVQrTPs7ouJg2wrqLugJPi7hUii6mhMqGSt5oz3yPeww>❗Muster roll Tracking</a></li>
 <a href=https://vbgramgrep.dord.gov.in/VBGRAMG/dynamic_material_track.aspx?payload=yE16mkRF69TuAOJsh6sh9j337JLEH-vgiajT9QSlVlSNgIKTFFJqo-j4d0Kw7W0ASDs5VpX0s8w8xaDqahifS9cO_Lnb11bp9H-HCFeWoviXRtAKPSdYO5yIT6loKP42FGFpoDm68qsa43isecFysQ>  ❗Material Bill Tracking</a></li>

<a href=https://vbgramgrep.dord.gov.in/VBGRAMG/dynamic_mat_track.aspx?payload=qhJ3tXx3zfxAtjMW5HCZuyckuH2IwJtU3sLwkqqlyrx--CgoaZgETt1BUoZYiM-ocjoua7bpOkjx15ALDJt15h9XaoB9yZzHEiWTQIoisIhqA7gaieGv8zsqKZdVxCEK_aVrJB38o-M4jcWF7Y9Y-Q>❗Mate Tracking</a></li>

            <li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/Citizen_html/Musternew.aspx?payload=-vDqJMEmnzg1V8UjhU9UZK002vwgRWv-u5uEJ72WPCMnAM1d6hDnmBoUEUmm8yQEkLrB38M9NIilKNmzx9Nc1u2tMSVND7OsezOxxITlLjqyl2m41UiBm0Je41rYjJK9Xe6tZiN_0KlETm7_7NDpKz_uwi9RMwv-rzgrG0AkrvtmdlAlBk6d-GUlXCuIN4hcEY1usVlqRY5SeYFJp8L36JrZRx2HpZCKT5oRxjwLQ5sgmFUCM_B9Co9-RFGLZVtY9KteRfY3iuE-ymAU22g0iRGfz6EAi6OI5dc_881l5p9frxpa9hsAD6bMW2dN3OB3u2TgmzVelm9AEWGfP-nAMg>📑 Muster Rolls</a></li>
            <li><a href="#">⚙️ Settings</a></li>
        </ul>

    </aside>

    <!-- Main Content -->
    <main class="main">

        <div class="page-title">
            <h2>Pattiam Gram Panchayat Monitoring Dashboard</h2>
            <p>Monitor scheme implementation, projects, beneficiaries and financial progress.</p>
        </div>

        <!-- Filters -->
        <section class="filter-box">

            <div class="filters">

                <div>
                    <label>District</label>
                    <select id="district">
                        <option>Select District</option>
                        <option>KANNUR</option>
                                           </select>
                </div>

                <div>
                    <label>Block Panchayat</label>
                    <select>
                        <option>Select Block</option>
                        <option>KUTHUPARAMBA</option>
                                           </select>
                </div>

                <div>
                    <label>Gram Panchayat</label>
                    <select>
                        <option>Select Panchayat</option>
                        <option>PATTIAM</option>
                       
                    </select>
                </div>

                <div>
                    <label>Financial Year</label>
                    <select>
                        <option>2026-27</option>
                                           </select>
                </div>

            </div>

            <button onclick="applyFilter()">REPORT <a href=https://vbgramgrep.dord.gov.in/VBGRAMG/IndexFrame.aspx?payload=iPj-AzfVDlAjNH7Q6XCteCh-Y51A1WO6n84SL9J1bxYq5nG-668vltW9F6eBHwGIukj0BBHYeHZu-A5SnIAxJ33lhs2pXOxCh3qGCAqs24tQmPmnMBrvETqXydHKgAqN8YbvNhQA2S9d5rgWSe13VG82oy8F-H1kHFqwRjR6uyFaIv9UrSlh4rY5dwVcfpNuvdHAg5ZEblPVQ0HVBiopJQk4RgNrn5wcSpL5cyJ5WdVetsi43dy2w3ZIX2q8Nw_TCfGiE9DZxCCiaOeBGrdmQOd7we9RFj56EiclCUHzNsc></a>
</button>

        </section>

        <!-- Summary Cards -->
        <section class="cards">

           <div class="card"> <div class="menu">
                <h3><B>GP LEVEL LOGINS <B></h3>  
<li><a href=https://vbgramgde2.dord.gov.in/VBGRAMG/Login.aspx?level=HomeGP&state_code=16>👥 DATA ENTRY  </a></li>
<li><a href=https://vbgramgde2.dord.gov.in/VBGRAMG/Login.aspx?payload=cyp-rF8qV6f8R7u5E6K8kZ-RFbhKDD1vNXxQuR1yiYKpksKcOXTuK-W7AUXmLfU8>👥 E-Mbook GP level </a></li>
<li><a href=https://vbgramgde2.dord.gov.in/VBGRAMG/Login.aspx?payload=MF1kfMseiO8iXYQnp_Vx3G577wqhSdIn2m61HGpS4OfqJh2C8y0BReh28Fsg1iBe>👥 E-Mbook BP level </a></li>
<li><a href=https://vbgramgweb1.dord.gov.in/VBGRAMG/FTO/Login.aspx?&level=HomeACGP&state_code=16>👥 FIRST SIGNATORY  </a></li>
<li><a href=https://vbgramgweb1.dord.gov.in/VBGRAMG/FTO/Login.aspx?&level=HomeWLGP&state_code=16>👥 SECOND SIGNATORY  </a></li>
<li><a href=https://secure.dord.gov.in/securev2/>👥 SECURE  </a></li>
<li><a href=https://bims.treasury.kerala.gov.in/index.php/login>👥 BIMS  </a></li>
               
            </div>  </div>
 <!-- Summary Cards -->
        <section class="cards">

           <div class="card"> <div class="menu">
                <h3><B>FINANCIAL REPORTS <B></h3>  
<li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/FTO/FTOReport.aspx?payload=lXA_RoFCngGgxRTUYviDX_0Y9RLVb20Ro0rRteNNVKln6ExYElFGoKcbTc3FB0cdm_Gmm8c6lyfipcwDJcsrrOiuN1C9e4nHB4pIof5800hVjt8Ow_BG1S-ZPPFnUnfBRbcRnJFxrMYbODeSeiVGUskuqjy-e8ieGSWp-byr69OmnZv6AR58yqCqC5bVuOVSnxdJEC25wpibVIbpzJ8ITuXYisurcrqQF11nZQOz7cky0xYYBIQz6BcFBRcJR5l3MDOQ1hnph990bHDUjG0iF9bBrhvuqMUiJdJLEN3_DGZSQxYqcwHvVs8QKyjFUqV->💰 FTO Status  </a></li>
<li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/writereaddata/citizen_out/funddisreport_1602006_eng_2627_.html>💰 Financial Statement </a></li>
<li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/state_html/outlayvscomest.aspx?payload=2hvI1E8ppR41bd08-xA2Pt614VULcm6s5C9pNB_MOvZOIIzPaNyXetL0botG0O8LwcCoRhBQgIqihXkRfaTtA1NMfgMs9ae7K2e5RTG1e4fJ23OHsarZET1DVuf4Ht5J4tpfHj9YA9-HrXKurkM_29POzN0yLTrgXZS32zQF1PDiNLruai5VbCa0OG1dwuvECC2YTr7uU2zeGpEKA-WkXwSQG8yJoz5B_PPyaKa3-4wqdQlFDh9D4Bre7QXARu8sXN60M3ZJKBwngmYQqRFPpIjr8tUL8BCDkHfOinePGE4NlgTLFpo2IBko_Kb-sj5y>💰 Outlas & Outcomes </a></li>
<li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/citizen_html/continexpnew.aspx?payload=ukwBKzrdhNo8IZ78fm8qf48v0SaNsbv3RI5JzvmFhFORhDEE-lPdhtNQ0e-9_s2xH8l_ano2-RIfbY-05fpiOSE5CVrUIVV5O4qwAj3yQ2utnPbx_OfxcmM5c5gCYDhpRYso-hSqge6VTXD19iFG47ArwL5YkIy7UgdQD6xngy8>💰  Administration Expences  </a></li>
<li><a href=https://vbgramgrep.dord.gov.in/VBGRAMG/citizen_html/demregister.aspx?payload=Iidu8NmdACTwXHQuohpZzFUJ28rlMB4zbHlzbSisQOOv3NvpEBnGFG7vT1L25EXKdqynn1U17FyfpE7jZyq88VQGaPBwDNW8vJntp0_FE-iv2BFNb8kUEPggbJfkvA3RFVP_uUNG3E9c7IIPsnoB5ucHplXpWMKFLt6zlO7fh5R7330tLoAIf4ehI09ZxClUX-gruUxTZ3aR2FhGmtF4C6Nju-Poke4LT1Ad9wpcrlKMMQwPGUKMucgTr1qlw0bK0s3hCNweJRqDL7uYxoRG3N3jHRhILLy8wf2Pq4A-KQg>📊 Progress Report  </a></li>

               
            </div>  </div>


                                                   </div>

        </div>

        <footer>
            VBGRAMG Grama Panchayat Level Monitoring System Developed and Maintained By Jibin V K AITA Pattiam GP © 2026
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
