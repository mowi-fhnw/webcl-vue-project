<template>
  <Eye/>
<!--
  <Signature/>
-->
  <CSSTriangle/>
  <CSSValidation/>
  <Todo/>
</template>

<script>
import Eye from './components/Eye.vue'
/*
import Signature from './components/Signature.vue'
*/
import CSSTriangle from './components/CSSTriangle.vue'
import CSSValidation from './components/CSSValidation.vue'
import Todo from './components/Todo.vue'

export default {
  name: 'App',
  components: {
    Eye,
/*
    Signature,
*/
/*
    Signature,
*/
    CSSTriangle,
    CSSValidation,
    Todo
  }
}
</script>
