<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	export let isOpenModal: boolean = false;
	const dispatch = createEventDispatcher();

	function closeModal() {
		isOpenModal = false;
		dispatch('closeModal', { isOpenModal });
	}

	function handleSubmit(e: Event) {
		const formData = new FormData(e.target as HTMLFormElement);

		const url = 'https://psicologaberenicebastidas.activehosted.com/proc.php';

		fetch(url, {
			method: 'POST',
			body: formData,
			mode: 'no-cors'
		})
			.then((response) => {
				setTimeout(() => {
					closeModal();
				}, 2000);
			})
			.catch((error) => {
				console.log(error);
			});
	}
</script>

<div id="background" style="--display: {isOpenModal ? 'block' : 'none'};" on:click={closeModal} />
<div id="modal" style="--display: {isOpenModal ? 'block' : 'none'};">
	<form
		on:submit|preventDefault={handleSubmit}
		class="flex flex-col gap-4 mx-4 md:mx-24 mt-4 md:mt-12"
	>
		<input type="hidden" name="u" value="39" />
		<input type="hidden" name="f" value="39" />
		<input type="hidden" name="s" />
		<input type="hidden" name="c" value="0" />
		<input type="hidden" name="m" value="0" />
		<input type="hidden" name="act" value="sub" />
		<input type="hidden" name="v" value="2" />
		<input type="hidden" name="or" value="92ffc03067285b93961e1fb80bcae25d" />

		<input
			type="text"
			name="fullname"
			placeholder="Nombre completo"
			class="border border-gray-400 appearance-none rounded w-full px-3 py-3   focus focus:border-indigo-600 focus:outline-none active:outline-none active:border-indigo-600 "
		/>
		<!-- onChange={handleChange} -->

		<input
			type="email"
			name="email"
			placeholder="Correo electrónico"
			class="border border-gray-400 appearance-none rounded w-full px-3 py-3   focus focus:border-indigo-600 focus:outline-none active:outline-none active:border-indigo-600 "
		/>
		<!-- onChange={handleChange} -->

		<button type="submit" class="px-8 bg-secondary h-14 bg-blue-600 text-white rounded-lg mx-auto">
			Enviar
		</button>

		<!-- <p class="mt-4 text-center text-xl font-bold">{formError}</p> -->
	</form>
</div>

<style>
	#background {
		display: var(--display);
		position: fixed;
		z-index: 1;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
	}

	#modal {
		display: var(--display);
		position: fixed;
		z-index: 2;
		padding: 20px;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		border: 4px solid rgb(231, 64, 123);
		background: #fff;
		filter: drop-shadow(0 0 10px rgb(231, 64, 123));
	}
</style>
