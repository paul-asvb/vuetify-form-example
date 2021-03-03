<template>
  <v-app>
    <v-app-bar app>
      <a href="https://github.com/paul-asvb/vuetify-form-example">go to code</a>
      <v-spacer />
      <v-checkbox v-model="$vuetify.theme.dark" label="Toggle DARK theme" hide-details />
      <v-spacer />
    </v-app-bar>

    <v-main>
      <v-form ref="frm" v-model="valid" class="pa-4">
        <v-jsf v-model="model" :schema="schema"/>
      </v-form>
      <div class="d-flex justify-center">
        <v-btn color="primary" @click="checkValidity">Validate</v-btn>
      </div>
    </v-main>
  </v-app>
</template>

<script>
import VJsf from '@koumoul/vjsf/lib/VJsf.js'
import '@koumoul/vjsf/lib/VJsf.css'
import '@koumoul/vjsf/lib/deps/third-party.js'

export default {
  name: 'App',
  components: { VJsf },
  data: () => ({
    valid: false,
    model:
      {
        comboBox: ['value-1', 'value-4'],
        chipGroup: ['value-1', 'value-4'],
      },
    schema: {
      type: 'object',
      properties: {
        comboBox:
          {
            type: 'array',
            title: 'Autocomplete combo-box',
            minItems: 1,
            items:
              {
                type: 'string',
                oneOf:
                  [
                    {
                      const: 'value-1',
                      title: 'item-1',
                    },
                    {
                      const: 'value-2',
                      title: 'item-2',
                    },
                    {
                      const: 'value-3',
                      title: 'item-3',
                    },
                    {
                      const: 'value-4',
                      title: 'item-4',
                    },
                  ]
              },
            description: 'This comboBox supports autocomplete',
            'x-display': 'autocomplete',
            'x-style': 'background:grey;',
            'x-class': 'px-4 pt-4',
            'x-props':
              {
                itemText: 'title',
                chips: true,
                deletableChips: true,
                smallChips: true,
                menuProps:
                  {
                    auto: true,
                    offsetY: true,
                    closeOnContentClick: true,
                  },
                solo: true,
                flat: true,
                clearable: true,
              },
          },
        chipGroup:
          {
            type: 'array',
            title: 'ChipGroup',
            items:
              {
                type: 'string',
                oneOf:
                  [
                    {
                      const: 'value-1',
                      title: 'item-1',
                    },
                    {
                      const: 'value-2',
                      title: 'item-2',
                    },
                    {
                      const: 'value-3',
                      title: 'item-3',
                    },
                    {
                      const: 'value-4',
                      title: 'item-4',
                    },
                  ]
              },
            'x-display': 'chip-group',
            'x-style': 'background:lightblue;',
            'x-class': 'pa-4',
            'x-props':
              {
                activeClass: 'primary',
              },
            'x-options':
              {
                chipItemProps:
                  {
                    filter: true,
                    // close: true,
                  }
              }
          },
      }
    }
  }),
  methods:
    {
      checkValidity()
      {
        this.$refs.frm.validate();
      }
    }
};
</script>

<style>
  .v-menu
  {
    display: block !important; /* for unknown reason on my PC .v-menu is defined as "display: none" */
  }
</style>
