# Modos de Falla

Existen varios modos de falla diferentes que pueden ocurrir en una base de datos, incluyendo:

- **Contención de Lectura**: Esto ocurre cuando varios clientes o procesos intentan leer datos desde la misma ubicación en la base de datos al mismo tiempo, lo que puede llevar a retrasos o errores.
- Contención de Escritura: Esto ocurre cuando varios clientes o procesos intentan escribir datos en la misma ubicación en la base de datos al mismo tiempo, lo que puede llevar a retrasos o errores.
- **Manada Rugiente**: Esto ocurre cuando un gran número de clientes o procesos intentan acceder al mismo recurso simultáneamente, lo que puede llevar al agotamiento del recurso y a un rendimiento reducido.
- **Cascada**: Esto ocurre cuando una falla en una parte del sistema de la base de datos provoca una reacción en cadena que lleva a fallas en otras partes del sistema.
- Bloqueo Mutuo: Esto ocurre cuando dos o más transacciones están esperando a que la otra libere un bloqueo en un recurso, lo que lleva a un punto muerto.
- **Corrupción**: Esto ocurre cuando los datos en la base de datos se corrompen, lo que puede llevar a errores o resultados inesperados al leer o escribir en la base de datos.
- **Falla de Hardware**: Esto ocurre cuando los componentes de hardware, como unidades de disco o memoria, fallan, lo que puede llevar a la pérdida o corrupción de datos.
- **Falla de Software**: Esto ocurre cuando los componentes de software, como el sistema de gestión de la base de datos o la aplicación, fallan, lo que puede llevar a errores o resultados inesperados.
- **Falla de Red**: Esto ocurre cuando la conexión de red entre la base de datos y el cliente se pierde, lo que puede llevar a errores o expiraciones al intentar acceder a la base de datos.
- **Ataque de Denegación de Servicio (DoS)**: Esto ocurre cuando un actor malicioso intenta abrumar la base de datos con solicitudes, lo que lleva al agotamiento de recursos y a un rendimiento reducido.
