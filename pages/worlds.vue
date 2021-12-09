<template>
  <div>
    <h1>Page Worlds</h1>
    <WorldStepper />
  </div>
</template>

<script lang="ts">
import WorldStepper from '~~/components/WorldStepper/WorldStepper.vue'

interface Worlds{
  name: string,
  value: number,
  levels: []
}

// interface Levels{
//     name: string,
//     reward: string,
//     data: string,
//     worldId: number,
//     type: string
// }

export default {
  name: 'WizmiIndex',
  components: { WorldStepper },
  layout: 'wizmi-base',
  setup () {
    const worlds = reactive({} as Worlds)
    const mockLevels = [
      {
        name: 'name',
        reward: 'reward',
        data: 'data',
        type: 'block'
      },
      {
        name: 'name 2',
        reward: 'reward',
        data: 'data',
        type: 'block'
      },
      {
        name: 'name 3',
        reward: 'reward',
        data: 'data',
        type: 'block'
      }
    ]
    const mockWorlds = [
      {
        name: 'world 1',
        value: 1,
        levels: mockLevels
      },
      {
        name: 'world 2',
        value: 2,
        levels: mockLevels
      }
    ]
    return {
      worlds,
      mockLevels,
      mockWorlds
    }
  },
  mounted () {
    this.ok()
  },
  methods: {
    ok () {
      console.log(this.mockWorlds)
    }
  }
}
</script>
