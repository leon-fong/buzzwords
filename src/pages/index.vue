<script setup lang="ts">
const name = $ref('')
const desc = $ref('')
const router = useRouter()
const go = () => {
  if (name)
    router.push(`/hi/${encodeURIComponent(name)}`)
}

watch(name, (old, now) => {
  if (now.length > 5)
    name = old
})

const handleRandom = () => {
  name = '只因飞狗跳'
  desc = '这是一段描述这是一段描述这是一段描述这是一段描述这是一段描述这是一段描述这是。'
}

const reset = () => {
  name = ''
  desc = ''
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
      p="x-40 y-20"
      bg="white"
      border="rounded"
    >
      <div flex>
        <Char v-for="item in name" :key="item" :value="item" :len="name.length" />
      </div>

      <div mt-8 text="left">
        <p text-xl font-bold>
          释义:
        </p>
        <p text-sm mt-3>
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
      border="~ rounded gray-200"
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
      border="~ rounded gray-200 "
      outline="none active:none"
      display="block"
      @keydown.enter="go"
    />

    <div>
      <button
        class="m-3 px-6 text-sm btn bg-[#2aae67]"
        @click="handleRandom"
      >
        随机
      </button>
      <button
        class="m-3 px-6 text-sm btn bg-[#2aae67]"
        :disabled="!name"
        @click="reset"
      >
        清空
      </button>
    </div>
    <button
      class="m-3 px-6 text-sm btn bg-[#2aae67]"
      :disabled="!name"
      @click="go"
    >
      生成
    </button>
  </div>
</template>
