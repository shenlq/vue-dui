<template>
	<div>
		<container>
			<navbar>
				<a v-link='{"name":"demo"}'><icon type="arrow-left"></icon></a>
				<span class="split"></span>
				<span>Button</span>
			</navbar>
			<content>
				<group>
					<group-item>
						<div>
							<btn style="default" @click="click">默认</btn>
							<btn href="http://github.com">Github</btn>
							<btn style="secondary" :v-link='{"name": "demo"}'>删除</btn>
						</div>
					</group-item>
				</group>
				<group-title>disabled</group-title>
				<group>
					<group-item>
						<div>
							<btn style="default" disabled>默认</btn>
							<btn style="primary" disabled>保存</btn>
							<btn style="secondary" disabled>删除</btn>
						</div>
					</group-item>
				</group>
				<group-title>once</group-title>
				<group>
					<group-item>
						<div>
							<btn style="default" @click="click" once>默认</btn>
							<btn style="primary" once>保存</btn>
							<btn style="secondary" once>删除</btn>
						</div>
					</group-item>
				</group>
				<group-title>sm button</group-title>
				<group>
					<group-item>
						<div>
							<btn style="default" size="sm">默认</btn>
							<btn style="primary" size="sm">提交</btn>
							<btn style="secondary" size="sm">取消</btn>
						</div>
					</group-item>
				</group>
				<group-title>block</group-title>
				<group>
					<group-item pure>
						<btn style="default" block @click="click">默认</btn>
					</group-item>
				</group>
				<group>
					<group-item pure>
						<btn style="primary" block once>主题</btn>
					</group-item>
				</group>
				<group>
					<group-item pure>
						<btn style="secondary" block>取消</btn>
					</group-item>
				</group>
			</content>
		</container>
	</div>
</template>


<script>
	import { Container, Content, Navbar, Group, GroupItem, GroupTitle, Btn, Icon } from '../components/index.js';

	export default {
		components: {
		  	Container,
		  	Content,
		  	Navbar,
		    Group,
		    GroupItem,
		    GroupTitle,
		    Btn,
		    Icon
		},
		methods: {
			click(){
				alert("click");
			}
		}
	};
</script>