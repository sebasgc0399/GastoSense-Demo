# GastoSense - Demo Publica

App web mobile-first de finanzas personales para registrar gastos/ingresos en segundos, visualizar metricas claras y actuar con ayuda de IA.

> Este repositorio es solo showcase (sin codigo). El repo principal es privado por comercializacion. Acceso bajo solicitud.

## Descripcion corta
GastoSense esta pensado para personas que quieren control rapido de su dinero sin hojas de calculo. Promesa: captura rapida, visualizaciones utiles y recomendaciones accionables.

## Demo (videos)
- Login + Google Auth (25-40s) - [Ver video](assets/videos/01-login.mp4)
- Inicio (resumen, presupuesto, tarjetas inteligentes) (30-45s) - [Ver video](assets/videos/02-home.mp4)
- Quick Add rapido (gasto/ingreso) (25-40s) - [Ver video](assets/videos/03-quick-add.mp4)
- Quick Add con IA (texto/voz <=10s) (35-60s) - [Ver video](assets/videos/04-quick-add-ia.mp4)
- Movimientos (filtros, editar/borrar, paginacion) (35-60s) - [Ver video](assets/videos/05-movimientos.mp4)
- Presupuesto total y por categoria (30-45s) - [Ver video](assets/videos/06-presupuestos.mp4)
- Metricas (gastos/ingresos, evolucion, top categorias) (35-60s) - [Ver video](assets/videos/07-metricas.mp4)
- Objetivos (metas y deudas) (30-45s) - [Ver video](assets/videos/08-objetivos.mp4)
- Asesor IA (acciones, tono, feed con grafico/CTA) (35-60s) - [Ver video](assets/videos/09-asesor-ia.mp4)
- Datos (export/import CSV/XLSX/JSON) (35-60s) - [Ver video](assets/videos/10-datos.mp4)
- Configuracion y planes (tema, BYOK, cuotas, pagos) (30-45s) - [Ver video](assets/videos/11-settings.mp4)

## Capturas
- Inicio: ![Inicio](assets/images/01-home.png)
- Quick Add: ![Quick Add](assets/images/02-quick-add.png)
- Movimientos: ![Movimientos](assets/images/03-movimientos.png)
- Metricas: ![Metricas](assets/images/04-metricas.png)
- Objetivos: ![Objetivos](assets/images/05-objetivos.png)
- Asesor IA: ![Asesor IA](assets/images/06-asesor-ia.png)
- Configuracion/Planes: ![Settings](assets/images/07-settings.png)

## Features
- Registro rapido de gastos e ingresos con Quick Add.
- Interpretacion por IA de texto o voz (hasta 10s) con sugerencia de categoria, fecha y metodo.
- Movimientos con filtros por fecha, categoria y busqueda; edicion y borrado.
- Presupuesto mensual total y por categoria con alertas 80/100% y progreso visual.
- Metricas con resumen mensual, comparativo vs mes anterior, evolucion diaria/acumulada y top categorias.
- Plantillas recurrentes para registrar gastos/ingresos frecuentes.
- Objetivos de ahorro y deudas con aportes y detalle.
- Asesor IA con acciones guiadas, tono amable/reganon y feed con grafico + CTA.
- Exportar e importar movimientos (CSV, XLSX, JSON) con vista previa.
- Gestion de categorias: crear, editar, reordenar, archivar y sugerir icono por IA.
- Configuracion: tema claro/oscuro, BYOK para IA, planes y cuotas; panel admin de roles.

## Tech Stack
- Frontend: React, TypeScript, Vite, Tailwind CSS, ECharts.
- Backend/Cloud: Firebase Auth, Firestore, Firebase Functions (Node.js 20), Secret Manager, Hosting.
- IA: OpenAI (texto y voz).
- Pagos: Wompi.
- Nota: no hay backend Express dedicado; la logica vive en Firebase Functions.

## Arquitectura (alto nivel)
Frontend web consume Firebase Auth/Firestore y llama a Functions para IA, planes y operaciones sensibles. Las claves BYOK se guardan en Secret Manager. Pagos se procesan via Wompi y se reflejan en el perfil del usuario.

```mermaid
flowchart LR
  UI[Web App React] --> Auth[Firebase Auth]
  UI --> DB[Firestore]
  UI --> CF[Firebase Functions (Node.js)]
  CF --> AI[OpenAI]
  CF --> Pay[Wompi]
  CF --> Secrets[Secret Manager]
