# Docker

**Docker** es un proyecto de [código abierto](https://es.wikipedia.org/wiki/C%C3%B3digo_abierto) que automatiza el despliegue de [aplicaciones](https://es.wikipedia.org/wiki/Aplicaci%C3%B3n_inform%C3%A1tica) dentro de [contenedores de software](https://es.wikipedia.org/wiki/Contenedores_de_software), proporcionando una capa adicional de abstracción y automatización de virtualización de aplicaciones en múltiples sistemas operativos.[1](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-SYS-CON_Media-1) Docker utiliza características de aislamiento de recursos del [kernel Linux](https://es.wikipedia.org/wiki/N%C3%BAcleo_Linux), tales como [cgroups](https://es.wikipedia.org/w/index.php?title=Cgroups&action=edit&redlink=1) y [espacios de nombres (namespaces)](https://es.wikipedia.org/wiki/Espacio_de_nombres) para permitir que "contenedores" independientes se ejecuten dentro de una sola instancia de Linux, evitando la sobrecarga de iniciar y mantener [máquinas virtuales](https://es.wikipedia.org/wiki/M%C3%A1quina_virtual).[2](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-2)

El soporte del kernel Linux para los espacios de nombres aísla la vista que tiene una aplicación de su entorno operativo,[3](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-3) incluyendo árboles de proceso, red, ID de usuario y sistemas de archivos montados, mientras que los cgroups del kernel proporcionan aislamiento de recursos, incluyendo la CPU, la memoria, el bloque de E/S y de la red. Desde la versión 0.9, Docker incluye la [biblioteca](https://es.wikipedia.org/wiki/Biblioteca_(inform%C3%A1tica)) libcontainer como su propia manera de utilizar directamente las facilidades de virtualización que ofrece el kernel Linux, además de utilizar las interfaces abstraídas de virtualización mediante [libvirt](https://es.wikipedia.org/w/index.php?title=Libvirt&action=edit&redlink=1), [LXC](https://es.wikipedia.org/wiki/LXC) (Linux Containers) y [systemd-nspawn](https://es.wikipedia.org/wiki/Systemd).[4](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-zdnet-7000030397-4)[5](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-5)[6](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-docker-blog-201403-6)

De acuerdo con la firma analista de la industria 451 Research, "Docker es una herramienta que puede empaquetar una aplicación y sus dependencias en un contenedor virtual que se puede ejecutar en cualquier servidor Linux. Esto ayuda a permitir la flexibilidad y portabilidad en donde la aplicación se puede ejecutar, ya sea en las instalaciones físicas, la [nube](https://es.wikipedia.org/wiki/Computaci%C3%B3n_en_la_nube) pública, nube privada, etc."[7](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-Linux-7)

## Resumen[[editar](https://es.wikipedia.org/w/index.php?title=Docker_(software)&action=edit&section=1)]

Docker puede utilizar diferentes interfaces para acceder a las capacidades de virtualizacion del kernel Linux.

!https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/Docker-linux-interfaces.svg/600px-Docker-linux-interfaces.svg.png

Docker implementa una [API](https://es.wikipedia.org/wiki/Interfaz_de_programaci%C3%B3n_de_aplicaciones) de alto nivel para proporcionar contenedores livianos que ejecutan procesos de manera aislada.[8](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-infoq-201303-8)

Construido sobre las facilidades proporcionadas por el [kernel Linux](https://es.wikipedia.org/wiki/N%C3%BAcleo_Linux) (principalmente cgroups y namespaces), un contenedor Docker, a diferencia de una máquina virtual, no requiere incluir un sistema operativo independiente.[7](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-Linux-7) En su lugar, se basa en las funcionalidades del kernel y utiliza el aislamiento de recursos (CPU, la memoria, el bloque E / S, red, etc.) y namespaces separados para aislar la vista de una aplicación del sistema operativo. Docker accede a la virtualización del kernel Linux ya sea directamente a través de la biblioteca libcontainer (disponible desde Docker 0.9), o indirectamente a través de [libvirt](https://es.wikipedia.org/w/index.php?title=Libvirt&action=edit&redlink=1), [LXC](https://es.wikipedia.org/wiki/LXC) o [systemd-nspawn](https://es.wikipedia.org/wiki/Systemd#NSPAWN). [6](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-docker-blog-201403-6)[9](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-infoq-201403-9)

Mediante el uso de contenedores, los recursos pueden ser aislados, los servicios restringidos, y se otorga a los procesos la capacidad de tener una visión casi completamente privada del sistema operativo con su propio identificador de espacio de proceso, la estructura del sistema de archivos, y las interfaces de red. Contenedores múltiples comparten el mismo núcleo, pero cada contenedor puede ser restringido a utilizar solo una cantidad definida de recursos como CPU, memoria y E / S.

Usar Docker para crear y gestionar contenedores puede simplificar la creación de [sistemas altamente distribuidos](https://es.wikipedia.org/wiki/Computaci%C3%B3n_distribuida), permitiendo que múltiples aplicaciones, las tareas de los trabajadores y otros procesos funcionen de forma autónoma en una única máquina física o en varias máquinas virtuales. Esto permite que el despliegue de nodos se realice a medida que se dispone de recursos o cuando se necesiten más nodos, lo que permite una [plataforma como servicio](https://es.wikipedia.org/wiki/Computaci%C3%B3n_en_la_nube#Plataforma_como_servicio) (PaaS - Platform as a Service) de estilo de despliegue y ampliación de los sistemas como [Apache Cassandra](https://es.wikipedia.org/wiki/Apache_Cassandra), [MongoDB](https://es.wikipedia.org/wiki/MongoDB) o [Riak](https://es.wikipedia.org/w/index.php?title=Riak&action=edit&redlink=1). Docker también simplifica la creación y el funcionamiento de las tareas de carga de trabajo o las colas y otros sistemas distribuidos. [10](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-CloudAve-10)[11](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-Iron.io-11)

### Integración[[editar](https://es.wikipedia.org/w/index.php?title=Docker_(software)&action=edit&section=2)]

Docker se puede integrar con diferentes herramientas de infraestructura, como [Amazon Web Services](https://es.wikipedia.org/wiki/Amazon_Web_Services),[12](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-12) [Ansible](https://es.wikipedia.org/wiki/Ansible_(software)),[13](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-13) [Cfengine](https://es.wikipedia.org/w/index.php?title=CFEngine&action=edit&redlink=1),[14](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-14) [Chef](https://es.wikipedia.org/w/index.php?title=Chef_(software)&action=edit&redlink=1),[15](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-15) [Google Cloud Platform](https://es.wikipedia.org/wiki/Google_Cloud_Platform),[16](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-16) [DigitalOcean](https://es.wikipedia.org/wiki/DigitalOcean),[17](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-17) [IBM Bluemix](https://es.wikipedia.org/wiki/Bluemix),[18](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-18) [Jelastic](https://en.wikipedia.org/wiki/Jelastic),[19](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-19) [Jenkins](https://es.wikipedia.org/wiki/Jenkins),[20](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-20) [Microsoft Azure](https://es.wikipedia.org/wiki/Microsoft_Azure),[21](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-21) [OpenStack](https://es.wikipedia.org/wiki/OpenStack) Nova,[22](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-22) [OpenSVC](https://es.wikipedia.org/w/index.php?title=OpenSVC&action=edit&redlink=1),[23](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-23) [Puppet](https://es.wikipedia.org/wiki/Puppet_(software)),[24](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-24) [Salt](https://en.wikipedia.org/wiki/Salt_(software)),[25](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-25) y [Vagrant](https://es.wikipedia.org/wiki/Vagrant_(software)).[26](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-26)

El proyecto Cloud Foundry Diego integra Docker con [Cloud Foundry](https://es.wikipedia.org/wiki/Cloud_Foundry) PaaS.[27](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-27)

El proyecto GearD tiene como objetivo integrar Docker en el de Red Hat [OpenShift](https://es.wikipedia.org/wiki/OpenShift) Origin PaaS. [28](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-28)

En respuesta a la disponibilidad de estas integraciónes, la plataforma de monitoreo, [Datadog](https://en.wikipedia.org/wiki/Datadog), desarrolló un reportaje sobre la tasa de adopción de los servicios de Docker por 7 000 empresas con infraestructuras basadas en la nube.[29](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-29)[30](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-30)

## Historia[[editar](https://es.wikipedia.org/w/index.php?title=Docker_(software)&action=edit&section=3)]

Solomon Hykes comenzó Docker como un proyecto interno dentro dotCloud,[31](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-31) empresa enfocado a una plataforma como un servicio (PaaS),[32](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-32) con las contribuciones iniciales de otros ingenieros de dotCloud, incluyendo Andrea Luzzardi y Francois-Xavier Bourlet. Jeff Lindsay también participó como colaborador independiente. Docker representa una evolución de la tecnología patentada de dotCloud, que es a su vez construida sobre proyectos de código abierto anteriores como Cloudlets.

Docker fue liberado como código abierto en marzo de 2013.[8](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-infoq-201303-8) El 13 de marzo de 2014, con el lanzamiento de la versión 0.9, Docker dejó de utilizar LXC como el entorno de ejecución por defecto y lo reemplazó con su propia biblioteca, libcontainer, escrito en *[Go](https://es.wikipedia.org/wiki/Go_(lenguaje_de_programaci%C3%B3n))*.[4](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-zdnet-7000030397-4)[9](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-infoq-201403-9) El 13 de abril de 2015, el proyecto tenía más de 20 700 estrellas de [GitHub](https://es.wikipedia.org/wiki/GitHub) (haciéndolo uno de los proyectos con más estrellas de GitHub, en 20.ª posición), más de 4 700 [bifurcaciones (*forks*)](https://es.wikipedia.org/wiki/Bifurcaci%C3%B3n_(desarrollo_de_software)), y casi 900 colaboradores.[33](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-GitHub-33)

Un análisis en 2018 mostró las siguientes organizaciones como las principales contribuyentes de Docker: [Red Hat](https://es.wikipedia.org/wiki/Red_Hat) (mayores contribuyentes, aún más que el equipo de Docker en sí), el equipo de Docker, [Microsoft](https://es.wikipedia.org/wiki/Microsoft), [IBM](https://es.wikipedia.org/wiki/IBM), [Google](https://es.wikipedia.org/wiki/Google), [Cisco Systems](https://es.wikipedia.org/wiki/Cisco_Systems) y [Amadeus IT Group](https://es.wikipedia.org/wiki/Amadeus_IT_Group).[34](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-34)

El 29 de julio de 2020 se dio a conocer la existencia de Doki, un malware que corre en el sistema operativo Linux que tiene por finalidad infectar la API de los contenedores Docker mal configurados. Algunas de sus acciones son las siguientes:[35](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-35)

- Crea URL única con vidas cortas para descargar payloads durante el ataque.
- Ha sido creado para ejecutar comandos recibidos desde sus operadores.
- Usa la biblioteca TLS para funciones criptograficas.

### Colaboración[[editar](https://es.wikipedia.org/w/index.php?title=Docker_(software)&action=edit&section=4)]

- El 23 de julio de 2013, dotCloud Inc., la entidad comercial detrás de Docker, anunció que el ex CEO de [Gluster](https://es.wikipedia.org/w/index.php?title=Gluster&action=edit&redlink=1) y [Plaxo](https://es.wikipedia.org/wiki/Plaxo), Ben Golub se había unido a la compañía, citando Docker como el principal foco de la empresa en adelante.
    
    [36](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-GigaOM-36)
    
- El 19 de septiembre de 2013, [Red Hat](https://es.wikipedia.org/wiki/Red_Hat) y Docker anunciaron una colaboración significativa alrededor de [Fedora](https://es.wikipedia.org/wiki/Fedora_(distribuci%C3%B3n_Linux)), [Red Hat Enterprise Linux](https://es.wikipedia.org/wiki/Red_Hat_Enterprise_Linux) y [OpenShift](https://es.wikipedia.org/wiki/OpenShift).
    
    [37](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-37)
    
- El 22 de enero de 2014, Docker anunció que había completado una ronda de [capital de riesgo](https://es.wikipedia.org/wiki/Capital_riesgo) Serie B de US$ 15.000.000, liderada por [Greylock Partners](https://es.wikipedia.org/w/index.php?title=Greylock_Partners&action=edit&redlink=1).
    
    [38](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-38)
    
- El 23 de julio de 2014, Docker adquirió la Orchard, hacedores de Fig.
    
    [39](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-39)
    
- El 16 de septiembre de 2014, Docker anunció que había completado una ronda de US$ 40 M de la Serie C, liderado por [Sequoia Capital](https://es.wikipedia.org/wiki/Sequoia_Capital).
    
    [40](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-40)
    
- El 15 de octubre de 2014, [Microsoft](https://es.wikipedia.org/wiki/Microsoft) anunció la integración del motor acoplable a la liberación de [Windows Server 2016](https://es.wikipedia.org/wiki/Windows_Server_2016) y soporte nativo para el rol de cliente Docker en Windows.
    
    [41](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-41)
    
    [42](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-42)
    
- El 4 de diciembre de 2014, [IBM](https://es.wikipedia.org/wiki/IBM) anunció una alianza estratégica con Docker que permite a las empresas la más eficiente, rápida y rentable generación y ejecución de la próxima generación de aplicaciones en la nube de IBM ("IBM Cloud").
    
    [43](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-43)
    
- El 7 de junio de 2016, [HPE](https://es.wikipedia.org/wiki/Hewlett_Packard_Enterprise) ([Hewlett Packard Enterprise](https://es.wikipedia.org/wiki/Hewlett_Packard_Enterprise)) anunció una alianza empresarial mundial con Docker que incluye una aproximación conjunta al mercado, venta de soluciones, ingeniería, soporte, servicios e intercambio de conocimientos para ayudar a los clientes a transformar y modernizar sus centros de datos, así como beneficiarse de un entorno de desarrollo más ágil. En el corazón de esta alianza está el programa HPE Docker Ready Server, único en la industria de los servidores, lo que garantiza que los servidores de HPE llevarán acoplado Docker y contarán con soporte comercial.
    
    [44](https://es.wikipedia.org/wiki/Docker_(software)#cite_note-44)
