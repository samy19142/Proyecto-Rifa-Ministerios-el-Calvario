# 🎰 Gran Rifa — Ministerios el Calvario

> Sistema de sorteo digital en tiempo real para eventos presenciales, desarrollado en React con animaciones interactivas, persistencia local y generación de reportes PDF.

---

## 📸 Vista previa

```
[Pantalla principal con bolas animadas, card de premio activo y número ganador en formato bolitas de lotería]
```

---

## 🚀 Características principales

- 🎱 **Animación de bolas estilo máquina de aire** — Las bolas vuelan aleatoriamente mientras el sorteo está en curso, simulando una máquina de lotería real.
- 🔢 **Revelación dígito a dígito** — El número ganador se revela progresivamente con confetti en cada dígito.
- 🏆 **Bolitas de lotería** — Cada dígito del número ganador se muestra dentro de una bolita circular con efecto 3D.
- 💾 **Persistencia con localStorage** — Los ganadores y el contador de intentos se guardan automáticamente en el navegador y se recuperan al recargar la página.
- 🎯 **3 intentos por premio** — Cada premio cuenta con 3 intentos para asignar un ganador; el botón se bloquea solo cuando esos intentos se agotan.
- 📄 **PDF profesional** — Genera un reporte con diseño corporativo, tarjetas por premio, estado visual y barra de progreso del sorteo.
- 🎉 **Confetti y fuegos artificiales** — Efectos visuales al revelar cada dígito y al completar el sorteo.
- 👁️ **Panel de ganadores flotante** — Lista lateral con imagen, nombre del premio y número ganador de cada premio.
- 🔄 **Navegación entre premios** — Permite avanzar o retroceder entre los premios disponibles.
- 🔁 **Reinicio completo** — Limpia todos los ganadores, reinicia los intentos a 3 y borra el almacenamiento local.

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Uso |
|---|---|
| [React 18](https://react.dev/) | Framework principal (Hooks: useState, useEffect, useRef) |
| [Tailwind CSS](https://tailwindcss.com/) | Estilos y diseño responsive |
| [jsPDF](https://github.com/parallax/jsPDF) | Generación de reportes PDF en el navegador |
| [canvas-confetti](https://github.com/catdad/canvas-confetti) | Efectos de confetti y fuegos artificiales |
| localStorage API | Persistencia de ganadores entre sesiones |

---

## 📁 Estructura del proyecto

```
gran-rifa/
├── public/
├── src/
│   ├── assets/
│   │   └── logo-ec_.png          # Logo de la organización
│   ├── App.jsx                   # Componente principal (todo en uno)
│   └── main.jsx
├── package.json
└── README.md
```

---

## ⚙️ Instalación y uso

### 1. Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/gran-rifa.git
cd gran-rifa
```

### 2. Instalar dependencias

```bash
npm install
```

### 3. Instalar dependencias requeridas

```bash
npm install jspdf canvas-confetti
```

### 4. Correr en desarrollo

```bash
npm run dev
```

### 5. Build para producción

```bash
npm run build
```

---

## 🎁 Configuración de premios

Los premios se configuran en el arreglo `initialPrizes` dentro de `App.jsx`:

```js
const initialPrizes = [
  {
    id: 1,
    name: "Nombre del premio",
    image: "URL o base64 de la imagen",
    price: "Premio #1",
    buttonBg: "bg-red-600",
    buttonHover: "hover:bg-red-700",
    winnerId: null,
    attemptsLeft: 3,
  },
  // ...más premios
];
```

> **Recomendación para eventos sin internet:** Convierte las imágenes a base64 para garantizar que se muestren correctamente sin conexión.

---

## 🎲 Lógica del sorteo

- El rango de boletos es del **00001 al 03000**.
- El sistema garantiza que **no se repita un ganador** entre premios.
- Cada premio dispone de **3 intentos** para asignar un ganador. Si falla un intento, el contador disminuye y el botón se bloqueará solo cuando se agoten los 3.
- El número se revela **dígito a dígito** con un intervalo de ~3.7 segundos por dígito.
- Las bolas dejan de volar automáticamente al finalizar el sorteo.

```js
// Rango configurable aquí:
Math.floor(Math.random() * 3000) + 1
```

---

## 💾 Persistencia (localStorage)

Los ganadores y los intentos restantes se almacenan automáticamente bajo la key `"rifa_winners"`:

```json
{
  "1": { "winnerId": "01234", "attemptsLeft": 2 },
  "2": { "winnerId": null, "attemptsLeft": 3 }
}
```

Para limpiar manualmente desde la consola del navegador:

```js
localStorage.removeItem("rifa_winners");
```

---

## 📄 Reporte PDF

El PDF generado incluye:

- Header con logo institucional, nombre del evento y fecha
- Tarjeta individual por cada premio con banda de color, número ganador y estado
- Resumen con conteo de premios asignados y barra de progreso
- Footer con datos de la organización

---

## 🏛️ Organización

**Ministerios el Calvario**
📞 PBX: (502) 2246-8080
🌐 Guatemala

---

## 📝 Licencia

Este proyecto fue desarrollado exclusivamente para uso interno de **Ministerios el Calvario**.
Todos los derechos reservados © 2025.
