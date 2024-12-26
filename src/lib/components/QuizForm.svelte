<script>
	const { pergunta, respostas, etapa, onSubmit } = $props();

	let localDataNascimento = $state('');
	import { removerAcentos } from '$lib/utils/string';
</script>

<div class="container">
	{#if removerAcentos(respostas[pergunta.id].toLowerCase() || '') === removerAcentos(pergunta.resposta.toLowerCase())}
		<img src={pergunta.URLimagem} alt="fantasma" class="fantasma" />
	{/if}
	{#if etapa === 0}
		{#if !(removerAcentos(respostas[pergunta.id].toLowerCase()) === removerAcentos(pergunta.resposta.toLowerCase()))}
			<p class="boas-vindas">Olá, {respostas[pergunta.id]}</p>
		{:else}
			<p class="boas-vindas">OIII MINHA PRETINHA!!</p>
		{/if}
	{/if}

	<div class="box">
		<form class="form-group" onsubmit={onSubmit}>
			<label for="name" class="pergunta">
				{pergunta.pergunta}
			</label>

			{#if etapa !== 8}
				<input type={pergunta.type} id="name" class="input" bind:value={respostas[pergunta.id]} />

				{#if etapa === 0}
					<label for="date" class="pergunta">data de nascimento</label>
					<input type="date" id="data" class="input" bind:value={localDataNascimento} />
				{/if}

				<button type="submit">PROXIMA PERGUNTA</button>
			{/if}

			{#if etapa === 8}
				<button type="submit">MOSTRAR PONTUAÇÃO</button>
			{/if}
		</form>
	</div>
</div>

<style>
	.fantasma {
		width: 24%;
		height: auto;
	}
	@media (max-width: 768px) {
		.fantasma {
			width: 95%;
		}
	}
	.container {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
		flex-direction: column;
		background-color: #f0f0f0;
		margin: 0;
		position: relative;
	}

	.form-group {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.pergunta {
		margin-bottom: 7px;
		text-align: center;
	}

	.input {
		width: 300px;
		margin-bottom: 20px;
	}

	.box {
		width: 370px;
		height: 180px;
		margin: 10px;
		align-items: center;
		display: flex;
		flex-direction: column;
		justify-content: center;
		border-radius: 10px;
		background-color: red;
		border: 2.13px solid #ccc;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
	}
	.boas-vindas {
		font-family: 'Hepta Slab', serif;
		font-size: 25px;
		margin: 0;
	}
</style>
