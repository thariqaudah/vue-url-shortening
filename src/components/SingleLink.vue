<template>
  <div class="single-link container">
    <p class="original-link">{{ link.originalLink }}</p>
    <div class="output">
      <p class="short-link">{{ link.fullShortLink }}</p>
      <button class="btn btn-sm btn-dark" v-if="isCopied">Copied!</button>
      <button class="btn btn-sm" @click="copyLink" v-else>Copy</button>
    </div>
  </div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
  name: 'SingleLink',
  props: ['link', 'copiedLink'],
  setup(props, { emit }) {
    const copied = ref(false);

    const isCopied = computed(
      () => copied.value && props.copiedLink === props.link.fullShortLink
    );

    const copyLink = async () => {
      await navigator.clipboard.writeText(props.link.fullShortLink);
      console.log('Copied!');
      copied.value = true;
      // Emit event to show the parent that something has been copeied to clipboard
      emit('copy');
    };

    return { copyLink, isCopied };
  },
};
</script>

<style lang="scss" scoped>
.single-link {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #fff;
  padding: 16px 24px;
  border-radius: 5px;

  @media (max-width: 375px) {
    flex-direction: column;
    padding: 0;
  }

  .original-link {
    width: 100%;
    color: #35323e;
    font-weight: 500;

    @media (max-width: 375px) {
      padding: 16px;
      border-bottom: 1px solid hsl(0, 0%, 75%);
    }
  }

  .output {
    display: flex;
    align-items: center;
    gap: 24px;

    @media (max-width: 375px) {
      width: 100%;
      flex-direction: column;
      gap: 16px;
      padding: 16px;
    }

    .short-link {
      width: 100%;
      color: #2acfcf;
      font-weight: 500;

      @media (max-width: 375px) {
        text-align: start;
      }
    }

    button {
      @media (max-width: 375px) {
        width: 100%;
      }
    }
  }
}
</style>
