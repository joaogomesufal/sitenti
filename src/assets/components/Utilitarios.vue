<template>
	<div id="utilitarios" class="section">
		{{ data}}
		<v-container grid-list-md>
			<v-layout row wrap>
				<v-flex md12 class="section-title">
					<h3>Utilitários</h3>
					<p>Ferramentas úteis.</p>
				</v-flex>
			</v-layout>
			
			<v-layout row wrap>
				<v-flex xs12 sm4 md3 v-for="utility in utilities" v-bind:key="utility.title">
					<v-card class="utility">
						<v-card-title class="light-blue darken-4 white--text">
							<v-icon dark left>{{utility.icon }}</v-icon> &nbsp; {{ utility.title }}
						</v-card-title>
						<v-card-text>
							<p>{{ utility.description }}</p>
						</v-card-text>

						<v-card-actions>
							<v-btn block :href="utility.link" target="_blank" color="blue-grey darken-4" dark>
								Acessar
								<v-icon right >navigate_next</v-icon>
							</v-btn>
						</v-card-actions>
					</v-card>
				</v-flex>
			</v-layout>
			<v-layout>
				<v-flex md12 class="section-title">
					<h4>Ferramentas de uso interno</h4>
				</v-flex>
			</v-layout>
			<v-layout row wrap>
				<v-flex xs6 md4 v-for="utility in utilities_links" v-bind:key="utility.title">
					<v-btn block :href="utility.link" target="_blank" color="blue-grey darken-4" dark>
						<v-icon left >{{utility.icon}}</v-icon>
						{{ utility.title }}
					</v-btn>
				</v-flex>
			</v-layout>

		</v-container>
	</div>
</template>

<script>
	import data_utilities from '../data/utilities.js'
	const {utilities, utilities_links} = data_utilities
	export default {
		data () {
			return {
				utilities,
				utilities_links,
			}
		},

		methods: {
			onScroll (e) {
				this.offsetTop = e.target.scrollTo
			}
		}
	}
</script>
