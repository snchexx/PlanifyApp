<script setup lang="ts">
const menuOpen = ref(false)
const authOpen = ref(false)
const authMode = ref<'login' | 'register'>('login')

const closeMenu = () => {
	menuOpen.value = false
}

const openAuth = (mode: 'login' | 'register' = 'login') => {
	authMode.value = mode
	authOpen.value = true
	closeMenu()
}

const closeAuth = () => {
	authOpen.value = false
}
</script>

<template>
	<main class="site-shell">
		<nav class="nav-wrap" aria-label="Navegación principal">
			<a class="brand" href="#inicio" aria-label="Planify, inicio" @click="closeMenu">
				<img src="~/assets/logo.png" alt="Planify" />
			</a>

			<button class="menu-toggle" type="button" aria-label="Abrir menú" :aria-expanded="menuOpen" @click="menuOpen = !menuOpen">
				<span></span><span></span>
			</button>

			<div class="nav-links" :class="{ 'is-open': menuOpen }">
				<a href="#sobre-planify" @click="closeMenu">Sobre Planify</a>
				<a href="#como-funciona" @click="closeMenu">Cómo funciona</a>
				<a href="#beneficios" @click="closeMenu">Beneficios</a>
				<a href="#ia" @click="closeMenu">IA para ti</a>
				<button class="login-link" type="button" @click="openAuth()">Iniciar sesión</button>
				<a class="nav-cta" href="#descarga" @click="closeMenu">Comenzar ahora <span>↗</span></a>
			</div>
		</nav>

		<section id="inicio" class="hero page-section">
			<div class="hero-copy reveal">
				<p class="eyebrow"><span class="eyebrow-dot"></span> Tu tiempo, en buenas manos</p>
				<h1>Organiza tu día.<br /><em>Vive lo importante.</em></h1>
				<p class="hero-text">Planify convierte tus pendientes en un plan claro y posible. Recuerda lo que importa, recibe orientación inteligente y avanza a tu ritmo.</p>
				<div class="hero-actions">
					<button class="button button-primary" type="button" @click="openAuth('register')">Descubre Planify <span>↗</span></button>
					<a class="text-link" href="#como-funciona"><span class="play-icon">▶</span> Mira cómo funciona</a>
				</div>
				<div class="hero-proof">
					<div class="avatar-stack" aria-hidden="true"><span>LM</span><span>AR</span><span>SC</span><span>+</span></div>
					<p><strong>Tu mejor versión empieza</strong><br />con un día bien organizado.</p>
				</div>
			</div>

			<div class="hero-visual reveal reveal-delay">
				<div class="visual-orbit orbit-one"></div>
				<div class="visual-orbit orbit-two"></div>
				<div class="floating-note note-top"><span class="note-icon">✦</span><span><strong>Tip del día</strong><small>Empieza por una cosa</small></span></div>
			<div class="phone-frame"><img src="~/assets/interfazprincipal.png" alt="Vista principal de la aplicación Planify" /></div>
				<div class="floating-note note-bottom"><span class="check-icon">✓</span><span><strong>Todo bajo control</strong><small>3 tareas completadas</small></span></div>
			</div>
		</section>

		<section class="marquee-strip" aria-label="Funciones de Planify">
			<span>RECUERDA</span><i>✦</i><span>ORGANIZA</span><i>✦</i><span>AVANZA</span><i>✦</i><span>RECUERDA</span><i>✦</i><span>ORGANIZA</span>
		</section>

		<section id="sobre-planify" class="about page-section">
			<div class="about-visual reveal">
				<div class="about-orbit"></div>
				<div class="about-card about-card-main"><span class="about-card-label">HOY</span><strong>Un día con intención</strong><span class="about-progress"><i></i></span><small>3 de 5 pasos completados</small></div>
				<div class="about-card about-card-note"><span>✦</span><p><strong>Un momento para ti</strong><small>Tu pausa también cuenta</small></p></div>
			</div>
			<div class="about-copy reveal reveal-delay">
				<p class="eyebrow"><span class="eyebrow-dot"></span> Qué es Planify</p>
				<h2>Más claridad.<br /><em>Menos ruido.</em></h2>
				<p>Planify es tu espacio para ordenar tareas, ideas y hábitos sin sentir que tu día te persigue. Reúne lo importante en un solo lugar y te ayuda a decidir cuál es el siguiente paso.</p>
				<div class="about-points"><span><b>01</b> Organiza lo esencial</span><span><b>02</b> Cuida tu energía</span><span><b>03</b> Avanza a tu ritmo</span></div>
			</div>
		</section>

		<section id="beneficios" class="benefits page-section">
			<div class="section-intro reveal"><p class="eyebrow"><span class="eyebrow-dot"></span> Mucho más que una agenda</p><h2>Tu día tiene un ritmo.<br /><em>Planify lo entiende.</em></h2></div>
			<div class="benefit-content">
				<p class="lead-copy reveal">Una aplicación pensada para quitar ruido de tu cabeza y devolver foco a tus decisiones. Todo lo que necesitas para hacer espacio a lo que de verdad cuenta.</p>
				<div class="benefit-list reveal reveal-delay">
					<article><span class="feature-number">01</span><div><h3>Recordatorios que se adaptan</h3><p>Recibe avisos en el momento correcto, con la flexibilidad que tu día necesita.</p></div><span class="arrow-mark">↗</span></article>
					<article><span class="feature-number">02</span><div><h3>Una mirada clara a tu día</h3><p>Convierte tus pendientes en pasos simples y descubre qué merece tu atención.</p></div><span class="arrow-mark">↗</span></article>
					<article><span class="feature-number">03</span><div><h3>Consejos para avanzar mejor</h3><p>Pequeñas prácticas, tips y pausas que ayudan a cuidar tu energía y tu tiempo.</p></div><span class="arrow-mark">↗</span></article>
				</div>
			</div>
		</section>

		<section id="ia" class="ai-section page-section">
			<div class="ai-art reveal"><div class="ai-glow"></div><div class="ai-symbol">✦</div><span class="ai-orbit-dot dot-a"></span><span class="ai-orbit-dot dot-b"></span><span class="ai-orbit-dot dot-c"></span></div>
			<div class="ai-copy reveal reveal-delay"><p class="eyebrow light"><span class="eyebrow-dot"></span> Tu asistente inteligente</p><h2>La inteligencia que<br /><em>trabaja contigo.</em></h2><p>Planify aprende de tu manera de organizarte y te acompaña sin imponer. Sugiere prioridades, propone rutinas y te da el empujón que necesitas para convertir intención en acción.</p><div class="ai-tags"><span>Prioridades claras</span><span>Rutinas posibles</span><span>Consejos a tu medida</span></div></div>
		</section>

		<section id="como-funciona" class="steps page-section">
			<div class="section-intro centered reveal"><p class="eyebrow"><span class="eyebrow-dot"></span> Empieza en minutos</p><h2>De pendiente a<br /><em>progreso real.</em></h2></div>
			<div class="step-grid">
				<article class="step-card reveal"><span class="step-icon">＋</span><span class="step-index">01</span><h3>Cuéntale qué necesitas</h3><p>Añade una tarea, un evento o eso que no quieres volver a olvidar.</p></article>
				<article class="step-card featured reveal reveal-delay"><span class="step-icon">✦</span><span class="step-index">02</span><h3>Planify ordena el camino</h3><p>La IA te ayuda a priorizar y a encontrar un momento realista para cada cosa.</p></article>
				<article class="step-card reveal reveal-delay-2"><span class="step-icon">✓</span><span class="step-index">03</span><h3>Haz espacio para vivir</h3><p>Avanza con calma, celebra lo que logras y reajusta cuando tu día cambie.</p></article>
			</div>
		</section>

		<section id="descarga" class="download page-section reveal">
			<div><p class="eyebrow"><span class="eyebrow-dot"></span> Planify en tu bolsillo</p><h2>Tu tiempo es tuyo.<br /><em>Llévalo contigo.</em></h2></div>
			<div class="download-action"><p>Descarga la app y organiza tu próximo día.</p><a class="button button-light play-store-button" href="https://play.google.com/store/search?q=Planify&c=apps" target="_blank" rel="noopener noreferrer"><span class="play-store-mark">▶</span> Conseguir en Google Play</a><button class="download-register" type="button" @click="openAuth('register')">O empieza desde la web <span>↗</span></button></div>
		</section>

		<footer><a class="brand footer-brand" href="#inicio"><img src="~/assets/logo.png" alt="Planify" /></a><p>Organiza hoy, logra mañana.</p><span>© 2024 Planify</span></footer>

		<div v-if="authOpen" class="auth-backdrop" role="presentation" @click.self="closeAuth">
			<section class="auth-modal" role="dialog" aria-modal="true" :aria-labelledby="authMode === 'login' ? 'login-title' : 'register-title'">
				<button class="modal-close" type="button" aria-label="Cerrar ventana" @click="closeAuth">×</button>
				<div class="auth-heading">
					<p class="eyebrow"><span class="eyebrow-dot"></span> Planifica tu próximo paso</p>
					<h2 v-if="authMode === 'login'" id="login-title">Qué bueno<br /><em>verte de nuevo.</em></h2>
					<h2 v-else id="register-title">Empieza a ordenar<br /><em>lo importante.</em></h2>
					<p>{{ authMode === 'login' ? 'Entra a tu espacio personal y retoma tu día.' : 'Crea tu cuenta y convierte tus pendientes en progreso.' }}</p>
				</div>

				<form class="auth-form" @submit.prevent="closeAuth">
					<label v-if="authMode === 'register'">Nombre completo<input type="text" placeholder="Tu nombre" autocomplete="name" required /></label>
					<label>Correo electrónico<input type="email" placeholder="tu@correo.com" autocomplete="email" required /></label>
					<label>Contraseña<input type="password" placeholder="Mínimo 8 caracteres" :autocomplete="authMode === 'login' ? 'current-password' : 'new-password'" minlength="8" required /></label>
					<label v-if="authMode === 'register'">Confirmar contraseña<input type="password" placeholder="Repite tu contraseña" autocomplete="new-password" minlength="8" required /></label>
					<div v-if="authMode === 'login'" class="form-options"><label class="check-label"><input type="checkbox" /> Recordarme</label><a href="#" @click.prevent>¿Olvidaste tu contraseña?</a></div>
					<button class="button button-primary auth-submit" type="submit">{{ authMode === 'login' ? 'Iniciar sesión' : 'Crear mi cuenta' }} <span>↗</span></button>
				</form>

				<p class="auth-switch">{{ authMode === 'login' ? '¿Aún no tienes cuenta?' : '¿Ya tienes una cuenta?' }} <button type="button" @click="authMode = authMode === 'login' ? 'register' : 'login'">{{ authMode === 'login' ? 'Regístrate aquí' : 'Inicia sesión' }}</button></p>
			</section>
		</div>
	</main>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Manrope:wght@600;700;800&display=swap');

