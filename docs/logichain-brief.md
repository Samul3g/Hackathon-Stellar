# PROJECT BRIEF: LogiChain API
**Solución de Liquidación Condicional y Garantía de Entregas mediante Blockchain e IoT**

## 1. Resumen Ejecutivo
LogiChain API es una infraestructura Web3/B2B diseñada para automatizar la resolución de disputas y la penalización por retrasos o desviaciones en servicios de entrega y logística (desde q-commerce como Uber Eats hasta e-commerce internacional como Temu o Amazon). Mediante el uso de la blockchain Stellar (Soroban), oráculos de ubicación y la firma criptográfica por hardware en smartphones (Secure Enclave), la plataforma ejecuta contratos inteligentes que ajustan automáticamente el costo del pedido o reembolsan al usuario sin intervención humana.

## 2. Definición del Problema
* **Pérdida de confianza y fricción en soporte:** El proceso actual para solicitar reembolsos por pedidos retrasados o perdidos requiere atención al cliente manual, generando costos operativos altos para las plataformas y frustración para los usuarios.
* **Fraude en la ubicación (GPS Spoofing):** Las aplicaciones actuales no pueden validar con certeza criptográfica si un repartidor realmente estuvo en la ubicación reportada o si utilizó software para alterar su ubicación GPS.
* **Altos costos de infraestructura Web3 previa:** Utilizar blockchains tradicionales (como Ethereum) para rastreo en tiempo real es inviable debido a las altas comisiones por transacción (gas fees).

## 3. Solución Propuesta
Una API REST/GraphQL que permite a las empresas de e-commerce y delivery integrar contratos inteligentes de custodia (escrow) y penalización en tiempo real:
1. **Monitoreo Criptográfico:** Registra las coordenadas GPS firmadas directamente por el chip de seguridad del teléfono (Apple Secure Enclave / Android KeyStore).
2. **Ejecución Automática:** El contrato inteligente en Soroban (Stellar) compara los datos recibidos contra la ruta y el tiempo pactados.
3. **Reembolsos/Descuentos dinámicos:** Si hay un retraso o desviación grave, la blockchain ejecuta automáticamente un reembolso parcial o total al cliente.

## 4. Objetivos del Proyecto
* Reducir a cero el costo de soporte manual para reclamos por entregas tardías en plataformas adheridas.
* Mantener los costos operativos blockchain en menos de $0.001 USD por pedido procesado.
* Proveer una API de integración "Plug & Play" que no requiera que las plataformas de delivery adapten su código a Web3 ni programen en Rust.

## 5. Arquitectura Técnica
[ App Repartidor / Smartphone ] -> Firma de coordenadas vía Secure Enclave
[ API Gateway (Node.js / Go) ] -> Oráculo de Validación
[ Blockchain Stellar (Soroban) ] -> Ejecución de reglas del contrato inteligente:
- En ruta y tiempo -> Liquidación 100% al repartidor/comercio
- Retraso leve -> Descuento automático (%) al usuario
- Desviación crítica -> Alerta de seguridad + Reembolso total

## 6. Métricas Clave y Parámetros
* **Infraestructura Blockchain:** Stellar Layer 1 (Smart Contracts en Soroban / Rust)
* **Costo por Transacción:** Aproximadamente $0.00001 - $0.0007 USD
* **Tiempo de Finalización:** 3 a 5 segundos por bloque
* **Seguridad Móvil:** Apple Secure Enclave / Android Hardware Keystore
* **Modelo de Entrega B2B:** API REST / Webhooks / SDKs para Flutter y React Native

## 7. Casos de Uso Iniciales
1. **Delivery Ultra-Local (Apps de Comida / Q-Commerce):** Reembolso progresivo automático si la entrega supera el tiempo estimado o el repartidor hace paradas no autorizadas.
2. **E-Commerce Internacional (Envíos Transfronterizos):** Liberación de pagos por hitos aduaneros y compensación automática si el paquete queda varado más días de lo estipulado.

## 8. Siguientes Pasos (Roadmap)
* [ ] Fase 1: Desarrollo del Smart Contract en Soroban (Rust) con reglas de tiempo, tolerancia geográfica y penalización.
* [ ] Fase 2: Creación del PoC (Prueba de Concepto) del SDK móvil para la firma criptográfica mediante el Secure Enclave del iPhone.
* [ ] Fase 3: Construcción del servicio de API Gateway y Oráculo de datos.
* [ ] Fase 4: Prueba piloto en la red de pruebas (Testnet) de Stellar simulando rutas de entrega reales.
