# Pincelar (PWA)

Hospede esta pasta com HTTPS (por exemplo GitHub Pages). O app é o `index.html`.

## Desativar versões antigas (Firebase)
No `index.html`, procure `const APP={version:'1.0.0',configUrl:''}`.
1. No Firebase, crie um documento no Firestore, por exemplo `config/app`, com os campos:
   `minVersion` (texto, ex. "1.1.0"), `disabled` (booleano), `message` (texto) e `updateUrl` (texto, opcional).
2. Permita só leitura pública desse documento nas regras do Firestore.
3. Coloque em `configUrl` o endereço REST do documento:
   `https://firestore.googleapis.com/v1/projects/SEU_PROJETO/databases/(default)/documents/config/app`
4. A cada atualização, suba `APP.version` e aumente `minVersion` no Firebase: as versões antigas mostram a tela "Atualização necessária".
Se o aplicativo estiver sem internet, ele não bloqueia.

## Planos, login e anúncios
O menu "Conta e planos (prévia)" é só visual. Login, cobrança, limites por plano e anúncios reais ainda precisam ser ligados (Firebase Auth, loja de assinaturas e rede de anúncios).
