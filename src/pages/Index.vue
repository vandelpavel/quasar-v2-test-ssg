<template>
  <q-page ref="componentRef" class="row items-center justify-evenly">
    <example-component
      title="Example component"
      active
      :todos="todos"
      :meta="meta"
    ></example-component>
    <!-- <div
      v-intersection.once="
        whenPastEnd(animateIn('fadeInDown', { duration: '800ms' }))
      "
      _non-real-prop="used to prevent eslint problems"
      data-animate
    >
      aooo
    </div> -->
    <q-btn label="Go to another page" to="another-page" />
  </q-page>
</template>

<script lang="ts">
import { Todo, Meta } from 'components/models';
import ExampleComponent from 'components/CompositionComponent.vue';
import { defineComponent, ref, Ref } from 'vue';
import { QPage } from 'quasar';
// import { useAnimate } from '@dreamonkey/quasar-app-extension-animate';

export default defineComponent({
  name: 'PageIndex',
  components: { ExampleComponent },
  setup() {
    const componentRef = ref() as Ref<QPage>;

    // const element = computed(() => componentRef.value.$el as HTMLElement);

    // const { whenPastEnd, animateIn } = useAnimate(element);

    const todos = ref<Todo[]>([
      {
        id: 1,
        content: 'ct1',
      },
      {
        id: 2,
        content: 'ct2',
      },
      {
        id: 3,
        content: 'ct3',
      },
      {
        id: 4,
        content: 'ct4',
      },
      {
        id: 5,
        content: 'ct5',
      },
    ]);

    const meta = ref<Meta>({
      totalCount: 1200,
    });

    return {
      todos,
      meta,
      // whenPastEnd, animateIn,
      componentRef,
    };
  },
});
</script>
