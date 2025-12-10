# examen-final-

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Universidad Privada del Sur</title>
    <style>
        /* Variables CSS simulando SASS (_variables.scss) */
        :root {
            --primary-color: #00285B; /* Azul marino */
            --secondary-color: #00A6ED; /* Celeste institucional */
            --light-gray: #F5F5F5; /* Gris claro */
        }

        /* Estilos generales */
        body {
            font-family: Arial, sans-serif;
            background-color: var(--light-gray);
            margin: 0;
            padding: 0;
            scroll-behavior: smooth; /* Scroll suave para navegación */
        }

        /* Mixin simulado para botones reutilizables (_mixins.scss) */
        .btn-primary {
            background-color: var(--primary-color);
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            transition: background-color 0.3s ease, transform 0.2s ease;
            cursor: pointer;
        }
        .btn-primary:hover {
            background-color: var(--secondary-color);
            transform: scale(1.05);
        }

        /* Encabezado con Flexbox */
        header {
            background-color: var(--primary-color);
            color: white;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        .logo {
            padding: 0.5rem; /* Relleno sutil alrededor del logo */
            border: 1px solid rgba(255, 255, 255, 0.2); /* Borde sutil blanco translúcido */
            border-radius: 5px; /* Bordes redondeados para suavizar */
            background-color: rgba(255, 255, 255, 0.1); /* Fondo sutil para resaltar */
        }
        .logo img {
            height: 60px; /* Tamaño aumentado para mejor apreciación */
            display: block;
        }
        nav a {
            color: white;
            text-decoration: none;
            margin: 0 1rem;
            transition: color 0.3s ease; /* Transición suave para botones del menú (Pregunta 3) */
        }
        nav a:hover {
            color: var(--secondary-color);
        }
        #mobile-menu {
            display: none;
            flex-direction: column;
            position: absolute;
            top: 100%;
            left: 0;
            width: 100%;
            background-color: var(--primary-color);
            padding: 1rem;
            animation: slideDown 0.3s ease-out;
        }
        @keyframes slideDown {
            from {
                transform: translateY(-100%);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }
        #mobile-menu a {
            margin: 0.5rem 0;
        }

        /* Banner principal con animación combinada fade-in + desplazamiento vertical (Pregunta 3) */
        #banner {
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 5rem 1rem;
            text-align: center;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeInSlide 1.5s ease-out forwards;
        }
        @keyframes fadeInSlide {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Sección de noticias con Grid responsivo (Pregunta 1) */
        #noticias {
            padding: 1rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        #noticias h2 {
            text-align: center;
            margin-bottom: 1rem;
            font-size: 1.5rem; /* Ajustado como subtítulo */
            color: var(--primary-color);
        }
        #noticias .grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1rem;
        }
        #noticias article {
            background-color: white;
            padding: 1rem;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: box-shadow 0.3s ease;
        }
        #noticias article:hover {
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        /* Sección de eventos con Grid responsivo (Pregunta 4) */
        #eventos {
            padding: 1rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        #eventos h2 {
            text-align: center;
            margin-bottom: 1rem;
            font-size: 1.5rem;
            color: var(--primary-color);
        }
        #eventos .grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1rem;
        }
        #eventos .card {
            background-color: white;
            padding: 1rem;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: box-shadow 0.3s ease;
        }
        #eventos .card:hover {
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }

        /* Sección de calendario */
        #calendario {
            padding: 1rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        #calendario h2 {
            text-align: center;
            margin-bottom: 1rem;
            font-size: 1.5rem;
            color: var(--primary-color);
        }
        #calendario ul {
            list-style: none;
            padding: 0;
        }
        #calendario li {
            background: white;
            padding: 1rem;
            margin: 0.5rem 0;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        /* Sección de contacto */
        #contacto {
            padding: 1rem;
            max-width: 1200px;
            margin: 0 auto;
            background-color: white;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        #contacto h2 {
            text-align: center;
            margin-bottom: 1rem;
            font-size: 1.5rem;
            color: var(--primary-color);
        }
        #contacto p {
            margin: 0.5rem 0;
            text-align: center;
        }

        /* Modal para inscripciones */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 200;
            justify-content: center;
            align-items: center;
        }
        .modal-content {
            background-color: white;
            padding: 2rem;
            border-radius: 5px;
            max-width: 500px;
            width: 90%;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
        }
        .modal-content h3 {
            margin-bottom: 1rem;
            color: var(--primary-color);
        }
        .modal-content form {
            display: flex;
            flex-direction: column;
        }
        .modal-content input, .modal-content button {
            margin: 0.5rem 0;
            padding: 0.5rem;
            border: 1px solid #ccc;
            border-radius: 3px;
        }
        .modal-content button {
            background-color: var(--primary-color);
            color: white;
            border: none;
            cursor: pointer;
        }
        .modal-content button:hover {
            background-color: var(--secondary-color);
        }
        .close {
            float: right;
            cursor: pointer;
            font-size: 1.5rem;
        }

        /* Pie de página con Flexbox */
        footer {
            background-color: #333;
            color: white;
            padding: 1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        /* Media queries para responsividad en tres resoluciones (Pregunta 1) */
        @media (min-width: 481px) and (max-width: 768px) { /* Tablet */
            #noticias .grid, #eventos .grid {
                grid-template-columns: repeat(2, 1fr);
            }
            nav.hidden-on-mobile {
                display: flex;
            }
        }
        @media (min-width: 769px) { /* Escritorio */
            #noticias .grid, #eventos .grid {
                grid-template-columns: repeat(3, 1fr);
            }
            nav.hidden-on-mobile {
                display: flex;
            }
        }
        @media (max-width: 480px) { /* Móvil */
            nav.hidden-on-mobile {
                display: none;
            }
            #banner {
                padding: 3rem 1rem; /* Ajuste para móvil */
            }
            .logo img {
                height: 50px; /* Ajuste de tamaño en móvil para no ocupar demasiado espacio */
            }
        }
    </style>
