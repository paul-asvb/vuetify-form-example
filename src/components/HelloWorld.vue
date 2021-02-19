<template>
  <v-col class="roi-observation bg-color-dark-black-light">
    <p class="color-white-light" style="margin-bottom:0px;">
      chip group
    </p>
    <v-chip-group :value="chipGroupItems" active-class="primary" column>
      <v-chip
        v-for="tag in chipGroupItems"
        :key="tag.text"
        color="black"
        small
        auto-select-first="true"
        :value="tag.text"
        @click="chipGroupItems = tag.text"
      >
        <span>{{ tag.text }}</span>
      </v-chip>
    </v-chip-group>

    <p class="color-white-light" style="margin-bottom:0px;">
      combobox
    </p>
    <v-combobox
      v-model="comboBoxModel"
      hide-details
      :items="comboBoxItem"
      multiple
      :hide-selected="true"
      allow-overflow
      :menu-props="{ closeOnContentClick: true }"
      chips
      solo
      flat
      full-width
      background-color="grey"
      color="black"
      item-color="black"
    >
      <template #selection="data">
        <v-chip
          :key="JSON.stringify(data.item)"
          close
          v-bind="data.attrs"
          :input-value="data.selected"
          :disabled="data.disabled"
          color="blue"
          small
          @click:close="data.parent.selectItem(data.item)"
        >
          <span> {{ data.item }}</span>
        </v-chip>
      </template>
    </v-combobox>
  </v-col>
</template>
<script>

export default {

  data: () => ({
comboBoxModel:null,
    comboBoxItem: [],
    chipGroupItems: [
      {
        text: "Hyperdense",
        value: "hyperdense"
      },
      {
        text: "Hypodense",
        value: "hypodense"
      },
      {
        text: "Isodense",
        value: "isodense"
      }
    ]
  }),
};
</script>

