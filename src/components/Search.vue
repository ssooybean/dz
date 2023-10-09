<template>
  <h2 class="w-fit mx-auto mt-16 text-2xl text-purple-800 font-bold">Статистка погоды</h2>
  <form action="#" class="w-fit mx-auto mt-8 flex flex-col gap-10 items-center">
    <div class="relative">
      <label>
        <input
          type="text"
          :value="req.city"
          @input="req.city = $event.target.value"
          required
          class="border-2 border-purple-300 rounded pl-4 pr-8 py-2 w-[300px] text-lg text-purple-400 focus:text-neutral-600 focus:outline-violet-800 peer"
        />
        <span
          class="transition-all absolute left-4 top-1/2 -translate-y-1/2 peer-valid:-translate-y-9 peer-focus:text-violet-800 w-14 text-center peer-valid:bg-white text-purple-400"
          >Город</span
        >
      </label>
    </div>
    <div class="relative">
      <label>
        <input
          type="date"
          id="start"
          name="start"
          min="2000-01-01"
          :value="req.from"
          @input="req.from = $event.target.value"
          required
          class="border-2 border-purple-300 rounded pl-4 pr-8 py-2 w-[300px] text-lg focus:outline-violet-800 text-purple-400 focus:text-neutral-600 peer"
        />
        <span
          class="absolute left-4 top-1/2 -translate-y-9 bg-white w-8 text-center text-purple-400 peer-focus:text-violet-800"
          >От:</span
        >
      </label>
    </div>
    <div class="relative">
      <label>
        <input
          type="date"
          id="end"
          name="end"
          min="2000-01-02"
          required
          :value="req.to"
          @input="req.to = $event.target.value"
          class="border-2 border-purple-300 rounded pl-4 pr-8 py-2 w-[300px] text-lg text-purple-400 focus:text-neutral-600 focus:outline-violet-800 peer"
        />
        <span
          class="absolute left-4 top-1/2 -translate-y-9 bg-white w-8 text-center text-purple-400 peer-focus:text-violet-800"
          >До:</span
        >
      </label>
    </div>
    <button
      type="button"
      @click="searchChart"
      class="border-2 rounded px-4 py-1 text-xl font-semibold bg-gradient-to-r from-blue-300 to-purple-600 bg-clip-text hover:bg-clip-padding text-transparent hover:text-white border-purple-300 w-fit"
    >
      Найти
    </button>
  </form>
</template>

<script>
export default {
  emits: ['search'],
  data() {
    return {
      req: {
        city: '',
        from: '',
        to: '',
      },
    };
  },
  methods: {
    searchChart() {
      this.$emit('search', this.req);
    },
  },
};
</script>
