<template lang="pug">
	.comfirm
		.comfirm__wrap
			p.comfirm__wrap__title 王大明先收您好，請確認以下資訊，付款完成後將寄通知信至您的E-mail信箱。
			p.comfirm__wrap__subtitle 訂單明細
			.comfirm__wrap__info.detail
				.detail__title
					p 訂單明細
					p 訂單編號 B122123423
				.detail__items
					.detail__items__item
						p iPhoneX 柴犬手機殼
						p ＄790
					.detail__items__item
						p 貓貓狗狗行動電源
						p ＄1080
				.detail__price
					p 總價
					p ＄1870

			p.comfirm__wrap__subtitle 付款方式
			.comfirm__wrap__info.payment
				.payment__wrap
					p 付款方式
					p 信用卡一次付清
				.payment__wrap
					p 收件者
					p 王大明
				.payment__wrap
					p E-mail
					p 123@gmail.com
		.comfirm__buttons
			router-link.comfirm__buttons__btn(to="/payment/credit-card") 上一步
			router-link.comfirm__buttons__btn(to="/payment/success") 確認付款
</template>
<script>
export default {
	
}
</script>
<style lang="sass" scoped>
.comfirm
	display: flex
	flex-direction: column
	justify-content: space-between
	align-items: cneter
	height: 65%

	&__wrap
		height: 400px

		&__title
			font-size: 16px
			font-weight: bold
			margin-bottom: 10px

		&__subtitle
			font-size: 16px
			font-weight: bold
			border-left: 5px solid #8344bb
			padding-left: 10px
			margin-bottom: 10px

		&__info
			padding: 15px
			border: 1px solid #e2e2e2
			border-radius: 20px
			background-color: #f5f5f5
			box-shadow: 1px 1px 5px #f6f2fa

		.detail
			margin-bottom: 15px
			&__title
				display: flex
				justify-content: space-between
				font-weight: bold
			&__items
				display: flex
				justify-content: space-between
				flex-direction: column
				border-top: 1px solid #6f6f6f
				border-bottom: 1px solid #6f6f6f
				margin: 15px 0
				padding: 10px 0
				&__item
					display: flex
					justify-content: space-between
					p
						color: #6f6f6f
			&__price
				display: flex
				justify-content: space-between
				font-weight: bold
				color: #8344bb
		.payment
			&__wrap
				display: flex
				p
					&:nth-child(1)
						width: 35%

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
			&:nth-child(1)
				margin-right: 30px

		.disable
			pointer-events: none
			background-color: #c7a4d0
			cursor: unset
</style>
