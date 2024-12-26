<script>
	const { pontuacao } = $props();
	let percentualPontuacao = $derived(((pontuacao - 1) / 8) * 100);
</script>

<div class="container">
	<p>sua pontuação foi de {percentualPontuacao}%</p>
</div>

<style>
	.container {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
		flex-direction: column;
		background-color: #f0f0f0;
		margin: 0;
	}
</style>
