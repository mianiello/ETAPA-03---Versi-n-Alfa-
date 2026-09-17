# 🚀 Proyecto TA-DIN - Digitalización de Procesos Industriales

> **Digitalización de procesos operativos y de control para una empresa de pintura electrostática.**  
> Este proyecto busca profesionalizar la gestión interna de TA-DIN para facilitar su transición e implementación hacia la certificación de las normas **ISO 9001** e **ISO 14001**.

---

## 👥 Datos del Equipo

* **Curso:** 7mo Informática B
* **Equipo:** N° 6
* **Fecha:** Septiembre 2026[cite: 1]

### 🛠️ Integrantes y Roles
* **Mía Niello:** Project Manager (PM) / Frontend Developer[cite: 1]
* **Catalina Quintana:** Frontend Developer / UX/UI Designer[cite: 1]
* **Tatiana Bravo:** Backend Developer[cite: 1]
* **Nicolás Perri:** Database Administrator (DB) / Backend Developer[cite: 1]
* **Milagros Camino:** Infraestructura de Seguridad[cite: 1]

---

## 📌 Visión General del Proyecto

**TA-DIN** es una empresa de servicios de pintura electrostática que busca posicionarse para captar clientes en los sectores petrolero, minero y telefónico[cite: 1]. El sistema digitaliza áreas clave para optimizar la toma de decisiones y cumplir con estándares de calidad internacionales[cite: 1].

### 🧱 Módulos del Sistema
1. **Módulo A – Página Web Institucional:** Interfaz pública para posicionamiento digital, captación B2B y canalización de consultas[cite: 1].
2. **Módulo B – Reloj Biométrico de Asistencias:** Integración de hardware biométrico (ZKTeco) conectado con MySQL para captura de fichadas en tiempo real[cite: 1].
3. **Módulo C – Plataforma Web de Recursos Humanos:** Procesamiento de marcas de asistencia, cálculo de horas laborales, matriz mensual auditables y generación de reportes para liquidación[cite: 1].
4. **Integración Comercial NFC:** Tarjetas de presentación interactivas para derivar clientes a la sección de contacto mediante tecnología NFC y códigos QR[cite: 1].

---

## 💻 Arquitectura y Stack Tecnológico

| Módulo | Tecnologías / Herramientas |
| :--- | :--- |
| **Módulo A (Página Web)** | HTML5, CSS3 (Responsive Design), Google Forms, Hosting DonWeb (FTP FileZilla)[cite: 1]. |
| **Módulo B (Biométrico)** | Hardware ZKTeco (iFace), ZKBioTime.Net, TCP/IP, SQLite / MySQL[cite: 1]. |
| **Módulo C (Panel RRHH)** | PHP 8 (SSR), MySQL, Bootstrap 5.3, JavaScript Vanilla[cite: 1]. |
| **Integración NFC** | Dispositivos físicos pasivos NFC + Códigos QR bidimensionales[cite: 1]. |

---

## ⚙️ Funcionalidades del Panel de RRHH (Módulo C)

* **Dashboard (Panel Principal):** Estado del hardware biométrico en tiempo real, conteo de empleados activos, métricas del día y últimas 5 fichadas[cite: 1].
* **Gestión de Empleados:** Alta, baja y vinculación unívoca entre el `ID de Reloj` y la base de datos MySQL[cite: 1].
* **Registros Crudos (Caja Negra):** Historial completo de marcaciones sin procesar. Permite cargas manuales justificadas[cite: 1].
* **Motor de Liquidación de Horas:** Cálculo automatizado de horas netas a pagar descontando llegadas tardes e inconsistencias[cite: 1].
* **Exportación de Reportes:** Generación nativa de planillas de liquidación en formato `.xls` (Excel)[cite: 1].
* **Matriz Mensual Auditables:** Mapa de calor con iconografía y códigos de color:
  * 🟢 **Verde:** Asistencia correcta[cite: 1].
  * 🟠 **Naranja:** Llegada tarde (supera tolerancia)[cite: 1].
  * 🔵 **Azul:** Olvido de fichada de salida / turno incompleto[cite: 1].
  * 🔴 **Rojo:** Ausencia[cite: 1].
  * ⚪ **Gris:** Marcación fuera de turno[cite: 1].

---

## 🔒 Seguridad y Protocolos de Privilegios

1. **Control de Sesión Nativo (`$_SESSION`):** Redirección inmediata a `login.php` ante accesos no autenticados en las rutas PHP[cite: 1].
2. **Protocolo de Confirmación de Privilegios:** Para acciones destructivas o sensibles (cargas manuales de asistencias, modificación de parámetros o bajas), el servidor requiere la re-ingreso activo de la contraseña de administrador vía `HTTP POST` antes de ejecutar transacciones SQL (`INSERT` / `DELETE`)[cite: 1].

---

## 📖 Manual Operativo y Guía de Uso (FAQ)

### 1. Operativa del Reloj Biométrico (ZKTeco)
* **Métodos soportados:** Reconocimiento facial, huella dactilar, tarjeta RFID y contraseña[cite: 1].
* **Uso recomendado:** Ubicarse a 0,5 metros con rostro descubierto para validación facial[cite: 1]. Para huella, apoyar el dedo centrado sobre el visor limpio[cite: 1].
* **Soporte Offline:** El dispositivo cuenta con memoria no volátil[cite: 1]. Al interrumpirse la red, guarda las fichadas en local y se sincroniza automáticamente al restablecer el enlace o mediante USB (FAT32)[cite: 1].

### 2. Configuración de Parámetros de Negocio
* Todas las reglas operativas (turnos, tolernacias de minutos y horas extras) se administran exclusivamente desde el **Panel Web de RRHH**, manteniendo la independencia del firmware del reloj[cite: 1].

---

## 🌐 Enlaces e Integración

* **Sitio Web Principal:** [tadin.com.ar](https://tadin.com.ar)[cite: 1]
* **Contacto Comercial / NFC:** [tadin.com.ar/contacto](https://tadin.com.ar/contacto)[cite: 1]
