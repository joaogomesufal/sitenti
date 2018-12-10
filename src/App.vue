<template>
	<div id="app">
		<v-app>
			<menu-nav></menu-nav>
			<main>
				<setores></setores>
				<utilitarios></utilitarios>
				<catalogo ></catalogo>
				<equipe ></equipe>
			</main>
		</v-app>
	</div>
</template>

<script>
import MenuNav from './assets/components/Menu.vue';
import Setores from './assets/components/Setores.vue';
import Utilitarios from './assets/components/Utilitarios.vue';
import Equipe from './assets/components/Equipe.vue';
import Catalogo from './assets/components/catalogo/Catalogo.vue';

export default {
	name: 'app',

	data () {
		return {
			height: 0
		}
	},

	components: {
		'setores': Setores,
		'utilitarios': Utilitarios,
		'equipe': Equipe,
		'catalogo': Catalogo,
		'menu-nav': MenuNav,

	},
}
</script>
