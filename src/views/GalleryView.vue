<template>
  <div class="gallery">
		<div class="container">
			<h1 class="heading"><span>Food</span> Gallery</h1>
			<div class="search-box">
				<form @submit.prevent="getFiltered">
					<i class="fa fa-search"></i>
					<input type="search" placeholder="Ex. Seafood, Beef, Dessert" v-model="query">
				</form>
			</div>
			<div class="image-container">
				<div class="image" v-for="item, index in ingredients" :key="index" >
					<img :src="item.strMealThumb + '/preview'" :alt="item.strMeal">
					<div class="content">
						<h3>{{ item.strMeal }}</h3>
						<p>{{ item.strCategory }}</p>
						<div class="stars">
							<i class="fas fa-star"></i>
							<i class="fas fa-star"></i>
							<i class="fas fa-star"></i>
							<i class="fas fa-star"></i>
							<i class="fas fa-star-half-alt"></i>
						</div>
						<a class="content-btn">add to cart</a>
					</div>
				</div>
			</div>
		</div>
	</div>
	<FooterComponent />
</template>

<script>
import FooterComponent from '@/components/FooterComponent'
import axios from 'axios'
export default {
  name: 'GalleryView',
	components: {
		FooterComponent
	},
	data () {
    return {
			query: null,
      ingredients: []
    }
  },
  methods: {
    async getMeals() {
      const URL = "https://www.themealdb.com/api/json/v1/1/random.php?key=1"
      var i = 0;
      while(i < 9) {
        this.ingredients.push((await axios.get(URL)).data.meals[0]);
        i++;
      }
    },
		async getFiltered() {
			const URL = "https://www.themealdb.com/api/json/v1/1/filter.php?c=" + this.query
			await axios.get(URL) 
				.then((response) => {
					this.ingredients = response.data.meals
					console.log(this.ingredients);
				})
				.catch((err) => {
					console.log(err)
				})
		}
  },
  mounted () {
    this.getMeals()
  }
}
</script>

<style lang="scss" scoped>
	.gallery {
		padding-top: 82px;

		.container {
			width: 82%;
			margin: 0 auto;

			.heading{
				text-align: center;
				font-size: 30px;
				padding-top: 20px;
				color: #B8D1F9;
				font-weight: 700;
				text-transform: uppercase;
				padding-bottom: 20px;

				span{
					font-size: 30px;
					color: #666;
					font-weight: 500;
					text-transform: uppercase;
				}
			}

			.search-box {
				width: 440px;
				height: 40px;
				background-color: white;
				border-radius: 30px;
				border: 1px solid #B8D1F9;
				display: flex;
				margin: auto;
				align-items: center;
				padding: 20px;
				margin-bottom: 20px;

				form {
					> i {
						font-size: 20px;
						color: #777
					}

					> input {
						flex: 1;
						height:40px;
						border: none;
						width: 360px;
						outline: none;
						font-size: 18px;
						padding-left: 10px;
					}
				}
			}

			.image-container {
				display: flex;
				flex-wrap: wrap;
				gap: 20px;
				margin-bottom: 20px;

				.image {
					height: 15rem;
					flex: 1 1 380px;
					border: 1rem solid #fff;
					box-shadow: 0 .5rem 1.5rem rgba(0, 0, 0, .1); 
					border-radius: 5px;
					position: relative;
					overflow: hidden;

					img {
						height: 100%;
						width: 100%;
						object-fit: cover;
					}

					.content {
						position: absolute;
						top: -120%;
						left: 0;
						height: 100%;
						width: 100%;
						background: rgba(255, 255, 255, .9);
						padding: 20px;
						text-align: center;
						justify-content: center;

						h3 {
							font-size: 18px;
							font-weight: 700;
							color: #333;
							padding-bottom: 4px;
						}

						.stars {
							padding-bottom: 20px;

							i {
								font-size: 16px;
								color: #FA9746;
							}
						}

						.content-btn {
							background: -webkit-linear-gradient(0deg, rgb(160 193 244)0%, rgb(119 164 229)100%);
							padding: 15px 20px;
							border: none;
							color: #ffffff;
							border-radius: 5px;
							width: 90%;
							display: inline-block;
							text-transform: uppercase;
							font-size: 14px;
							font-weight: 500;
							cursor: pointer;
							margin-bottom: 15px;

							&:hover, :active{
								box-shadow: 0 20px 20px 0 rgb(132 144 255 / 30%);
							}
						}
					}
				}
			}
		}
		.container .image-container .image:hover .content{
			top:0;
		}
	}
</style>