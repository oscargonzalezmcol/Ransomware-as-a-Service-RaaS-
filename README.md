# Ransomware-as-a-Service-RaaS
Esta nueva modalidad de infección opera mediante grupos especializados de ciberdelincuentes que funcionan bajo un modelo de negocio estructurado, donde socios menos técnicos ("afiliados") distribuyen su malware a cambio de un porcentaje de las ganancias. Este esquema refleja un ecosistema criminal cada vez más sofisticado y descentralizado, permitiendo que actores con distintos niveles de expertise colaboren para escalar los ataques y maximizar su impacto.

Los obejtivos es analizar exhaustivamente el modelo Ransomware-as-a-Service (RaaS) de LockBit 3.0, documentando:

1. El vector de ataque completo (inicial → persistencia → cifrado → doble extorsión).
2. Las tácticas, técnicas y procedimientos (TTP) mapeadas a MITRE ATT&CK.
3. Indicadores de compromiso (IOCs) y reglas de detección reutilizables.
4. Medidas de mitigación alineadas a CIS Controls y NIST CSF.
5. Tendencias del ecosistema RaaS y comparativa con REvil, BlackCat y RansomHub.

Acontinuación lista de grupos reconocidos que usan esta modalidad :

REvil (Sodinokibi)
(S/f). Akamai.com. Recuperado el 15 de junio de 2025, de https://www.akamai.com/glossary/what-is-revil

LockBit
(S/f-b). Hipaajournal.com. Recuperado el 15 de junio de 2025, de https://www.hipaajournal.com/lockbit-ransomware-group-hacked/

BlackCat (ALPHV)
(S/f). Akamai.com. Recuperado el 15 de junio de 2025, de https://www.akamai.com/es/glossary/what-is-blackcat-ransomware

El grupo mas activo a la fecha para este tipo de servicios de malware es LockBit que busca automáticamente objetivos valiosos, propaga la infección y cifra todos los sistemas informáticos accesibles en una red.

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



# Videos de como funciona Lockbit

Estos videos son un ejemplo de como este tipo de ramsonware infecta los equipos

 [![Ver Video](https://img.youtube.com/vi/6PEA0nFyc0Q/0.jpg)](https://www.youtube.com/watch?v=6PEA0nFyc0Q)

[![Ver Video en YouTube](https://img.youtube.com/vi/sS6_1r5hxi8/0.jpg)](https://www.youtube.com/watch?v=sS6_1r5hxi8)

# Analsisi de sandbox
![image](https://github.com/user-attachments/assets/0ae59d15-b764-468a-baf4-7d961be116bf)


 




