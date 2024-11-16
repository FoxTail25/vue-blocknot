<script setup>
import Ta from './components/ta.vue'
</script>
<script>
export default {
	data() {
		return {
			posts_arr: [
				{
					id: 1,
					title: 'Запись_1',
					post: '1 Здесь пока ничего нет',
					active: false
				},
				{
					id: 2,
					title: 'Запись_2',
					post: '2 Здесь пока ничего нет',
					active: false
				},
				{
					id: 3,
					title: 'Запись_3',
					post: '3 Здесь пока ничего нет',
					active: false
				},
			]
		}
	},
	methods: {
		setActivePost: function (id) {
			this.posts_arr = this.posts_arr.map(e => {
				if (e.id == id) {
					e.active = true;
				} else {
					e.active = false
				}
				return e
			})
		},
		changePost: function (id, text) {
			// console.log('vue', id, text)
			this.post_arr = this.posts_arr.map(e => {
				if (e.id === id) {
					e.post = text;
				}
				return e
			})
		}
	},
	computed: {
		active_post: function () {
			let activ = this.posts_arr.filter(e => e.active == true)[0]
			if (activ) {
				return activ
			} else {
				return {}
			}
		},
	}
}
</script>

<template>
	<h1>Блокнот</h1>
	<aside>
		<h2>
			все записи
		</h2>
		<ul>
			<li v-for="elem in posts_arr" @click="setActivePost(elem.id)" :key="elem.id">{{ elem.title }}
			</li>
		</ul>
	</aside>
	<main>
		<Ta :id="active_post?.id" :title="active_post?.title" :post="active_post?.post" @changePost="changePost" />
	</main>
</template>

<style scoped>
aside,
main {
	border: 1px solid black;
	border-radius: 5px;
	padding: 4px;
	height: 100%;
}

h2 {
	text-align: center;
}

h1 {
	grid-row: 1/2;
	grid-column: 1/3;
	text-align: center;
	height: 3rem;
}
</style>


























<!-- <script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style> -->
