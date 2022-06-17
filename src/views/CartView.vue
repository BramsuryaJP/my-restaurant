<template>
	<h1><span>Food</span> Cart</h1>
	<div class="container cart-page">
		<table>
			<tr>
				<th>Product</th>
				<th>Quantity</th>
				<th>Subtotal</th>
			</tr>
			<tr v-for="item, index in ingredients" :key="index">
				<td>
					<div class="cart-info" >
						<img :src="item.strMealThumb + '/preview'" alt="">
						<div class="info">
							{{ item.strMeal }}
							<br>
							<small>Harga: Rp. 40.000</small>
							<br>
							<a href="">remove</a>
						</div>
					</div>
				</td>
				<td><input type="number" value="1"></td>
				<td>Rp. 40.000</td>
			</tr>
		</table>
		<div class="total-price">
			<table>
				<tr>
					<td>Total Harga</td>
					<td>Rp. 120.000</td>
				</tr>
				<tr>
					<td>Pajak</td>
					<td>Rp. 12.000</td>
				</tr>
				<tr>
					<td>Total</td>
					<td>Rp. 108.000</td>
				</tr>
			</table>
		</div>
		<div class="button">
			<router-link to="/pesanan-sukses" class="btn-checkout">proceed to checkout</router-link>
		</div>
	</div>
	<FooterComponent />
</template>

<script>
import FooterComponent from '@/components/FooterComponent'
import axios from 'axios'
export default {
	name: 'CartView',
	components: {
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
			while(i < 4) {
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
	h1 {
		padding-top: 102px;
		width: 82%;
		margin: 0 auto;
		text-align: center;
		font-size: 30px;
		color: #B8D1F9;
		font-weight: 700;
		text-transform: uppercase;

		span {
			font-size: 30px;
			color: #666;
			font-weight: 500;
			text-transform: uppercase;
		}
	}

	.container {
		max-width: 82%;
		margin: auto;
		padding-left: 25px;
		padding-right: 25px;
	}
  .cart-page {
		margin: 35px auto;

		table {
			width: 100%;
			border-collapse: collapse;

			.cart-info {
				display: flex;
				flex-wrap: wrap;

				.info {
					padding-top: 5px;
				}
			}

			th {
				text-align: left;
				padding: 10px;
				color: #fff;
				background: #77A4E5;
				font-weight: 500;
			}

			td {
				padding: 10px 5px;

				&:last-child {
					text-align: right
				}

				input {
					width: 40px;
					height: 30px;
					padding: 5px;
				}

				a {
					color: #ff523b;
					font-size: 14px;
					text-decoration: none;
				}

				img {
					width: 80px;
					height: 80px;
					margin-right: 10px;
				}
			}
		}

		.total-price {
			display: flex;
			justify-content: flex-end;

			table {
				border-top: 3px solid #77A4E5;
				width: 100%;
				max-width: 400px;
			}

			td:last-child {
				text-align: right;
			}
		}

		.button {
			display: flex;
			justify-content: flex-end;

			.btn-checkout {
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
				display: flex;
				justify-content: center;
				width: 100%;
				max-width: 400px;

				&:hover {
					background: -webkit-linear-gradient(0deg, rgb(160 193 244)0%, rgb(119 164 229)100%);
				}
			}
		}
	}

	@media only screen and (max-width: 600px) {
		.cart-info {
			p {
				display: none;
			}
		}
	}
</style>