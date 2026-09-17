<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Presentación Proyecto TA-DIN - Equipo 6</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-dark: #061a14;
            --bg-dark-card: #0a2920;
            --bg-light: #f8fafc;
            --bg-light-card: #ffffff;
            
            --text-dark: #f1f5f9;
            --text-dark-muted: #94a3b8;
            --text-light: #0f172a;
            --text-light-muted: #64748b;
            
            --primary: #059669;
            --primary-bright: #34d399;
            --primary-light: #d1fae5;
            --primary-dark: #047857;
            
            --accent: #10b981;
            --border-light: #e2e8f0;
            --border-dark: #134e40;
            
            --status-green: #10b981;
            --status-orange: #f59e0b;
            --status-blue: #3b82f6;
            --status-red: #ef4444;
            --status-gray: #6b7280;
            
            --font-main: 'Plus Jakarta Sans', sans-serif;
            --font-code: 'JetBrains Mono', monospace;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: var(--font-main);
            background-color: #030a08;
            color: var(--text-light);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
        }

        /* Presentation Container */
        .presentation-container {
            width: 100vw;
            height: 100vh;
            max-width: 1600px;
            max-height: 900px;
            position: relative;
            background-color: var(--bg-light);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }

        /* Slides Wrapper */
        .slides-wrapper {
            flex: 1;
            position: relative;
            width: 100%;
            height: 100%;
        }

        .slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.4s ease, transform 0.4s ease;
            transform: scale(0.98);
            padding: 3.5rem 4rem;
            display: flex;
            flex-direction: column;
            overflow-y: auto;
            background-color: var(--bg-light);
            color: var(--text-light);
        }

        .slide.active {
            opacity: 1;
            visibility: visible;
            transform: scale(1);
            z-index: 2;
        }

        /* Theme Variations for Slides */
        .slide.theme-dark {
            background-color: var(--bg-dark);
            color: var(--text-dark);
        }

        /* Slide Header */
        .slide-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 2rem;
            border-bottom: 2px solid var(--border-light);
            padding-bottom: 1rem;
        }

        .slide.theme-dark .slide-header {
            border-bottom-color: var(--border-dark);
        }

        .slide-title-group h2 {
            font-size: 2.2rem;
            font-weight: 800;
            letter-spacing: -0.025em;
            color: var(--text-light);
            line-height: 1.2;
        }

        .slide.theme-dark .slide-title-group h2 {
            color: var(--text-dark);
        }

        .slide-title-group p {
            font-size: 1rem;
            color: var(--primary);
            font-weight: 600;
            margin-top: 0.25rem;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        .slide.theme-dark .slide-title-group p {
            color: var(--primary-bright);
        }

        .badge-tag {
            background: var(--primary-light);
            color: var(--primary-dark);
            padding: 0.4rem 0.8rem;
            border-radius: 6px;
            font-size: 0.85rem;
            font-weight: 700;
            font-family: var(--font-code);
        }

        .slide.theme-dark .badge-tag {
            background: var(--border-dark);
            color: var(--primary-bright);
        }

        /* Grid Layouts */
        .grid-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            flex: 1;
        }

        .grid-3 {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 1.5rem;
            flex: 1;
        }

        .grid-1-2 {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 2rem;
            flex: 1;
        }

        /* Card Elements */
        .card {
            background: var(--bg-light-card);
            border: 1px solid var(--border-light);
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
            display: flex;
            flex-direction: column;
        }

        .slide.theme-dark .card {
            background: var(--bg-dark-card);
            border-color: var(--border-dark);
            box-shadow: none;
        }

        .card-header {
            display: flex;
            align-items: center;
            gap: 0.75rem;
            margin-bottom: 1rem;
        }

        .card-icon {
            width: 36px;
            height: 36px;
            border-radius: 8px;
            background: var(--primary-light);
            color: var(--primary-dark);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.1rem;
        }

        .slide.theme-dark .card-icon {
            background: var(--border-dark);
            color: var(--primary-bright);
        }

        .card-title {
            font-size: 1.25rem;
            font-weight: 700;
        }

        /* Typography & Lists */
        p, li {
            font-size: 0.95rem;
            line-height: 1.6;
            color: var(--text-light-muted);
        }

        .slide.theme-dark p, 
        .slide.theme-dark li {
            color: var(--text-dark-muted);
        }

        strong {
            color: var(--text-light);
        }

        .slide.theme-dark strong {
            color: var(--text-dark);
        }

        ul {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 0.6rem;
        }

        ul.styled-list li {
            position: relative;
            padding-left: 1.25rem;
        }

        ul.styled-list li::before {
            content: "▪";
            position: absolute;
            left: 0;
            color: var(--primary);
            font-size: 1.2rem;
            line-height: 1;
        }

        .slide.theme-dark ul.styled-list li::before {
            color: var(--primary-bright);
        }

        /* Specific Cover Slide */
        .cover-content {
            display: flex;
            flex-direction: column;
            justify-content: center;
            height: 100%;
            max-width: 1000px;
            margin: 0 auto;
        }

        .cover-title {
            font-size: 4rem;
            font-weight: 800;
            letter-spacing: -0.04em;
            color: #ffffff;
            line-height: 1.1;
            margin-bottom: 0.5rem;
        }

        .cover-subtitle {
            font-size: 1.5rem;
            color: var(--primary-bright);
            font-weight: 500;
            margin-bottom: 2.5rem;
        }

        .team-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .team-member {
            background: var(--bg-dark-card);
            border: 1px solid var(--border-dark);
            padding: 1rem;
            border-radius: 8px;
        }

        .team-member .name {
            font-weight: 700;
            color: #ffffff;
            font-size: 1rem;
        }

        .team-member .role {
            font-size: 0.8rem;
            color: var(--primary-bright);
            font-weight: 600;
        }

        /* Matrix Status Palette */
        .status-pill {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.3rem 0.6rem;
            border-radius: 6px;
            font-size: 0.8rem;
            font-weight: 700;
            color: white;
            margin-bottom: 0.4rem;
        }

        .bg-verde { background-color: var(--status-green); }
        .bg-naranja { background-color: var(--status-orange); }
        .bg-azul { background-color: var(--status-blue); }
        .bg-rojo { background-color: var(--status-red); }
        .bg-gris { background-color: var(--status-gray); }

        /* Code Block Mock */
        .code-box {
            font-family: var(--font-code);
            background: #020d09;
            color: #34d399;
            padding: 1rem;
            border-radius: 8px;
            font-size: 0.85rem;
            border: 1px solid var(--border-dark);
            overflow-x: auto;
            margin-top: 0.5rem;
        }

        /* Images / Visual Mockups */
        .img-card {
            width: 100%;
            height: 100%;
            max-height: 380px;
            object-fit: cover;
            border-radius: 8px;
            border: 1px solid var(--border-light);
        }

        /* Navigation Bar */
        .nav-bar {
            height: 60px;
            background: var(--bg-dark);
            border-top: 1px solid var(--border-dark);
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
            z-index: 10;
        }

        .nav-controls {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .btn-nav {
            background: var(--bg-dark-card);
            border: 1px solid var(--border-dark);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.9rem;
            transition: all 0.2s;
        }

        .btn-nav:hover {
            background: var(--primary);
            border-color: var(--primary);
        }

        .btn-nav:disabled {
            opacity: 0.3;
            cursor: not-allowed;
            background: var(--bg-dark-card);
            border-color: var(--border-dark);
        }

        .slide-indicator {
            color: var(--text-dark-muted);
            font-size: 0.9rem;
            font-weight: 600;
            font-family: var(--font-code);
        }

        /* Helper for editable text */
        [contenteditable="true"]:hover {
            outline: 1px dashed var(--primary-bright);
        }

        [contenteditable="true"]:focus {
            outline: 2px solid var(--primary-bright);
            background: rgba(52, 211, 153, 0.05);
        }
    </style>
</head>
<body>

    <div class="presentation-container">
        <div class="slides-wrapper">

            <!-- DIAPO 1: CARÁTULA -->
            <div class="slide theme-dark active" id="slide-1">
                <div class="cover-content">
                    <div style="margin-bottom: 1rem;">
                        <span class="badge-tag" contenteditable="true">CURSO 7° INFORMÁTICA B • EQUIPO N° 6</span>
                    </div>
                    <h1 class="cover-title" contenteditable="true">PROYECTO TA-DIN</h1>
                    <p class="cover-subtitle" contenteditable="true">Digitalización de procesos para una empresa de pintura electrostática</p>
                    
                    <div style="margin-top: 1.5rem;">
                        <p style="color: var(--text-dark-muted); font-size: 0.9rem; text-transform: uppercase; letter-spacing: 0.05em; font-weight: 700;" contenteditable="true">Integrantes y Roles</p>
                        <div class="team-grid">
                            <div class="team-member">
                                <div class="name" contenteditable="true">Mía Niello</div>
                                <div class="role" contenteditable="true">PM / Frontend</div>
                            </div>
                            <div class="team-member">
                                <div class="name" contenteditable="true">Catalina Quintana</div>
                                <div class="role" contenteditable="true">Frontend · UX/UI</div>
                            </div>
                            <div class="team-member">
                                <div class="name" contenteditable="true">Tatiana Bravo</div>
                                <div class="role" contenteditable="true">Backend</div>
                            </div>
                            <div class="team-member">
                                <div class="name" contenteditable="true">Nicolás Perri</div>
                                <div class="role" contenteditable="true">DB · Backend</div>
                            </div>
                            <div class="team-member">
                                <div class="name" contenteditable="true">Milagros Camino</div>
                                <div class="role" contenteditable="true">Infraestructura / Seg.</div>
                            </div>
                        </div>
                    </div>

                    <div style="margin-top: 2rem; color: var(--text-dark-muted); font-size: 0.85rem; font-family: var(--font-code);" contenteditable="true">
                        Fecha: Septiembre 2026
                    </div>
                </div>
            </div>

            <!-- DIAPO 2: PROPÓSITO Y MÓDULOS -->
            <div class="slide" id="slide-2">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p contenteditable="true">Contexto & Alcance</p>
                        <h2 contenteditable="true">Propósito del Proyecto y Módulos</h2>
                    </div>
                    <span class="badge-tag" contenteditable="true">DIAPO 02</span>
                </div>

                <div class="card" style="margin-bottom: 1.5rem; background: var(--primary-light); border-color: #a7f3d0;">
                    <p style="color: var(--primary-dark); font-weight: 600; font-size: 1.05rem;" contenteditable="true">
                        🎯 <strong>Objetivo Principal:</strong> TA-DIN busca profesionalizarse para captar clientes en los sectores petrolero, minero y telefónico. La digitalización de sus procesos sienta las bases indispensables para avanzar hacia la certificación de las normas <strong>ISO 9001</strong> e <strong>ISO 14001</strong>.
                    </p>
                </div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">A</div>
                            <div class="card-title" contenteditable="true">Página Web</div>
                        </div>
                        <ul class="styled-list">
                            <li contenteditable="true">Interfaz pública optimizada.</li>
                            <li contenteditable="true">Posiciona la presencia digital de TA-DIN.</li>
                            <li contenteditable="true">Canaliza consultas a través de Google Forms.</li>
                            <li contenteditable="true">Captación ágil de clientes B2B.</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">B</div>
                            <div class="card-title" contenteditable="true">Reloj Biométrico</div>
                        </div>
                        <ul class="styled-list">
                            <li contenteditable="true">Registro de fichadas en tiempo real.</li>
                            <li contenteditable="true">Hardware biométrico ZKTeco.</li>
                            <li contenteditable="true">Conexión directa a base de datos MySQL.</li>
                            <li contenteditable="true">Seguimiento exacto de horarios y presentismo.</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">C</div>
                            <div class="card-title" contenteditable="true">Plataforma RRHH</div>
                        </div>
                        <ul class="styled-list">
                            <li contenteditable="true">Procesamiento de datos de asistencia.</li>
                            <li contenteditable="true">Paneles visuales y dashboards.</li>
                            <li contenteditable="true">Cálculo exacto de horas netas trabajadas.</li>
                            <li contenteditable="true">Exportación de liquidación de sueldos.</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- DIAPO 3: AVANCES & TECNOLOGÍA NFC -->
            <div class="slide" id="slide-3">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p contenteditable="true">Despliegue Comercial</p>
                        <h2 contenteditable="true">Avances en la Web e Integración NFC</h2>
                    </div>
                    <span class="badge-tag" contenteditable="true">DIAPO 03</span>
                </div>

                <div class="grid-2">
                    <div style="display: flex; flex-direction: column; gap: 1rem;">
                        <div class="card">
                            <div class="card-title" style="margin-bottom: 0.5rem;" contenteditable="true">Estado de la Web Institucional</div>
                            <p contenteditable="true">La estructura principal del sitio web (<strong>tadin.com.ar</strong>) se encuentra finalizada. Los trabajos recientes correspondieron a ajustes de estilo y optimizaciones menores.</p>
                        </div>

                        <div class="card">
                            <div class="card-title" style="margin-bottom: 0.5rem;" contenteditable="true">Innovación Comercial: Tarjetas NFC + QR</div>
                            <p contenteditable="true" style="margin-bottom: 0.75rem;">Se desplegó la ruta <strong>tadin.com.ar/contacto</strong> para interactuar de forma inmediata con clientes en reuniones o eventos de la industria:</p>
                            <ul class="styled-list">
                                <li contenteditable="true"><strong>Tecnología NFC:</strong> Contacto directo aproximando la tarjeta al smartphone.</li>
                                <li contenteditable="true"><strong>Código QR de respaldo:</strong> Para dispositivos sin sensor NFC activo.</li>
                            </ul>
                        </div>
                    </div>

                    <div class="card" style="align-items: center; justify-content: center; background: #fafafa;">
                        <img src="http://googleusercontent.com/image_collection/image_retrieval/4026302465452109570_0" alt="Tarjeta NFC TA-DIN" class="img-card">
                    </div>
                </div>
            </div>

            <!-- DIAPO 4: MÓDULO C - RECURSOS HUMANOS -->
            <div class="slide" id="slide-4">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p contenteditable="true">Módulo C</p>
                        <h2 contenteditable="true">Página de Recursos Humanos</h2>
                    </div>
                    <span class="badge-tag" contenteditable="true">DIAPO 04</span>
                </div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);" contenteditable="true">1. Dashboard (Panel Principal)</div>
                        <p contenteditable="true">Estado de red (IP/puerto del biométrico), total de empleados activos, fichadas del día y los últimos 5 movimientos físicos registrados.</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);" contenteditable="true">2. Gestión de Empleados</div>
                        <p contenteditable="true">Altas y bajas. <strong>Requisito clave:</strong> El "ID de Reloj" debe coincidir estrictamente con el número de enrolamiento del equipo ZKTeco.</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);" contenteditable="true">3. Registros Crudos</div>
                        <p contenteditable="true">Caja negra del sistema. Almacena marcaciones sin procesar. Permite cargas manuales justificadas bajo clave de administrador.</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);" contenteditable="true">4. Liquidación de Horas</div>
                        <p contenteditable="true">Motor matemático. Filtra llegadas tardes y turnos incompletos para determinar Horas Netas a Pagar. Exporta a Excel profesional.</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);" contenteditable="true">5. Matriz Mensual</div>
                        <p contenteditable="true">Mapa de calor interactivo que audita el mes completo mediante códigos de color visuales (Presente, Ausente, Tarde, Olvido).</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);" contenteditable="true">6. Configuración de Red</div>
                        <p contenteditable="true">Administración de la IP del reloj, turnos corporativos (mañana/tarde) y los minutos de tolerancia de llegada tarde.</p>
                    </div>
                </div>
            </div>

            <!-- DIAPO 5: SEGURIDAD Y PRIVILEGIOS -->
            <div class="slide" id="slide-5">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p contenteditable="true">Seguridad del Sistema</p>
                        <h2 contenteditable="true">Confirmación de Privilegios y Autenticación</h2>
                    </div>
                    <span class="badge-tag" contenteditable="true">DIAPO 05</span>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">🔐</div>
                            <div class="card-title" contenteditable="true">1. Control de Sesión Native ($_SESSION)</div>
                        </div>
                        <ul class="styled-list">
                            <li contenteditable="true">Acceso restringido a todas las rutas PHP.</li>
                            <li contenteditable="true">Requiere sesión activa iniciada previamente en <code>login.php</code>.</li>
                            <li contenteditable="true">Si no se detecta token de sesión válido, el servidor redirige automáticamente al login sin renderizar datos.</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">🛡️</div>
                            <div class="card-title" contenteditable="true">2. Protocolo de Confirmación de Privilegios</div>
                        </div>
                        <p contenteditable="true" style="margin-bottom: 0.75rem;">Para acciones de alto impacto (cargas manuales de marcaciones, justificación de ausencias o eliminación de datos):</p>
                        <ul class="styled-list">
                            <li contenteditable="true">La sesión de administrador activa <strong>no es suficiente</strong>.</li>
                            <li contenteditable="true">La petición <code>HTTP POST</code> debe incluir la contraseña actual del administrador.</li>
                            <li contenteditable="true">El backend re-valida la clave contra MySQL antes de autorizar cualquier sentencia <code>INSERT</code> o <code>DELETE</code>.</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- DIAPO 6: DOCUMENTACIÓN TÉCNICA -->
            <div class="slide" id="slide-6">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p contenteditable="true">Arquitectura de Software</p>
                        <h2 contenteditable="true">Documentación Técnica de Módulos</h2>
                    </div>
                    <span class="badge-tag" contenteditable="true">DIAPO 06</span>
                </div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-title" style="color: var(--primary);" contenteditable="true">Módulo A: Web Institucional</div>
                        <ul class="styled-list" style="margin-top: 0.5rem;">
                            <li contenteditable="true"><strong>Frontend:</strong> HTML5, CSS3 Responsivo.</li>
                            <li contenteditable="true"><strong>Servidor:</strong> Hosting DonWeb vía FTP (FileZilla).</li>
                            <li contenteditable="true"><strong>Objetivo:</strong> Posicionamiento B2B.</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary);" contenteditable="true">Módulo B: Reloj Biométrico</div>
                        <ul class="styled-list" style="margin-top: 0.5rem;">
                            <li contenteditable="true"><strong>Hardware:</strong> ZKTeco + ZKBioTime.Net.</li>
                            <li contenteditable="true"><strong>Red:</strong> TCP/IP en Red Local.</li>
                            <li contenteditable="true"><strong>Tablas clave:</strong> <code>USUARIO</code> (Templates faciales y de huella) y <code>LOG_MARCACION</code>.</li>
                            <li contenteditable="true"><strong>Algoritmo:</strong> Match 1:N (&lt; 1s).</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary);" contenteditable="true">Módulo C: Plataforma RRHH</div>
                        <ul class="styled-list" style="margin-top: 0.5rem;">
                            <li contenteditable="true"><strong>Stack:</strong> PHP 8 (SSR), MySQL, Bootstrap 5.3, JS Vanilla.</li>
                            <li contenteditable="true"><strong>Tablas MySQL:</strong> <code>empleados</code>, <code>registros_asistencia</code>, <code>configuracion</code>.</li>
                            <li contenteditable="true"><strong>Reportes:</strong> Exportador nativo a Excel (<code>.xls</code>).</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- DIAPO 7: MANUAL DE USUARIO & FAQ -->
            <div class="slide" id="slide-7">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p contenteditable="true">Operación y Buenas Prácticas</p>
                        <h2 contenteditable="true">Manual de Usuario & Contingencias</h2>
                    </div>
                    <span class="badge-tag" contenteditable="true">DIAPO 07</span>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <div class="card-title" style="margin-bottom: 0.75rem;" contenteditable="true">📷 Operativa del Reloj iFace (Hardware)</div>
                        <ul class="styled-list">
                            <li contenteditable="true"><strong>Identificación:</strong> Reconocimiento facial, huella dactilar, clave o tarjeta RFID.</li>
                            <li contenteditable="true"><strong>Uso correcto:</strong> Rostro a 0.5m erguido y neutral. Para huellas, usar dedo índice o medio bien centrado.</li>
                            <li contenteditable="true"><strong>Falla de red/Luz:</strong> Memoria no volátil offline. Sincroniza al volver el enlace o mediante USB FAT32.</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-title" style="margin-bottom: 0.75rem;" contenteditable="true">🎨 Matriz Mensual de Asistencia (Simbología)</div>
                        <div style="display: flex; flex-direction: column; gap: 0.4rem;">
                            <div><span class="status-pill bg-verde">Verde</span> <span style="font-size: 0.85rem;" contenteditable="true">Asistencia Correcta</span></div>
                            <div><span class="status-pill bg-naranja">Naranja</span> <span style="font-size: 0.85rem;" contenteditable="true">Llegada Tarde (Excede tolerancia)</span></div>
                            <div><span class="status-pill bg-azul">Azul (!)</span> <span style="font-size: 0.85rem;" contenteditable="true">Turno Incompleto / Olvido de Salida</span></div>
                            <div><span class="status-pill bg-rojo">Rojo</span> <span style="font-size: 0.85rem;" contenteditable="true">Ausente / Falta Justificada</span></div>
                            <div><span class="status-pill bg-gris">Gris (🌙)</span> <span style="font-size: 0.85rem;" contenteditable="true">Fichada Fuera de Turno</span></div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- DIAPO 8: LANDING PAGE SHOWCASE -->
            <div class="slide" id="slide-8">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p contenteditable="true">Demostración Visual</p>
                        <h2 contenteditable="true">Landing Page & Presencia Digital</h2>
                    </div>
                    <span class="badge-tag" contenteditable="true">DIAPO 08</span>
                </div>

                <div class="card" style="height: 80%; justify-content: center; align-items: center; background: #0f172a; border-color: #334155;">
                    <div style="text-align: center; color: white;">
                        <p style="font-size: 1.25rem; font-weight: 700; color: var(--primary-bright); margin-bottom: 0.5rem;" contenteditable="true">
                            🌐 Sitio Web Oficial: tadin.com.ar
                        </p>
                        <p style="color: var(--text-dark-muted); max-width: 600px; margin: 0 auto 1.5rem auto;" contenteditable="true">
                            Diseñado con enfoque en conversión industrial, velocidad de carga y adaptabilidad total a pantallas de computadoras y dispositivos móviles.
                        </p>
                        <div class="code-box" style="display: inline-block; text-align: left;" contenteditable="true">
                            HTTP GET / 200 OK<br>
                            SSL Certificate: Active (HTTPS)<br>
                            Lead Capture Integration: Active
                        </div>
                    </div>
                </div>
            </div>

            <!-- DIAPO 9: CIERRE / CARÁTULA FINAL -->
            <div class="slide theme-dark" id="slide-9">
                <div class="cover-content" style="text-align: center;">
                    <h1 class="cover-title" contenteditable="true">¡Muchas Gracias!</h1>
                    <p class="cover-subtitle" contenteditable="true">Proyecto TA-DIN • Preguntas y Comentarios</p>
                    <div style="margin-top: 2rem;">
                        <span class="badge-tag" contenteditable="true">EQUIPO N° 6 • SEPTIEMBRE 2026</span>
                    </div>
                </div>
            </div>

        </div>

        <!-- Barra de Navegación -->
        <div class="nav-bar">
            <div class="slide-indicator">
                Diapositiva <span id="current-slide">1</span> de <span id="total-slides">9</span>
            </div>
            <div class="nav-controls">
                <button class="btn-nav" id="prev-btn" onclick="changeSlide(-1)">❮ Anterior</button>
                <button class="btn-nav" id="next-btn" onclick="changeSlide(1)">Siguiente ❯</button>
            </div>
        </div>
    </div>

    <script>
        let currentSlide = 0;
        const slides = document.querySelectorAll('.slide');
        const totalSlides = slides.length;

        document.getElementById('total-slides').innerText = totalSlides;

        function updateSlide() {
            slides.forEach((slide, index) => {
                if (index === currentSlide) {
                    slide.classList.add('active');
                } else {
                    slide.classList.remove('active');
                }
            });

            document.getElementById('current-slide').innerText = currentSlide + 1;
            document.getElementById('prev-btn').disabled = (currentSlide === 0);
            document.getElementById('next-btn').disabled = (currentSlide === totalSlides - 1);
        }

        function changeSlide(direction) {
            currentSlide += direction;
            if (currentSlide < 0) currentSlide = 0;
            if (currentSlide >= totalSlides) currentSlide = totalSlides - 1;
            updateSlide();
        }

        // Navegación mediante teclado (flechas de dirección)
        document.addEventListener('keydown', function(e) {
            if (e.key === "ArrowRight" || e.key === "PageDown") {
                changeSlide(1);
            } else if (e.key === "ArrowLeft" || e.key === "PageUp") {
                changeSlide(-1);
            }
        });

        // Inicializar
        updateSlide();
    </script>
</body>
</html>.ar/contacto)[cite: 1]
