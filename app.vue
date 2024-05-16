<script setup lang="ts">
  const fooCookie = useCookie('foo', {
    default: () => 'FOO'
  })
  const barCookie = useCookie('bar', {
    default: () => 'BAR',
    decode(value) {
      console.log({action: 'decode', baz: value, source: 'bar'})
      return value
    },
  })
  const bazCookie = useCookie('baz', {
    decode(value) {
      console.log({action: 'decode', baz: value, source: 'baz'})
      return value
    },
    encode(value) {
      console.log({action: 'encode', baz: value})
      return value
    },
  })
  onMounted(() => {
    console.log(`All cookies: ${document.cookie}`)
  })
</script>
<template>
  <div>
    <h1>Coookies</h1>
    <div>
      <p>Foo: "{{ fooCookie }}"</p>
      <p>Bar: "{{ barCookie }}"</p>
      <p>Baz: "{{ bazCookie}}"</p>
    </div>
  </div>
</template>
