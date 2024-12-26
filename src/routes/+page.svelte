<script>
	import { PERGUNTAS } from '$lib/data/perguntas';
	import QuizForm from '$lib/components/QuizForm.svelte';
	import Resultado from '$lib/components/Resultado.svelte';
	import { removerAcentos } from '$lib/utils/string';

	let etapa = $state(0);
	let pontuacao = $state(0);

	let respostas = $state({
		nome: '',
		florFavorita: '',
		comidaFav: '',
		diaConhecemos: '',
		corFav: '',
		raiz: '',
		areaEspecializar: '',
		filmeFav: '',
		construcao: ''
	});

	function verificaResposta(perguntaAtual) {
		const respostaUsuario = removerAcentos(respostas[perguntaAtual.id]?.toLowerCase() || '');
		const respostaCorreta = removerAcentos(perguntaAtual.resposta.toLowerCase());
		return respostaUsuario === respostaCorreta;
	}

	function handleSubmit(e) {
		e.preventDefault();
		const perguntaAtual = PERGUNTAS[etapa];
		if (verificaResposta(perguntaAtual)) {
			pontuacao++;
		}
		etapa++;
	}
</script>

{#each PERGUNTAS as pergunta, index (pergunta.id)}
	{#if etapa === index}
		<QuizForm {pergunta} {respostas} {etapa} {pontuacao} onSubmit={handleSubmit} />
	{/if}
{/each}

{#if etapa === 9}
	<Resultado {pontuacao} />
{/if}
