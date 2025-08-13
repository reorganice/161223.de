<script>
	let year = new Date().getFullYear();
</script>

<footer>
	<section>
		<div>
			<p>info@161223.de</p>
			<p>+49 176 32892563</p>
			<p>Bogenstrasse 54i</p>
			<p>D-20144 Hamburg</p>
		</div>
		<div style="text-align: right;">
			<p>Paul Linus Weilandt</p>
			<p><a href="/impressum">Kontakt / Impressum</a></p>
			<p><a href="/legal">Datenschutzerklärung</a></p>
			<p>©{year} - <a href="/">161223.de</a></p>
		</div>
	</section>
</footer>

<style>
	footer {
		min-height: max-content;
		padding-inline: var(--spacing-inline);
	}

	section {
		display: flex;
		justify-content: space-around;
		max-width: 100%;
		margin-block: var(--spacing-block);
	}

	div p {
		white-space: nowrap;
		font-size: var(--font-size-body-sm);
		font-weight: normal;
		margin-block: 0.4em;
		margin: 0.4em 0;
	}
</style>