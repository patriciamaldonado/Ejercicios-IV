# Ejercicios Introducción a la infraestructura virtual: concepto y soporte físico

### Ejercicio 1
**Consultar en el catálogo de alguna tienda de informática el precio de un ordenador tipo servidor y calcular su coste de amortización a cuatro y siete años. Consultar este artículo en Infoautónomos sobre el tema.**


Se va a calcular la amortización de un [servidor](http://infobarna.com/es/producte-793/primergy-tx1330-m2.html) con un coste de 899,00 € sin IVA, comprado a principio de año para calcular periodos anuales completos.

Para calcular la amortización dividimos el precio del servidor (sin IVA) entre los años (4 y 7).

- Para una amortización a 4 años:
~~~
     899,00/4 =224,75 €/año
~~~

- Para una amortización a 7 años:
~~~
    899,00/7 = 128,43 €/año
~~~

### Ejercicio 2

**Usando las tablas de precios de servicios de alojamiento en Internet “clásicos”, es decir, que ofrezcan Virtual Private Servers o servidores físicos, y de proveedores de servicios en la nube, comparar el coste durante un año de un ordenador con un procesador estándar (escogerlo de forma que sea el mismo tipo de procesador en los dos vendedores) y con el resto de las características similares (tamaño de disco duro equivalente a transferencia de disco duro) en el caso de que la infraestructura comprada se usa solo el 1% o el 10% del tiempo.**

> [Servidor cloud](https://www.swhosting.com/es/cloud) 6,80€/mes
  - 2 vCore
  - 2 GB RAM
  - 20 GB de disco SSD
  - Tráfico ilimitado
   - FireWall Perimetral Capa 4
   - 6,80€/mes

> [VPS](https://gigas.com/cloud-vps) 15,8€* Al mes
 - 2 GB RAM
 - 2 cores 2.1GHz/core
 - 50 GB de disco
  -transferencia ilimitada

1. Servidor cloud :  

  - Uso 10%:  

    6,80 x 0.1 (10%) = 0,68 €/mes
    0,68 €/mes x 12 meses = 8,16 €/año  

  - Uso 1%:  

    6,80 x 0.01 (1%) = 0,068 €/mes          
     0,068 €/mes  x 12 meses =  0,816 €/año


2. VPS: 15,8€/mes

     - 15,8€/mes x 12 meses = 189,6 €/año

Como vemos cuando tenemos poco uso es recomendable escoger un server cloud ajustado a nuestras necesidades, el ahorro puede ser de unos 180 €.


### Ejercicio 3

**En general, cualquier ordenador con menos de 5 o 6 años tendrá estos flags. ¿Qué modelo de procesador es? ¿Qué aparece como salida de esa orden? Si usas una máquina virtual, ¿qué resultado da? ¿Y en una Raspberry Pi o, si tienes acceso, el procesador del móvil?**

- Portátil ASUS: Intel® Core™ i7-4510U CPU @ 2.00GHz × 4
     > egrep '^flags.*(vmx|svm)' /proc/cpuinfo
     ~~~
     flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb invpcid_single ssbd ibrs ibpb stibp pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts md_clear flush_l1d
     ~~~

- Xiaomi Redmi Note 7. Para ver las características hardaware he usado la aplicación Droid hardware info.

~~~
DISPOSITIVO
Modelo: Redmi Note 7 (lavender_eea)
Fabricante: Xiaomi
Versión de Banda Base: MPSS.AT.3.1-00777-SDM660_GEN_PACK-1.191301.1.192385.1
Versión RIL: Qualcomm RIL 1.0
Número de compilación: PKQ1.180904.001
Construir Huella Digital: xiaomi/lavender_eea/lavender:9/PKQ1.180904.001/V10.2.7.0.PFGEUXM:user/release-keys
Gestor de Arranque: unknown
Java VM: ART 2.1.0
Versión de Sistema Operativo: P (9)
SDK: 28

MONITOR
Resolución: 1080x2340 pixels
Densidad de Software: 440 dpi
Frecuencia de actualización: 60 Hz

**PROCESADOR**
Arquitectura del CPU: AArch64 Processor rev 2 (aarch64)
Tablero: sdm660
Chipset: Qualcomm Technologies, Inc SDM660
Nucleos: 8
Frecuencia del reloj: 1843 MHz - 2208 MHz
Conjunto de Instrucciones: arm64-v8a
Caracteristicas del CPU: fp asimd evtstrm aes pmull sha1 sha2 crc32
Regulador de CPU: interactive
Versión del Kernel: 4.4.153-perf+
Arquitectura del Kernel: aarch64

GRÁFICOS
Renderizador: Adreno (TM) 512
Proveedor: Qualcomm
Versión OpenGL: OpenGL ES 3.2

RAM
Total: 2732 MB
Java Heap: 256 MB

~~~
- La máquina virtual no tiene el flag que soporta virtualización por hardware.


### Ejercicio 4

**1. Comprobar si el núcleo instalado en tu ordenador contiene este módulo del kernel usando la orden kvm-ok. Alternativamente (o además), usar lscpu como se indica arriba.**

  - kvm-ok
    KMV está activado

    ~~~
    INFO: /dev/kvm exists
    KVM acceleration can be used
    ~~~

  - lscpu

     ~~~
    patri@patri-Ubuntu:~$ lscpu
    Arquitectura:          x86_64
    modo(s) de operación de las CPUs:32-bit, 64-bit
    Orden de bytes:        Little Endian
    CPU(s):                4
    On-line CPU(s) list:   0-3
    Hilo(s) de procesamiento por núcleo:2
    Núcleo(s) por «socket»:2
    Socket(s):             1
    Modo(s) NUMA:          1
    ID de fabricante:      GenuineIntel
    Familia de CPU:        6
    Modelo:                69
    Model name:            Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz
    Revisión:             1
    CPU MHz:               1392.320
    CPU max MHz:           3100,0000
    CPU min MHz:           800,0000
    BogoMIPS:              5188.09
    Virtualización:       VT-x
    Caché L1d:            32K
    Caché L1i:            32K
    Caché L2:             256K
    Caché L3:             4096K
    NUMA node0 CPU(s):     0-3
    Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm epb invpcid_single ssbd ibrs ibpb stibp pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts md_clear flush_l1d

    ~~~



**2. Instalar un hipervisor para gestionar máquinas virtuales, que más adelante se podrá usar en pruebas y ejercicios.**

  Tengo instalado VirtualBox 5.2

  ~~~
  patri@patri-Ubuntu:~$ VBoxManage --version
  5.2.32r132073
  ~~~

### Ejercicio 5

**Darse de alta en servicios de nube usando ofertas gratuitas o cupones que pueda proporcionar el profesor.**  

Me he dado de alta en Amazon Web Services.

### Ejercicio 6

**Darse de alta en una web que permita hacer pruebas con alguno de los sistemas de gestión de nube anteriores.**
