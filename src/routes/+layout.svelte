<script>
	import "../app.css";
	import Icon from "@iconify/svelte";
	import "@fontsource/poppins";
	import { onMount } from "svelte";
	let { children } = $props();

	let isMenuOpen = $state(false);
	let isMobile = $state(false);

	const checkMobile = () => {
		isMobile = window.innerWidth <= 768;
	};

	const toggleMenu = () => {
		isMenuOpen = !isMenuOpen;
	};

	onMount(() => {
		checkMobile();
		window.addEventListener("resize", checkMobile);

		return () => {
			window.removeEventListener("resize", checkMobile);
		};
	});
</script>

<svelte:window on:resize={checkMobile} />

<main>
	<div class="nav">
		<div class="logo">
			<a href="/" class="logo-link">
				<img src="favicon.PNG" alt="Logo" class="logo-img" />
				<h1 class="username">swiftcurated</h1>
			</a>
		</div>

		<button class="menu-toggle" onclick={toggleMenu}>
			<Icon
				icon={isMenuOpen ? "mdi:close" : "mdi:menu"}
				width="24"
				height="24"
			/>
		</button>

		<ul class="menulist" class:active={isMenuOpen}>
			<li>
				<a
					href="/blackpink-gamakay-gmk67-customized-mechanical-keyboard"
					onclick={toggleMenu}
				>
					Keyboard
					{#if isMobile}
						<Icon
							icon="ep:right"
							width="20"
							height="20"
							class="menu-icon"
						/>
					{/if}
				</a>
			</li>
			<li>
				<a
					href="/logitech-g304-lightspeed-wireless-gaming-mouse"
					onclick={toggleMenu}
				>
					Mouse
					{#if isMobile}
						<Icon
							icon="ep:right"
							width="20"
							height="20"
							class="menu-icon"
						/>
					{/if}
				</a>
			</li>
			<li class="social-links">
				<a
					href="https://www.instagram.com/swiftcurated"
					target="_blank"
					rel="noopener"
				>
					<Icon icon="mdi:instagram" width="20" height="20" />
				</a>
			</li>
		</ul>
	</div>

	{@render children()}

	<footer class="footer">
		<div class="footer-content">
			<p>
				&copy; {new Date().getFullYear()} Swift Curated. All rights reserved.
			</p>
		</div>
	</footer>
</main>

<style lang="scss">
	main {
		font-family: "Poppins", sans-serif;
	}

	.nav {
		position: fixed;
		top: 0;
		right: 0;
		padding: 1rem 3%;
		width: 100%;
		z-index: 1000;
		display: flex;
		align-items: center;
		justify-content: space-between;
		transition: all 0.6s ease;
		background: rgba(255, 255, 255, 0.4);
		backdrop-filter: blur(10px);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		height: 80px;

		.logo {
			display: flex;
			align-items: center;

			.logo-link {
				display: flex;
				align-items: center;
				text-decoration: none;

				.logo-img {
					width: 50px;
					height: 50px;
					border-radius: 50%;
					object-fit: cover;
					margin-right: 10px;
				}
			}

			.username {
				font-weight: bold;
			}
		}

		.menu-toggle {
			display: none;
			background: none;
			border: none;
			cursor: pointer;
			padding: 5px;
			z-index: 1001;
		}

		.menulist {
			display: flex;
			list-style: none;
			margin: 0;
			padding: 0;
			gap: 10px;

			li {
				a {
					display: flex;
					align-items: center;
					text-decoration: none;
					color: inherit;
					padding: 8px 16px;

					.menu-icon {
						margin-left: 10px;
						flex-shrink: 0;
					}
				}
			}

			&.active {
				right: 0;
			}

			.social-links {
				display: none;

				@media (max-width: 768px) {
					display: flex;
					justify-content: center;
					width: 100%;
					margin-top: auto;
					padding: 1rem 0;
					border-top: 1px solid rgba(0, 0, 0, 0.1);
				}

				a {
					color: inherit;
				}
			}
		}

		@media (max-width: 768px) {
			padding: 15px 5%;

			.menu-toggle {
				display: block;
			}

			.menulist {
				position: fixed;
				top: 80px;
				right: -100%;
				width: 70%;
				height: calc(100vh - 80px);
				background: white;
				backdrop-filter: blur(10px);
				flex-direction: column;
				align-items: flex-start;
				justify-content: flex-start;
				transition: all 0.5s ease;
				padding: 30px 0;
				gap: 10px;
				z-index: 999;
				border-left: 1px solid rgba(0, 0, 0, 0.1);

				li {
					width: 100%;
					padding: 5px 10px;

					a {
						display: flex;
						align-items: center;
						justify-content: space-between;
						width: 100%;
						padding: 6px 1.5rem;
					}
				}
			}
		}

		@media (max-width: 480px) {
			.logo {
				.logo-link {
					.logo-img {
						width: 40px;
						height: 40px;
					}
				}

				.username {
					font-size: 0.9rem;
				}
			}

			.menulist {
				width: 80%;
			}
		}
	}

	.footer {
		padding: 2rem;
		text-align: center;

		.footer-content {
			display: flex;
			justify-content: center;
			align-items: center;
			max-width: 1200px;
			margin: 0 auto;
		}

		@media (max-width: 768px) {
			padding: 5px;

			p {
				font-size: 0.9rem;
			}
		}
	}
</style>
