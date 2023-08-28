<template lang="pug">
	div
		div(class="posts__container")
			img(class="posts-logo__svg", src="@/assets/svg/logo.svg")
			h1(class="posts-header__h1")
				mark Скидки и бонусы
				br
				| для клиентов Журналуса
		#posts(class="posts-grid__container container")
			figure#fist-post
				img(class="posts-own__img", src="@/assets/jpeg/sale.jpg")
				figcaption
					span Николай Иронов
					h1 Скидка на подписку нейросети Николай Иронов
					hr
					p Мгновенно создаёт крутую айдентику, учитывая особенности каждого бизнеса.
					button(@click="copyCode(0)", class="posts-button white__button") {{buttonArr[0]}}
			figure#second-post
				img(class="posts-own__img", src="@/assets/jpeg/naray.svg")
				span.span-black naray.one
				h1 10% скидка на онлайн-генератор мерча для всех точек мира
				hr.hr-black
				p Простой инструмент для создания уникального мерча любимого района.
				button.posts-button(@click="copyCode(1)") {{buttonArr[1]}}
			figure#prev-post
				div(class="posts-own__circle")
				span.span-black naray.one
				h1 10% скидка на онлайн-генератор мерча для всех точек мира
				hr.hr-black
				p Простой инструмент для создания уникального мерча любимого района.
				button.posts-button(@click="copyCode(2)") {{buttonArr[2]}}
			figure#last-post
				div(class="figure-img__container", id="last-img__container")
					img#last-img(class="posts-own__img", src="@/assets/jpeg/dashamail.png")
				figcaption(id="last-post__figure")
					span.span-black DashaMail
					h1 Полугодовая подписка на email-рассылку
					hr
					p Чудесная компания, занимающейся рассылкой электронной почты.
					button.posts-button(@click="copyCode(3)") {{buttonArr[3]}}

</template>

<script>
export default {
	name: 'posts',
	data () {
		return {
			buttonText: 'Промо-код скопирован',
			buttonNum: -1,
			resizeInt: null,
			codeShowTimeout: null
		}
	},
	computed: {
		buttonArr () {
			if(this.buttonNum === 0)
				return ['Промо-код скопирован', 'SDXPD13', 'SDXPD13', 'SDXPD13']
			if(this.buttonNum === 1)
				return ['SDXPD13', 'Промо-код скопирован', 'SDXPD13', 'SDXPD13']
			if(this.buttonNum === 2)
				return ['SDXPD13', 'SDXPD13', 'Промо-код скопирован', 'SDXPD13']
			if(this.buttonNum === 3)
				return ['SDXPD13', 'SDXPD13', 'SDXPD13', 'Промо-код скопирован']
			else
				return ['SDXPD13', 'SDXPD13', 'SDXPD13', 'SDXPD13']
		}
	},
	mounted() {
		this.resizeEvent()
		this.resizeInt = window.addEventListener("resize", (event) => this.resizeEvent());
	},
	methods: {
		copyCode (i) {
			navigator.clipboard.writeText('SDXPD13');
			this.buttonNum = i
			this.codeShowTimeout = null
			this.codeShowTimeout = setTimeout(()=>{
				this.buttonNum = -1
			}, 3000)
			this.resizeEvent()
		},
		resizeEvent() {
			if (window.screen.width > 1024) {
				let size = document.getElementById('fist-post').offsetHeight +
				document.getElementById('second-post').offsetHeight - document.getElementById('prev-post').offsetHeight - 48 
				document.getElementById("last-post").style.height = size + 'px';
				document.getElementById("last-img").style.height = 265 + 'px';
			}
			else {
				document.getElementById("last-img").style.height = 162 + 'px';
				document.getElementById("last-post").style.height = 543 + 'px';
			}
			let imgSize = document.getElementById('last-post').offsetHeight - document.getElementById('last-post__figure').offsetHeight
			document.getElementById('last-img__container').style.height = imgSize + 'px';
		}
	},
	beforeDestroy () {
	    clearInterval(this.resizeInt)
	},
}

</script>


<style lang="sass" scoped>
$light-green: #00ff19
$bg-grey: #F2F2F2
$light-blue: #2B4EEF

.posts__container
	display: flex
	flex-direction: row
	gap: 20px
	margin-bottom: 48px

.posts-grid__container

	.posts-logo__svg 
		width: 107px
		height: 99px

	.posts-own__img
		width: 100%
		object-fit: contain

	figure
		.posts-own__circle 
			width: 137px
			height: 137px
			margin: auto
			margin-top: 19px
			margin-bottom: 26px
			border-radius: 50%
			background-color: $light-green

		&:first-child
			figcaption
				color: white

			img
				height: 100%

		&:nth-child(2), &:nth-child(3)
			background-color: $bg-grey
			padding: 24px
			display: flex
			flex-direction: column
			
			flex-wrap: nowrap
			gap: 10px

			img
				margin: auto
				width: 174px
				height: 136px
				margin-bottom: 27px
				padding-top: 35px


		&:nth-child(4) 
			background-color: $bg-grey
			padding: 24px
			display: flex
			
			flex-direction: column
			
			flex-wrap: nowrap
			gap: 10px


			img
				width: 360px
				object-fit: contain
				height: 265px
				margin: auto
	img
		max-width: 100%
		display: block

	figure
		position: relative
		margin: 0
		display: grid
		border-radius: 24px
		grid-template-rows: 1fr auto
		margin-bottom: 24px
		break-inside: avoid


		> img
			grid-row: 1 / -1
			grid-column: 1

		.posts-button
			background-color: black
			color: white
			border: none
			padding: 16px 32px
			margin: auto
			margin-top: 22px
			border-radius: 8px

		.white__button
			background-color: white
			color: black
		button:hover 
			background-color: $light-blue
			color: white

	figcaption
		position: absolute
		bottom: 0
		z-index: 1
		padding: 24px
		gap: 10px
		display: flex
		flex-direction: column
		text-align: left


.container
	column-count: 2
	column-gap: 24px
	padding-bottom: 208px


#last-img__container
	display: flex
	align-items: center
	justify-content: center




@media (max-width: 1024px)
	.posts__container
		flex-direction: column
		gap: 24px

		.posts-logo__svg 
			width: 85px
			height: 78px

	.posts-grid__container figure
		margin-bottom: 12px

	.container 
		column-gap: 12px
		column-count: 1
	
	figcaption
		padding: 12px !important


	#second-post, #prev-post, #last-post
		padding: 12px !important
	
	#last-post__figure
		padding: 0 12px 12px 0 !important

	figcaption
		width: calc(100% - 24px)

</style>