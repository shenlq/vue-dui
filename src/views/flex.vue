<template>
	<div>
		<container>
			<navbar>
				<a v-link='{"name": "demo"}'><icon type="arrow-left"></icon></a>
				<span class="split"></span>
				<span>Flex</span>
			</navbar>
			<content>
				<group-title>等比栅栏</group-title>
				<flex class="demo-flex">
					<flex-item class="text-center demo-flex-item">1</flex-item>
					<flex-item class="text-center demo-flex-item">2</flex-item>
					<flex-item class="text-center demo-flex-item">3</flex-item>
					<flex-item class="text-center demo-flex-item">4</flex-item>
					<flex-item class="text-center demo-flex-item">5</flex-item>
					<flex-item class="text-center demo-flex-item">6</flex-item>
				</flex>
				<flex class="demo-flex">
					<flex-item class="text-center demo-flex-item">1</flex-item>
					<flex-item class="text-center demo-flex-item">2</flex-item>
					<flex-item class="text-center demo-flex-item">3</flex-item>
				</flex>
				<flex class="demo-flex">
					<flex-item class="text-center demo-flex-item">1</flex-item>
					<flex-item class="text-center demo-flex-item">2</flex-item>
				</flex>
				<group-title>根据子元素宽度自动排列</group-title>

				<flex class="demo-flex" wrap="wrap" justify="between">
					<div class="text-center demo-flex-wrap-item">1</div>
					<div class="text-center demo-flex-wrap-item">2</div>
					<div class="text-center demo-flex-wrap-item">3</div>
					<div class="text-center demo-flex-wrap-item">4</div>
					<div class="text-center demo-flex-wrap-item">5</div>
				</flex>
			</content>
		</container>
	</div>
</template>


<script>
	import { Container, Content, GroupTitle, Navbar, Flex, FlexItem, Icon } from '../components/index.js';

	export default {
		components: {
		  	Container,
		  	Content,
		  	GroupTitle,
		  	Navbar,
		    Flex,
		    FlexItem,
		    Icon
		}
	};
</script>

<style>
	.demo-flex{
		margin-bottom: 1rem;
	}

	.demo-flex-item{
		color: #fff;
		padding: 0.6rem;
		background: green;
		border-radius: 2px;
	}

	.demo-flex-item:not(:last-child){
		margin-right: 0.6rem;
	}

	.demo-flex-wrap-item{
		color: #fff;
		padding: 0.6rem;
		background: green;
		border-radius: 2px;
		width: 49%;
		margin-top: 0.6rem;
	}
</style>