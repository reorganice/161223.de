<!-- Simple Portfolio Layout - Step 1 -->
<script>
	import { projects } from '$lib/projects.js';
</script>

<svelte:head>
	<title>161223 DESIGN</title>
	<meta name="description" content="Executive Philosophy, Interior Design & Manufacturing" />
</svelte:head>

<!-- Simple vertical sections like original -->
<main class="portfolio">
	{#each projects as project}
		<section class="project-section">
			<!-- Simple image display -->
			<img 
				src="/images/{project.name}_1_161223_paul_linus_weilandt.jpg"
				alt={project.displayName}
				class="project-image"
			/>
			
			<!-- Project info overlay -->
			<div class="project-info">
				<h1 class="project-title text-headline text-secondary">
					{project.displayName}
				</h1>
				<div class="project-details text-body text-secondary">
					<p>{project.type}</p>
					<p>{project.materials}</p>
					<p>{project.location} {project.year}</p>
				</div>
			</div>
		</section>
	{/each}
</main>

<style>
	.portfolio {
		background-color: white;
	}

	.project-section {
		height: 77vh;
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
		overflow: hidden;
		text-transform: uppercase;
	}

	.project-image {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		object-position: center;
		filter: grayscale(100%);
	}

	.project-info {
		position: relative;
		z-index: 10;
		text-align: center;
		padding: var(--spacing-inline);
		opacity: var(--opacity-reduced);
		text-shadow: 0px 1px 1px rgba(0, 0, 0, 0.3);
	}

	.project-title {
		margin-bottom: var(--spacing-block);
		line-height: var(--line-height);
	}

	.project-details p {
		margin: 0;
		line-height: var(--line-height);
	}
</style>
