<template>
  <div>
    <button @click="toggleAccessibility">Toggle Accessibility</button>
    <article>
      <h1 :aria-hidden="accessibilityEnabled ? 'false' : 'true'" :class="{'highlight': accessibilityEnabled}">Sample Article</h1>
      <p :aria-live="accessibilityEnabled ? 'polite' : 'off'" :class="{'highlight': accessibilityEnabled}">
        This is a paragraph demonstrating accessibility attributes.
      </p>
      <img src="../assets/logo.png" alt="Placeholder Image"
           :aria-describedby="accessibilityEnabled ? 'imageDesc' : ''"
           :class="{'highlight': accessibilityEnabled}"/>
      <p v-if="accessibilityEnabled" id="imageDesc" class="highlight">This is a description of the image.</p>
      <ul>
        <li v-for="(item, index) in items" :key="index" :aria-label="accessibilityEnabled ? `Item ${index + 1}` : ''"
            :class="{'highlight': accessibilityEnabled}">
          List Item {{ index + 1 }}
        </li>
      </ul>
      <button :aria-pressed="accessibilityEnabled ? 'true' : 'false'" :class="{'highlight': accessibilityEnabled}">
        Click Me
      </button>
    </article>
  </div>
</template>

<script>
export default {
  data() {
    return {
      accessibilityEnabled: false,
      items: ["Item 1", "Item 2", "Item 3"]
    };
  },
  methods: {
    toggleAccessibility() {
      this.accessibilityEnabled = !this.accessibilityEnabled;
    }
  }
};
</script>

<style>
.highlight {
  color: blue;
  font-weight: bold;
}
</style>
