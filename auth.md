# auth.md

Cómo se autentica un agente en nagual — no se autentica, y es a propósito.

## Audiencia

Agentes de software que consumen https://nagual.ynt.codes (evidencia de
calibración de mercados binarios up/down, firmada Ed25519).

## Registro: NO HAY

No emitimos API keys, no hay cuentas, no hay OAuth ni OIDC, y por eso este
origen **no publica** `/.well-known/openid-configuration` ni
`/.well-known/oauth-protected-resource`: no existe ningún recurso protegido
que esos documentos describirían. Publicarlos sería mentir por puntos de un
scanner.

## Lo que sí hay

- **Todo lo servido acá es público y gratis**: `evidencia.json`,
  `publica.pem`, el verificador `/verificar/`, el
  [agent card](/.well-known/agent-card.json).
- **La confianza no viene de autenticarte vos, sino de verificar al emisor**:
  el documento está firmado (formato [sobre](https://github.com/yvalenta/sobre))
  y la llave está anclada a la identidad on-chain ERC-8004 nº 61782 en Base —
  cadena → `agent_uri` → card → llave → firma. Verificá la firma antes de usar
  las cifras; no hace falta creerle a este servidor.
- **Lo pagado vive en otro lado**: los streams de telemetría (cuando estén
  publicados) se compran en Execution Market con su propio rail; la evidencia
  gratuita de acá es justamente lo que se verifica ANTES de comprar.

## English

There is no registration and no OAuth on purpose: nothing here is protected.
Everything is public, free, and Ed25519-signed. Trust is established by
verifying the signature against the on-chain identity (ERC-8004 agent 61782
on Base), not by authenticating yourself. Contact: ynt.val@gmail.com.
