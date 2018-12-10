<template>
	<div id="equipe" class="section">
		<v-container>
			<v-layout row>
				<v-flex md12 class="section-title">
					<h3>Equipe</h3>
					<p>Servidores e suas funções.</p>
				</v-flex>
			</v-layout>

			<v-layout row wrap class="plus" v-for="setor in setores" v-bind:key="setor.nome">
				<v-flex sm12 xs12 md4 class="employee" v-for="integrante in setor.integrantes" v-bind:key="integrante.nome">
						<div class="employee-avatar">
							<img :src="integrante.imagem" alt="">
						</div>
						<div class="employee-description">
							<h3 class="name">{{integrante.nome}}</h3>
							<h4 class="function">{{integrante.cargo}}</h4>
						</div>
				</v-flex>
			</v-layout>

		</v-container>
	</div>
</template>

<script>
	export default {

		data () {
			return {
				setores: [
					{ nome: "Sistemas", integrantes: [
						{nome: "Rômulo Nunes de Oliveira", imagem: require("../images/romulo.png"), cargo: "Coordenador"},
						{nome: "Italo Carlo Lopes Silva", imagem: require("../images/italo.png"), cargo: "Analista"},
						{nome: "Marcos José Ferreira Neto", imagem: require("../images/marcos.png"), cargo: "Técnico"},
					]},
					{ nome: "Redes", integrantes: [
						{nome: "Deive Fabian Valeriano Gomes", imagem: require("../images/deive.png"), cargo: "Analista"},
						{nome: "Carlisson Borges Tenorio Galdino", imagem: require("../images/carlisson.png"), cargo: "Analista"},
						{nome: "William Nunes Avila", imagem: require("../images/william.png"), cargo: "Analista"},
					]},
					{ nome: "Manutenção", integrantes: [
						{nome: "Marcelo Almeida Santana", imagem: require("../images/marcelo.png"), cargo: "Analista"},
						{nome: "Wellington Batalha Santos", imagem: require("../images/welington.png"), cargo: "Técnico"},
					]}
				]
			}
		},
	}
</script>
