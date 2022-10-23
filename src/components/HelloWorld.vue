<template>
  <div class="hello" v-for="posts in post">
	<h3>Название поста : {{ posts.title }}</h3>
	<p>Описание : {{ posts.body }}</p>
  </div>

  .<div class="container">
    <div class="row">
	<h2>Создание поста</h2>
		<form method="post">
			<input @input="inputTitle" v-bind:value="title" class="title__post" type="text" name="" id="" placeholder="Название поста">
			<input @input="inputBody" v-bind:value="body" class="body__post" type="text" name="" id="" placeholder="Описание поста">
			<button class="btn button__add-post" type="submit" @click.prevent="createPost">Добавить</button>
		</form>
	</div>
  </div>
</template>

<script lang="ts">
	export default {
		data() {
			return {
				post: [
					{id:1, title: 'Первый пост', body:"описание"},
					{id:2, title: 'Второй пост', body:"описание"},
					{id:3, title: 'Третий пост', body:"описание поста три"},
				],
				title: '',
				body: '',
			}
		},
		methods: {
			createPost() {
				const newPost = {
					id: Date.now(),
					title:this.title,
					body:this.body,
				}
				this.post.push(newPost);
				this.title = '';
				this.body = '';
			},
			inputTitle(event: any): void {
				this.title = event.target.value;
			},
			inputBody(event: any) {
				this.body = event.target.value;
			}
		},
	}
</script>

<style scoped lang="scss">
	.title__post, .body__post {
		padding: 10px;
		margin: 10px;
		border-radius: 30px;
		text-align: center;
			&.disabled {
				display: none;
			}
	}
	.btn {
		&.button__add-post {
			padding: 15px;
			margin: 10px;
			border-radius: 30px;
			text-align: center;
			background-color: none;
			font-weight: 700;
			border: none;
			cursor: pointer;
		}
	}
</style>
