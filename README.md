# Billetera Digital - Caso 2 (Angular)

Proyecto de la T1 del curso Soluciones Web y Aplicaciones Distribuidas (UPN).

La misma billetera del Caso 1, pero en Angular y con dos componentes. `BilleteraComponent` es el padre: guarda el saldo y la lista de movimientos. `NuevoMovimientoComponent` es el hijo: tiene el formulario, valida el monto y le avisa al padre cuando el movimiento es válido. El hijo nunca cambia el saldo por su cuenta.

## Versiones

- Node.js 22.12.0
- npm 10.9.0
- Angular y Angular CLI 21.2
- Bootstrap 5.3.3

## Cómo ejecutarlo

Para descargar el proyecto:

```
git clone https://github.com/Jordy1094/billetera-angular.git
cd billetera-angular
```

Luego, desde la carpeta del proyecto:

```
npm install
ng serve
```

`npm install` solo hace falta la primera vez. Si no tienes Angular CLI instalado, usa `npm start` en lugar de `ng serve`.

Luego abre http://localhost:4200/

## Dónde está cada cosa

```
src/app/
  app.ts, app.html                         solo contienen a la billetera
  movimiento.ts                            tipo de dato Movimiento
  billetera/billetera.ts y .html           componente padre
  nuevo-movimiento/nuevo-movimiento.ts y .html   componente hijo
```

- El saldo se muestra con interpolación y el historial con `@for`.
- Si no hay movimientos, un `@if` muestra "Aún no hay movimientos".
- El hijo recibe el saldo con `input()` y envía el movimiento con `output()`.
- Cuando el monto no es válido, el error sale con `@if` y el botón se desactiva con `[disabled]`.

## Pruebas que hicimos

Todas empiezan con saldo de S/ 250.00 y el historial vacío.

1. Recarga de S/ 100.00: el saldo queda en S/ 350.00.
2. Gasto de S/ 50.00: el saldo queda en S/ 300.00 y el gasto sale primero en la lista.
3. Gasto de S/ 400.00: sale "Saldo insuficiente para realizar el gasto" y el botón se desactiva.
4. Monto en cero, negativo o vacío: sale el error y no se puede registrar.
