# nagual-evidencia en la constelación

Declaración de este repo para el grafo de proyectos de la casa (lo lee
el observatorio interno de la casa, que documenta el formato). Repo público:
solo superficies públicas.

| campo | valor |
|---|---|
| id | nagual-evidencia |
| clase | app |
| qué | la vitrina de nagual: evidencia de calibración firmada Ed25519 (`evidencia.json` + `publica.pem`), servida gratis y verificable offline |
| dónde | GitHub Pages → `https://nagual.ynt.codes` |
| servicio | `—` (páginas estáticas) |
| atiende | agentes y compradores que verifican antes de pagar; el contenido lo deposita la operación privada |
| contexto | `README.md` |
| visibilidad | público: `github:yvalenta/nagual-evidencia` |

## Aristas

| a | b | tipo | por | medición |
|---|---|---|---|---|
| nagual-evidencia | github | publica | GitHub Pages sirve `https://nagual.ynt.codes` (CNAME) | `http https://nagual.ynt.codes 200` |
| nagual-evidencia | nagual | mira | la evidencia que este repo sirve la firma y deposita nagual, que ya declara `publica` de su lado | `—` |
