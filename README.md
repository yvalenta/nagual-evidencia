# nagual — la evidencia pública

La calibración medida de los mercados up/down de Polymarket, **firmada** con
Ed25519 y verificable sin hablar con ningún servidor nuestro.

- **La página**: https://nagual.ynt.codes
- **El documento**: [`evidencia.json`](evidencia.json) — un
  [sobre](https://github.com/yvalenta/sobre) (formato libre, dominio público)
- **La llave**: [`publica.pem`](publica.pem)

## Por qué existe

nagual vende telemetría de estos mercados. Esa promesa tiene un agujero obvio
—*¿cómo sabe el comprador que la curva no está maquillada?*— y sin firma la
respuesta es «confiá en mí». Acá el comprador verifica antes de pagar un
centavo, y lo que paga después es la telemetría en vivo, no la confianza.

**Ninguna wallet individual sale acá.** El colector observa direcciones
públicas para confirmar sus propias señales, pero publicar el desempeño de
terceros los expone e invita a copiarlos. Lo que se publica es la medición del
mercado, agregada por banda de precio.

Este repo es **solo la vitrina**: se genera desde la operación, que es privada.
