# MeetFlow Frontend — Editor colaborativo de diagramas de secuencia UML

Frontend web para crear **diagramas de secuencia UML** de forma colaborativa. Los usuarios crean "reuniones" con un código, invitan a otros y editan el mismo diagrama en tiempo real; el resultado puede exportarse como imagen SVG o guardarse en el servidor.

> Proyecto académico — Ingeniería de Software I, UAGRM (2024).
> El backend (API + Socket.IO) está en el repositorio [Meetflow-Backend](https://github.com/Fabio0406/Meetflow-Backend) y se desplegó en Railway.

## Funcionalidades

- Registro, inicio de sesión y configuración de la cuenta.
- Página principal con los diagramas del usuario.
- Creación de **reuniones** (salas) con código de acceso, en `/reunion/:id/:codigo`.
- **Edición en tiempo real** con Socket.IO: los cambios de cada usuario se transmiten al resto.
- Diagrama de secuencia con **líneas de vida, activaciones y mensajes**, dibujado con GoJS.
- Exportación del diagrama a **SVG** e importación desde JSON.

## Tecnologías

- React 18 + TypeScript + Vite
- GoJS / gojs-react (diagramas)
- Socket.IO client
- Material UI, styled-components, Tailwind CSS
- Axios, React Router, js-cookie, file-saver

## Estructura

```
src/
├── App.tsx               # Rutas
├── axiosInstance.tsx     # Cliente HTTP (URL del backend)
├── UserContext.tsx       # Sesión del usuario
├── components/           # header, topbar, footer, posts
└── view/
    ├── DiagramWrapper.tsx  # Plantillas GoJS del diagrama de secuencia
    ├── Diagram/            # Utilidades de arrastre
    ├── Reunion/            # Sala colaborativa
    ├── write/              # Crear / unirse a una reunión
    ├── homepage/, login/, register/, settings/
```

## Requisitos

- Node.js 18 o superior
- El backend [Meetflow-Backend](https://github.com/Fabio0406/Meetflow-Backend) en ejecución

## Instalación

```bash
npm install
npm run dev
```

La URL del backend se configura en `src/axiosInstance.tsx` y en las conexiones de Socket.IO dentro de `src/view/`.

## Rutas

| Ruta | Descripción |
|---|---|
| `/` , `/posts` | Inicio |
| `/register` , `/login` | Registro e inicio de sesión |
| `/diagramas` | Crear o unirse a una reunión |
| `/reunion/:id/:codigo` | Editor colaborativo |
| `/settings` | Configuración de la cuenta |
