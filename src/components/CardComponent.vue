<template>
	<div class="card">
		<img :src="ingredient.strMealThumb + '/preview'" :alt="ingredient.strMeal">
		<h3>{{ ingredient.strMeal }}</h3>
		<div class="stars">
			<i class="fas fa-star"></i>
			<i class="fas fa-star"></i>
			<i class="fas fa-star"></i>
			<i class="fas fa-star"></i>
			<i class="fas fa-star-half-alt"></i>
		</div>
		<a class="btn-add-cart">add to cart</a>
	</div>
</template>

<script>
export default {
  name: "CardComponent",
  props: ["ingredient"]
}
</script>

<style lang="scss" scoped>
	.card {
		padding: 15px;
		background: #fff;
		border-radius: 5px;
		border: 1px solid rgba(0, 0, 0, .2);
		box-shadow: 0 .5rem 1.5rem rgba(0, 0, 0, .1);  
		position: relative;
		overflow: hidden;
		height: 400px;
		text-align: center;

		h3{
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
			height: 45%;
			width: 80%;
			margin: 1rem 0;
		}

		.btn-add-cart {
			margin-top: 1rem;
			display: inline-block;
			font-size: 14px;
			text-transform: uppercase;
			text-decoration: none;
			color:#fff;
			width: 80%;
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
</style>