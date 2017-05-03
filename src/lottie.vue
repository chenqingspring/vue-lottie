<template>
    <div :style="style" ref="lavContainer"></div>
</template>

<script>
  import bodymovin from 'bodymovin';

  export default {
    props: {
      options: {
        type: Object,
        required: true
      },
      height: Number,
      width: Number,
    },

    data () {
      return {
        style: {
          width: this.width ? `${this.width}px` : '100%',
          height: this.height ? `${this.height}px` : '100%',
          overflow: 'hidden',
          margin: '0 auto'
        }
      }
    },

    mounted () {
      this.anim = bodymovin.loadAnimation({
          container: this.$refs.lavContainer,
          renderer: 'svg',
          loop: this.options.loop !== false,
          autoplay: this.options.autoplay !== false,
          animationData: this.options.animationData
        }
      );
      this.$emit('animCreated', this.anim)
    }
  }
</script>
