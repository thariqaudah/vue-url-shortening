<template>
  <div class="shorten-form container">
    <div class="form-container">
      <form class="form" @submit.prevent="shorteningLink">
        <div class="input-container">
          <input
            type="text"
            placeholder="Shorten a link from here..."
            :class="{ error: error }"
            v-model="originalLink"
          />
          <p class="error-msg" v-show="error">{{ errorMsg }}</p>
        </div>
        <button type="submit" class="btn">Shorten It!</button>
      </form>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'ShortenForm',
  setup(props, { emit }) {
    const originalLink = ref(null);
    const error = ref(false);
    const errorMsg = ref(null);

    const shorteningLink = async () => {
      errorMsg.value = null;
      error.value = false;

      // Check if field is empty
      if (!originalLink.value) {
        error.value = true;
        errorMsg.value = 'Please add a link';
        console.log('Error: Please add a link!');
        return;
      }

      // Send request to API
      const response = await fetch(
        `https://api.shrtco.de/v2/shorten?url=${originalLink.value}`
      );
      if (response.ok) {
        originalLink.value = null;
        const data = await response.json();
        console.log('Success', data);
        // Create new var
        const newLink = {
          originalLink: data.result.original_link,
          fullShortLink: data.result.full_short_link,
        };
        // Emit an event
        emit('createLink', newLink);
      } else {
        error.value = true;
        errorMsg.value = 'Please enter a valid link';
        console.log(response);
      }
    };

    return { originalLink, error, errorMsg, shorteningLink };
  },
};
</script>

<style lang="scss" scoped>
.shorten-form {
  background-color: #3b3054;
  padding: 48px 48px 16px 48px;
  border-radius: 9px;
  background-image: url('../assets/bg-shorten-desktop.svg');
  background-repeat: no-repeat;
  background-size: cover;
  transform: translateY(-50%);

  @media (max-width: 375px) {
    padding: 24px;
    background-image: url('../assets/bg-shorten-mobile.svg');
  }

  .form-container {
    min-height: 100px;
  }

  .form {
    display: flex;
    gap: 24px;

    @media (max-width: 375px) {
      flex-direction: column;
    }

    .input-container {
      flex: 1;

      input {
        width: 100%;
        border: none;
        padding: 16px 24px;
        font-family: inherit;
        font-size: inherit;
        color: #35323e;
        border: 3px solid transparent;
        border-radius: 7px;

        &::placeholder {
          color: #9e9aa7;
        }

        &.error {
          border: 3px solid #f46262;

          &::placeholder {
            color: #f46262;
            opacity: 0.5;
          }
        }

        &:focus {
          outline: none;
          border: 3px solid rgba(42, 207, 207, 0.5);
        }
      }

      .error-msg {
        font-size: 16px;
        font-style: italic;
        color: #f46262;
        margin-top: 8px;
      }
    }
  }
}

.output {
  transform: translateY(-50%);
}
</style>
