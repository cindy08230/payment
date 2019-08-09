<template lang="pug">
	.homepage
		.homepage__payment
			.homepage__payment__wrap(
				v-for="(way, index) in paymentWay"
				:key="way.handle"
				:class="{ 'payment-active': way.handle === chooseWay }"
				@click="chooseWay = way.handle")
				.icon
					img(:src="way.image", :alt="way.title")
				.content
					h3.content__title(v-text="way.title")
					p.content__subtitle(v-text="way.subtitle")
		.homepage__buttons
			.homepage__buttons__btn.disable 上一步
			router-link.homepage__buttons__btn(
				:to="nextLink"
				:class="{ disable : chooseWay !== 'credit-card' }") 下一步
</template>
<script>
export default {
	props:{
		paymentWay:{
			type: Array,
			required: true
		}
	},
	data(){
		return {
			nextLink: '/payment',
			chooseWay: ''
		}
	},
	watch: {
		chooseWay(){
			this.nextLink = `/payment/${this.chooseWay}`
		}
	}
}
</script>
<style lang="sass" scoped>
.homepage
	display: flex
	flex-direction: column
	justify-content: space-between
	height: 65%
	&__payment
		height: 400px
		&__wrap
			display: flex
			align-items: center
			padding: 5px 15px
			width: 70%
			border: 1px solid #f6f2fa
			border-radius: 10px
			margin: 0 auto
			box-shadow: 1px 1px 5px #f6f2fa
			cursor: pointer

			&:not(:last-of-type)
				margin-bottom: 10px

			.icon
				width: 50px
				margin-right: 10px

			.content
				&__title
					font-size: 16px
				&__subtitle
					font-size: 12px
					color: #aaa

		.payment-active
			border: 1px solid #9159c2
			color: #9159c2
			outline: none

			.content__subtitle
				color: #9159c2

	&__buttons
		display: flex
		justify-content: space-between
		margin: 0 auto
		width: 100%

		&__btn
			width: 45%
			height: 40px
			border-radius: 50px
			background-color: #8344bb
			display: flex
			align-items: center
			justify-content: center
			color: #fff
			cursor: pointer
			text-decoration: none

		.disable
			pointer-events: none
			background-color: #c7a4d0
			cursor: unset
			
</style>
