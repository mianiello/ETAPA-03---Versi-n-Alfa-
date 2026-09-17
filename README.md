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

        .slide.theme-dark {
            background-color: var(--bg-dark);
            color: var(--text-dark);
        }

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
    </style>
</head>
<body>

    <div class="presentation-container">
        <div class="slides-wrapper">

            <!-- DIAPO 1 -->
            <div class="slide theme-dark active" id="slide-1">
                <div class="cover-content">
                    <div style="margin-bottom: 1rem;">
                        <span class="badge-tag">CURSO 7° INFORMÁTICA B • EQUIPO N° 6</span>
                    </div>
                    <h1 class="cover-title">PROYECTO TA-DIN</h1>
                    <p class="cover-subtitle">Digitalización de procesos para una empresa de pintura electrostática</p>
                    
                    <div style="margin-top: 1.5rem;">
                        <p style="color: var(--text-dark-muted); font-size: 0.9rem; text-transform: uppercase; letter-spacing: 0.05em; font-weight: 700;">Integrantes y Roles</p>
                        <div class="team-grid">
                            <div class="team-member">
                                <div class="name">Mía Niello</div>
                                <div class="role">PM / Frontend</div>
                            </div>
                            <div class="team-member">
                                <div class="name">Catalina Quintana</div>
                                <div class="role">Frontend · UX/UI</div>
                            </div>
                            <div class="team-member">
                                <div class="name">Tatiana Bravo</div>
                                <div class="role">Backend</div>
                            </div>
                            <div class="team-member">
                                <div class="name">Nicolás Perri</div>
                                <div class="role">DB · Backend</div>
                            </div>
                            <div class="team-member">
                                <div class="name">Milagros Camino</div>
                                <div class="role">Infraestructura / Seg.</div>
                            </div>
                        </div>
                    </div>

                    <div style="margin-top: 2rem; color: var(--text-dark-muted); font-size: 0.85rem; font-family: var(--font-code);">
                        Fecha: Septiembre 2026
                    </div>
                </div>
            </div>

            <!-- DIAPO 2 -->
            <div class="slide" id="slide-2">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p>Contexto & Alcance</p>
                        <h2>Propósito del Proyecto y Módulos</h2>
                    </div>
                    <span class="badge-tag">DIAPO 02</span>
                </div>

                <div class="card" style="margin-bottom: 1.5rem; background: var(--primary-light); border-color: #a7f3d0;">
                    <p style="color: var(--primary-dark); font-weight: 600; font-size: 1.05rem;">
                        🎯 <strong>Objetivo Principal:</strong> TA-DIN busca profesionalizarse para captar clientes en los sectores petrolero, minero y telefónico[cite: 1]. La digitalización de sus procesos sienta las bases indispensables para avanzar hacia la certificación de las normas <strong>ISO 9001</strong> e <strong>ISO 14001</strong>[cite: 1].
                    </p>
                </div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">A</div>
                            <div class="card-title">Página Web</div>
                        </div>
                        <ul class="styled-list">
                            <li>Interfaz pública optimizada[cite: 1].</li>
                            <li>Posiciona la presencia digital de TA-DIN[cite: 1].</li>
                            <li>Canaliza consultas a través de Google Forms[cite: 1].</li>
                            <li>Captación ágil de clientes B2B[cite: 1].</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">B</div>
                            <div class="card-title">Reloj Biométrico</div>
                        </div>
                        <ul class="styled-list">
                            <li>Registro de fichadas en tiempo real[cite: 1].</li>
                            <li>Hardware biométrico ZKTeco[cite: 1].</li>
                            <li>Conexión directa a base de datos MySQL[cite: 1].</li>
                            <li>Seguimiento exacto de horarios y presentismo[cite: 1].</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">C</div>
                            <div class="card-title">Plataforma RRHH</div>
                        </div>
                        <ul class="styled-list">
                            <li>Procesamiento de datos de asistencia[cite: 1].</li>
                            <li>Paneles visuales y dashboards[cite: 1].</li>
                            <li>Cálculo exacto de horas netas trabajadas[cite: 1].</li>
                            <li>Exportación de liquidación de sueldos[cite: 1].</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- DIAPO 3 -->
            <div class="slide" id="slide-3">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p>Despliegue Comercial</p>
                        <h2>Avances en la Web e Integración NFC</h2>
                    </div>
                    <span class="badge-tag">DIAPO 03</span>
                </div>

                <div class="grid-2">
                    <div style="display: flex; flex-direction: column; gap: 1rem;">
                        <div class="card">
                            <div class="card-title" style="margin-bottom: 0.5rem;">Estado de la Web Institucional</div>
                            <p>La estructura principal del sitio web (<strong>tadin.com.ar</strong>) se encuentra finalizada[cite: 1]. Los trabajos recientes correspondieron a ajustes de estilo y optimizaciones menores[cite: 1].</p>
                        </div>

                        <div class="card">
                            <div class="card-title" style="margin-bottom: 0.5rem;">Innovación Comercial: Tarjetas NFC + QR</div>
                            <p style="margin-bottom: 0.75rem;">Se desplegó la ruta <strong>tadin.com.ar/contacto</strong> para interactuar de forma inmediata con clientes en reuniones o eventos de la industria[cite: 1]:</p>
                            <ul class="styled-list">
                                <li><strong>Tecnología NFC:</strong> Contacto directo aproximando la tarjeta al smartphone[cite: 1].</li>
                                <li><strong>Código QR de respaldo:</strong> Para dispositivos sin sensor NFC activo[cite: 1].</li>
                            </ul>
                        </div>
                    </div>

                    <div class="card" style="align-items: center; justify-content: center; background: #fafafa; border: 2px dashed var(--border-light);">
                        <div style="text-align: center; color: var(--text-light-muted);">
                            <p style="font-size: 2rem; margin-bottom: 0.5rem;">💳</p>
                            <p style="font-weight: 700;">Tarjeta Virtual NFC & QR</p>
                            <p style="font-size: 0.85rem; margin-top: 0.25rem;">tadin.com.ar/contacto</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- DIAPO 4 -->
            <div class="slide" id="slide-4">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p>Módulo C</p>
                        <h2>Página de Recursos Humanos</h2>
                    </div>
                    <span class="badge-tag">DIAPO 04</span>
                </div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);">1. Dashboard (Panel Principal)</div>
                        <p>Estado de red (IP/puerto del biométrico), total de empleados activos, fichadas del día y los últimos 5 movimientos físicos registrados[cite: 1].</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);">2. Gestión de Empleados</div>
                        <p>Altas y bajas[cite: 1]. <strong>Requisito clave:</strong> El "ID de Reloj" debe coincidir estrictamente con el número de enrolamiento del equipo ZKTeco[cite: 1].</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);">3. Registros Crudos</div>
                        <p>Caja negra del sistema[cite: 1]. Almacena marcaciones sin procesar[cite: 1]. Permite cargas manuales justificadas bajo clave de administrador[cite: 1].</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);">4. Liquidación de Horas</div>
                        <p>Motor matemático[cite: 1]. Filtra llegadas tardes y turnos incompletos para determinar Horas Netas a Pagar[cite: 1]. Exporta a Excel profesional[cite: 1].</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);">5. Matriz Mensual</div>
                        <p>Mapa de calor interactivo que audita el mes completo mediante códigos de color visuales (Presente, Ausente, Tarde, Olvido)[cite: 1].</p>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary-dark);">6. Configuración de Red</div>
                        <p>Administración de la IP del reloj, turnos corporativos (mañana/tarde) y los minutos de tolerancia de llegada tarde[cite: 1].</p>
                    </div>
                </div>
            </div>

            <!-- DIAPO 5 -->
            <div class="slide" id="slide-5">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p>Seguridad del Sistema</p>
                        <h2>Confirmación de Privilegios y Autenticación</h2>
                    </div>
                    <span class="badge-tag">DIAPO 05</span>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">🔐</div>
                            <div class="card-title">1. Control de Sesión Nativo ($_SESSION)</div>
                        </div>
                        <ul class="styled-list">
                            <li>Acceso restringido a todas las rutas PHP[cite: 1].</li>
                            <li>Requiere sesión activa iniciada previamente en <code>login.php</code>[cite: 1].</li>
                            <li>Si no existe token de sesión válido, el servidor redirige automáticamente al login sin renderizar datos[cite: 1].</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-header">
                            <div class="card-icon">🛡️</div>
                            <div class="card-title">2. Protocolo de Confirmación de Privilegios</div>
                        </div>
                        <p style="margin-bottom: 0.75rem;">Para acciones de alto impacto (cargas manuales de marcaciones, justificación de ausencias o bajas)[cite: 1]:</p>
                        <ul class="styled-list">
                            <li>La sesión de administrador activa <strong>no es suficiente</strong>[cite: 1].</li>
                            <li>La petición <code>HTTP POST</code> exige la contraseña del administrador[cite: 1].</li>
                            <li>El backend re-valida la clave contra MySQL antes de autorizar cualquier sentencia <code>INSERT</code> o <code>DELETE</code>[cite: 1].</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- DIAPO 6 -->
            <div class="slide" id="slide-6">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p>Arquitectura de Software</p>
                        <h2>Documentación Técnica de Módulos</h2>
                    </div>
                    <span class="badge-tag">DIAPO 06</span>
                </div>

                <div class="grid-3">
                    <div class="card">
                        <div class="card-title" style="color: var(--primary);">Módulo A: Web Institucional</div>
                        <ul class="styled-list" style="margin-top: 0.5rem;">
                            <li><strong>Frontend:</strong> HTML5, CSS3 Responsivo[cite: 1].</li>
                            <li><strong>Servidor:</strong> Hosting DonWeb vía FTP (FileZilla)[cite: 1].</li>
                            <li><strong>Objetivo:</strong> Posicionamiento B2B[cite: 1].</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary);">Módulo B: Reloj Biométrico</div>
                        <ul class="styled-list" style="margin-top: 0.5rem;">
                            <li><strong>Hardware:</strong> ZKTeco + ZKBioTime.Net[cite: 1].</li>
                            <li><strong>Red:</strong> TCP/IP en Red Local[cite: 1].</li>
                            <li><strong>Tablas clave:</strong> <code>USUARIO</code> y <code>LOG_MARCACION</code>[cite: 1].</li>
                            <li><strong>Algoritmo:</strong> Match 1:N (&lt; 1s)[cite: 1].</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-title" style="color: var(--primary);">Módulo C: Plataforma RRHH</div>
                        <ul class="styled-list" style="margin-top: 0.5rem;">
                            <li><strong>Stack:</strong> PHP 8 (SSR), MySQL, Bootstrap 5.3, JS Vanilla[cite: 1].</li>
                            <li><strong>Tablas MySQL:</strong> <code>empleados</code>, <code>registros_asistencia</code>, <code>configuracion</code>[cite: 1].</li>
                            <li><strong>Reportes:</strong> Exportador nativo a Excel (<code>.xls</code>)[cite: 1].</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- DIAPO 7 -->
            <div class="slide" id="slide-7">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p>Operación y Buenas Prácticas</p>
                        <h2>Manual de Usuario & Contingencias</h2>
                    </div>
                    <span class="badge-tag">DIAPO 07</span>
                </div>

                <div class="grid-2">
                    <div class="card">
                        <div class="card-title" style="margin-bottom: 0.75rem;">📷 Operativa del Reloj iFace (Hardware)</div>
                        <ul class="styled-list">
                            <li><strong>Identificación:</strong> Reconocimiento facial, huella dactilar, clave o tarjeta RFID[cite: 1].</li>
                            <li><strong>Uso correcto:</strong> Rostro a 0.5m erguido y neutral[cite: 1]. Para huellas, usar dedo índice o medio centrado[cite: 1].</li>
                            <li><strong>Falla de red/Luz:</strong> Memoria no volátil offline[cite: 1]. Sincroniza al volver la red o mediante USB FAT32[cite: 1].</li>
                        </ul>
                    </div>

                    <div class="card">
                        <div class="card-title" style="margin-bottom: 0.75rem;">🎨 Matriz Mensual de Asistencia (Simbología)</div>
                        <div style="display: flex; flex-direction: column; gap: 0.4rem;">
                            <div><span class="status-pill bg-verde">Verde</span> <span style="font-size: 0.85rem;">Asistencia Correcta[cite: 1]</span></div>
                            <div><span class="status-pill bg-naranja">Naranja</span> <span style="font-size: 0.85rem;">Llegada Tarde (Excede tolerancia)[cite: 1]</span></div>
                            <div><span class="status-pill bg-azul">Azul (!)</span> <span style="font-size: 0.85rem;">Turno Incompleto / Olvido de Salida[cite: 1]</span></div>
                            <div><span class="status-pill bg-rojo">Rojo</span> <span style="font-size: 0.85rem;">Ausente / Falta Justificada[cite: 1]</span></div>
                            <div><span class="status-pill bg-gris">Gris (🌙)</span> <span style="font-size: 0.85rem;">Fichada Fuera de Turno[cite: 1]</span></div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- DIAPO 8 -->
            <div class="slide" id="slide-8">
                <div class="slide-header">
                    <div class="slide-title-group">
                        <p>Demostración Visual</p>
                        <h2>Landing Page & Presencia Digital</h2>
                    </div>
                    <span class="badge-tag">DIAPO 08</span>
                </div>

                <div class="card" style="height: 80%; justify-content: center; align-items: center; background: #0f172a; border-color: #334155;">
                    <div style="text-align: center; color: white;">
                        <p style="font-size: 1.25rem; font-weight: 700; color: var(--primary-bright); margin-bottom: 0.5rem;">
                            🌐 Sitio Web Oficial: tadin.com.ar
                        </p>
                        <p style="color: var(--text-dark-muted); max-width: 600px; margin: 0 auto 1.5rem auto;">
                            Diseñado con enfoque en conversión industrial, velocidad de carga y adaptabilidad total a pantallas de computadoras y dispositivos móviles.
                        </p>
                        <div class="code-box" style="display: inline-block; text-align: left;">
                            HTTP GET / 200 OK<br>
                            SSL Certificate: Active (HTTPS)<br>
                            Lead Capture Integration: Active
                        </div>
                    </div>
                </div>
            </div>

            <!-- DIAPO 9 -->
            <div class="slide theme-dark" id="slide-9">
                <div class="cover-content" style="text-align: center;">
                    <h1 class="cover-title">¡Muchas Gracias!</h1>
                    <p class="cover-subtitle">Proyecto TA-DIN • Preguntas y Comentarios</p>
                    <div style="margin-top: 2rem;">
                        <span class="badge-tag">EQUIPO N° 6 • SEPTIEMBRE 2026</span>
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

        document.addEventListener('keydown', function(e) {
            if (e.key === "ArrowRight" || e.key === "PageDown") {
                changeSlide(1);
            } else if (e.key === "ArrowLeft" || e.key === "PageUp") {
                changeSlide(-1);
            }
        });

        updateSlide();
    </script>
</body>
</html>
