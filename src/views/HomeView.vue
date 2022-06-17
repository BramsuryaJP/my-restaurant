<template>
	<div class="home">
		<HeroComponent />
		<section class="menus" id="menus">
			<h1 class="heading"><span>Our</span> Menu</h1>
			<router-link to="/gallery" class="all-menus">Lihat Semua</router-link>

			<div class="card-container">
				<CardComponent  v-for="item, index in ingredients" :key="index" :ingredient="item" />
			</div>
		</section>
	</div>
	<FooterComponent />
</template>

<script>
import HeroComponent from '@/components/HeroComponent.vue'
import CardComponent from '@/components/CardComponent.vue'
import FooterComponent from '@/components/FooterComponent.vue'
import axios from 'axios'

export default {
	name:	'HomeView',
	components: {
		HeroComponent,
		CardComponent,
		FooterComponent
	},
	data () {
		return {
			ingredients: []
		}
	},
	methods: {
		async getIngredients() {
			const URL = "https://www.themealdb.com/api/json/v1/1/random.php?key=1"
			var i = 0;
			while(i < 6) {
				this.ingredients.push((await axios.get(URL)).data.meals[0]);
				i++;
			}
		}
	},
	mounted () {
		this.getIngredients()
	}
}
</script>
<style lang="scss" scoped>
	.home {
		padding-top: 82px;
	}

	.menus {
		max-width: 82%;
		margin: 0 auto;
		padding-bottom: 20px;

		.heading {
			text-align: center;
			font-size: 30px;
			padding-top: 20px;
			color: #B8D1F9;
			font-weight: 700;
			text-transform: uppercase;
			padding-bottom: 20px;

			span {
				font-size: 30px;
				color: #666;
				font-weight: 500;
				text-transform: uppercase;
			}
		}

		.all-menus {
			font-weight: 500;
			text-decoration: none;
			display: flex;
			justify-content: right;
			color: #000;

			&:hover {
				color: #FA9746;
			}
		}

		.card-container {     
			display: grid;
			grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
			gap: 20px;
			padding-top: 20px;
			padding-bottom: 20px;

			.card {
				padding: 15px;
				background: #fff;
				border-radius: 5px;
				border: 1px solid rgba(0, 0, 0, .2);
				box-shadow: 0 .5rem 1.5rem rgba(0, 0, 0, .1);  
				position: relative;
				overflow: hidden;
				text-align: center;

				h3 {
					font-size: 16px;
				}

				.stars {
					padding: 5px 0;

					i {
						font-size: 16px;
						color: #FA9746;
					}
				}

				img {
					height: 17rem;
					margin: 1rem 0;
				}

				.btn-add-cart {
					margin-top: 1rem;
					display: inline-block;
					font-size: 14px;
					text-transform: uppercase;
					text-decoration: none;
					color:#fff;
					background: #77A4E5;
					border-radius: 5px;
					font-weight: 500;
					cursor: pointer;
					padding:13px 40px;

					&:hover {
						background: -webkit-linear-gradient(0deg, rgb(160 193 244)0%, rgb(119 164 229)100%);
					}
				}
			}
		}
	}
</style>
