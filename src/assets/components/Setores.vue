<template>

	<div id="setores" class="section">
		<v-container grid-list-md>
			<v-layout row wrap>
				<v-flex xs12 class="section-title">
					<h3>Setores</h3>
					<p>Divisões do Núcleo de Tecnologia e suas funções:</p>
				</v-flex>
			</v-layout>

			<v-layout row wrap>
				<v-flex xs12 sm4 md4>
					<v-card class="setor manutencao" dark>
						<v-card-title>
							<h3>Manutenção</h3>	
						</v-card-title>
						<v-card-text>
							<p>Realiza manutenções de equipamentos de informática, realizar manutenção preventiva, instalação de antivírus e suporte técnico.</p>
						</v-card-text>
					</v-card>
				</v-flex>

				<v-flex xs12 sm4 md4>
					<v-card class="setor sistemas" dark>
						<v-card-title>
							<h3>Sistemas</h3>	
						</v-card-title>
						<v-card-text>
							<p>Setor responsável pelo desenvolvimento e manutenção web e de softwares relevantes para a comunidade acadêmica da UFAL.</p>
						</v-card-text>
					</v-card>
				</v-flex>

				<v-flex xs12 sm4 md4>
					<v-card class="setor redes" dark>
						<v-card-title>
							<h3>Redes</h3>	
						</v-card-title>
						<v-card-text>
							<p>Responde pelo planejamento, configuração, reparos e administração dos equipamentos ativos, serviços e servidores nas diversas redes internas do Campus.</p>
						</v-card-text>
					</v-card>
				</v-flex>
			</v-layout>

		</v-container>
	</div>
</template>

<script>
	export default {

		data () {
			return {

			}
		}
	}
</script>
