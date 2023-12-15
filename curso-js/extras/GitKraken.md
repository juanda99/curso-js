## Problemas con Git

- Yo hago cambios
git pull (traeis cambios)

- Vosotros haceis cambios
git add -A
git commit -m "mensaje"
git push (servidor)


Cogeis mis cambios:
git pull

Problemas:
- Vosotros también habéis hecho cambios en los mismos ficheros
	- Debemos hacer un commit previo nosotros  para tener "marcha atrás"
- Qué pasa cuando los dos cambiamos el mismo fichero
	- git config pull.rebase false


