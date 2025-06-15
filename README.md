# Ransomware as a Service (RaaS)

Los objetivos es analizar exhaustivamente el modelo Ransomware-as-a-Service (RaaS) de LockBit 3.0:

1. El vector de ataque completo (inicial → persistencia → cifrado → doble extorsión).
2. Las tácticas, técnicas y procedimientos (TTP) mapeadas a MITRE ATT&CK.
3. Indicadores de compromiso (IOCs).
4. Medidas de mitigación alineadas a CIS Controls y NIST CSF.
5. Tendencias del ecosistema RaaS y comparativa con REvil, BlackCat y RansomHub.

**Grupos reconocidos que utilizan esta modalidad**

REvil (Sodinokibi)    
(S/f). Akamai.com. Recuperado el 15 de junio de 2025, de https://www.akamai.com/glossary/what-is-revil

LockBit   
(S/f-b). Hipaajournal.com. Recuperado el 15 de junio de 2025, de https://www.hipaajournal.com/lockbit-ransomware-group-hacked/

BlackCat (ALPHV)    
(S/f). Akamai.com. Recuperado el 15 de junio de 2025, de https://www.akamai.com/es/glossary/what-is-blackcat-ransomware

El grupo más activo a la fecha para este tipo de servicios de malware es LockBit que busca automáticamente objetivos valiosos, propaga la infección y cifra todos los sistemas informáticos accesibles en una red.

# Vector de ataque
LockBit suele infiltrarse mediante RDP explotado, phishing, vulnerabilidades en aplicaciones expuestas (como VPN o servidores web) y credenciales robadas. Una vez dentro, desactiva defensas, elimina copias de seguridad y se propaga lateralmente usando herramientas como PsExec o políticas de grupo (GPOs).

