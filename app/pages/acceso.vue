<script setup lang="ts">
const route = useRoute()
const mode = ref<'login' | 'register'>(route.query.mode === 'register' ? 'register' : 'login')
const submitted = ref(false)
const password = ref('')
const confirmPassword = ref('')

watch(() => route.query.mode, (value) => {
	mode.value = value === 'register' ? 'register' : 'login'
	submitted.value = false
})

const submitForm = () => {
	submitted.value = true
}
</script>

<template>
	<main class="access-page">
		<header class="access-header">
			<NuxtLink class="access-brand" to="/" aria-label="Planify, volver al inicio">
				<img src="~/assets/logo.png" alt="Planify" />
			</NuxtLink>
			<NuxtLink class="back-link" to="/"><span aria-hidden="true">←</span> Volver al inicio</NuxtLink>
		</header>

		<div class="access-layout">
			<section class="access-story" aria-label="Tu espacio Planify">
				<p class="access-eyebrow"><span></span> TU TIEMPO, EN BUENAS MANOS</p>
				<h1>Un día más claro<br />empieza <em>aquí.</em></h1>
				<p class="story-copy">Haz espacio para lo importante. Tu plan, tus ideas y tus próximos pasos, en un solo lugar.</p>
				<div class="day-preview" aria-label="Vista previa del plan de hoy">
					<div class="preview-top"><span>MIÉRCOLES, 09 OCT</span><span class="preview-mark">✦</span></div>
					<strong>Un día con intención</strong>
					<div class="preview-progress"><i></i></div>
					<div class="preview-bottom"><span>3 de 5 pasos completados</span><span>60%</span></div>
					<div class="preview-task"><span class="task-check">✓</span><span>Preparar la semana</span><small>09:30</small></div>
				</div>
				<p class="story-foot"><span>✳</span> Un paso a la vez también es avanzar.</p>
			</section>

		<section class="access-form-panel" aria-labelledby="access-title">
			<div class="form-heading">
				<p class="form-eyebrow">{{ mode === 'login' ? 'QUÉ BUENO TENERTE DE VUELTA' : 'EMPIEZA A TU RITMO' }}</p>
				<h2 id="access-title">{{ mode === 'login' ? 'Inicia sesión' : 'Crea tu cuenta' }}</h2>
				<p>{{ mode === 'login' ? 'Entra a tu espacio y retoma tu día.' : 'Un espacio para organizar lo que importa.' }}</p>
			</div>

			<form class="access-form" @submit.prevent="submitForm">
				<label v-if="mode === 'register'">
					Nombre completo
					<input type="text" name="name" placeholder="Tu nombre" autocomplete="name" required />
				</label>
				<label>
					Correo electrónico
					<input type="email" name="email" placeholder="tu@correo.com" autocomplete="email" required />
				</label>
				<label>
					Contraseña
					<input v-model="password" type="password" name="password" placeholder="Mínimo 8 caracteres" :autocomplete="mode === 'login' ? 'current-password' : 'new-password'" minlength="8" required />
				</label>
				<label v-if="mode === 'register'">
					Repite tu contraseña
					<input v-model="confirmPassword" type="password" name="confirm-password" placeholder="Confirma tu contraseña" autocomplete="new-password" minlength="8" required />
				</label>
				<label v-if="mode === 'login'" class="remember-option"><input type="checkbox" name="remember" /> Recordarme</label>
				<p v-if="mode === 'register' && confirmPassword && password !== confirmPassword" class="form-error" role="alert">Las contraseñas no coinciden.</p>
				<button class="submit-button" type="submit" :disabled="mode === 'register' && password !== confirmPassword">
					{{ mode === 'login' ? 'Iniciar sesión' : 'Crear mi cuenta' }} <span aria-hidden="true">↗</span>
				</button>
				<p v-if="submitted" class="form-notice" role="status">La pantalla está lista. Para habilitar el acceso real, conecta un servicio de autenticación.</p>
			</form>

			<p class="mode-switch">
				{{ mode === 'login' ? '¿Aún no tienes cuenta?' : '¿Ya tienes una cuenta?' }}
				<button type="button" @click="mode = mode === 'login' ? 'register' : 'login'; submitted = false; password = ''; confirmPassword = ''">
					{{ mode === 'login' ? 'Regístrate' : 'Inicia sesión' }}
				</button>
			</p>
		</section>
		</div>
	</main>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Manrope:wght@600;700;800&display=swap');

