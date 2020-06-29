# Aprendiendo React desde cero
[Guía](https://www.youtube.com/watch?v=T_j60n1zgu0&feature=youtu.be)\
[Oficial](https://es.reactjs.org/)

## Notas
🤔 Node es un motor de js que permite programar en js "lado servidor". React corre js "lado cliente". Es medio confuso pero en realidad lo que  estamos haciendo con react corre en el navegador. Usa Node para "compilar" y para devs. Pero en realidad "no corre en node" sino que es contenido estático\
✔️ interfaces de usuario independientes de la plataforma, utilizando adaptadores\
👉 es declarativo (vs imperativo)\
👉 basado en componentes (reutilizables)\
👻 Facebook\
📈 [trends](https://www.npmtrends.com/angular-vs-react-vs-vue)

## Dependencias y entorno
```sh
$ node -v
v14.3.0
$ code-oss -v
1.45.1
5763d909d5f12fe19f215cbfdd29a91c0fa9208a
x64
```

## Repositorio
```sh
$ git log
$ git remote add origin https://github.com/diegobollini/react_freestyle.git
$ git commit -m "primera sesión 30'"
$ git push -u origin master
```

## Conectar visualstudio + github
```
code-oss://vscode.github-authentication/did-authenticate?windowId
Copy the token.
Switch back to VS code.
Click Signing in to null... in the status bar.
Paste the token and hit enter.
```

## Sesión práctica 01: HTML
[Test environment](https://diegobollini.github.io/react_freestyle/)

### Favicon: una gilada
 ```html
    <link rel="icon" href="https://img.icons8.com/pastel-glyph/64/000000/monitor.png">
```

### Construyendo nuestra app
Todo lo que definamos a este componente, se aplica (por ejemplo definir la etiqueta h4 para el parámetro name, podría ser strong):
```html
const $app = document.getElementById('app');
            const Avatar = params => {
                const src = `https://randomuser.me/api/portraits/women/${params.id}.jpg`;
                return `<picture>
                    <img src="${src}" />
                    <h4>${params.name}</h4>
                </picture>
                `;
            };
```

### Constante "Avatar"
Previamente definimos esta constante en index.html, buscando la imagen de acuerdo a la id definida en estas líneas:
```html
$app.innerHTML += Avatar({ id:12, name: "nombre1"});
$app.innerHTML += Avatar({ id:23, name: "nombre2"});
```

### Cambiar transparencia / opacidad al clickear una imagen
```html
$app.querySelectorAll('img').forEach(img => {
            img.addEventListener('click', () => {
                img.classList.toggle('disabled')
```

## Sesión práctica 02: Arranca react, reactdom, etc.
Agrego las siguientes etiquetas según la [documentación](https://es.reactjs.org/docs/add-react-to-a-website.html#step-2-add-the-script-tags):

```html
<!-- Cargar React. -->
  <!-- Nota: cuando se despliegue, reemplazar "development.js" con "production.min.js". -->
  <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script> #librería "base" de react
  <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script> #para que react funcione en el navegador
```
- TIP: coma separa 2 argumentos de una función, punto te permite entrar a una función dentro de la clase

Entonces creo la app Avatar pero con react a lo guaso, importando directamente en el html:
```html
const $app = document.getElementById('app');
            const h = React.createElement;

            const Avatar = params =>{
                const src = `https://randomuser.me/api/portraits/women/${params.id}.jpg`;
                return h('img', {src});
            };
            ReactDOM.render(h(Avatar, { id: 18 }), $app);
```

## Sesión práctica 03: reactdom, jsx, babel y más
Podríamos utilizar el tercer parámetro de una función para renderizar más de una imagen, pero claramente no tiene sentido:
```html
ReactDOM.render(
                h("div", null, [h(Avatar, { id: 21 }), h(Avatar, { id: 24 })]),$app);
```

Prueba JSX de forma rápida
```html
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
type="text/babel"
```
## Sesión práctica 04: componentes, estados
Por ejemplo buen uso de props:
```html
const Avatar = props => {
    <strong>{props.name}</strong>
```
Puedo desestructurar "objetos":
```html
const Avatar = ({id, name, size}) => {
    <strong>{name}</strong>
```