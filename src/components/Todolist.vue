<template>
	<div id="Todolist">
		<div class="Todolist-text">
			<el-input v-model="todo" placeholder="请添加任务">
				<i slot="suffix" class="el-input__icon el-icon-plus" @click="addTodolist"></i>
			</el-input>
		</div>
		<h2>待完成</h2>
		<ul class="Todolist-list">
			<li v-for="(item,index) in todos" v-if="item.checked == false">
				<el-checkbox @change="updateTodolist" v-model="item.checked">{{item.todo}}</el-checkbox>
				<div class="Todolist-deleat">
					<el-button @click="removeTodolist(index)" type="primary" icon="el-icon-delete"></el-button>
				</div>
				
			</li>
		</ul>
		<h2>已完成</h2>
		<ul class="Todolist-list">
			<li v-for="(item,index) in todos" v-if="item.checked == true">
				<el-checkbox @change="updateTodolist" v-model="item.checked">{{item.todo}}</el-checkbox>
				<div class="Todolist-deleat">
					<el-button @click="removeTodolist(index)" type="primary" icon="el-icon-delete"></el-button>
				</div>
				
			</li>
		</ul>
	</div>
</template>

<script>
	export default{
		name:"Todolist",
		data(){
			return{
				todo:"",
				todos:[{
					"checked":false,
					"todo":"学习angular"
				},{
					"checked":true,
					"todo":"学习vue"
				},{
					"checked":false,
					"todo":"学习react"
				},{
					"checked":false,
					"todo":"学习flex"
				},{
					"checked":true,
					"todo":"学习threejs"
				},{
					"checked":true,
					"todo":"学习cesiumjs"
				},{
					"checked":true,
					"todo":"学习videojs"
				},{
					"checked":true,
					"todo":"学习jquery"
				},{
					"checked":true,
					"todo":"学习gulp"
				}]
			}
		},
		methods:{
			addTodolist(){
				//输入框有值才添加
				if (this.todo) {
					this.todos.push({
						checked:false,
						todo:this.todo
					});
					sessionStorage.setItem("todos",JSON.stringify(this.todos));
					this.todo = "";
				};
			},
			removeTodolist(index){
				this.todos.splice(index,1);
				sessionStorage.setItem("todos",JSON.stringify(this.todos));
			},
			updateTodolist(){
				sessionStorage.setItem("todos",JSON.stringify(this.todos));
			}
		},
		mounted:function(){
			
			var todos = JSON.parse(sessionStorage.getItem("todos"));
			if (todos) {
				this.todos = todos;
				this.addTodolist();
			};
			
		}
	}
</script>

<style scoped>
	body,html,ul,li{
		padding: 0;
		margin: 0;
	}
	ul,li{
		list-style: none;
	}
	#Todolist{
		padding: 20px;
	}
	.Todolist-text{
		padding: 20px;
	}
	.Todolist-list>li{
		border-bottom: 1px solid #999;
		padding: 10px;
	}
	.Todolist-list>li:after{
		content: "";
		display: block;
		height: 0;
		clear: both;
	}
	.Todolist-deleat{
		float: right;
	}
</style>