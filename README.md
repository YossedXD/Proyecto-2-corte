# Proyecto DevOps

Este proyecto tiene como propósito diseñar, implementar y analizar una infraestructura virtualizada y contenerizada orientada a entornos DevOps. A través de su desarrollo se integraron conceptos de administración de sistemas Linux, redes, virtualización, automatización y monitoreo de servicios.

---

## Infraestructura base

El entorno fue construido sobre una arquitectura centralizada, en la que una máquina virtual principal (Administrador), basada en **Debian**, se encargó de la gestión y monitorización del resto de las dependencias. Desde esta máquina se controlaron los servicios, métricas y configuraciones del sistema.

Cada una de las áreas de la organización se implementó dentro de su propio entorno virtual o contenedor, con su respectiva subred y funciones específicas:

- **Recursos Humanos:** desplegado sobre una máquina virtual con **Arch Linux**, utilizada principalmente para tareas administrativas y de gestión de usuarios.  
- **Tecnología:** implementado mediante **Rocky Linux** como máquina virtual, sirviendo de entorno de desarrollo y pruebas de software.  
- **Financiera:** configurada dentro de un contenedor **Garuda Linux**, enfocado en la ejecución de servicios financieros y control de procesos contables.  
- **Comercial y Ventas:** implementada con un contenedor **Fedora**, responsable de las aplicaciones orientadas al cliente y ventas.

La red se estructuró en subredes independientes, una por cada dependencia, con comunicación restringida para mantener el aislamiento entre áreas. Este enfoque garantizó una mejor segmentación del tráfico y control de accesos.

---

## Proceso de instalación y configuración

El desarrollo de la infraestructura comenzó con la instalación del sistema base en la máquina administradora. Se descargó la ISO estable de Debian, configurando la virtualización con **QEMU/KVM**, la administración mediante **virt-manager**, y las herramientas de monitoreo necesarias.

Para las dependencias, se realizaron los siguientes pasos:

- En **Recursos Humanos (Arch Linux)** se preparó la imagen base, se configuró la red interna y se instalaron los paquetes esenciales para la gestión del sistema.  
- En **Tecnología (Rocky Linux)** se desplegó la máquina virtual desde la imagen oficial, estableciendo su subred y añadiendo herramientas de desarrollo y análisis.  
- En **Financiera (Garuda Linux)** se configuró un contenedor Docker, creando una red específica y adaptando los servicios requeridos por la dependencia.  
- En **Comercial y Ventas (Fedora)** se construyó un contenedor independiente con conexión a la red comercial y herramientas enfocadas en la gestión de ventas.

Las tecnologías empleadas incluyeron **QEMU/KVM** para la virtualización, **Docker** para la creación de contenedores y una variedad de distribuciones Linux para garantizar diversidad y compatibilidad entre sistemas.

---

## Expansión de la infraestructura

En una segunda etapa, la infraestructura se amplió para incluir nuevas máquinas y contenedores que extendieron la capacidad de cada dependencia.

- **Recursos Humanos:** se añadió una máquina virtual adicional con **Manjaro**, integrada a la subred existente para aumentar la capacidad de procesamiento. También se intentó implementar un contenedor con **CentOS**, pero debido a limitaciones técnicas no se logró completar la instalación, documentándose el proceso como referencia para futuras implementaciones.  
- **Tecnología:** incorporó dos nuevas máquinas virtuales: **Kali Linux**, orientada a pruebas de seguridad y análisis forense, y **Linux Mint**, destinada a tareas de desarrollo con entorno gráfico optimizado.  
- **Financiera:** amplió su capacidad mediante contenedores **Ubuntu** (para servicios estables de largo plazo) y **Alpine** (para procesos ligeros y seguros).  
- **Comercial y Ventas:** añadió una máquina virtual **AlmaLinux** como reemplazo conceptual de CentOS, y un contenedor **Debian** para aplicaciones comerciales.

Durante esta fase, se evidenció un inconveniente con la instalación de CentOS, el cual impedía establecer el gateway necesario para la comunicación entre dependencias. A pesar de ello, las subredes aisladas funcionaron correctamente de manera interna.

---

## Monitoreo y análisis del sistema

El sistema de monitoreo fue diseñado para analizar el comportamiento y rendimiento de todas las máquinas y contenedores en ejecución. Se implementaron múltiples herramientas que permitieron obtener una visión integral del entorno.

### Análisis de hardware y sistema
Se emplearon comandos como `dmidecode`, `hwinfo`, `lspci`, `lsusb` y `dmesg` para identificar los dispositivos del sistema, así como `uname`, `free`, `df`, `lshw` e `inxi` para obtener información sobre el kernel, la memoria, el almacenamiento y la configuración general.

### Monitoreo en tiempo real
Se utilizaron utilidades como `atop`, `iotop`, `iftop` y `glances` para supervisar recursos, tráfico de red y actividad del sistema. Adicionalmente, `bpytop` y `ss -tulnp` facilitaron el control visual y la verificación de puertos activos.

### Gestión de procesos y servicios
El monitoreo de procesos se realizó con `top`, `ps aux`, `pstree` y `dstat`, mientras que el control de servicios bajo **systemd** se llevó a cabo mediante `systemctl`, `systemd-cgtop`, `systemd-analyze` y `journalctl`.  
Para el análisis de red, se usaron `ss`, `lsof`, `glances --webserver` y `nmcli`.

### Gestión de archivos y discos
Herramientas como `ncdu`, `baobab`, `tree` y `rsync` facilitaron la evaluación del uso de almacenamiento y la sincronización de datos. Para el análisis de discos, se utilizó `smartctl` con el fin de verificar el estado de los dispositivos y prevenir fallos.

### Análisis avanzado de red
Se integró **Netdata** como sistema de monitoreo en tiempo real con dashboards personalizados para cada dependencia, además de **Wireshark**, que permitió la captura y análisis detallado de paquetes de red.

### Desarrollo web y auditoría
Dentro de la dependencia Comercial se desplegó una aplicación con **Streamlit**, que permitió visualizar información empresarial y evaluar el consumo de recursos en ejecución.  
Asimismo, se aplicaron auditorías de seguridad con **Lynis**, y análisis de red mediante **Nmap**, lo que ayudó a identificar vulnerabilidades y servicios expuestos.

---

## Resultados y conclusiones

Al finalizar la implementación, se obtuvieron métricas precisas sobre el rendimiento del sistema, incluyendo uso de CPU, memoria, tráfico de red y estado de discos. Los resultados evidenciaron una infraestructura estable, con una línea base de rendimiento definida y áreas de mejora identificadas.

El proyecto permitió establecer un entorno de virtualización y contenedorización eficiente, demostrando la viabilidad de segmentar y monitorear dependencias en un entorno controlado. Además, se fortalecieron habilidades prácticas en automatización, despliegue de sistemas y análisis de seguridad, cumpliendo los objetivos planteados desde la perspectiva de DevOps.

---

## Autores

*(Agrega aquí los nombres de los integrantes del grupo)*
