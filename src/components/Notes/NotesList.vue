<template lang="pug">
.notes-list
  .note-item(v-for="(note, index) in items" :key="index")
    .note-header {{ note.title }}
      span.note-close(@click="$emit('onRemove', index)") &#10005;
    .note-footer
      ul.tags-list(v-if="note.tags.length")
        li(v-for="tag in note.tags" :key="tag").tag-item.isPreview {{tag}}
</template>

<script lang="ts">
export default {
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="scss">
.notes-list {
  padding: 40px 0;
}

.note-item {
  width: 100%;
  padding: 18px 20px;
  margin-bottom: 20px;
  border-radius: 14px;
  background-color: #ffffff;
  transition: all 0.25s cubic-bezier(0.02, 0.01, 0.47, 1);
  box-shadow: 0 30px 30px rgba(0, 0, 0, 0.02);

  &:hover {
    box-shadow: 0 30px 30px rgba(0, 0, 0, 0.04);
    transform: translate(0, -6px);
    transition-delay: 0s !important;
  }
}

.note-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.note-footer {
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: start;
}

.note-close {
  cursor: pointer;
}

.tag-item {
  padding: 8px 22px;
  margin-right: 10px;
  background-color: #fff;
  border-radius: 22px;
  user-select: none;
  cursor: pointer;

  &.isActive {
    background-color: #42b883;
    color: #fff;
  }

  &.isPreview {
    padding: 0;
    color: #42b883;
    cursor: default;

    &:before {
      content: "#";
    }
  }

  &:last-child {
    margin-right: 0;
  }
}</style>
