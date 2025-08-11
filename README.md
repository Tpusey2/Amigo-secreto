let amigos = [];

function adicionarAmigo() {
  const input = document.getElementById("nombreInput");
  const nombre = input.value.trim();

  if (nombre === "") {
    alert("Por favor, inserte un nombre.");
    return;
  }

  amigos.push(nombre);
  input.value = "";
  mostrarLista();
}

function mostrarLista() {
  const lista = document.getElementById("listaAmigos");
  lista.innerHTML = "";

  amigos.forEach(function (amigo) {
    const li = document.createElement("li");
    li.textContent = amigo;
    lista.appendChild(li);
  });
}

function sortearAmigo() {
  if (amigos.length === 0) {
    alert("La lista está vacía. Agrega al menos un amigo.");
    return;
  }

  const indiceAleatorio = Math.floor(Math.random() * amigos.length);
  const amigoSorteado = amigos[indiceAleatorio];

  const resultado = document.getElementById("resultado");
  resultado.innerHTML = `🎉 El amigo secreto es: <strong>${amigoSorteado}</strong>`;
}

// Espera a que el HTML esté cargado antes de conectar los botones
document.addEventListener("DOMContentLoaded", function () {
  const btnAdicionar = document.getElementById("btnAdicionar");
  const btnSortear = document.getElementById("btnSortear");

  btnAdicionar.addEventListener("click", adicionarAmigo);
  btnSortear.addEventListener("click", sortearAmigo);
});

