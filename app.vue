<script setup lang="ts">
  const fooCookie = useCookie('foo', {
    default: () => 'FOO'
  })
  const barCookie = useCookie('bar', {
    default: () => 'BAR'
  })
  const bazCookie = useCookie('baz', {
    decode(value) {
      console.log({action: 'decode', baz: value})
      return value
    },
    encode(value) {
      console.log({action: 'encode', baz: value})
      return value
    },
  })
</script>
<template>
  <div>
    <h1>Coookies</h1>
    <div>
      <p>{{ fooCookie }}</p>
      <p>{{ barCookie }}</p>
      <p>{{ bazCookie }}</p>
    </div>
  </div>
</template>
