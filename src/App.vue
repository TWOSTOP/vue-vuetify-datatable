<template>
  <v-app id="inspire">
   
    <v-toolbar
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      color="blue darken-3"
      dark
      app
      fixed
    >
      <v-toolbar-title style="width: 300px" class="ml-0 pl-3">
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
        <span class="hidden-sm-and-down">Cloud 서버 스펙</span>
      </v-toolbar-title>
      <v-text-field
        flat
        solo-inverted
        prepend-icon="search"
        label="Search"
        class="hidden-sm-and-down"
      ></v-text-field>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>apps</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>notifications</v-icon>
      </v-btn>
      <v-btn icon large>
        <v-avatar size="32px" tile>
          <img
            src="https://vuetifyjs.com/static/doc-images/logo.svg"
            alt="Vuetify"
          >
        </v-avatar>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container fluid fill-height>
        <v-layout >
        <v-flex xs5>
        <h2>원래데이터</h2>
        <v-data-table
    :headers="headers"
    :items="desserts"
    hide-actions
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.SERVER_NM }}</td>
      <td class="text-xs-right">{{ props.item.CORE_CNT }}</td>
      <td class="text-xs-right">{{ props.item.MEM_SIZE }}</td>
      <td class="text-xs-right">{{ props.item.DISK_VOLUME }}</td>
      <td class="text-xs-right">{{ props.item.OS_TYPE }}</td>
      <td class="text-xs-right">{{ props.item.DB_TYPE }}</td>
      <td class="text-xs-right">{{ props.item.WEB_SERV_TYPE }}</td>
    </template>
  </v-data-table>
      </v-flex>
      <v-flex xs6 offset-xs1>
      <h2>시점 정보가 있는 데이터</h2>
        <v-data-table
    :headers="specHistsHeaders"
    :items="specHists"
    hide-actions
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
    <td>{{ props.item.ROW_START }}</td>
    <td>{{ props.item.ROW_END }}</td>
      <td>{{ props.item.SERVER_NM }}</td>
      <td class="text-xs-right">{{ props.item.CORE_CNT }}</td>
      <td class="text-xs-right">{{ props.item.MEM_SIZE }}</td>
      <td class="text-xs-right">{{ props.item.DISK_VOLUME }}</td>
      <td class="text-xs-right">{{ props.item.OS_TYPE }}</td>
      <td class="text-xs-right">{{ props.item.DB_TYPE }}</td>
      <td class="text-xs-right">{{ props.item.WEB_SERV_TYPE }}</td>
    </template>
  </v-data-table>
      </v-flex>
        
        </v-layout>
      </v-container>
    </v-content>
    <v-btn
      fab
      bottom
      right
      color="pink"
      dark
      fixed
      @click.stop="dialog = !dialog"
    >
      <v-icon>add</v-icon>
    </v-btn>
    
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      dialog: false,
      drawer: null,
      items: [
        { icon: 'contacts', text: 'Contacts' },
        { icon: 'history', text: 'Frequently contacted' },
        { icon: 'content_copy', text: 'Duplicates' },
        {
          icon: 'keyboard_arrow_up',
          'icon-alt': 'keyboard_arrow_down',
          text: 'Labels',
          model: true,
          children: [
            { icon: 'add', text: 'Create label1111' }
          ]
        },
        {
          icon: 'keyboard_arrow_up',
          'icon-alt': 'keyboard_arrow_down',
          text: 'More',
          model: false,
          children: [
            { text: 'Import', children: [ { text: 'level2' }, { text: 't2' } ] },
            { text: 'Export' },
            { text: 'Print' },
            { text: 'Undo changes' },
            { text: 'Other contacts' }
          ]
        },
        { icon: 'settings', text: 'Settings' },
        { icon: 'chat_bubble', text: 'Send feedback' },
        { icon: 'help', text: 'Help' },
        { icon: 'phonelink', text: 'App downloads' },
        { icon: 'keyboard', text: 'Go to the old version' }
      ],
      headers: [
        {
          text: '서버명',
          align: 'left',
          sortable: false,
          value: 'SERVER_NM'
        },
        { text: 'CPU CORE 수', value: 'CORE_CNT' },
        { text: 'MEMORY 크기', value: 'MEM_SIZE' },
        { text: '디스크 용량', value: 'DISK_VOLUME' },
        { text: 'OS', value: 'OS_TYPE' },
        { text: 'DB', value: 'DB_TYPE' },
        { text: 'WEB SERVER', value: 'WEB_SERV_TYPE' }
      ],
      specHistsHeaders: [
        {
          text: '시작일',
          align: 'left',
          sortable: false,
          value: 'ROW_START'
        },
        {
          text: '종료일',
          align: 'left',
          sortable: false,
          value: 'ROW_END'
        },
        {
          text: '서버명',
          align: 'left',
          value: 'SERVER_NM'
        },
        { text: 'CPU CORE 수', value: 'CORE_CNT' },
        { text: 'MEMORY 크기', value: 'MEM_SIZE' },
        { text: '디스크 용량', value: 'DISK_VOLUME' },
        { text: 'OS', value: 'OS_TYPE' },
        { text: 'DB', value: 'DB_TYPE' },
        { text: 'WEB SERVER', value: 'WEB_SERV_TYPE' }
      ],
      desserts: [
        {
          value: false,
          name: 'CC-GDB-01',
          CORE_CNT: 2,
          MEM_SIZE: 4096,
          DISK_VOLUME: 50,
          OS_TYPE: 'CentOS 7.4',
          DB_TYPE: 'MariaDB 10.2',
          WEB_SERV_TYPE: 'Nginx'
        },
        {
          value: false,
          name: 'CC-Admin',
          CORE_CNT: 4,
          MEM_SIZE: 8192,
          DISK_VOLUME: 500,
          OS_TYPE: 'Windows Server 2012',
          DB_TYPE: 'MSSQL',
          WEB_SERV_TYPE: 'IIS'
        }
      ],
      specHists: []
    }),
    created: function () {
      console.log('created')
      this.axios.get('http://localhost:3000/specs').then((response) => {
        console.log('response.data:', response.data)
        this.desserts = response.data
      })
      this.axios.get('http://localhost:3000/specs/history').then((response) => {
        console.log('[history]response.data:', response.data)
        this.specHists = response.data
      })
    },
    props: {
      source: String
    }
  }
</script>