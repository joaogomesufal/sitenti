<template>
  <div id="catalogo-servicos" class="section">
    <v-container>
      <v-layout row>
        <v-flex md12 class="section-title">
          <h3>Catálogo de Serviços</h3>
          <p>Pesquise e solicite os serviços disponibilizados pelo NTI.</p>
        </v-flex>
      </v-layout>

      <v-layout row  mb-1>
        <v-flex md12>
          <v-card color="blue darken-3" dark>
            <v-layout row wrap>
            <v-flex xs12 md6>
                <v-card-title>Pesquisa</v-card-title>
                <v-card-text>
                  <v-text-field
                  box
                    label="Pesquisar serviço ..."
                    append-icon="search"
                    v-model="search"
                  >
                  </v-text-field >
                    </v-card-text>
            </v-flex>

            <v-flex md6>
                <v-card-title>Filtros</v-card-title>
                <v-card-text>
                  <v-layout row wrap> 
                    <v-flex md4 xs12>
                      <v-switch hide-details label="Manutenção" v-model="services.networks.status" color="light-blue lighten-2"></v-switch>
                    </v-flex>
                    <v-flex md4 xs12>
                      <v-switch hide-details label="Redes" v-model="services.maintenance.status" color="light-blue lighten-2"></v-switch>
                    </v-flex>
                    <v-flex md4 xs12>
                      <v-switch hide-details label="Sistemas" v-model="services.systems.status" color="light-blue lighten-2"></v-switch>
                    </v-flex>
                  </v-layout>
                </v-card-text>
            </v-flex>
            </v-layout>
          </v-card>
        </v-flex>
      </v-layout>

      <v-layout row wrap>
        <v-flex md12 mb-1 v-show="services.networks.status">
          <v-card>
            <v-card-title>
              <h3>{{ services.networks.name }}</h3>
            </v-card-title>
          <v-card-text>
            <v-expansion-panel>
              <v-expansion-panel-content v-for="service in filteredNetworkServices" v-bind:key="service.name">
                <div slot="header">
                  <p>
                    {{ service.name | uppercase}}
                  </p>
                </div>
                <v-card flat color="blue-grey darken-4">
                    <v-card-text>
                      <v-layout row wrap>
                        <v-flex x12 md8>
                          <v-card color="blue-grey darken-4" class="white--text">
                            <v-card-title>
                              <v-icon left color="white">description</v-icon> &nbsp; Descrição 
                            </v-card-title>
                            <v-card-text>
                              {{ service.description }}
                            </v-card-text>
                          </v-card>
                          <v-card color="blue-grey darken-4" class="white--text" v-show="service.quick_help">
                            <v-card-title>
                              <v-icon left color="white">live_help</v-icon> &nbsp; Ajuda Rápida
                            </v-card-title>
                            <v-card-text>
                              {{ service.quick_help }}
                            </v-card-text>
                          </v-card>
                        </v-flex>

                        <v-flex x12 md4>
                          <v-card color="blue-grey darken-3" class="white--text">
                            <v-card-title>
                              <v-icon left color="white">people</v-icon> &nbsp; Públic Alvo
                            </v-card-title>
                            <v-card-text>
                              {{ service.target_public }}
                            </v-card-text>
                          </v-card>

                          <v-card color="blue-grey darken-3" class="white--text" v-show="service.requirements"> 
                            <v-card-title>
                              <v-icon left color="white">list</v-icon> &nbsp; Requisitos
                            </v-card-title>
                            <v-card-text>
                              {{ service.requirements }}
                            </v-card-text>
                          </v-card>
                        </v-flex>
                      </v-layout> 
                    </v-card-text>
                </v-card>
              </v-expansion-panel-content>
          </v-expansion-panel>
          </v-card-text>
           </v-card>
        </v-flex>

        <v-flex md12 mb-1 v-show="services.maintenance.status">
          <v-card>
            <v-card-title>
              <h3>{{ services.maintenance.name }}</h3>
            </v-card-title>
          <v-card-text>
            <v-expansion-panel>
              <v-expansion-panel-content v-for="service in filteredMaintenanceServices" v-bind:key="service.name">
                <div slot="header">
                  <p>
                    {{ service.name | uppercase }}
                  </p>
                </div>
                <v-card color="blue-grey darken-4">
                    <v-card-text>
                     <v-layout row wrap>
                        <v-flex x12 md8>
                          <v-card color="blue-grey darken-4" class="white--text">
                            <v-card-title>
                              <v-icon left color="white">description</v-icon> &nbsp; Descrição 
                            </v-card-title>
                            <v-card-text>
                              {{ service.description }}
                            </v-card-text>
                          </v-card>
                          <v-card color="blue-grey darken-4" class="white--text" v-show="service.quick_help">
                            <v-card-title>
                              <v-icon left color="white">live_help</v-icon> &nbsp; Ajuda Rápida
                            </v-card-title>
                            <v-card-text>
                              {{ service.quick_help }}
                            </v-card-text>
                          </v-card>
                        </v-flex>

                        <v-flex xs12 md4>
                          <v-card color="blue-grey darken-3" class="white--text">
                            <v-card-title>
                              <v-icon left color="white">people</v-icon> &nbsp; Públic Alvo
                            </v-card-title>
                            <v-card-text>
                              {{ service.target_public }}
                            </v-card-text>
                          </v-card>

                          <v-card color="blue-grey darken-3" class="white--text" v-show="service.requirements"> 
                            <v-card-title>
                              <v-icon left color="white">list</v-icon> &nbsp; Requisitos
                            </v-card-title>
                            <v-card-text>
                              {{ service.requirements }}
                            </v-card-text>
                          </v-card>
                        </v-flex>
                      </v-layout> 
                    </v-card-text>
                </v-card>
              </v-expansion-panel-content>
          </v-expansion-panel>
          </v-card-text>
           </v-card>
        </v-flex>

        <v-flex md12 mb-1 v-show="services.systems.status">
          <v-card>
            <v-card-title>
              <h3>{{ services.systems.name }}</h3>
            </v-card-title>
          <v-card-text>
            <v-expansion-panel>
              <v-expansion-panel-content v-for="service in filteredSystemsServices" v-bind:key="service.name">
                <div slot="header">
                  <p>
                    {{ service.name | uppercase}}
                  </p>
                </div>
                <v-card color="blue-grey darken-4">
                    <v-card-text>
                      <v-layout row wrap>
                        <v-flex x12 md8>
                          <v-card color="blue-grey darken-4" class="white--text">
                            <v-card-title>
                              <v-icon left color="white">description</v-icon> &nbsp; Descrição 
                            </v-card-title>
                            <v-card-text>
                              {{ service.description }}
                            </v-card-text>
                          </v-card>
                          <v-card color="blue-grey darken-4" class="white--text" v-show="service.quick_help">
                            <v-card-title>
                              <v-icon left color="white">live_help</v-icon> &nbsp; Ajuda Rápida
                            </v-card-title>
                            <v-card-text>
                              {{ service.quick_help }}
                            </v-card-text>
                          </v-card>
                        </v-flex>

                        <v-flex md4>
                          <v-card color="blue-grey darken-3" class="white--text">
                            <v-card-title>
                              <v-icon left color="white">people</v-icon> &nbsp; Públic Alvo
                            </v-card-title>
                            <v-card-text>
                              {{ service.target_public }}
                            </v-card-text>
                          </v-card>

                          <v-card color="blue-grey darken-3" class="white--text" v-show="service.requirements"> 
                            <v-card-title>
                              <v-icon left color="white">list</v-icon> &nbsp; Requisitos
                            </v-card-title>
                            <v-card-text>
                              {{ service.requirements }}
                            </v-card-text>
                          </v-card>
                        </v-flex>
                      </v-layout> 
                    </v-card-text>
                </v-card>
              </v-expansion-panel-content>
          </v-expansion-panel>
          </v-card-text>
           </v-card>
        </v-flex>
      </v-layout>

  </v-container>
