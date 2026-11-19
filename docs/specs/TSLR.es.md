# Especificación TSLR — Tiempo Solar Local Real (EXPERIMENTAL)

- **Estado: EXPERIMENTAL** — separado del núcleo normativo ·
  **Versión:** 1.0.0 · **Línea base:** GUS v3.1.1
- **Edición consolidada:** [`../spec/gus-3.0.0.md`](../spec/gus-3.0.0.md) (§9.6, Capa 3)
- **Licencia:** CC-BY-4.0 · Mantenida por: verared contributors

> **Este perfil NO forma parte de la garantía de conformidad del
> calendario ni de la marca canónica.** No existe implementación de
> referencia en este repositorio; la especificación declara el contrato
> para implementaciones futuras (p. ej. un repositorio satélite
> `gerarion-tslr`).

## 1. Alcance

Verificación astronómica opcional (Capa 3) para evidencia forense de
Nivel 3: posición solar calculada con efemérides, cuórum de nodos
maestros y perfil de integridad de los registros.

## 2. Reglas previstas

1. Posición solar (altitud/azimut) calculada con efemérides (DE440) y
   **`ephemeris_hash` obligatorio**: una actualización de la efeméride
   nunca invalida retroactivamente una firma anterior.
2. **Cuórum 3-de-4 Nodos Maestros** (Jerusalén 31.7683°N/35.2137°E,
   Sèvres (BIPM) 48.8292°N/2.2203°E, Santiago 33.4489°S/70.6693°O,
   Sídney 33.8688°S/151.2093°E): sin punto único de fallo de
   verificación.
3. **Protocolo polar** (|φ| > 66,5°): el cálculo por altura/azimut es
   degenerado en noches o días polares; el verificador degrada la marca
   a Nivel 2 y registra la condición.
4. **Invariantes de integridad:** monotonía de `tai_seconds`,
   consistencia ciclo/hora del observador, consistencia de día de
   semana (I-1), consistencia año↔TAI y verificabilidad de la efeméride
   declarada; logs con hash encadenado y doble sello
   (`gero_canonical` + `tai_seconds`) en eventos críticos.

## 3. Fuentes de verdad

Todavía ninguna: la spec es la fuente. Cualquier implementación futura
deberá publicar sus propios vectores CC0 y su batería reproducible.

## 4. Vectores aplicables

Ninguno todavía en este repositorio.

## 5. Madurez y límites

- **Experimental.** No forma parte de la garantía de conformancia.
- GUS no sustituye los controles de seguridad del sistema operativo, el
  aislamiento de hardware ni las mitigaciones de red: los cubre por
  fuera, nunca en su lugar.
- La verificación TSLR proporciona **detección determinista de
  manipulación** y trazabilidad; no afirmaciones de infalsificabilidad.

## 6. Referencias

- Sección 9.6 de la edición consolidada; `docs/spec/threat-model.md`.
