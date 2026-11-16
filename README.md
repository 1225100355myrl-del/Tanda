# Tanda Doloreña — Evidencias de funcionamiento (TDD)

Proyecto de ahorro rotativo vecinal (tanda) en Flutter, construido con TDD.

## Cómo ejecutar

```bash
flutter pub get
flutter test      # pruebas de lógica
flutter run       # app en el emulador
```

## Reglas de negocio protegidas

1. Cada participante aporta como máximo una vez por ronda.
2. Solo puede aportar quien pertenece a la tanda.
3. La ronda solo se cierra cuando todos aportaron.
4. Al cerrar, el turno va a quien corresponde según el orden acordado y se avanza.
5. Al terminar la tanda no se aceptan más aportaciones.

---

## Parte A — Pruebas

### 1. Estructura del proyecto
Carpetas `lib/` (`logica`, `modelos`, `presentation`, `main.dart`) y `test/`.

![Estructura del proyecto](capturas/01_estructura_proyecto.png)

### 2. `flutter test` en verde
Todas las pruebas pasan (12 en total).

![flutter test](capturas/02_flutter_test_verde.png)

---

## Parte B — App en el emulador

### 4. Pantalla inicial
Ronda 1 de 4, barra en 0 y Ana resaltada como turno actual.

![Pantalla inicial](capturas/04_pantalla_inicial.png)

### 5. Aportaciones parciales
Ana y Beto ya aportaron; la barra avanza al 50 %.

![Aportaciones parciales](capturas/05_aportaciones_parciales.png)

### 6. No se puede cerrar la ronda sin todas las aportaciones
Aviso "Todavía faltan vecinos por aportar."

![Cierre sin todos](capturas/06_cierre_sin_todos.png)

### 7. Ronda completa
Los 4 vecinos aportaron.

![Ronda completa](capturas/07_ronda_completa.png)

### 8. Animación del beneficiario
Diálogo "¡Turno entregado!" al cerrar la ronda.

![Animación del beneficiario](capturas/08_animacion_beneficiario.png)

### 9. Ronda 2
El turno avanzó: Ana con ✓ y Beto como turno actual.

![Ronda 2](capturas/09_ronda_2.png)

### 10. Ronda 3 — beneficiario
Se respeta el orden de turnos.

![Ronda 3](capturas/10_ronda_3_beneficiario_beto.png)

### 11. Tanda terminada
Todos recibieron su turno y los botones quedan deshabilitados.

![Tanda terminada](capturas/11_tanda_terminada.png)

---

## Checklist del proyecto

- [x] Cada regla de negocio tiene su propia prueba
- [x] El orden de turnos se respeta exactamente como fue definido
- [x] La tanda rechaza aportaciones después de terminar
- [x] La interfaz no decide quién recibe el turno; se lo pregunta a `ServicioTanda`
- [x] La prueba de integración recorre una tanda completa

## Estructura

```
lib/
  modelos/        participante.dart, tanda.dart, cierre_ronda.dart
  logica/         resultado_aportacion.dart, resultado_cierre.dart, servicio_tanda.dart
  presentation/   tanda_screen.dart
  main.dart
test/
  servicio_tanda_test.dart
capturas/         evidencias
```
