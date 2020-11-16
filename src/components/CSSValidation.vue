<template>
  Show various input types and how they validate.

  <form>
    <label>text, search  </label>  <input id="input1" type="text" pattern="[a-z]*">
    <label>list          </label>  <input list="inputs">
    <label>email         </label>  <input type="email" >
    <label>url           </label>  <input type="url" >
    <label>tel           </label>  <input type="tel" >
    <label>number        </label>  <input type="number" >
    <label>date          </label>  <input type="date" >
    <label>datetime-local</label>  <input type="datetime-local" >
    <label>time          </label>  <input type="time" >
    <label>week          </label>  <input type="week" >
    <label>month         </label>  <input type="month" >
    <label>color         </label>  <input type="color" >
  </form>
  radio, checkbox, range

  <datalist id="inputs">
    <option value="a aa aaa aaaa" />
    <option value="b bb bbb bbbb" />
    <option value="c cc ccc cccc" />
  </datalist>
</template>

<script>
export default {
  name: 'CSSValidation'
}

</script>

<style scoped>
form {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-gap: .3em 1em;
}

input:invalid {
  color: red;
}
</style>
