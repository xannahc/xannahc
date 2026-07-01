## Hi there 👋

El bug que se escondía en la conversión de moneda: cómo arreglamos el cálculo del subtotal
Contexto
Entre octubre y diciembre de 2024 formé parte de un equipo de trabajo (junto a compañeras de curso) desarrollando una tienda online como parte de un desafío práctico. El proyecto incluía funcionalidades típicas de e-commerce: catálogo de productos, carrito de compras, checkout, perfil de usuario y cálculo de precios. Trabajamos de forma colaborativa usando Git y GitHub, con Pull Requests para revisar e integrar cada cambio al repositorio principal.
Una de las partes críticas del carrito de compras era el cálculo del subtotal: la app debía sumar los productos agregados y convertir su valor a pesos uruguayos (UYU) para mostrarle al usuario el monto correcto antes de pagar.
Problema
La primera versión de la función de subtotal se implementó y funcionó, pero al poco tiempo detectamos que el monto mostrado no era el correcto: el subtotal no reflejaba bien lo que había en el carrito. Después de revisar el código con el equipo, identificamos que el problema estaba en el conversor de moneda: la lógica que transformaba los precios a pesos uruguayos tenía un error, y eso arrastraba un cálculo incorrecto a toda la función del subtotal.
No fue un error que se detectara y resolviera en un solo intento: tuvimos que pasar por varias iteraciones antes de dar con la causa real del problema.
Acciones
Primer intento: implementamos la función de subtotal (funcionalidad básica de suma de productos en el carrito).
Primer reajuste: al notar que el valor no cuadraba, hicimos un primer ajuste rápido, pero el problema persistía parcialmente.
Revisión en equipo: nos sentamos a revisar juntas el código función por función, en lugar de seguir "parchando" a ciegas. Ahí fue donde detectamos que el error específico estaba en el conversor de pesos, no en la lógica de suma en sí.
Corrección definitiva: reescribí la función del conversor de moneda para que operara correctamente, y de paso integré la conversión directamente al flujo del subtotal, para que el carrito mostrara siempre el monto correcto en pesos uruguayos.
Validación: probamos con distintos productos y cantidades en el carrito para confirmar que el subtotal ahora coincidía con lo esperado antes de fusionar el cambio a la rama principal.
Este proceso funcionó como una especie de post-mortem informal: en vez de simplemente "arreglar y avanzar", nos detuvimos como equipo a entender por qué fallaba, en lugar de solo tratar el síntoma.
Aprendizajes
Un síntoma visible no siempre indica la causa raíz. El subtotal se veía mal, pero la causa real estaba un nivel más abajo, en el conversor de moneda.
Revisar en equipo antes de "parchar" ahorra tiempo. Los primeros ajustes individuales no resolvieron el problema de fondo; la revisión conjunta sí.
Las funciones que manejan dinero necesitan testeo extra. Desde entonces, priorizamos probar con varios casos (distintas cantidades, distintos productos) antes de dar por cerrada una función relacionada a cálculos o pagos.
Los Pull Requests ayudan a que el error no pase desapercibido. Al revisar el código en PR antes de fusionarlo, el equipo pudo detectar y comentar sobre el problema en vez de que llegara sin revisión a la rama principal.
Evidencia de control de versiones
Pull Request donde se detecta y corrige el error del conversor y el cálculo del subtotal: #35 – "Nuevo arreglo función cálculo de subtotal" (3 nov 2024) Acceso a commit: https://github.com/LoanaNDS/workspace-inicial/commit/feb54164982b80af2ccf0fbc89566700c232e87e 

Intentos previos documentados en el historial: #32 – "Agregado de funcionalidad subtotal", #33 – "Reajuste subtotal", #34 – "Ajustes". Acceso al commit: https://github.com/LoanaNDS/workspace-inicial/commit/d8fecc8ba696abcbd7cd3d03da48b699bbc91816 - https://github.com/LoanaNDS/workspace-inicial/commit/b56a808dbfae01bb5841e10c94105033a5fa7149 


Repositorio: https://github.com/LoanaNDS/workspace-inicial.git 
Reflexión sobre feedback radicalmente sincero
Durante este proceso, el momento clave no fue el primer parche que intenté sola, sino cuando el equipo se sentó a revisar el código en conjunto y alguien señaló directamente que el problema no estaba donde yo pensaba, sino en el conversor. Esa observación fue directa y concreta, sin rodeos, pero se dio en un ambiente de confianza donde el objetivo era mejorar el producto, no señalar culpables.
Aplicar esa retroalimentación sin ponerme a la defensiva me permitió llegar a la causa real del problema mucho más rápido de lo que hubiera logrado sola. Aprendí que aceptar una corrección directa sobre mi propio código —en lugar de justificarlo— es lo que permite que el equipo avance de verdad.


