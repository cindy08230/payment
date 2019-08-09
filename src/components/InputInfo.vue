<template lang="pug">
	.info
		.info__wrap
			.info__wrap__image
				img(src="../assets/undraw_Credit_card_3ed6.svg")
			.info__wrap__content
				h3.info__wrap__content__title 輸入信用卡資訊
				input.info__wrap__content__input(placeholder="信用卡號" v-model="cardID")
				input.info__wrap__content__input(placeholder="持有人姓名" v-model="name")
				.info__wrap__content__half
					input.info__wrap__content__input.input-half(placeholder="有效月/年" v-model="date")
					input.info__wrap__content__input.input-half(placeholder="CVV" v-model="cvv")
		.info__buttons
			router-link.info__buttons__btn(to="/payment") 上一步
			router-link.info__buttons__btn(
				to="/payment/comfirm-order"
				:class="{disable: !isButtonDisable}") 下一步
</template>
<script>
export default {
	data(){
		return {
			cardID: '',
			name: '',
			date: '',
			cvv: ''
		}
	},
	computed: {
		isButtonDisable() {
			return Boolean(this.cardID && this.name && this.date && this.cvv)
		}
	}
}
</script>
<style lang="sass" scoped>
.info
	display: flex
	flex-direction: column
	justify-content: space-between
	align-items: cneter
	height: 65%
	&__wrap
		height: 400px
		&__image
			max-width: 170px
			width: 100%
			margin: 0 auto
			margin-bottom: 20px
		
		&__content
			display: flex
			flex-direction: column
			justify-content: flex-start
			align-items: cneter
			padding: 0 30px

			&__title
				margin-bottom: 20px

			&__input
				width: calc(100% - 30px)
				height: 50px
				background-color: #eee
				border-radius: 50px
				outline: none
				padding: 0 15px
				margin-bottom: 20px
				font-size: 16px

			&__half
				display: flex
				justify-content: space-between

			.input-half
				width: calc(45% - 30px)

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
