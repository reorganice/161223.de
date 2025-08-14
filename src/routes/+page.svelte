<!-- Simple Portfolio Layout with Slideshow -->
<script>
	import { projects } from '$lib/projects.js';
	
	// Simple slideshow state - one slide index per project
	let currentSlides = projects.reduce((acc, project) => {
		acc[project.id] = 1; // Start at slide 1
		return acc;
	}, {});

	function nextSlide(projectId) {
		const project = projects.find(p => p.id === projectId);
		if (currentSlides[projectId] < project.totalImages) {
			currentSlides[projectId]++;
		} else {
			currentSlides[projectId] = 1; // Loop back to first
		}
	}

	function prevSlide(projectId) {
		const project = projects.find(p => p.id === projectId);
		if (currentSlides[projectId] > 1) {
			currentSlides[projectId]--;
		} else {
			currentSlides[projectId] = project.totalImages; // Loop to last
		}
	}
</script>

<svelte:head>
	<title>161223 DESIGN</title>
	<meta name="description" content="Executive Philosophy, Interior Design & Manufacturing" />
</svelte:head>

<!-- Simple vertical sections like original -->
<main class="portfolio">
	{#each projects as project}
		<section class="project-section">
			<!-- Slideshow image with click areas -->
			<div class="image-container">
				<img 
					src="/images/{project.name}_{currentSlides[project.id]}_161223_paul_linus_weilandt.jpg"
					alt="{project.displayName} - Image {currentSlides[project.id]}"
					class="project-image"
				/>
				
				<!-- Click areas for navigation -->
				<button 
					class="nav-area nav-left"
					onclick={() => prevSlide(project.id)}
					aria-label="Previous image"
				></button>
				
				<button 
					class="nav-area nav-right"
					onclick={() => nextSlide(project.id)}
					aria-label="Next image"
				></button>
				
				<!-- Slide indicator -->
				<div class="slide-indicator">
					{currentSlides[project.id]} / {project.totalImages}
				</div>
			</div>
			
			<!-- Project info overlay - moved to left side -->
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

	.image-container {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}

	.project-image {
		width: 100%;
		height: 100%;
		object-fit: cover;
		object-position: center;
		filter: grayscale(100%);
		transition: filter 0.3s ease;
	}

	.project-section:hover .project-image {
		filter: grayscale(0%);
	}

	.nav-area {
		position: absolute;
		top: 0;
		height: 100%;
		width: 50%;
		background: transparent;
		border: none;
		cursor: pointer;
		z-index: 5;
	}

	.nav-left {
		left: 0;
	}

	.nav-right {
		right: 0;
	}

	.nav-area:hover {
		background: rgba(0, 0, 0, 0.03);
	}

	.slide-indicator {
		position: absolute;
		bottom: 1rem;
		right: 1rem;
		background: rgba(0, 0, 0, 0.2);
		color: white;
		padding: 0.125rem 0.375rem;
		border-radius: 0.125rem;
		font-size: var(--font-size-body-sm);
		z-index: 6;
		opacity: 0.6;
		font-weight: normal;
	}

	.project-info {
		position: absolute;
		left: var(--spacing-inline);
		top: 50%;
		transform: translateY(-50%);
		z-index: 10;
		text-align: left;
		opacity: var(--opacity-reduced);
		text-shadow: 0px 1px 1px rgba(0, 0, 0, 0.3);
		pointer-events: none;
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
