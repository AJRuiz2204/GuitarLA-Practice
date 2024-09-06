
# Proyecto React + Vite

Este proyecto es una plantilla mínima para configurar React con Vite, con soporte para HMR (Hot Module Replacement) y ESLint para mantener la calidad del código.

## Requisitos Previos

Asegúrate de tener instalados los siguientes componentes antes de continuar con la configuración:

- **Node.js** (versión 14 o superior)
- **npm** (versión 6 o superior) o **yarn**

## Instalación y Ejecución

Sigue los pasos a continuación para clonar y ejecutar el proyecto en tu máquina local:

### 1. Clonar el repositorio
   Ejecuta el siguiente comando en tu terminal para clonar el repositorio:

   ```bash
   git clone https://github.com/tu-usuario/tu-repositorio.git
   ```

### 2. Navegar al directorio del proyecto
   Cambia el directorio a la carpeta del proyecto:

   ```bash
   cd tu-repositorio
   ```

### 3. Instalar dependencias
   Instala las dependencias del proyecto usando npm o yarn:

   ```bash
   npm install
   # o
   yarn install
   ```

### 4. Iniciar el servidor de desarrollo
   Para iniciar el servidor de desarrollo con hot reload, ejecuta:

   ```bash
   npm run dev
   # o
   yarn dev
   ```

   Ahora, abre tu navegador en `http://localhost:3000` para ver la aplicación funcionando.

## Scripts Disponibles

En el archivo `package.json`, se incluyen los siguientes scripts útiles:

- **`npm run dev`**: Inicia el servidor de desarrollo.
- **`npm run build`**: Genera una versión optimizada para producción.
- **`npm run preview`**: Previsualiza el build de producción.
- **`npm run lint`**: Revisa el código usando ESLint para detectar errores y buenas prácticas.

## Estructura del Proyecto

La estructura básica del proyecto es la siguiente:

```
.
├── src
│   ├── assets/               # Archivos estáticos (imágenes, fuentes, etc.)
│   ├── components/           # Componentes reutilizables de React
│   ├── App.jsx               # Componente principal
│   └── main.jsx              # Punto de entrada de la aplicación
├── public/                   # Archivos públicos (índex.html, favicon, etc.)
├── .eslintrc.js              # Configuración de ESLint
├── vite.config.js            # Configuración de Vite
└── package.json              # Dependencias y scripts del proyecto
```

## Hooks de React Utilizados

Este proyecto utiliza varios hooks de React para manejar el estado y los efectos secundarios en los componentes. A continuación, se detallan los más importantes:

### useState
El hook `useState` se utiliza para manejar el estado en componentes funcionales.

**Ejemplo:**

```jsx
import React, { useState } from 'react';

function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Has hecho clic {contador} veces</p>
      <button onClick={() => setContador(contador + 1)}>
        Incrementar
      </button>
    </div>
  );
}

export default Contador;
```

### useEffect
El hook `useEffect` se utiliza para manejar efectos secundarios, como la obtención de datos o suscripciones.

**Ejemplo:**

```jsx
import React, { useEffect, useState } from 'react';

function Datos() {
  const [datos, setDatos] = useState([]);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setDatos(data));
  }, []);

  return (
    <ul>
      {datos.map(item => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}

export default Datos;
```

### useContext
El hook `useContext` se utiliza para acceder a valores compartidos a través de un contexto.

**Ejemplo:**

```jsx
import React, { useContext } from 'react';
import { TemaContexto } from './TemaContexto';

function Boton() {
  const tema = useContext(TemaContexto);

  return (
    <button style={{ background: tema.background, color: tema.color }}>
      Botón con tema
    </button>
  );
}

export default Boton;
```

## Configuración de ESLint

Este proyecto incluye una configuración básica de ESLint para garantizar la calidad del código. Puedes personalizar las reglas en el archivo `.eslintrc.js` según las necesidades de tu proyecto.

### Ejemplo de Configuración:

```javascript
module.exports = {
  env: {
    browser: true,
    es2021: true,
  },
  extends: [
    'eslint:recommended',
    'plugin:react/recommended',
    'plugin:@typescript-eslint/recommended',
  ],
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: 'latest',
    sourceType: 'module',
  },
  plugins: ['react', '@typescript-eslint'],
  rules: {
    'react/react-in-jsx-scope': 'off',
    '@typescript-eslint/no-unused-vars': 'warn',
  },
};
```

## Créditos y Agradecimientos

Este proyecto utiliza las siguientes herramientas y librerías:

- [Vite](https://vitejs.dev/) - Motor de construcción rápido para proyectos frontend.
- [React](https://reactjs.org/) - Librería para construir interfaces de usuario.
- [ESLint](https://eslint.org/) - Herramienta para identificar y reportar patrones en el código JavaScript.
- [SWC](https://swc.rs/) - Un compilador JavaScript rápido que reemplaza Babel para React Fast Refresh.

Si tienes alguna pregunta o sugerencia, no dudes en abrir un **issue** o enviar un **pull request**.
