# StoreLink — Frontend

Aplicación web de comercio electrónico conectada a la API de StoreLink. Incluye una tienda para clientes y un panel administrativo para gestionar el catálogo, pedidos, promociones y usuarios.

## Funcionalidades

- Catálogo de productos y vista de detalle.
- Registro, inicio de sesión y acceso según los roles `ADMIN` y `CUSTOMER`.
- Carrito de compras, checkout y confirmación de pedidos.
- Perfil del cliente e historial de pedidos.
- Administración de productos, categorías y promociones.
- Actualización del estado de pedidos y bloqueo o desbloqueo de usuarios.

## Tecnologías

Angular 21 · TypeScript 5.9 · Bootstrap 5 · Bootstrap Icons · RxJS · Angular Router · HttpClient · Vitest

## Instalación y ejecución

Requiere **Node.js compatible con Angular 21**, **npm** y el [backend de StoreLink](https://github.com/thoonidev/StoreLink-Backend) configurado y en ejecución. El proyecto declara `npm@11.9.0` como gestor de paquetes.

```bash
git clone https://github.com/thoonidev/StoreLink-Frontend.git
cd StoreLink-Frontend
npm ci
npm start
```

Abre `http://localhost:4200`. Puedes explorar el catálogo y registrarte como cliente; el registro requiere que exista el rol `CUSTOMER` en la base de datos del backend. Para utilizar el panel administrativo necesitas una cuenta con el rol `ADMIN`.

## Conexión con el backend

Configura la dirección de la API en `src/environment/environment.ts`:

```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:8080/storelink/api',
};
```

El backend debe permitir el origen `http://localhost:4200` en su configuración CORS. El frontend guarda el token JWT en `localStorage` y lo adjunta a las solicitudes mediante un interceptor.

El repositorio también incluye `environment.prod.ts`, pero `angular.json` no configura su sustitución automática. Antes de desplegar, configura `fileReplacements` para utilizar ese archivo y ajusta la URL de producción.

El checkout se conecta al módulo de **pagos simulados** del backend; no procesa cobros reales.

## Comandos

| Comando | Descripción |
| --- | --- |
| `npm start` | Inicia el servidor de desarrollo. |
| `npm run build` | Genera la compilación de producción en `dist/storelink-frontend/`. |
| `npm run watch` | Compila en modo desarrollo y observa los cambios. |
| `npm test` | Ejecuta las pruebas con Vitest mediante Angular CLI. |
