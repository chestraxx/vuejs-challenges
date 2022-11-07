import { h, defineComponent } from 'vue';

export default defineComponent({
  name: 'MyButton',
  emits: ['customClick'],
  props: ['disabled', 'customClick'],
  render() {
    return h(
      'button',
      {
        disabled: this.disabled,
        onClick: () => this.$emit('customClick'),
      },
      this.$slots
    );
  },
});
