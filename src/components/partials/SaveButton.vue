/* Copyright 2017-2018, Frameshift Labs, Inc., All rights reserved. */
<template>
  <a
    v-if="analysis"
    class="analysis-save-button"
    @click.prevent="toggleSaveModal"
  >
    <v-icon>{{ iconName }}</v-icon>
    <span>{{ buttonLabel }}</span>
  </a>
</template>

<script>

export default {
  name: 'SaveButton',
  props: {
    showingSaveModal: {
      type: Boolean,
      required: true,
    },
    analysis: null
  },
  computed: {
    buttonLabel() {
      if (this.analysis && this.analysis.id) {
        return "Analysis";
      } else{ 
        return "Add to Mosaic";
      }
    },
    iconName() {
      if (this.analysis && this.analysis.id) {
        return "edit";
      } else{ 
        return "add";
      }
    },
  },
  methods: {
    toggleSaveModal() {
      this.showingSaveModal ? this.$emit('save-modal:set-visibility', false) : this.$emit('save-modal:set-visibility', true);
    },
  },
};
</script>

<style lang="scss" scoped>
.analysis-save-button {
  margin-left: 50px;
  height: 30px;
  margin-bottom: 4px;  
  width: 140px;
  border-radius: 5px;
  background-color: #007dd4;
  box-shadow: 0 4px 5px 0 rgba(0, 0, 0, .14),
              0 1px 10px 0 rgba(0, 0, 0, .12),
              0 2px 4px -1px rgba(0, 0, 0, .2);
  cursor: pointer;
  user-select: none;
  display: flex;
  justify-content: center;
  align-items: center;

  span {
    color: white;
    font-weight: 500;
    margin-left: 2px;
  }

  &:hover {
    text-decoration: none;
  }

  &:active {
    box-shadow: 0 2px 2px 0 rgba(0, 0, 0, .14),
                0 3px 1px -2px rgba(0, 0, 0, .2),
                0 1px 5px 0 rgba(0, 0, 0, .12);
  }

  i.material-icons {
    font-size: 18px;
  }

  &__icon {
    display: block;
    width: 100%;
    line-height: 70px;
    text-align: center;
    color: #fff;
  }
}
</style>
