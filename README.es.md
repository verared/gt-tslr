# Tiempo Solar Local Real (EXPERIMENTAL)

Parte de la suite de referencia **Gerarion** (verared/gerarion `v3.3.0`,
Gerarion Universal Standard). Este directorio es un **paquete de
exportación** listo para publicarse (o consumirse) como repositorio
satélite `verared/gt-tslr`; conserva las rutas relativas del repositorio
base para componer módulos.

## El problema único que resuelve

Verificación astronómica opcional para evidencia forense de Nivel 3. PERFIL EXPERIMENTAL: separado del núcleo normativo; sin implementación de referencia todavía. La estructura inicial está lista para desarrollo independiente.

## Estado normativo

- **EXPERIMENTAL** (`maturity: experimental`) — línea base `v3.3.0` (aritmética y vectores
  congelados: GUS v3.0.0).
- Especificación(es) incluida(s): `docs/specs/TSLR.es.md`, `docs/specs/TSLR.en.md`
- Manifiesto de integridad verificable: [`EXPORT-MANIFEST.json`](EXPORT-MANIFEST.json)
- Matriz oficial de compatibilidad: [`COMPATIBILITY.md`](https://github.com/verared/gerarion/blob/v3.3.0/COMPATIBILITY.md)

## Las 5 Garantías de Distribución

| # | Garantía | Mecanismo verificable |
|---|---|---|
| 1 | **Integridad SHA-256** | Mapa `files` en [`EXPORT-MANIFEST.json`](EXPORT-MANIFEST.json) verificado con `--verify-existing`. |
| 2 | **Procedencia declarada** | Campos `source_repo`, `source_tag` (`v3.3.0`) y `source_commit` (SHA-1 de 40 caracteres). |
| 3 | **Autenticidad de publicación** | Firma Ed25519 separada `EXPORT-MANIFEST.json.sig` verificable con `--trusted-pub-key` (sin autorreferencia). |
| 4 | **Reproducibilidad** | Re-exportación determinista bit a bit desde el mismo `--source-commit`. |
| 5 | **Conformidad funcional** | Suite de vectores normativos CC0 e integración cruzada en C11, Python y JavaScript. |

## Dependencias

- `gt-core` (*verared/gt-core*): tipos base y servicios del núcleo.
Base común: `verared/gerarion` `v3.3.0`.

## Contenido

- `EXPORT-MANIFEST.json`
- `LICENSE`
- `NOTICE`
- `docs/specs/TSLR.en.md`
- `docs/specs/TSLR.es.md`
- `src/.gitkeep`
- `tests/.gitkeep`
- `vectors/.gitkeep`

## Uso offline

No requiere red, cuentas, registro de paquetes ni frameworks:

```bash
python3 -c 'import sys; sys.path.insert(0, "src"); import gerarion'
```

## Verificación

Con Python ≥ 3.9 y `reuse` instalado:

```bash
reuse lint                                    # licencias al 100 %
# (sin código compilable en este módulo)
```

Desde `verared/gerarion`, la integridad y (opcionalmente) la autenticidad de firma separada se verifican con:

```bash
python3 tools/export_module.py --verify-existing /ruta/a/gt-tslr
# Con verificación criptográfica de EXPORT-MANIFEST.json.sig:
python3 tools/export_module.py --verify-existing /ruta/a/gt-tslr --trusted-pub-key /ruta/a/release-pub.pem
```

## Contrato de sincronización con `verared/gerarion`

Este paquete es **generado, no editado a mano**: se regenera byte a
byte desde `verared/gerarion v3.3.0` con
`python3 tools/export_module.py --module gt-tslr --out <dir>`. La fuente
de verdad normativa (especificaciones, vectores CC0, núcleos de
referencia de las tres plataformas y la batería completa) permanece en
`verared/gerarion`; los satélites `verared/gt-tslr` la consumen y no forkean la
aritmética. Las actualizaciones fluyen regenerando la exportación desde
un tag del repositorio base; nunca editando los archivos exportados.