:root { --navy: #082d5b; --blue: #1164c4; --green: #18b96b; --mint: #e5faef; --ice: #f4f9fd; --ink-soft: #5c7186; }
* { box-sizing: border-box; }
html { scroll-behavior: smooth; }
body { margin: 0; background: var(--ice); color: var(--navy); font-family: 'DM Sans', sans-serif; }
a { color: inherit; text-decoration: none; }
.site-shell { overflow: hidden; }
.nav-wrap, .page-section, footer { width: min(1180px, calc(100% - 80px)); margin: auto; }
.nav-wrap { align-items: center; display: flex; justify-content: space-between; min-height: 84px; }
.brand img { display: block; height: 52px; object-fit: contain; width: 130px; }
.nav-links { align-items: center; display: flex; gap: 28px; color: var(--ink-soft); font-size: .86rem; font-weight: 600; }
.nav-links a { transition: color .2s ease; }.nav-links a:hover { color: var(--green); }.nav-cta { color: var(--navy) !important; }.nav-cta span, .button span { color: var(--green); font-size: 1.1rem; margin-left: 10px; }.menu-toggle { display: none; }
.login-link { background: none; border: 0; color: var(--navy); cursor: pointer; font: inherit; padding: 0; }.login-link:hover { color: var(--green); }
.hero { align-items: center; display: grid; gap: 40px; grid-template-columns: 1fr 1fr; min-height: 670px; padding: 60px 0 85px; }
.eyebrow { align-items: center; color: var(--green); display: flex; font-size: .72rem; font-weight: 700; gap: 9px; letter-spacing: .12em; margin: 0 0 22px; text-transform: uppercase; }.eyebrow-dot { background: var(--green); border-radius: 99px; height: 7px; width: 7px; }
h1, h2, h3, p { margin-top: 0; } h1, h2 { font-family: 'Manrope', sans-serif; letter-spacing: -.055em; } h1 { font-size: clamp(3.2rem, 5.6vw, 5.2rem); line-height: 1.02; margin-bottom: 28px; } h1 em, h2 em { color: var(--green); font-style: normal; }
.hero-text { color: var(--ink-soft); font-size: 1.04rem; line-height: 1.75; max-width: 470px; }.hero-actions { align-items: center; display: flex; gap: 27px; margin-top: 34px; }.button { align-items: center; border-radius: 4px; display: inline-flex; font-size: .86rem; font-weight: 700; justify-content: center; padding: 16px 22px; transition: transform .2s ease, box-shadow .2s ease; }.button:hover { box-shadow: 0 12px 28px #082d5b22; transform: translateY(-2px); }.button-primary { background: var(--navy); color: white; }.button-primary span { color: #6de799; }.text-link { color: var(--navy); font-size: .82rem; font-weight: 700; }.play-icon { align-items: center; border: 1px solid #bad4de; border-radius: 50%; color: var(--green); display: inline-flex; font-size: .55rem; height: 27px; justify-content: center; margin-right: 8px; width: 27px; }.hero-proof { align-items: center; display: flex; gap: 15px; margin-top: 55px; }.avatar-stack { display: flex; }.avatar-stack span { align-items: center; background: var(--green); border: 2px solid var(--ice); border-radius: 50%; color: white; display: flex; font-size: .52rem; font-weight: 700; height: 31px; justify-content: center; margin-left: -7px; width: 31px; }.avatar-stack span:first-child { margin-left: 0; background: #1672c9; }.avatar-stack span:nth-child(2) { background: #79b7d4; }.avatar-stack span:nth-child(3) { background: #1f9e88; }.avatar-stack span:last-child { background: white; color: var(--green); }.hero-proof p { color: var(--ink-soft); font-size: .72rem; line-height: 1.4; margin: 0; }.hero-proof strong { color: var(--navy); }
.hero-visual { align-items: center; display: flex; height: 570px; justify-content: center; position: relative; }.phone-frame { background: linear-gradient(180deg, #f4f8fb, #edf5f5); border: 8px solid rgba(255,255,255,0.9); border-radius: 30px; box-shadow: 18px 30px 28px rgba(8,45,91,0.15); overflow: hidden; position: relative; transform: rotate(4deg); width: min(275px, 65%); z-index: 2; }.phone-frame::before { content: ''; background: rgba(255,255,255,0.18); border-radius: 18px; inset: 10px; position: absolute; } .phone-frame img { display: block; height: auto; width: 100%; border-radius: 22px; position: relative; z-index: 1; }.visual-orbit { border: 1px solid #8dddb7; border-radius: 50%; height: 510px; position: absolute; transform: rotate(-25deg); width: 370px; }.orbit-one { border-color: #b6deee; }.orbit-two { height: 430px; transform: rotate(33deg); width: 530px; }.floating-note { align-items: center; background: white; border-radius: 8px; box-shadow: 0 15px 35px #082d5b18; display: flex; font-size: .72rem; gap: 10px; padding: 13px 16px; position: absolute; z-index: 3; }.floating-note strong, .floating-note small { display: block; }.floating-note small { color: var(--ink-soft); font-size: .63rem; margin-top: 3px; }.note-top { right: 0; top: 112px; }.note-bottom { bottom: 105px; left: 0; }.note-icon, .check-icon { align-items: center; background: #dff9eb; border-radius: 50%; color: var(--green); display: inline-flex; font-size: 1.1rem; height: 34px; justify-content: center; width: 34px; }.check-icon { background: var(--green); color: white; font-weight: 700; }
.marquee-strip { align-items: center; background: var(--navy); color: white; display: flex; font-family: 'Manrope', sans-serif; font-size: .78rem; font-weight: 700; gap: 42px; justify-content: center; letter-spacing: .16em; min-height: 70px; overflow: hidden; }.marquee-strip i { color: #51de91; font-style: normal; }
.about { align-items: center; display: grid; gap: 110px; grid-template-columns: 1fr 1fr; padding: 135px 0 125px; }.about-visual { align-items: center; display: flex; height: 350px; justify-content: center; position: relative; }.about-orbit { border: 1px solid #a9dfe2; border-radius: 50%; height: 310px; position: absolute; transform: rotate(-28deg); width: 430px; }.about-orbit::before { background: var(--green); border: 7px solid var(--ice); border-radius: 50%; content: ''; height: 15px; left: 13%; position: absolute; top: 10%; width: 15px; }.about-card { background: white; border-radius: 7px; box-shadow: 0 18px 40px #082d5b17; position: absolute; }.about-card-main { padding: 26px 28px; transform: rotate(-4deg); width: 265px; z-index: 2; }.about-card-label { color: var(--green); display: block; font-size: .68rem; font-weight: 700; letter-spacing: .14em; margin-bottom: 17px; }.about-card-main strong { display: block; font-family: 'Manrope', sans-serif; font-size: 1.2rem; margin-bottom: 24px; }.about-progress { background: #e1edf0; border-radius: 20px; display: block; height: 7px; margin-bottom: 12px; overflow: hidden; }.about-progress i { background: var(--green); border-radius: inherit; display: block; height: 100%; width: 60%; }.about-card small { color: var(--ink-soft); font-size: .68rem; }.about-card-note { align-items: center; display: flex; gap: 11px; padding: 14px 17px; right: 0; top: 53px; transform: rotate(5deg); z-index: 3; }.about-card-note > span { align-items: center; background: #def9eb; border-radius: 50%; color: var(--green); display: flex; height: 34px; justify-content: center; width: 34px; }.about-card-note p { margin: 0; }.about-card-note strong, .about-card-note small { display: block; }.about-card-note strong { font-size: .72rem; }.about-card-note small { margin-top: 4px; }.about-copy > p:not(.eyebrow) { color: var(--ink-soft); font-size: 1.05rem; line-height: 1.75; max-width: 480px; }.about-copy h2 { font-size: clamp(2.5rem, 4vw, 4rem); line-height: 1.05; margin-bottom: 28px; }.about-points { border-top: 1px solid #cddfe7; display: grid; gap: 14px; margin-top: 32px; padding-top: 20px; }.about-points span { color: var(--navy); font-size: .82rem; font-weight: 600; }.about-points b { color: var(--green); font-size: .7rem; margin-right: 15px; }
.benefits { padding: 130px 0 145px; }.section-intro h2, .ai-copy h2, .download h2 { font-size: clamp(2.5rem, 4vw, 4rem); line-height: 1.05; margin-bottom: 0; }.benefit-content { display: grid; gap: 100px; grid-template-columns: .65fr 1fr; margin-top: 80px; }.lead-copy { color: var(--ink-soft); font-size: 1.12rem; line-height: 1.7; max-width: 300px; }.benefit-list article { align-items: center; border-top: 1px solid #cddfe7; display: flex; gap: 22px; padding: 25px 0; }.feature-number { color: var(--green); font-size: .73rem; font-weight: 700; }.benefit-list h3 { font-family: 'Manrope', sans-serif; font-size: 1.03rem; letter-spacing: -.02em; margin-bottom: 6px; }.benefit-list p { color: var(--ink-soft); font-size: .85rem; line-height: 1.5; margin: 0; }.arrow-mark { color: var(--green); font-size: 1.2rem; margin-left: auto; }
.ai-section { align-items: center; background: var(--navy); color: white; display: grid; gap: 100px; grid-template-columns: .9fr 1fr; max-width: none; padding: 110px max(40px, calc((100vw - 1180px) / 2)); position: relative; }.ai-art { align-items: center; display: flex; height: 360px; justify-content: center; position: relative; }.ai-glow { background: #1bbb6b; border-radius: 50%; box-shadow: 0 0 90px 35px #169e6a; height: 155px; opacity: .8; width: 155px; }.ai-symbol { align-items: center; background: white; border-radius: 50%; color: var(--green); display: flex; font-size: 4rem; height: 120px; justify-content: center; position: absolute; width: 120px; }.ai-art::before, .ai-art::after { border: 1px solid #4382a7; border-radius: 50%; content: ''; height: 270px; position: absolute; transform: rotate(35deg); width: 390px; }.ai-art::after { height: 390px; transform: rotate(-35deg); width: 270px; }.ai-orbit-dot { background: #65e89d; border-radius: 50%; height: 11px; position: absolute; width: 11px; }.dot-a { left: 16%; top: 22%; }.dot-b { right: 10%; top: 67%; background: #48bbeb; }.dot-c { right: 27%; top: 12%; }.light { color: #65e89d; }.ai-copy h2 { margin-bottom: 30px; }.ai-copy > p:not(.eyebrow) { color: #c0d3e0; font-size: 1.02rem; line-height: 1.75; max-width: 520px; }.ai-tags { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 30px; }.ai-tags span { border: 1px solid #376486; border-radius: 30px; color: #d8e6ed; font-size: .73rem; padding: 9px 14px; }
.steps { padding: 140px 0; }.centered { text-align: center; }.centered .eyebrow { justify-content: center; }.step-grid { display: grid; gap: 20px; grid-template-columns: repeat(3, 1fr); margin-top: 75px; }.step-card { border-top: 3px solid #bcd9e4; padding: 28px 15px 20px 0; position: relative; }.step-card.featured { border-color: var(--green); }.step-icon { align-items: center; border: 1px solid #c7dfe5; border-radius: 50%; color: var(--green); display: flex; font-size: 1.35rem; height: 43px; justify-content: center; margin-bottom: 50px; width: 43px; }.step-index { color: var(--ink-soft); font-size: .7rem; position: absolute; right: 0; top: 31px; }.step-card h3 { font-family: 'Manrope', sans-serif; font-size: 1.1rem; letter-spacing: -.02em; }.step-card p { color: var(--ink-soft); font-size: .88rem; line-height: 1.6; max-width: 270px; }
.download { align-items: end; background: #d9f8e8; display: flex; justify-content: space-between; max-width: none; padding: 85px max(40px, calc((100vw - 1180px) / 2)); }.download-action { text-align: right; }.download-action p { color: #318362; font-size: .85rem; margin-bottom: 18px; }.button-light { background: var(--green); color: white; }.button-light span { color: white; }.play-store-button { gap: 9px; }.play-store-mark { font-size: .8rem !important; margin: 0 !important; }.download-register { background: none; border: 0; color: var(--navy); cursor: pointer; display: block; font: inherit; font-size: .75rem; font-weight: 700; margin: 15px 0 0 auto; padding: 0; }.download-register span { color: var(--green); margin-left: 5px; }footer { align-items: center; display: flex; justify-content: space-between; min-height: 100px; }footer p, footer > span { color: var(--ink-soft); font-size: .72rem; }.footer-brand img { height: 39px; width: 98px; }
.auth-backdrop { align-items: center; background: #082d5b99; display: flex; inset: 0; justify-content: center; padding: 24px; position: fixed; z-index: 20; }.auth-modal { background: white; border-radius: 8px; box-shadow: 0 25px 70px #082d5b45; max-height: calc(100vh - 48px); max-width: 470px; overflow-y: auto; padding: 48px; position: relative; width: 100%; }.modal-close { background: none; border: 0; color: var(--ink-soft); cursor: pointer; font-size: 1.8rem; line-height: 1; padding: 4px; position: absolute; right: 20px; top: 18px; }.auth-heading h2 { font-size: clamp(2.25rem, 5vw, 3.3rem); line-height: 1.03; margin-bottom: 14px; }.auth-heading > p:last-child { color: var(--ink-soft); font-size: .9rem; line-height: 1.5; margin-bottom: 30px; }.auth-form { display: grid; gap: 17px; }.auth-form > label { color: var(--navy); display: grid; font-size: .75rem; font-weight: 700; gap: 7px; }.auth-form input[type='email'], .auth-form input[type='password'], .auth-form input[type='text'] { border: 1px solid #cbdde5; border-radius: 3px; color: var(--navy); font: inherit; font-size: .88rem; outline: 0; padding: 13px 14px; transition: border-color .2s ease, box-shadow .2s ease; width: 100%; }.auth-form input:focus { border-color: var(--green); box-shadow: 0 0 0 3px #18b96b20; }.form-options { align-items: center; display: flex; font-size: .72rem; justify-content: space-between; }.check-label { align-items: center; color: var(--ink-soft); display: flex; font-weight: 500; gap: 7px; }.check-label input { accent-color: var(--green); }.form-options a { color: var(--blue); }.auth-submit { border: 0; cursor: pointer; margin-top: 4px; width: 100%; }.auth-switch { color: var(--ink-soft); font-size: .78rem; margin: 25px 0 0; text-align: center; }.auth-switch button { background: none; border: 0; color: var(--blue); cursor: pointer; font: inherit; font-weight: 700; padding: 0; }
.reveal { animation: rise .8s both; animation-timeline: view(); animation-range: entry 10% cover 30%; }@keyframes rise { from { opacity: 0; transform: translateY(22px); } to { opacity: 1; transform: translateY(0); } }
@media (max-width: 760px) { .nav-wrap, .page-section, footer { width: min(100% - 40px, 580px); }.nav-wrap { min-height: 72px; }.brand img { height: 45px; width: 112px; }.menu-toggle { background: none; border: 0; display: flex; flex-direction: column; gap: 5px; padding: 10px; }.menu-toggle span { background: var(--navy); display: block; height: 2px; width: 22px; }.nav-links { background: var(--ice); box-shadow: 0 15px 25px #082d5b12; display: none; flex-direction: column; gap: 20px; left: 0; padding: 25px; position: absolute; right: 0; top: 72px; z-index: 9; }.nav-links.is-open { display: flex; }.hero { display: flex; flex-direction: column; min-height: 0; padding: 55px 0 70px; }.hero-copy { width: 100%; }.hero-visual { height: 500px; margin-top: 12px; width: 100%; }.phone-frame { width: min(250px, 66%); }.note-top { right: -2px; top: 60px; }.note-bottom { bottom: 70px; left: -5px; }.visual-orbit { height: 420px; width: 300px; }.orbit-two { height: 360px; width: 440px; }.marquee-strip { gap: 22px; justify-content: flex-start; padding-left: 28px; white-space: nowrap; }.about { display: flex; flex-direction: column; gap: 45px; padding: 90px 0; }.about-visual { height: 300px; width: 100%; }.about-orbit { height: 260px; width: 350px; }.about-card-note { right: -5px; top: 34px; }.about-card-main { left: 8%; }.benefits, .steps { padding: 90px 0; }.benefit-content, .ai-section { display: flex; flex-direction: column; gap: 35px; margin-top: 45px; }.lead-copy { max-width: 430px; }.ai-section { padding: 75px 20px; }.ai-art { height: 270px; order: 2; }.ai-copy { order: 1; }.ai-art::before { height: 210px; width: 300px; }.ai-art::after { height: 300px; width: 210px; }.step-grid { grid-template-columns: 1fr; margin-top: 50px; }.step-card { padding-bottom: 25px; }.step-icon { margin-bottom: 30px; }.download { align-items: start; flex-direction: column; gap: 38px; padding: 65px 20px; width: 100%; }.download-action { text-align: left; }.download-register { margin-left: 0; }footer { flex-wrap: wrap; gap: 10px; padding: 22px 0; }.auth-modal { padding: 40px 24px 28px; } }
@media (prefers-reduced-motion: reduce) { html { scroll-behavior: auto; }.reveal { animation: none; } }
</style>