![image](https://github.com/user-attachments/assets/a6e379b1-91bc-4f19-ada1-65acf5c9b7d4)

Referencias:
 StopRansomware: LockBit 3.0. (s/f). Cybersecurity and Infrastructure Security    Agency CISA. Recuperado el 15 de junio de 2025, de https://www.cisa.gov/news-    events/cybersecurity-advisories/aa23-075a
 
 To HADES and back: UNC2165 shifts to LOCKBIT to evade sanctions. (2022, junio 2). Google Cloud Blog. https://cloud.google.com/blog/topics/threat-intelligence/unc2165-shifts-to-evade-sanctions/


# Mapa MITRE ATT&CK

LockBit inicia con acceso inicial mediante phishing, RDP explotado o vulnerabilidades en servicios expuestos. Una vez dentro, ejecuta scripts para desactivar antivirus (Windows Defender, Carbon Black) y elimina copias de seguridad (vssadmin) para evitar recuperación. Usa herramientas como PsExec y WMI para movimiento lateral, robando credenciales con Mimikatz o Kerberoasting.
Para evadir defensas, borra logs (wevtutil), excluye carpetas del antivirus y se propaga mediante GPOs. Antes de cifrar, exfiltra datos con Rclone o MEGA. Finalmente, despliega notas de rescate y cambia fondos de pantalla para extorsión.

![image](https://github.com/user-attachments/assets/1a9533de-78fa-4024-acef-b9425ad06522)

Understanding ransomware threat actors: LockBit. (s/f). Cybersecurity and Infrastructure Security Agency CISA. Recuperado el 15 de junio de 2025, de https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-165a

# Videos de cómo funciona Lockbit

Estos videos son un ejemplo de cómo este tipo de Ransomware infecta los equipos

 [![Ver Video](https://img.youtube.com/vi/6PEA0nFyc0Q/0.jpg)](https://www.youtube.com/watch?v=6PEA0nFyc0Q)

[![Ver Video en YouTube](https://img.youtube.com/vi/sS6_1r5hxi8/0.jpg)](https://www.youtube.com/watch?v=sS6_1r5hxi8)

# Artículos científicos clave

El Ransomware-as-a-Service (RaaS) está evolucionando hacia un modelo más sofisticado y accesible, democratizando la ciberdelincuencia al permitir que actores con pocos conocimientos técnicos lancen ataques devastadores. ** Actualmente, las plataformas RaaS ofrecen herramientas más avanzadas, como cifrado adaptativo, evasión de detección y soporte 24/7, lo que ha incrementado su eficacia y propagación. Esto ha llevado a un aumento en ataques contra sectores críticos como salud, educación y gobiernos, con un impacto económico y operacional significativo. Además, la adopción de criptomonedas privadas (como Monero) y técnicas de lavado más complejas dificultan el rastreo de pagos. Como resultado, el RaaS no solo se ha convertido en una amenaza más persistente, sino también en un negocio criminal más rentable y escalable, exigiendo mayores esfuerzos en ciberseguridad, concientización y cooperación internacional para su mitigación.

**Referencia:**
Meland, P. H., Bayoumy, Y. F. F., & Sindre, G. (2020). "The Ransomware-as-a-Service economy within the darknet". Computers & Security, 92, 101762. https://doi.org/10.1016/j.cose.2020.101762
Para literatura adicional sobre modelos económicos: Economics of RaaS - Google Scholar

# Análisis de SandBox

A continuación realizamos un ejercicio de detonar un ejecutable del malware LOCKBIT y al ejecutarse, verifica privilegios e idioma del sistema para evitar regiones específicas, mientras detecta entornos virtuales (como Wireshark o Process Hacker) para evadir análisis; si identifica un entorno controlado, aborta la ejecución. Su comportamiento incluye cifrado rápido de archivos, eliminación de copias de sombra (vssadmin) y modificación de políticas de grupo para propagarse lateralmente.
![image](https://github.com/user-attachments/assets/85b48c63-7581-4d09-a72e-d8bed6b2e888)

# Casos reales 2023-2025

Investigando en la red, encontramos varios casos de filtración de información en múltiples entidades, a continuación alguna de ellas:

El 7 de mayo de 2024, durante la Operación Cronos de la Agencia Nacional contra el Crimen del Reino Unido y sus socios, se reveló la presunta identidad del operador de la franquicia LockBit 3.0, también conocida como LockBitSupp : Dmitry Yuryevich Khoroshev.

El grupo LockBit se atribuye un ataque de Ransomware contra un banco del sudeste asiático.

LockBit 3.0 regresó en mayo para lanzar 176 ataques de ransomware, el 37 % del total del mes. Esto representa un enorme aumento intermensual del 665 % para el grupo de ransomware como servicio (RaaS).

**Referencia:**

Rieß-Marchive, V. (2025, 9 de mayo). Ransomware: What the LockBit 3.0 data leak reveals. ComputerWeekly.
https://www.computerweekly.com/news/366623780/Ransomware-What-the-LockBit-30-data-leak-reveals

Roberts, P. (2023, May 2). LockBit remains most prominent ransomware in May. Infosecurity Magazine.
https://www.infosecurity-magazine.com/news/lockbit-prominent-ransomware-may/

# Comparativa de LockBit con otros RAAS

LockBit debutó en 2019 con su versión 1.0 (“ABCD”), centrada en un cifrado multihilo básico; en 2021 llegó LockBit 2.0 o *Red*, que profesionalizó el modelo RaaS con un portal para afiliados y doble extorsión. En 2022, LockBit 3.0 o *Black* añadió triple extorsión, un programa de recompensas y su *builder* filtrado, mientras que la variante *Green* (2023) integró código de Conti y técnicas avanzadas de evasión. Desde 2024 se observan builds 4.x con mejoras incrementales—BYOVD, soporte ESXi/NAS—manteniendo el reparto clásico 80 / 20 entre desarrolladores y afiliados.

![image](https://github.com/user-attachments/assets/44ff3b5e-6bb8-462b-b0f5-3ffbe6c242e6)

LockBit se consolidó como el RaaS más exitoso gracias a su modelo de negocio altamente eficiente:

**LockBit**
* Líder en 2023 con el 26% de ataques, destacando ataques a Royal Mail y TSMC.
* Modelo RaaS eficiente (hasta 90% para afiliados) y resiliente a operaciones policiales.
* Enfocado en TI, finanzas y servicios profesionales, principalmente en EE.UU. y Europa.

**BlackCat (ALPHV)**
* Tecnología avanzada (variante Sphynx en Rust) y extorsión triple.
* Atacó NextGen Healthcare y Reddit (exigiendo $4.5M).
* Más del 50% de víctimas en Norteamérica, con foco en salud y finanzas.

**Clop**
* Especializado en explotar vulnerabilidades (GoAnywhere, MOVEit, PaperCut).
* 50% de sus víctimas fueron grandes empresas (Shell, Departamento de Energía de EE.UU.).
* Concentró el 71.6% de ataques en Norteamérica, con rescates multimillonarios.

**Referencia**
Trend Micro. (2023). LockBit, BlackCat, and Clop prevail as top RaaS groups for 1H 2023.
Recuperado de https://www.trendmicro.com/vinfo/us/security/news/ransomware-by-the-numbers/lockbit-blackcat-and-clop-prevail-as-top-raas-groups-for-1h-2023

# LockBit: A Cheat Sheet and IOC

A continuación, un panorama de las vulnerabilidades y tácticas que conforman su arsenal.

![image](https://github.com/user-attachments/assets/5656ca9c-dcc3-4c0d-ae9e-ea92c2b8c826)


**Referencia**
Securin. (2023). All about LockBit ransomware. https://www.securin.io/articles/all-about-lockbit-ransomware


**Indicadores de Compromiso LockBit**

Para prevenir infección por este tipo de Ransomware debemos monitorear conexiones RDP no autorizadas, actividad sospechosa con herramientas como PsExec/WMI, y patrones de cifrado rápido con extensiones .lockbit. Implementar detección de comandos maliciosos como vssadmin delete shadows y tráfico a dominios C2 asociados (ej: *.onion).

**Referencia**
Cybersecurity and Infrastructure Security Agency. (2023). *AA23-075A: LockBit 3.0 ransomware*. U.S. Department of Homeland Security. https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-075a
![image](https://github.com/user-attachments/assets/bb1ae710-9a52-454c-a5aa-0571303e0be5)



 




