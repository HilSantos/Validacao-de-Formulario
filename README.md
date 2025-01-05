# Validacao-de-Formulario
ValidForm II - ProZ Educação

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="style.css">
  <script src="script.js" defer></script>
  <title>Validação de formulário</title>
</head>
<body>
  <form action="">
    <h2>Formulário de cadastro</h2>
    <label for="username">*Username:</label>
    <input type="text" id="username" name="username">
    <p id="username-helper" class="helper-text">Mensagem de ajuda</p>

  <label for="email">*E-mail:</label>
    <input type="email" id="email" name="email">
    <p id="email-helper" class="helper-text ">Mensagem de ajuda</p>

  <label for="idade" class="required-popup">Idade:</label>
    <input type="number" id="idade" name="idade">
    <p id="idade-helper" class="helper-text">Mensagem de ajuda</p>

  <label for="senha">*Senha:</label>
    <input type="password" id="senha" name="senha">
    <p id="senha-helper" class="helper-text">Mensagem de ajuda</p>

  <label for="confirma-senha">*Confirmar senha:</label>
    <input type="password" id="confirma-senha" name="confirma-senha">
    <p id="confirma-senha-helper" class="helper-text">Mensagem de ajuda</p>

    <button type="submit">Enviar</button>
  </form>
</body>
</html>
============================================================================================================

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: #202020;
}

body {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #101010;
}

form {
  display: flex;
  flex-direction: column;
  width: 400px;
  background-color: lightgray;
  border-radius: 16px;
  padding: 1.5rem 40px;
}

h2 {
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
}

label {
  margin-bottom: .2rem;
  position: relative;
}

label:not(:first-of-type){
  margin-top: 1rem;
}

input {
  padding: .2rem .5rem;
}

.helper-text {
  display: none;
  font-size: .8rem;
  color: darkred;
}

button {
  width: 100px;
  height: 40px;
  margin-top: 1.5rem;
  font-size: 1rem;
  align-self: center;
}

/* ---------- Estilos dinâmicos ---------- */
.required-popup::after {
  content: "*Campo obrigatório";
  position: absolute;
  top: 0;
  right: 0;
  color: #DFDFDF;
  font-size: .65rem;
  padding: .2rem .3rem;
  width: auto;
  display: block;
  background-color: #202020;
}

input.error {
  border: solid 2px #992020;
  background-color: #CCBBBB;
  color: #662020;
}

input.correct {
  background-color: #BBCCBB;
  border: solid 2px #206620;
  color: #206620;
}

.visible {
  display: block;
}
===========================================================================================================

let usernameInput = document.getElementById("username");
let usernameLabel = document.querySelector('label[for="username"]');
let usernameHelper = document.getElementById("username-helper");


// Mostrar popup de campo obrigatório
usernameInput.addEventListener("focus", ()=> {
  usernameLabel.classList.add("required-popup");
})

// Ocultar popup de campo obrigatório

usernameInput.addEventListener("blur", ()=> {
  usernameLabel.classList.remove("required-popup");
})


// Validar valor do input
usernameInput.addEventListener("change", (evento) =>{
  let valor = evento.target.value;
  if(valor.length < 3){
    usernameInput.classList.add("error");
    usernameInput.classList.remove("correct");
    usernameHelper.innerText = "O nome precisa ter pelo menos 3 caracteres";
    usernameHelper.classList.add("visible");
  } else{
    usernameInput.classList.add("correct");
    usernameInput.classList.remove("error");
    usernameHelper.classList.remove("remove");
  }
})


let emailInput = document.getElementById("email");
let emaileLabel = document.querySelector('label[for="email"]');
let emailHelper = document.getElementById("email-helper");


emailInput.addEventListener("change", (evento) =>{
  let valor = evento.target.value;
  //console.log(valor.includes("a"))
  if(valor.includes("@") && valor.includes(".com") ){
    console.log("E-mail Válido");
  }else{
    console.log("E-mail Inválido");
  }
}
