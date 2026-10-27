Hito 8 - Pizzería Mamma Mía ��

Este proyecto corresponde al Hito 8 de la Academia Desafío Latam (Talentos
Digitales). El objetivo principal es validar los conocimientos de React Router II e
implementar la autenticación real con el backend mediante JSON Web Tokens
(JWT).

* Link del Proyecto: https://hito-8-pizzeria-mamma-mia-gamma.vercel.app/

�� Descripción del Proyecto

En este hito final se integra la autenticación real del sistema consumiendo las rutas
de Auth, Perfil y Checkout provistas por el backend mediante JWT.

��️ Tecnologías y Conceptos Aplicados

● React &amp; React Router II
● Context API (UserContext)
● Autenticación con JWT (JSON Web Token)
● Fetch API / Peticiones HTTP asíncronas

�� Endpoints del Backend

El backend expone los siguientes endpoints para el funcionamiento del sistema:

�� Autenticación (Auth)

● POST /api/auth/login
● POST /api/auth/register

Estructura del Body (JSON):

{
&quot;email&quot;: &quot;test@example.com&quot;,
&quot;password&quot;: &quot;123123&quot;
}

�� Checkout &amp; �� Perfil
Nota: Estas rutas requieren enviar el token JWT en la cabecera (Header) de la
petición.

● POST /api/checkouts
○ Envía la información del carrito para simular la compra.
○ Body (JSON):

{
&quot;cart&quot;: [...]
}


● GET /api/auth/me
○ Obtiene la información del perfil del usuario autenticado.

�� Manejo de Token JWT

Para autenticar las peticiones protegidas (/api/checkouts y /api/auth/me), se debe
incluir el token en el header Authorization de la siguiente manera:

Authorization: Bearer token_jwtEjemplo de Petición (fetch):

await fetch(&quot;http://localhost:5000/api/checkouts&quot;, {
method: &quot;POST&quot;,
headers: {
&quot;Content-Type&quot;: &quot;application/json&quot;,
&quot;Authorization&quot;: `Bearer ${token_jwt}`
},
body: JSON.stringify({
cart: carrito
})
});

✅ Requerimientos del Hito
1. UserContext - Login y Register: Implementar los métodos para autenticarse
e inscribirse consumiendo /api/auth/login y /api/auth/register. Almacenar el
token JWT y el email en el estado correspondiente.
2. UserContext - Logout: Implementar un método para cerrar sesión que
elimine el token y el email del estado.
3. UserContext - Perfil: Implementar un método para consultar el perfil del
usuario autenticado mediante la ruta /api/auth/me.
4. Páginas de Login y Register: Integrar los métodos creados en UserContext
para acceder al sistema.
5. Página de Perfil (Profile): Mostrar el email del usuario autenticado y un
botón para cerrar sesión.
6. Navbar: El botón logout debe ejecutar el cierre de sesión del usuario.

7. Página de Carrito (Cart.jsx): Implementar el envío del carrito de compras al
backend consumiendo la ruta /api/checkouts.
8. Mensaje de Confirmación: Mostrar un mensaje de éxito en Cart.jsx cuando
se complete la compra correctamente.
