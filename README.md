const express = require("express");
const bodyParser = require("body-parser");

const app = express();
const PORT = process.env.PORT || 3300;

// Middleware para procesar datos JSON y datos en formularios
app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

// Ruta GET de bienvenida
app.get("/", (req, res) => {
  res.status(200).send({ msg: "Alfredo Grijalva, 22040062" });
});

// Ruta POST que responde con un saludo personalizado
app.post("/welcome", (req, res) => {
  const { username } = req.body; // Obtenemos 'username' del cuerpo de la solicitud
  res.status(200).send({ msg: `¡Hola, ${username}!` });
});

// Inicia el servidor
app.listen(PORT, () => {
  console.log(`Tu servidor está corriendo en http://localhost:${PORT}`);
});
