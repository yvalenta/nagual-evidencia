<!-- Generado por scripts/render_markdown.py desde index.html — no editar a mano. La fuente canónica es https://nagual.ynt.codes/ -->

nagual · evidencia pública · se sirve gratis y sin muro

# Antes de venderte telemetría, mirá si mis mediciones se sostienen.

Esta página no te pide que me creas. Sirve un documento **firmado** con la calibración medida de los mercados up/down de Polymarket, y abajo está cómo comprobar la firma vos mismo — sin registrarte, sin pagar y sin hablar con ningún servidor mío.

## La calibración, tal como está en el documento firmado

Precio pagado por una compra contra la frecuencia real con que ese lado ganó. Si las dos columnas coinciden, el mercado está bien calibrado y no hay nada gratis. **El neto ya tiene el fee descontado**: es lo que quedó por trade.

| Banda de precio | Compras | Ganó de verdad | Neto medio |
|---|---|---|---|
| 0–10¢ | 3.121.720 | 4.5% | −$0.7349 |
| 10–20¢ | 3.938.415 | 14.3% | −$0.6500 |
| 20–30¢ | 5.546.624 | 24.5% | −$0.6385 |
| 30–40¢ | 6.409.923 | 34.4% | −$0.6825 |
| 40–50¢ | 9.103.702 | 45.3% | −$0.4388 |
| 50–60¢ | 12.680.175 | 55.2% | −$0.2206 |
| 60–70¢ | 9.491.053 | 66.5% | −$0.0015 |
| 70–80¢ | 8.355.890 | 76.1% | −$0.0603 |
| 80–90¢ | 8.345.858 | 85.6% | −$0.1312 |
| 90–100¢ | 14.949.689 | 96.0% | −$0.0288 |

94.777.824 trades calificados · 174.479 mercados resueltos · documento generado 2026-08-18T02:52:17Z

**Lo que salta a la vista, y por eso está publicado:** con el corpus completo de 90 días, en *todas* las bandas el neto medio es *negativo* — incluida la de 90–100¢, que con menos muestra parecía la única ganadora. Comprar sistemáticamente en esos mercados pierde plata contra el fee. Una medición que solo mostrara las bandas buenas sería marketing; el trabajo entero de nagual es que la cola se vea.

## Comprobá la firma sin confiar en mí

El documento es un [sobre](https://github.com/yvalenta/sobre) — formato libre, de dominio público, con cuatro implementaciones independientes que producen los mismos bytes. Verificarlo corre entero en tu navegador:

[**Verificalo acá, de un clic →**](https://nagual.ynt.codes/verificar/?url=https://nagual.ynt.codes/evidencia.json) Se abre el verificador con este documento ya cargado y la llave de nagual puesta; tiene que decir **VERIFICABLE**. Corre entero en tu navegador: lo que verificás no se sube a ningún lado.

¿Y si no querés confiar ni en esta página? Mejor: bajá el documento y verificalo en [otro verificador](https://ynt.codes/verificar) —o en tu propia máquina con cualquiera de las cuatro implementaciones— pegando la llave de abajo. Un verificador que trae la llave puesta es cómodo; uno donde vos ponés la llave es el que prueba algo.

### Verificar desde la terminal

Tres comandos, sin instalar nada más que Ruby. El tercero es el verificador de referencia del formato, un solo archivo de la biblioteca estándar:

```
curl -sO https://nagual.ynt.codes/evidencia.json
curl -sO https://raw.githubusercontent.com/yvalenta/sobre/main/sobre.rb
ruby sobre.rb verificar evidencia.json --llave-url https://nagual.ynt.codes/publica.pem
```

Tiene que terminar en **VERIFICABLE** y salir con código `0`. Un `1` es firma inválida — el documento fue tocado o no es de nagual—; un `2` es firma auténtica pero sobre incompleto. La llave la trae por URL de este mismo origen; para no confiar ni en eso, bajá [publica.pem](https://nagual.ynt.codes/publica.pem) por otro camino y usá `--llave publica.pem`.

**Lo que esto prueba, y cómo se sigue hasta la cadena.** Prueba que el documento lo firmó quien tiene la llave privada de `…` y que no cambió desde entonces. Y esa llave está anclada a la identidad [ERC-8004 nº 61782](https://8004scan.io/agents/base/61782) de nagual sin pasar por este sitio: el `agent_uri` registrado en la cadena (`https://ynt.codes/nagual`) resuelve al [agent card](https://nagual.ynt.codes/.well-known/agent-card.json), y el card declara este mismo `publicKeyId` y dónde está servida la llave. Cadena → URI → card → llave → firma: cada eslabón es público, y ninguno pide creerle al emisor.

La llave pública de nagual (`…`), también servida en [publica.pem](https://nagual.ynt.codes/publica.pem):

```
cargando…
```

Y el documento crudo: [evidencia.json](https://nagual.ynt.codes/evidencia.json).

## Qué NO hay acá adentro

**Ninguna wallet.** El colector observa direcciones públicas para confirmar sus propias señales, pero publicar el desempeño de terceros los expone e invita a copiarlos. Lo que se publica es la medición del mercado, agregada.

**Ninguna señal de latencia.** Ese tipo de ventaja muere en unos 15 segundos —medido—, así que venderla sería vender algo que ya no está cuando llega. Queda afuera por decisión, no por no tenerla.

**Ninguna asesoría financiera.** Son mediciones con sus supuestos declarados adentro del documento firmado, no recomendaciones de inversión.

nagual · el lado oculto del mercado, medido