</head>
<body>
    <!-- Encabezado con logotipo y menú (Pregunta 1) -->
    <header>
        <div class="logo">
            <img src="https://upload.wikimedia.org/wikipedia/commons/d/d1/Logo_de_la_Universidad_Cient%C3%ADfica_del_Sur.png" alt="Logo Universidad Privada del Sur">
        </div>
        <nav class="hidden-on-mobile">
            <a href="#inicio">Inicio</a>
            <a href="#noticias">Noticias</a>
            <a href="#eventos">Eventos</a>
            <a href="#calendario">Calendario</a>
            <a href="#contacto">Contacto</a>
        </nav>
        <!-- Menú móvil desplegable con animación slide-down -->
        <button id="menu-toggle" aria-label="Abrir menú" style="background: none; border: none; color: white; font-size: 1.5rem;">☰</button>
        <nav id="mobile-menu">
            <a href="#inicio">Inicio</a>
            <a href="#noticias">Noticias</a>
            <a href="#eventos">Eventos</a>
            <a href="#calendario">Calendario</a>
            <a href="#contacto">Contacto</a>
        </nav>
    </header>

    <!-- Banner principal con mensaje institucional y animación (Pregunta 1 y 3) -->
    <section id="inicio">
        <div id="banner">
            <h1>Bienvenidos a la Universidad Privada del Sur</h1>
            <p>Innovación, excelencia y compromiso con el futuro.</p>
            <button class="btn-primary" onclick="alert('Esta sección está en mantenimiento. Disculpe las molestias.')">Explorar Carreras</button>
        </div>
    </section>

    <!-- Main con secciones ordenadas -->
    <main>
        <!-- Sección de noticias con tarjetas (Pregunta 1) -->
        <section id="noticias">
            <h2>Últimas Noticias</h2>
            <div class="grid">
                <article>
                    <h3>Nueva Carrera en Tecnología</h3>
                    <p>Descubre nuestra nueva oferta académica en Ingeniería de Software.</p>
                    <a href="#" style="color: var(--primary-color);">Leer más</a>
                </article>
                <article>
                    <h3>Evento de Graduación</h3>
                    <p>Celebra con nosotros el éxito de nuestros estudiantes el 30 de noviembre.</p>
                    <a href="#" style="color: var(--primary-color);">Leer más</a>
                </article>
                <article>
                    <h3>Investigación en Sostenibilidad</h3>
                    <p>Proyectos innovadores para un mundo mejor, liderados por nuestros investigadores.</p>
                    <a href="#" style="color: var(--primary-color);">Leer más</a>
                </article>
            </div>
        </section>

        <!-- Sección de Eventos Académicos (Pregunta 4) -->
        <section id="eventos">
            <h2>Eventos Académicos</h2>
            <div class="grid">
                <div class="card">
                    <h3>Conferencia de Innovación</h3>
                    <p>Fecha: 15 de enero, 2025</p>
                    <button class="btn-primary" onclick="openModal('Conferencia de Innovación')">Inscribirse</button>
                </div>
                <div class="card">
                    <h3>Taller de Programación</h3>
                    <p>Fecha: 20 de enero, 2025</p>
                    <button class="btn-primary" onclick="openModal('Taller de Programación')">Inscribirse</button>
                </div>
                <div class="card">
                    <h3>Seminario de Sostenibilidad</h3>
                    <p>Fecha: 25 de enero, 2025</p>
                    <button class="btn-primary" onclick="openModal('Seminario de Sostenibilidad')">Inscribirse</button>
                </div>
            </div>
        </section>

        <!-- Sección de Calendario de Eventos Académicos -->
        <section id="calendario">
            <h2>Calendario de Eventos Académicos</h2>
            <ul>
                <li><strong>15 Ene - Conferencia de Innovación</strong>: Sala Principal, 10:00 AM</li>
                <li><strong>20 Ene - Taller de Programación</strong>: Laboratorio 3, 2:00 PM</li>
                <li><strong>25 Ene - Seminario de Sostenibilidad</strong>: Auditorio, 9:00 AM</li>
            </ul>
        </section>

        <!-- Sección de Contacto -->
        <section id="contacto">
            <h2>Contacto</h2>
            <p><strong>Teléfono:</strong> 930 394 203</p>
            <p><strong>Dirección:</strong> Av. San Felipe 1109, Jesús María, Lima, Perú</p>
        </section>
    </main>

    <!-- Modal para inscripciones -->
    <div id="inscription-modal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal()">&times;</span>
            <h3>Inscripciones del Evento</h3>
            <form id="inscription-form">
                <label for="event-name">Evento:</label>
                <input type="text" id="event-name" readonly>
                <label for="name">Nombre:</label>
                <input type="text" id="name" required>
                <label for="email">Email:</label>
                <input type="email" id="email" required>
                <button type="submit">Enviar Inscripción</button>
            </form>
        </div>
    </div>

    <!-- Pie de página (Pregunta 1) -->
    <footer>
        <p>&copy; 2025 Universidad Privada del Sur</p>
        <div>
            <a href="#" aria-label="Facebook" style="margin: 0 0.5rem; color: white;">FB</a>
            <a href="#" aria-label="Twitter" style="margin: 0 0.5rem; color: white;">TW</a>
            <a href="#" aria-label="Instagram" style="margin: 0 0.5rem; color: white;">IG</a>
        </div>
    </footer>

    <script>
        // JavaScript para menú móvil con animación slide-down
        const menuToggle = document.getElementById('menu-toggle');
        const mobileMenu = document.getElementById('mobile-menu');
        menuToggle.addEventListener('click', () => {
            if (mobileMenu.style.display === 'flex') {
                mobileMenu.style.display = 'none';
            } else {
                mobileMenu.style.display = 'flex';
            }
        });

        // Funcionalidad adicional: Scroll suave a secciones
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
                // Cerrar menú móvil después de clic
                mobileMenu.style.display = 'none';
            });
        });

        // Funcionalidad para modal de inscripciones
        function openModal(eventName) {
            document.getElementById('event-name').value = eventName;
            document.getElementById('inscription-modal').style.display = 'flex';
        }

        function closeModal() {
            document.getElementById('inscription-modal').style.display = 'none';
        }

        // Manejar envío del formulario
        document.getElementById('inscription-form').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Inscripción enviada exitosamente para ' + document.getElementById('event-name').value);
            closeModal();
        });

        // Cerrar modal al hacer clic fuera
        window.onclick = function(event) {
            const modal = document.getElementById('inscription-modal');
            if (event.target === modal) {
                closeModal();
            }
        };
    </script>
</body>
</html>
