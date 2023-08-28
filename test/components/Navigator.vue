<template lang="pug">
    div(class="nav__container")
      div(class="nav-vector__svg")
        svg(viewBox="0 0 32 32", fill="none", xmlns="http://www.w3.org/2000/svg")
          path(d="M14 6L5 15.5L14 25", color="black", stroke-width="3")
      p К профилю
</template>

<style lang="sass" scoped>
$light-blue: #2B4EEF

.nav__container
	display: flex
	flex-direction: row
	align-items: center
	margin-bottom: 45px
	cursor: pointer

	.nav-vector__svg
		width: 32px
		height: 32px
		stroke: black
		
.nav__container:hover
	color: $light-blue

	.nav-vector__svg
		stroke: $light-blue

@media (max-width: 1024px)
	.nav__container
		margin-bottom: 32px

		.nav-vector__svg
			width: 16px
			height: 16px
</style>