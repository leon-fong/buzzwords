<script setup lang="ts">
const name = $ref('')
const desc = $ref('')
const router = useRouter()
const go = () => {
  if (name)
    router.push(`/hi/${encodeURIComponent(name)}`)
}
</script>

<template>
  <div w="600px" m="0 auto">
    <h1 text-3xl>
      网络热词生成器
    </h1>

    <div py-4 />

    <div
      flex
      flex-col
      p="x-30 y-20"
      bg="white"
      border="rounded"
    >
      <div flex>
        <Char v-for="item in name" :key="item" :value="item" />
      </div>

      <div mt-10 text="left">
        <p text-2xl font-bold>
          释义:
        </p>
        <p text-xl>
          {{ desc }}
        </p>
      </div>
    </div>

    <input
      id="input"
      v-model="name"
      placeholder="标题"
      type="text"
      autocomplete="false"
      m="y-5 auto"
      p="x-4 y-2"
      w="400px"
      text="left"
      bg="transparent"
      border="~ rounded gray-200 dark:gray-700"
      outline="none active:none"
      display="block"
      @keydown.enter="go"
    >

    <textarea
      id="input"
      v-model="desc"
      placeholder="释义"
      type="textarea"
      autocomplete="false"
      m="y-5 auto"
      p="x-4 y-2"
      w="400px"
      text="left"
      bg="transparent"
      border="~ rounded gray-200 dark:gray-700"
      outline="none active:none"
      display="block"
      @keydown.enter="go"
    />

    <div>
      <button
        class="m-3 px-6 text-sm btn bg-[#2aae67]"
        :disabled="!name"
        @click="go"
      >
        生成
      </button>
    </div>
  </div>
</template>
