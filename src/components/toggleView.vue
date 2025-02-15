<template>
  <div>
    <button :aria-label="accessibilityEnabled ? 'false' : 'true'" 
    :aria-expanded="accessibilityEnabled.toString()"
    aria-controls="article-content"
    @click="toggleAccessibility">Toggle Accessibility</button>
    <article>
      <h1 :aria-hidden="accessibilityEnabled ? 'false' : 'true'" :class="{'highlight': accessibilityEnabled}">Sample Article</h1>
      <p :aria-live="accessibilityEnabled ? 'polite' : 'off'" :class="{'highlight': accessibilityEnabled}">
        This is a paragraph demonstrating accessibility attributes.
      </p>
      <img src="../assets/logo.png" alt="Placeholder Image"
           :aria-describedby="accessibilityEnabled ? 'imageDesc' : ''"
           :class="{'highlight': accessibilityEnabled}"/>
      <p v-if="accessibilityEnabled" id="imageDesc" class="highlight">This is a description of the image.</p>
      <ul> ARIA attributes are used to enhance the accessibility of web content.
        <li v-for="(item, index) in items" :key="index" 
        :aria-label="accessibilityEnabled ? `Item ${index + 1}` : ''"
            :class="{'highlight': accessibilityEnabled}">
            {{ item }}
        </li>
      </ul>
      <button :aria-pressed="pressed ? 'true' : 'false'" 
      :aria-label="accessibilityEnabled ? 'true' : 'false'" 
      :class="{'highlight': accessibilityEnabled}" 
      @click="pressedBtn">
        Click Me
      </button>
    </article>

    <h1>Accessible Article</h1>
    <article
      id="article-content"
      role="document"
      :aria-hidden="!accessibilityEnabled"
    >
      <p>This paragraph explains the importance of ARIA attributes.</p>
    </article>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pressed: false,
      accessibilityEnabled: false,
      items: ["Roles", "Properties"]
    };
  },
  methods: {
    toggleAccessibility() {
      this.accessibilityEnabled = !this.accessibilityEnabled;
    },
    pressedBtn() {
      this.pressed = !this.pressed;
      console.log("Button pressed");
    }
  }
};
</script>

<style>
.highlight {
  color: blue;
  font-weight: bold;
}
li {
  display: flex;
  align-items: flex-start;
  margin: 10px 0;
}
</style>
