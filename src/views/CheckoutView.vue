<template>
	<main>
		<section class="section-checkout section">
			<div class="container grid grid-two-column">
				<div class="section-checkout-data">
					<h1 class="checkout-heading">SUKSES!!</h1>
					<p class="checkout-paragraph">
						Pesanan Anda Segera Diproses. Selamat Menunggu
					</p>
				</div>
				<div class="section-checkout-image">
					<img src="../assets/images/checkout.png" alt="" class="checkout-img">
				</div>
			</div>
		</section>
	</main>
	<FooterComponent />
</template>

<script>
import FooterComponent from '@/components/FooterComponent.vue'
export default {
	name:	'CheckoutView',
	components: {
		FooterComponent
	}
}
</script>

<style lang="scss" scoped>
	.section {
		padding: 88px 0;

		.container {
			max-width: 90%;
			margin: 0 auto;

			&.grid {
				display: grid;
				gap: 10px;
			}

			&.grid-two-column {
				grid-template-columns: repeat(2, 1fr);
				margin-top: 29px
			}
		}
	}

	.section-checkout {
		background-color: #fff;
	}

	.section-checkout-data{
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin: auto;

		.checkout-top-data {
			text-transform: uppercase;
			font-weight: 500;
			font-size: 12px;
			margin-top: 15px;
			color: rgb(119 164 229);
		}

		.checkout-heading {
			text-transform: uppercase;
			font-weight: 700;
			font-size: 48px;
			margin-top: 40px;
		}

		.checkout-paragraph {
			margin-top: 10px;
			margin-bottom: 50px;
			max-width: 23rem;
			font-size: 16px;
		}
	}

	.section-checkout-image {
		display: flex;
		justify-content: center;
		align-items: center;

		.checkout-img {
			max-width: 90%;
		}
	}

	@media (max-width: 980px) {
		.container {
			padding: 0 3.2rem;
		}

		.section-checkout {
			h1 {
				margin-top: 20px;
				line-height: 1.05;
			}

			p {
				text-align: center;
			}
		}
	}

	@media only screen and (max-width: 780px) {
		.container {
			max-width: 720px;
		}
		
		.section-checkout {
			.grid-two-column {
				grid-template-columns: 1fr;
			}
		}

		.grid-two-column>.section-checkout-data {
			order: 2;
		}

		.grid-two-column>.section-checkout-image {
			order: 1;
		}


		.section-checkout-data {
			align-items: center;
		}

		.checkout-heading {
			text-align: center;
		}
		.hero-paragraph {
			text-align: center;
			margin-top: 2rem;
			font-size: 16px;
		}

		.section-checkout{
			img {
					width: 100%;
			}
		}
	}

	@media only screen and (max-width: 375px) {
		.container {
			max-width: 720px;
		}
		
		.section-checkout {
			.grid-two-column {
				grid-template-columns: 1fr;
				padding-top: 50px;
			}
		}

		.grid-two-column>.section-checkout-data {
			order: 2;
		}

		.grid-two-column>.section-checkout-image {
			order: 1;
		}

		.section-checkout-data {
			align-items: center;
		}

		.checkout-heading {
			text-align: center;
		}
		.hero-paragraph {
			text-align: center;
			margin-top: 2rem;
			font-size: 16px;
		}

		.section-checkout{
			img {
				width: 100%;
			}
		}
	}
</style>