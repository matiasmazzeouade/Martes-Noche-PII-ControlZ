# Sistema de Gestión de Impresión

El sistema funciona como el intermediario entre los usuarios y una impresora. Su función principal consta en administrar las solicitudes de impresión de manera ordenada, evitando que los documentos se mezclen o se pierdan al momento que varias personas envien archivos al mismo tiempo. EL contrato elegido es tipo "Cola", dado que las solicitudes entrantes se almacenan y al momento de ejecutar las impresiones van saliendo en orden, usando de esta manera el concepto "FIFO: First in, First Out"

## ACTIVIDAD 1

### Alto Nivel (Usuario) Métodos:
1-Inicializar (crear cola)
2-imprimir  
3-escanear  
4-fotocopiar  

### Bajo Nivel (Implementadores) Métodos:
1-agregarACola  
2-eliminarCola  
3-modificarPosicion  
4-verCantidadDeDocumentos  
5-cancelarDocumento  

## ACTIVIDAD 2

### Estrategia 1:
Arreglo con Punteros de Inicio y FinEs la más eficiente para una impresora. Usamos variables externas para saber dónde está el primer documento y dónde agregar el próximo.  
Rendimiento: Muy rápido. No importa si hay 2 o 200 archivos esperando, agregar uno nuevo a la cola es instantáneo.  
Uso: Es la ideal para que el usuario no note demoras al enviar su archivo.

### Estrategia 2:
Inicio Fijo en Posición. En esta estrategia, cada vez que una hoja termina de imprimirse y sale de la cola, todos los demás documentos deben "moverse" una posición hacia adelante en la memoria para que el siguiente siempre esté en el índice 0.  
Rendimiento: Muy ineficiente. Si la cola está llena, la impresora pierde tiempo moviendo datos de lugar en vez de procesar el siguiente trabajo.  
Uso: No se recomienda para sistemas con mucho tráfico de documentos.

### Estrategia 3:
Cantidad de Archivos en el Índice 0En esta opción, la primera celda del arreglo guarda el número total de documentos pendientes.  
Rendimiento: Rápido, similar a la Estrategia 1.  
Punto Crítico: Sacrificamos espacio. Si la memoria de la impresora permite 10 archivos, solo podremos guardar 9, ya que el primer lugar lo ocupa el contador. Además, hay que tener cuidado de no mezclar el "número de archivos" con los "datos del archivo".
