<template>
  <v-app id="template" color="primary" light app>
    <v-navigation-drawer v-model="drawer" app clipped color="primary">
      <v-container>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title white--text text--lighten-2">
              Navigation lists
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-divider />
        <v-list nav dense>
          <v-list-group
            v-for="nav_list in nav_lists"
            :key="nav_list.name"
            :prepend-icon="nav_list.icon"
            no-action
            :append-icon="nav_list.lists ? undefined : ''"
          >
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title>{{ nav_list.name }}</v-list-item-title>
              </v-list-item-content>
            </template>
            <v-list-item v-for="list in nav_list.lists" :key="list">
              <v-list-item-content>
                <v-list-item-title>{{ list }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </v-list>
      </v-container>
    </v-navigation-drawer>
    <v-app-bar
      absolute
      color="primary"
      dark
      shrink-on-scroll
      src="https://picsum.photos/1920/1080?random"
      scroll-target="#scrolling-techniques-2"
    >
      <v-app-bar-nav-icon @click="drawer=!drawer" />
      <v-toolbar-title>
        Vuetify
        <!-- <v-spacer></v-spacer> -->
        <!-- <v-toolbar-items> -->
        <!-- <v-btn text>Button</v-btn> -->
        <!-- </v-toolbar-items> -->
        <v-btn outlined x-large>
          Button1
        </v-btn>
        <v-btn outlined x-large>
          Button2
        </v-btn>
        <!-- <v-spacer></v-spacer> -->
        <!-- <v-toolbar-items class="d-flex align-center mb-6"> -->
        <v-btn outlined x-large>
          Button3
        </v-btn>
        <v-menu offset-y>
          <template v-slot:activator="{on}">
            <v-btn outlined x-large v-on="on">
              Button4
              <v-icon>
                mdi-menu-down
              </v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>
                  Button4-1
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>
                  Button4-2
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-menu>
        <v-menu offset-y>
          <template v-slot:activator="{on}">
            <v-btn outlined x-large v-on="on">
              Button5
              <v-icon>
                mdi-menu-down
              </v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-subheader>
              Get help
            </v-subheader>
            <v-list-item v-for="support in supports" :key="support.name" :to="support.link_to" :href="support.link_href">
              <!-- <v-list-item v-for="support in supports" :key="support.name"> -->
              <!-- <template v-if="isInternalLink(support.link)">
                <nuxt-link :to="support.link">{{ link.name }}</nuxt-link>
              </template>
              <template v-else>
                <a :href="support.link">{{ support.name }}</a>
              </template> -->
              <v-list-item-icon>
                <v-icon>{{ support.icon }}</v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title>{{ support.name }}</v-list-item-title>
              </v-list-item-content>
            </v-list-item>
            <!-- <v-list-item v-for="support in supports" :key="support">
            <v-list-item-content>
              <v-list-item-title>{{ support }}</v-list-item-title>
            </v-list-item-content>
            </v-list-item> -->
          </v-list>
        </v-menu>
        <!-- </v-toolbar-items> -->
      </v-toolbar-title>
    </v-app-bar>
    <div>
      <img
        src="/v.png"
        alt="Vuetify.js"
        class="mb-5"
      >
      <blockquote class="blockquote">
        &#8220;First, solve the problem. Then, write the code.&#8221;
        <footer>
          <small>
            <em>&mdash;John Johnson</em>
          </small>
        </footer>
      </blockquote>
      <v-card-actions>
        <v-btn
          color="primary"
          nuxt
          to="/"
        >
          Home page
        </v-btn>
      </v-card-actions>
    </div>
    <v-footer color="primary" dark app>
      Vuetify
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: null,
      // supports: [
      //   'Consulting and suppourt',
      //   'Discord community',
      //   'Report a bug',
      //   'Github issue board',
      //   'Stack overview'
      // ]
      supports: [
        {
          name: 'Home',
          icon: 'mdi-github',
          link_to: '/',
          link_href: ''
        },
        {
          name: 'Reference2',
          icon: 'mdi-github',
          link_to: '',
          link_href: 'https://vuejs.org'
        },
        {
          name: 'Reference3',
          icon: 'mdi-github',
          link_to: '',
          link_href: 'https://vuetifyjs.com/en/'
        },
        {
          name: 'Reference4',
          icon: 'mdi-github',
          link_to: '',
          link_href: 'https://nuxtjs.org'
        },
        {
          name: 'Reference4',
          icon: 'mdi-github',
          link_to: '',
          link_href: 'https://reffect.co.jp/vue/vuetify-for-beginner'
        },
        {
          name: 'Consulting and suppourt',
          icon: 'mdi-vuetify',
          link_to: '/',
          link_href: ''
        },
        {
          name: 'Discord community',
          icon: 'mdi-discord',
          link_to: '/',
          link_href: ''
        },
        {
          name: 'Report a bug',
          icon: 'mdi-bug',
          link_to: '/',
          link_href: ''
        },
        {
          name: 'Github issue board',
          icon: 'mdi-github',
          link_to: '/',
          link_href: ''
        },
        {
          name: 'Stack overview',
          icon: 'mdi-stack-overflow',
          link_to: '/',
          link_href: ''
        }
      ],
      // supports: [
      //   { name: 'Consulting and suppourt', icon: 'mdi-vuetify' },
      //   { name: 'Discord community', icon: 'mdi-discord' },
      //   { name: 'Report a bug', icon: 'mdi-bug' },
      //   { name: 'Github issue board', icon: 'mdi-github' },
      //   { name: 'Stack overview', icon: 'mdi-stack-overflow' }
      // ],
      nav_lists: [
        {
          name: 'Getting Started',
          icon: 'mdi-speedometer',
          lists: ['Quick Start', 'Pre-made layouts']
        },
        {
          name: 'Customization',
          icon: 'mdi-cogs'
        },
        {
          name: 'Styles & animations',
          icon: 'mdi-palette',
          lists: ['Colors', 'Content', 'Display']
        },
        {
          name: 'UI Components',
          icon: 'mdi-view-dashboard',
          lists: ['API explorer', 'Alerts']
        },
        {
          name: 'Directives',
          icon: 'mdi-function'
        },
        {
          name: 'Preminum themes',
          icon: 'mdi-vuetify'
        }
      ]
    }
  }
}
</script>
