<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	import Countdown from '$lib/Countdown.svelte';
	let done = false;

	import Modal from '$lib/Modal.svelte';

	let isOpenModal = false;
	function openModal() {
		isOpenModal = true;
	}

	export function closeModal() {
		isOpenModal = false;
	}
</script>

<svelte:head>
	<title>Bienvenido al Webinar.</title>
	<meta name="description" content="Webminar Berenice Bastidas" />
</svelte:head>

<main>
	<Modal {isOpenModal} on:closeModal={closeModal} />

	<section
		class="py-12 container mx-auto md:bg-gradient-to-r from-primary via-white to-white md:grid md:grid-cols-2 "
	>
		<img src="/images/webinar-berenice.webp" alt="Webinar" class="w-1/2 md:w-full" />
		<div class="flex flex-col items-center m-4">
			<h1 class="text-xl md:text-2xl text-primary">
				Webinar <span class="text-black">Gratuito</span> Online
			</h1>
			<h2 class="text-2xl text-black md:text-5xl md:py-4 text-center">
				Los 3 Secretos Para Vender Tu Consulta Con Éxito Online En Internet
			</h2>
			<button
				class="bg-primary py-4 px-8 text-white sm:text-lg rounded-full m-4"
				on:click={openModal}>RESERVAR MI LUGAR AHORA</button
			>
			<p class="text-xs">Da click en el botón para registrarte</p>
		</div>
	</section>
	<section class="my-4 bg-primary text-white py-8">
		<div class="container mx-auto ">
			<div class="grid md:grid-cols-2 mx-12 md:mx-4 gap-4 place-items-start sm:place-items-center">
				<div class="flex gap-4 justify-center items-center">
					<img src="/images/boleto.webp" alt="Boleto" class="w-16 h-16 rounded-full" />
					<div>
						<h3>Reserva tu Lugar</h3>
						<p>29 de Junio</p>
					</div>
				</div>
				<div>
					<div class="flex gap-4 justify-center items-center">
						<img
							src="/images/anfritrion_small.webp"
							alt="anfritrion"
							class="w-16 h-16 rounded-full"
						/>
						<div>
							<h3>Psicóloga Berenice Bastidas</h3>
							<p>Anfritrión del taller</p>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>
	<section class="container mx-auto py-8">
		<div class="mx-4">
			<h3 class="text-2xl md:text-5xl text-center">Lo Que Aprenderás En Este Exclusivo Evento</h3>
		</div>
		<div class="grid md:grid-cols-3 mx-12 md:gap-16 lg:mx-24 md:my-12">
			<div class="m-4">
				<h4 class="text-xl font-semibold">Secreto #1</h4>
				<div class="bg-gradient-to-r from-primary  to-white h-3 my-2" />
				<p>La razón de por que cualquier persona puede conseguir pacientes en internet</p>
			</div>
			<div class="m-4">
				<h4 class="text-xl font-semibold">Secreto #2</h4>
				<div class="bg-gradient-to-r from-primary  to-white h-3 my-2" />
				<p>Por que el boca a boca para conseguir pacientes, ya no funciona en la era digital</p>
			</div>
			<div class="m-4">
				<h4 class="text-xl font-semibold">Secreto #3</h4>
				<div class="bg-gradient-to-r from-primary  to-white h-3 my-2" />
				<p>
					La formula triplé y por que es la única que necesitas para ganarte la vida con tu
					profesión
				</p>
			</div>
		</div>
	</section>
	<section class="my-4 bg-primary text-white md:mx-auto py-8 text-center px-4">
		<div class="container mx-auto ">
			<h3 class="text-2xl md:text-4xl">TENEMOS LUGARES LIMITADOS A ESTE WEBINAR</h3>
		</div>

		<div class="flex justify-center pt-4" />
	</section>
	<section class="container my-4 mx-auto">
		<div class="grid md:grid-cols-3 items-center">
			<div class="md:col-span-2 mx-8">
				<h2 class="text-2xl md:text-3xl">Acerca de Berenice Bastidas</h2>
				<div class="bg-gradient-to-r from-primary  to-white h-6 my-2" />
				<p>
					Psicóloga de profesión desde hace 15 años y en los últimos años me he dedicado ayudar a
					Psicólogos, Nutriologos y Profesionales de la Salud a que multipliquen sus ingresos
					incrementando su número de pacientes con estragia a través de internet incluso empezando
					desde cero
				</p>
			</div>

			<div class="flex justify-center my-4 md:my-0 ">
				<img src="/images/berenice_portrait.webp" alt="Berenice Bastidas" class="" />
			</div>
		</div>
	</section>

	<section class="my-4 bg-primary text-white ">
		<div class="container md:mx-auto py-8 text-center px-4">
			<h3 class="text-md md:text-lg">
				¿Eres Psicólogo, Nutriologo, Terapeuta, Profesional de la Salud, Dentista o Coach?
			</h3>
			<h2 class="text-xl md:text-2xl">APROVECHA ESTA OPORTUNIDAD, SI NO ES AHORA CUANDO..</h2>
			<p class="text-sm sm:text-base">¡Este Webinar Gratuito Si Es Para Ti</p>
		</div>
	</section>

	<section class="container mx-auto pb-8">
		<h2 class="text-2xl text-black md:text-4xl md:py-4 md:mx-12 mx-4 text-center ">
			Los 3 Secretos Para Vender Tu Consulta Con Éxito Online En Internet
		</h2>

		<div class="flex flex-col items-center justify-center flex-1">
			<button
				class="bg-primary py-4 px-8 text-white sm:text-lg rounded-full m-4 "
				on:click={openModal}>RESERVAR MI LUGAR AHORA</button
			>
			<p class="text-xs">Da click en el botón para registrarte</p>
			<p class="text-sm sm:text-base">
				Tu oportunidad de registro expira cuando el reloj se detenga
			</p>
			<Countdown on:completed={() => (done = true)} />
			<img src="/images/LogoIncrementaColor.svg" alt="Berenice Bastidas" class="" />
		</div>
	</section>
</main>
