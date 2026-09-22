# GIM — Gestor de Información Meteorológica del Parque Nacional Lanín

Webapp para visualizar y explorar el índice FWI (Fire Weather Index) de las estaciones meteorológicas del Parque Nacional Lanín.

🔗 **Producción:** [gim-pnl.vercel.app](https://gim-pnl.vercel.app)

## Stack

- React + Vite + TypeScript
- Tailwind CSS

## Desarrollo local

```bash
npm install
npm run dev
```

La app corre en `http://localhost:5174`. Ver `CLAUDE.md` para el detalle de la API consumida y las convenciones del proyecto.

## Build

```bash
npm run build
```

## Expandiendo la configuración de ESLint

Si vas a seguir desarrollando esta aplicación, se recomienda habilitar reglas de lint con reconocimiento de tipos:

```js
export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Otras configs...

      // Reemplazar tseslint.configs.recommended por esto
      tseslint.configs.recommendedTypeChecked,
      // O, para reglas más estrictas
      tseslint.configs.strictTypeChecked,
      // Opcionalmente, reglas de estilo
      tseslint.configs.stylisticTypeChecked,

      // Otras configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // otras opciones...
    },
  },
])
```

También se pueden instalar [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) y [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) para reglas específicas de React:

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x'
import reactDom from 'eslint-plugin-react-dom'

export default defineConfig([
  globalIgnores(['dist']),
  {
    files: ['**/*.{ts,tsx}'],
    extends: [
      // Otras configs...
      reactX.configs['recommended-typescript'],
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ['./tsconfig.node.json', './tsconfig.app.json'],
        tsconfigRootDir: import.meta.dirname,
      },
      // otras opciones...
    },
  },
])
```
