<template>
  <BImg v-bind="computedImgProps" :class="baseClass" />
</template>

<script setup lang="ts">
import BImg from '../BImg.vue'
import type {BCardImgProps} from '../../types'
import {omit} from '../../utils'
import {computed, toRef} from 'vue'
import {useDefaults} from '../../composables'

const _props = withDefaults(defineProps<BCardImgProps>(), {
  bottom: false,
  top: false,
  // BImg props
  blank: undefined,
  blankColor: undefined,
  block: undefined,
  center: undefined,
  end: undefined,
  fluid: undefined,
  fluidGrow: undefined,
  height: undefined,
  lazy: undefined,
  rounded: undefined,
  roundedBottom: undefined,
  roundedEnd: undefined,
  roundedStart: undefined,
  roundedTop: undefined,
  sizes: undefined,
  src: undefined,
  srcset: undefined,
  start: undefined,
  thumbnail: undefined,
  width: undefined,
  // End BImg props
})
const props = useDefaults(_props, 'BCardImg')

const baseClass = toRef(() =>
  props.top
    ? 'card-img-top'
    : props.end
      ? 'card-img-right'
      : props.bottom
        ? 'card-img-bottom'
        : props.start
          ? 'card-img-left'
          : 'card-img'
)

const computedImgProps = computed(() => omit(props, ['bottom', 'top', 'end', 'start']))
</script>