</div>
</template>

<script>
export default {
  data() {
    return {
      search: '',
      windowWidth: 0,
      services: 
      {
        networks: {
          status: true,
          name: "Redes",
          data: 
          [
            {
                name: 'ACESSO À INTERNET SEM FIO',
                description: 'Dentro do espaço físico do Campus Arapiraca, é fornecido acesso a Internet sem fio por meio das redes ArapiracaUfal, UfalMovel, OutC, OutD, Ufal5G',
                target_public: 'Comunidade Acadêmica e visitantes',
                requirements: 'Dispositivo computacional que permita acesso a rede sem fio. Smartphone, tablet, notebook ou outro',
                quick_help: 'Senha de acesso ufalsong'
            },
            {
                name: 'RAMAL INSTITUCIONAL PELO CELULAR',
                description: 'Permite ao smartphone realizar ligações para outros ramais da Ufal e também receber ligações.',
                target_public: 'Servidores',
                requirements: 'Preenchimento de formulário de solicitação e possuir um smartphone que ofereça supoerte ao aplicativo.',
                quick_help: ''
            },
            {
                name: 'ACESSO REMOTO A MÁQUINA INTERNA',
                description: 'Acesso externo a máquina localizada dentro do Campus Arapiraca',
                target_public: 'Servidores e alunos autorizados por servidores',
                requirements: 'Equipamento com IP fixo em conformidade com políticas internas de Redes; serviço VNC, RDP ou SSH devidamente configurado; solicitação e criação de usuário para esta finalidade no setor de Redes ',
                quick_help: ''
            },
            {
                name: 'DISPONIBILIZAÇÃO DE SERVIÇO WEB',
                description: 'Disponibilização de serviço web interno ao Campus Arapiraca na internet.',
                target_public: 'Servidores',
                requirements: ' Equipamento com serviço HTTP devidamente configurado; sistema respondendo a partir de um subdiretório (por exemplo my.ara/sistema e não my.ara/); solicitação no setor de Redes ',
                quick_help: ''
            },
            {
                name: 'PÁGINA DE WIKI',
                description: 'Página para divulgação de conteúdo sob gestão do solicitante.',
                target_public: 'Servidores',
                requirements: 'Solicitação não conflitante com o conjunto de informações públicas oficialmente nas páginas da Ufal mantidas pela Ascom; solicitação no setor de Redes.',
                quick_help: ''
            },
            {
                name: 'BIBLIOTECA DE DISTRIBUIÇÕES GNU/LINUX',
                description: 'Coletânea de imagens de CD e DVD de instalação de Sistemas Operacionais cuja licença permita redistribuição.',
                target_public: 'Comunidade Acadêmica',
                requirements: 'Acesso a central.arapiraca.ufal.br/cdteca',
                quick_help: ''
            },
            {
                name: 'AGENDA TELEFÔNICA',
                description: 'Agenda com todos os ramais físicos do Campus Arapiraca (e polos) e do Campus do Sertão (e polo).',
                target_public: 'Sociedade',
                requirements: 'Acesso a sistemas.arapiraca.ufal.br/telefones',
                quick_help: ''
            },
            {
                name: 'MONITORAMENTO DE TRÁFEGO WEB',
                description: 'Visualização da estrutura de rede física do Campus Arapiraca e o status dos equipamentos.',
                target_public: 'Comunidade Acadêmica',
                requirements: 'Acesso a central.arapiraca.ufal.br/ e seleção da opção "Tráfego"',
                quick_help: ''
            },
            {
                name: 'SERVIDOR DE ARQUIVOS',
                description: 'Serviço que permite acesso e compartilhamento de arquivos',
                target_public: 'Servidores',
                requirements: 'Solicitação no setor de Redes. Para acessar o usuário deve estar na rede do Campus Arapiraca - Sede.',
                quick_help: ''
            },
            {
                name: 'ARQUIVOS EM NUVEM',
                description: 'Servidor de arquivos acessível via interface web ou via sincronização automática, com serviços associados, como calendário, agenda de contatos e compartilhamento de arquivos.',
                target_public: 'Servidores',
                requirements: 'Solicitação no setor de Redes; acesso a central.arapiraca.ufal.br/drive',
                quick_help: ''
            },
            {
                name: 'BLOG',
                description: 'Serviço de blog acessível via Internet',
                target_public: 'Servidores',
                requirements: 'Solicitação não conflitante com o conjunto de informações públicas oficialmente nas páginas da Ufal mantidas pela Ascom; solicitação no setor de Redes',
                quick_help: ''
            },
            {
                name: 'CONFERÊNCIA EM AUDIO',
                description: 'erviço de conversação em grupo com recurso de gravação da conversa pelos próprios participantes',
                target_public: 'Comunidade Acadêmica',
                requirements: 'Todos os participantes devem ter o cliente Mumble instalado.',
                quick_help: 'Instalar cliente Mumble; acessar via cliente Mumble a central.arapiraca.ufal.br, na porta 64738  '
            },
            {
                name: 'MÁQUINA VIRTUAL',
                description: 'Disponibilização de uma máquina para auxiliar em atividade técnica ou acadêmica',
                target_public: 'Servidores',
                requirements: 'Solicitar no setor de Redes.',
                quick_help: ''
            }
          ]
        },

        maintenance: {
          status: true,
          name: "Manutenção",
          data: [
            {
                name: "Instalação ou substituição Computador",
                description: "Será instalado ou substituido o computador no setor desejado",
                target_public: "Dicentes e Técnicos	",
                requirements: "Saber se tem computador disponível para a instalação/substituição",
                quick_help: "Para verificar se tem computadores disponiveis entrar em contato com o ramal: 1828",
            },
            {
                name: "Instalação / atualização dos aplicativos do computador",
                description: "Serão instalados ou atualizados os aplicativos do computador",
                target_public: "Técnicos e Dicentes	",
                requirements: "O aplicativo ter licença de uso	",
                quick_help: "",
            },
            {
                name: "Instalação / atualização dos aplicativos no Laboratório",
                description: "Serão instalados ou atualizados os aplicativos em todos os computadores do laboratório especificado",
                target_public: "Técnicos e Dicentes	",
                requirements: "O aplicativo ter licença de uso e especificar o laboratório",
                quick_help: "",
            },
            {
                name: "Criação / Alteração dos usuários locais do computador",
                description: "Serão criados ou alterados os usuários locais do computador",
                target_public: "Técnicos e Dicentes	",
                requirements: "",
                quick_help: "",
            },
            {
                name: "Testar Equipamento	",
                description: "Será realizado o diagnóstico e avaliação do equipamento solicitado",
                target_public: "Técnicos e Dicentes	",
                requirements: "O equipamento pertercer a UFAL - Campus Arapiraca			",
                quick_help: "",
            },
            {
                name: "Formatar o Computador	",
                description: "Serão apagados todos os dados do computador e instalado o sistema operacioal de acordo com a licença permitida						",
                target_public: "Técnicos e Dicentes	",
                requirements: "Ter realizado o backup dos dados	",
                quick_help: "",
            },
          ],
        },
        systems: {
          status: true,
          name: "Sistemas",
          data: [
            {
                name: "ALTERAÇÃO DE E-MAIL",
                description: "Consiste na susbstituição do e-mail cadastrado no sistema da UFAL",
                target_public: "Discentes e Servidores",
                requirements: "Apresentar um documento oficial de identificação com foto e informar o e-mail desejado",
                quick_help: `Caso tenha acesso ao sistema Perfil, realize o login no sistema https://sistemas.ufal.br/perfil/ utilizando a sua senha, clique no link "Alterar e-mail secundário". Na tela que aparecer, digite o e-mail desejado.													
                Caso não lembre da senha, na tela de login do sistema Perfil, clique no link "Esqueceu a senha?". Na tela que aparecer, digite o seu CPF e clique no botão "Recuperar Senha" para que um link de recuperação se senha seja enviado para seu e-mail secundário.													
                Caso não tenha acesso ao e-mail cadastrado no sistema e também não consiga acessar o sistema Perfil, procure o CRCA ou a secretaria da sua unidade e solicite a alteração do e-mail secundário.`,
            },
            {
                name: "MANUTENÇÃO DOS SISTEMAS INSTITUCIONAIS",
                description: "Consiste na atualização e correções dos principais sistemas utilizados pela instituição: SIGAA, SIGRH, SIPAC, SIGADMIN, SIWEB, SICAM, PERGAMUM, PERFIL, etc. ",
                target_public: "Discentes e Servidores",
                requirements: "Enviar pelo e-mail institucional a descrição detalhada do problema com os prints da tela para ajudar na correção",
                quick_help: "",
            },
            {
                name: "AJUSTE DE CONTEÚDO NO SITE",
                description: "Consiste na atualização ou correção de informações",
                target_public: "Servidores",
                requirements: "O responsável por determinada área no site deve enviar o conteúdo (texto, imagens, arquivos, links) conforme deve ser colocado no site utilizando seu e-mail institucional",
                quick_help: "",
            },
            {
                name: "CADASTRO DE USUÁRIO NO SITE",
                description: "Consiste na criação de um usuário para gerenciar determinda área do site",
                target_public: "Servidores",
                requirements: "Solicitação do responsável pelo setor utilizando seu e-mail institucional para informar os dados do novo usuário",
                quick_help: "",
            },
            {
                name: "NOVAS ÁREAS NO SITE",
                description: "Consiste na inclusão de conteúdo",
                target_public: "Servidores",
                requirements: "Envio do conteúdo que deve ser colocado no site pelo responsável do setor na instituição ou da área no site utilizando o seu e-mail institucional.",
                quick_help: "",
            },
            {
                name: "TREINAMENTO DE USUÁRIOS",
                description: "Consiste na orientação sobre o uso dos sistemas e na disponibilização de minicursos",
                target_public: "Discentes e Servidores",
                requirements: "Solicitação através do email institucional (servidores) e inscrição nos minicursos disponibilizados (Discentes e Servidores) ",
            }
          ],
        }
      }
    }
  },

  computed: {
    filteredNetworkServices () {
      return this.services.networks.data.filter((service) => {
        return service.name.toLowerCase().match(this.search.toLowerCase()) 
      })
    },
    filteredMaintenanceServices () {
      return this.services.maintenance.data.filter((service) => {
        return service.name.toLowerCase().match(this.search.toLowerCase())
      })
    },
    filteredSystemsServices () {
      return this.services.systems.data.filter((service) => {
        return service.name.toLowerCase().match(this.search.toLowerCase()) 
      })
    }
  },

  created() {
    this.$nextTick(() => {
      window.addEventListener('resize', () => {
        this.windowWidth = window.innerWidth
      });
    })
  },

  filters: {
    uppercase(text) {
      return text.toUpperCase()
    },

    limite(text) {
      if(text.length > 30)
        return text.substring(0,30) + '...'
      else 
        return text.substring(0,30)
    }
  }
}
</script>

<style scoped>

</style>
