<template>
  <div class="container">
    <img
      src="https://yesno.wtf/assets/yes/5-64c2804cc48057b94fd0b3eaf323d92c.gif"
      alt="No se puede ver"
    />
    <br />
    <div class="pregunta-container">
      <input type="text" placeholder="Hazme una pregunta!..." />
      <p>Recuerda Terminar con el signo de interrogación (?)</p>
      <h2>Sere Millonario?</h2>
      <h1>Yes, No</h1>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
img {
  height: 100vh;
  width: 100vw;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  left: 0;
  top: 0;
}

.pregunta-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);

  width: 350px;
  background-color: white;
  padding: 20px;
  border-radius: 15px;

  border: 2px solid black;
  box-shadow: 2px 8px black;
  text-align: center;
}

input {
  width: 100%;
  text-align: center;
  font-size: 24px;
  border: 2px solid black;
  border-radius: 15px;
  height: 30px;
  padding: 10ñx 15px;
  border: none;
}
input:focus {
  outline: none;
}
h1,
h2,
p {
    color: black;
}
p{
    font-size: 24px;
}
h2{
    margin-top: 150px;
}
</style>
