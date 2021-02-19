<template>
<div>
  <v-col style="background:grey;">
   <p style="margin-bottom:0px;">
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
    >
      <template #selection="data">
        <v-chip
          :key="JSON.stringify(data.item)"
          close
          v-bind="data.attrs"
          :input-value="data.selected"
          :disabled="data.disabled"
          small
          @click:close="data.parent.selectItem(data.item)"
        >
          <span> {{ data.item }}</span>
        </v-chip>
      </template>
    </v-combobox>

  </v-col>
   <v-col style="background:lightblue;">
   
 
     <p class="color-white-light" style="margin-bottom:0px;">
      chip group
    </p>
    <v-chip-group :value="chipGroupModel" active-class="primary" column>
      <v-chip
        v-for="tag in chipGroupItems"
        :key="tag.text"
        small
        auto-select-first="true"
        :value="tag.value"
        @click="chipGroupModel = tag.text"
      >
        <span>{{ tag.text }}</span>
      </v-chip>
    </v-chip-group>

  </v-col>
</div>
</template>
<script>

export default {

  data: () => ({
comboBoxModel:null,
chipGroupModel:null,
    comboBoxItem: ["item-1","item-2","item-3","item-4"],
    chipGroupItems: [
      {
        text: "item-text-1",
        value: "item-value-1"
      },
      {
        text: "item-text-2",
        value: "item-value-2"
      },
      {
        text: "item-text-3",
        value: "item-value-4"
      }
    ]
  }),
};
</script>