.access-page { --access-navy: #082d5b; --access-green: #18b96b; --access-muted: #5c7186; background: #f4f9fd; color: var(--access-navy); font-family: 'DM Sans', sans-serif; min-height: 100vh; }
.access-header { align-items: center; display: flex; justify-content: space-between; margin: 0 auto; max-width: 1180px; min-height: 84px; width: calc(100% - 80px); }
.access-brand img { display: block; height: 48px; object-fit: contain; width: 120px; }
.back-link { color: var(--access-muted); font-size: .82rem; font-weight: 600; }.back-link span { color: var(--access-green); font-size: 1.1rem; margin-right: 7px; }
.access-layout { align-items: center; display: grid; gap: clamp(55px, 9vw, 140px); grid-template-columns: 1fr 440px; margin: 0 auto; max-width: 1080px; min-height: calc(100vh - 84px); padding: 55px 0 90px; width: calc(100% - 80px); }
.access-story { max-width: 500px; }.access-eyebrow, .form-eyebrow { align-items: center; color: var(--access-green); display: flex; font-size: .68rem; font-weight: 700; gap: 9px; letter-spacing: .12em; margin: 0 0 20px; }.access-eyebrow span { background: var(--access-green); border-radius: 50%; height: 7px; width: 7px; }
.access-story h1 { font-family: 'Manrope', sans-serif; font-size: 3.65rem; letter-spacing: -.045em; line-height: 1.06; margin: 0 0 20px; }.access-story h1 em { color: var(--access-green); font-style: normal; }.story-copy { color: var(--access-muted); font-size: 1rem; line-height: 1.7; max-width: 410px; }
.day-preview { background: white; border: 1px solid #e4edf1; border-radius: 7px; box-shadow: 0 22px 50px #082d5b12; margin-top: 36px; max-width: 400px; padding: 23px 25px; transform: rotate(-2deg); }.preview-top, .preview-bottom { align-items: center; color: var(--access-muted); display: flex; font-size: .62rem; justify-content: space-between; }.preview-top { font-weight: 700; letter-spacing: .08em; margin-bottom: 20px; }.preview-mark { align-items: center; background: #e5faef; border-radius: 50%; color: var(--access-green); display: flex; font-size: .9rem; height: 29px; justify-content: center; width: 29px; }.day-preview > strong { display: block; font-family: 'Manrope', sans-serif; font-size: 1.08rem; margin-bottom: 17px; }.preview-progress { background: #e3edf0; border-radius: 9px; height: 6px; overflow: hidden; }.preview-progress i { background: var(--access-green); border-radius: inherit; display: block; height: 100%; width: 60%; }.preview-bottom { margin-top: 8px; }.preview-task { align-items: center; border-top: 1px solid #edf2f4; display: flex; font-size: .73rem; gap: 10px; margin-top: 19px; padding-top: 15px; }.task-check { align-items: center; background: var(--access-green); border-radius: 50%; color: white; display: flex; height: 21px; justify-content: center; width: 21px; }.preview-task small { color: var(--access-muted); margin-left: auto; }.story-foot { color: var(--access-muted); font-size: .74rem; margin: 25px 0 0; }.story-foot span { color: var(--access-green); margin-right: 6px; }
.access-form-panel { background: white; border: 1px solid #e4edf1; border-radius: 7px; box-shadow: 0 18px 55px #082d5b0c; padding: 38px; }.form-eyebrow { font-size: .62rem; margin-bottom: 13px; }.form-heading h2 { font-family: 'Manrope', sans-serif; font-size: 2rem; letter-spacing: -.04em; margin: 0 0 8px; }.form-heading > p:last-child { color: var(--access-muted); font-size: .83rem; margin: 0 0 28px; }
.access-form { display: grid; gap: 16px; }.access-form > label:not(.remember-option) { color: var(--access-navy); display: grid; font-size: .72rem; font-weight: 700; gap: 7px; }.access-form input:not([type='checkbox']) { background: white; border: 1px solid #cbdde5; border-radius: 3px; color: var(--access-navy); font: inherit; font-size: .83rem; outline: 0; padding: 12px; width: 100%; }.access-form input:focus { border-color: var(--access-green); box-shadow: 0 0 0 3px #18b96b20; }.remember-option { align-items: center; color: var(--access-muted); display: flex; font-size: .72rem; gap: 7px; }.remember-option input { accent-color: var(--access-green); }
.submit-button { align-items: center; background: var(--access-navy); border: 0; border-radius: 3px; color: white; cursor: pointer; display: flex; font: inherit; font-size: .82rem; font-weight: 700; justify-content: space-between; margin-top: 3px; padding: 14px 16px; transition: background .2s ease, transform .2s ease; }.submit-button:hover:not(:disabled) { background: #10477f; transform: translateY(-1px); }.submit-button:disabled { cursor: not-allowed; opacity: .55; }.submit-button span { color: #6de799; font-size: 1rem; }.mode-switch { color: var(--access-muted); font-size: .75rem; margin: 23px 0 0; text-align: center; }.mode-switch button { background: none; border: 0; color: #1164c4; cursor: pointer; font: inherit; font-weight: 700; padding: 0 0 0 4px; }.form-error { color: #b42318; font-size: .72rem; margin: -7px 0 0; }.form-notice { background: #e5faef; border-left: 3px solid var(--access-green); color: #246548; font-size: .73rem; line-height: 1.5; margin: 0; padding: 10px 12px; }
@media (max-width: 800px) { .access-header { min-height: 72px; width: calc(100% - 40px); }.access-layout { gap: 40px; grid-template-columns: 1fr; max-width: 520px; min-height: 0; padding: 55px 0 75px; width: calc(100% - 40px); }.access-story h1 { font-size: 3rem; }.day-preview { margin-top: 25px; }.story-foot { margin-top: 20px; }.access-form-panel { padding: 30px; } }
@media (max-width: 420px) { .access-form-panel { padding: 24px 20px; }.back-link { font-size: .75rem; }.access-story h1 { font-size: 2.55rem; } }
</style>