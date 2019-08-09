<template lang="pug">
	.success
		.success__image
			img(src="../assets/undraw_successful_purchase_uyin-2.svg")
		h2.success__title 感謝您的購買
		p.success__content 系統已寄出通知信至您的E-mail信箱。您訂購的商品預計在2-3天後送達！
		router-link.success__button(to="/payment") 繼續購物
</template>
<script>
export default {
    
}
</script>
<style lang="sass" scoped>
.success
	height: 65%
	display: flex
	flex-direction: column
	align-items: center

	&__image
		max-width: 300px
		width: 100%
		margin-top: 25px

	&__title
		margin: 25px 0 15px

	&__content
		margin-bottom: 30px
		color: #adadad
		text-align: center

	&__button
		width: 80%
		height: 40px
		border-radius: 50px
		background-color: #8344bb
		display: flex
		align-items: center
		justify-content: center
		color: #fff
		cursor: pointer
		text-decoration: none
</style>
