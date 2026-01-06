# GastoSense — Demo Pública (Showcase)

App web **mobile-first** de finanzas personales para **registrar gastos/ingresos en segundos**, visualizar **métricas claras** y actuar con ayuda de **IA**.

> Este repositorio es **solo showcase (sin código)**.  
> El repositorio principal es **privado por comercialización**. Acceso bajo solicitud.

---

## Índice
- [Descripción](#descripción)
- [Demo](#demo)
- [Capturas](#capturas)
- [Características](#características)
- [Tech Stack](#tech-stack)
- [Arquitectura](#arquitectura)
- [Seguridad y privacidad](#seguridad-y-privacidad)
- [Roadmap](#roadmap)
- [Contacto](#contacto)
- [Activos a preparar](#activos-a-preparar)

---

## Descripción
GastoSense está pensado para personas que quieren control rápido de su dinero **sin depender de hojas de cálculo**.

**Promesa:** captura rápida, visualizaciones útiles y recomendaciones accionables.

---

## Demo
Proximamente al publico...

### Videos (25–60s)
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

---

## Capturas
- Inicio — ![Inicio](assets/images/01-home.png)
- Quick Add — ![Quick Add](assets/images/02-quick-add.png)
- Movimientos — ![Movimientos](assets/images/03-movimientos.png)
- Métricas — ![Métricas](assets/images/04-metricas.png)
- Objetivos — ![Objetivos](assets/images/05-objetivos.png)
- Asesor IA — ![Asesor IA](assets/images/06-asesor-ia.png)
- Configuración/Planes — ![Settings](assets/images/07-settings.png)

---

## Características
- Registro rápido de gastos e ingresos con **Quick Add**.
- **IA** para interpretar texto o voz (≤10s) con sugerencia de categoría, fecha y método.
- Movimientos con filtros por fecha/categoría/búsqueda; edición y borrado.
- Presupuesto mensual total y por categoría con alertas 80/100% y progreso visual.
- Métricas: resumen mensual, comparativo vs. mes anterior, evolución y top categorías.
- Plantillas recurrentes para registrar movimientos frecuentes.
- Objetivos de ahorro y deudas con aportes e historial.
- Asesor IA con acciones guiadas, tono (amable / exigente / “regañón”) y feed con gráfico + CTA.
- Exportar e importar movimientos (CSV, XLSX, JSON) con vista previa.
- Gestión de categorías: crear, editar, reordenar, archivar y sugerir ícono con IA.
- Configuración: tema claro/oscuro, BYOK para IA, planes/cuotas y gestión de acceso (si aplica).

---

## Tech Stack
- **Frontend:** React, TypeScript, Vite, Tailwind CSS, ECharts.
- **Backend/Cloud:** Firebase Auth, Firestore, Firebase Functions (Node.js 20), Secret Manager, Hosting.
- **IA:** OpenAI (texto y voz).
- **Pagos:** Wompi.
- **Nota:** no hay backend Express dedicado; la lógica vive en Firebase Functions.

---

## Arquitectura
Frontend web consume Firebase Auth/Firestore y llama a Functions para IA, planes y operaciones sensibles.  
Las claves BYOK se guardan en Secret Manager. Pagos se procesan vía Wompi y se reflejan en el perfil del usuario.

```mermaid
flowchart LR
  UI[Web App React] --> Auth[Firebase Auth]
  UI --> DB[Firestore]
  UI --> CF[Firebase Functions (Node.js)]
  CF --> AI[OpenAI]
  CF --> Pay[Wompi]
  CF --> Secrets[Secret Manager]
