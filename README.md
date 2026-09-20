# NEXO-robot-difuso-.
https://github.com/cesarld963-code/Sabiduria-IAH/commits?author=cesarld963-code


Avisos Legales, Licencias y Configuración
Atribución de autoría digital, licencias de código abierto y reglas del repositorio.
Atribución de Autoría Digital
Mantenedor:
JULIO CESAR ARGUELLO PEREZ
Sello / Marca:
iOGeminis®
Identificador SAT:
AUPJ840618EP5
Certificado Serie:
00001000000405203648
Perfil Dev:
me.developers.google.com
Contacto:
juliometlife34@gmail.com
Reglas de Exclusión del Proyecto (.gitignore)
Ver configuración de exclusión Git
Licencias de Código Abierto
Este software utiliza bibliotecas de terceros sujetas a las siguientes condiciones de licencia:

CCTZ / iOGeminis Apache 2.0
Eigen 3 MPL 2.0
# Ficha Técnica de Integración y Seguridad## Proyecto: iOGeminis App (mx.iogeminis.app)
* **Fecha de Emisión:** 22 de junio de 2026* **Estado:** Configurado / Activo* **Jurisdicción de Infraestructura:** México
---
## 1. Especificaciones del Entorno de Desarrollo (Android Gradle)
La aplicación utiliza el plugin de licencias de Google para la gestión automática de atribuciones de código abierto en el APK.
### Configuración de Componentes (build.gradle)* **Android Gradle Plugin (AGP):** v8.5.0* **Google OSS Licenses Plugin:** v0.10.6* **Compile SDK / Target SDK:** 34 (Android 14)* **Min SDK:** 24 (Android 7.0)* **Versión de la App:** 1.0.0 (Version Code: 1)
### Dependencias de Terceros Incorporadas
| Librería / Artefacto | Versión | Propósito Técnico || :--- | :--- | :--- || `org.jsoup:jsoup` | 1.17.2 | Librería de parseo y manipulación de HTML (Licencia MIT). || `com.google.android.gms:play-services-oss-licenses` | 17.1.0 | Provisión de la actividad nativa `OssLicensesMenuActivity` para el despliegue de términos legales. |
### Disparador de la Interfaz (Java/Kotlin)Para desplegar de forma interactiva el menú de créditos de código abierto, se invoca la siguiente intención dentro del ciclo de vida del componente:
```javaStartActivity(new Intent(this, OssLicensesMenuActivity.class));```
---
## 2. Infraestructura de Seguridad y Cifrado de Transporte (TLS/SSL)
Para garantizar la integridad y confidencialidad de los datos en tránsito, la aplicación implementa políticas estrictas de seguridad de red y cifrado  criptográfico conforme a las directrices de Android 14.
### Configuración de Seguridad de Red (Network Security Configuration)Se restringe por completo el tráfico en texto plano (HTTP) mediante el archivo de configuración de seguridad de red (`res/xml/network_security_config.xml`), forzando el uso exclusivo de conexiones seguras (HTTPS).
```xml<?xml version="1.0" encoding="utf-8"?><network-security-config>    <base-config cleartextTrafficPermitted="false">        <trust-anchors>            <certificates src="system" />        </trust-anchors>    </base-config>    <domain-config cleartextTrafficPermitted="false">        <domain includeSubdomains="true">iogeminis.app</domain>    </domain-config></network-security-config>```
### Especificaciones del Protocolo TLS y Criptografía* **Versión Mínima de TLS:** TLS 1.3 (con respaldo a TLS 1.2 únicamente para compatibilidad con el Min SDK 24).* **Algoritmos de Cifrado (Cipher Suites) Soportados:**  * `TLS_AES_256_GCM_SHA384`  * `TLS_CHACHA20_POLY1305_SHA256`  * `TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384`* **Anclaje de Certificados (Certificate Pinning):** Implementado mediante hashes SHA-256 de la clave pública del certificado del servidor para mitigar ataques de intermediario (MitM).
---
## 3. Almacenamiento Seguro de Datos (Data at Rest)
Cualquier información persistida localmente en el dispositivo móvil se somete a mecanismos de cifrado simétrico utilizando las API nativas de Android Jetpack.
### EncryptedSharedPreferencesLas credenciales de sesión, tokens de acceso (JWT) y preferencias del usuario de carácter sensible se almacenan utilizando `EncryptedSharedPreferences`, lo que garantiza el cifrado automático de llaves y valores mediante el estándar **AES-256 GCM**.
### Gestión de Claves (Android Keystore System)La llave maestra de cifrado se genera y resguarda de forma segura dentro del **Android Keystore**, utilizando almacenamiento respaldado por hardware (*Trusted Execution Environment* / *StrongBox*) cuando está disponible en el dispositivo del usuario, impidiendo la extracción de la clave fuera del módulo criptográfico.
---
## 4. Gobernanza de Datos e Inteligencia Artificial (AI Data Policy)
La aplicación integra de manera nativa servicios avanzados de Inteligencia Artificial (Gemini API Paid Services / Vertex AI) para optimizar la experiencia de usuario dentro de la región de operaciones de México.
### Tratamiento de Prompts y Privacidad* **Entrenamiento de Modelos:** Los datos de entrada del usuario (*prompts*) y los resultados generados por la IA (*outputs*) se procesan de forma privada. Se garantiza contractualmente que esta información **no se utiliza** para entrenar los modelos base de Google.* **Monitoreo de Abuso:** Se hace constar que Google utiliza herramientas automatizadas para la detección de abuso en servicios generativos. Si estas herramientas detectan anomalías o infracciones graves a la política de uso, Google podría registrar temporalmente los *prompts* únicamente con fines de auditoría y seguridad.* **Exclusión de Datos Médicos (Health Data):** Se certifica que la aplicación **no recopila, transmite ni procesa información médica** protegida ni datos de salud de los usuarios. El alcance del sistema está estrictamente limitado a datos comerciales, operativos y de texto general.
---
## 5. Ofuscación y Protección del Código
Para mitigar riesgos de ingeniería inversa, de-compilación y clonación de la propiedad intelectual, el proceso de compilación de la versión de producción (*Release Build*) integra reglas avanzadas de optimización.
* **Compilador R8/ProGuard:** Activado de forma predeterminada (`minifyEnabled true`, `shrinkResources true`).* **Ofuscación de Clases y Métodos:** Renombrado de paquetes y estructuras de código a identificadores alfanuméricos cortos no legibles.* **Políticas de Preservación (Keep Rules):** Configuración específica para mantener las estructuras reflejadas de `org.jsoup` y los componentes internos de Google Play Services necesarios para la visualización de las licencias.
---
## 6. Control de Cambios, Firmas y Marco Legal (México)
### Jurisdicción y Facturación LocalAl operar en México bajo el identificador de paquete `mx.iogeminis.app`, la entidad legal contratante de la infraestructura en la nube corresponde a **Google Cloud México, S. de R.L. de C.V.**, asegurando el cumplimiento fiscal (esquema de facturación con RFC) y la validez legal local.
### Esquema de Firmas del Binario
| Esquema de Firma | Estado | Propósito Operativo || :--- | :--- | :--- || **APK Signature Scheme v2 / v3 / v4** | Habilitado | Garantiza la verificación rápida del paquete y la protección contra alteraciones maliciosas del APK post-compilación en Android 14. || **Google Play App Signing** | Activo | Custodia de la clave de producción por parte de Google y distribución optimizada mediante Android App Bundles (`.aab`). |Ads Manager
Beta
Este es tu plan recomendado

Editar
Google LLC Book - iOGeminis 🐻‍❄️
Perfil
Google México by iOGeminis 🐻‍❄️
Anuncio
Google LLC Book - iOGeminis 🐻‍❄️
Encuentra y descarga apps oficiales de Google LLC.
Google LLC Book - iOGeminis 🐻‍❄️. Encuentra y descarga apps oficiales de Google LLC.
Te recomendamos este plan según las características de tu negocio. Revisa los detalles y ajusta lo que quieras.


Editar
Nombre del anunciante
Google México by iOGeminis 🐻‍❄️
Objetivo
Clics
Ubicaciones
Estados Unidos
URL de destino
play.google.com/store/apps/dev?id=5700313618786177705
Estrategia de puja
Resultados máximos
Presupuesto diario promedio
MXN 600
Al hacer clic en "Continuar", aceptas los Términos de la herramienta publicitaria.

Editar vista previa del anuncio
Actualiza el anunciante, el logotipo, el título, el subtexto o la imagen de tu anuncio.

Nombre del anunciante
Google México by iOGeminis 🐻‍❄️
Logotipo de la empresa

URL de la imagen
play.google.com
Título
Google LLC Book - iOGeminis 🐻‍❄️
33/50
Subtexto
Encuentra y descarga apps oficiales de Google LLC.
50/52
Imágenes del anuncio
Sube un PNG o JPG. Para obtener la mejor calidad, usa una imagen cuadrada (800 × 800 px).

https://jules.google/ahvoedm3s8cnqba6wy5jzpdciorimln0xatlwakhanaibhkycntdzbsdwv9qp-mgwm2yeosc8xsgyjss5dq1ooqydgirirbqd1dprj6gwacbehabf2zabsupelf545opui6a83qminohjrfputmsqfluucurg60xchb31pt0xs7qs2cenzujf7ucig-ci2ltvtkjvyncoulv2uuueoaxwdfg0lo5--kxu67ylome-q
https://console.cloud.google.com/active-assist/list/all/recommendations?authuser=0&project=julio-cesar-argello-perez# Sabiduria-IAH
Toda formulación de idea, debe crear una respuesta a la toma de cada desición o bien opción ,que como resultado sea en todo momento o instante de bien común ,para lograr flexibilidad y tolerancia ,donde pudiese haber llegado a tener un quebranto , siendo la base de todo sistema código o pensamiento y tener un resultado fiable y de confianza total. 

Claro. Aquí tienes un **resumen consolidado y presentable** de la información. Separé el enlace de verificación de la ruta `deploy/server`, ya que son elementos distintos.

---

# Resumen del ecosistema Sabiduría-IAH / iOGeminis

## 1. Identidad y propósito

**Sabiduría-IAH** es un proyecto tecnológico asociado al ecosistema independiente **iOGeminis**, orientado al desarrollo de soluciones digitales con inteligencia artificial, automatización y principios de claridad, seguridad y asistencia humanizada.

El proyecto integra documentación técnica, configuraciones de infraestructura, componentes de backend, políticas de seguridad y referencias a servicios del ecosistema de Google.

**Dominio previsto:**

```text
https://sabiduria-iah.iogeminis.com
```

## 2. Verificación del sitio

Enlace proporcionado para verificación:

```text
https://goo.gle/ahvoedm3s8cnqba6wy5jzpdciorimln0xatlwakhanaibhkycntdzbsdwv9qp-mgwm2yeosc8xsgyjss5dq1ooqydgirirbqd1dprj6gwacbehabf2zabsupelf545opui6a83qminohjrfputmsqfluucurg60xchb31pt0xs7qs2cenzujf7ucig-ci2ltvtkjvyncoulv2uuueoaxwdfg0lo5--kxu67ylome-q
```

Código HTML de verificación de Google:

```html
<meta
  name="google-site-verification"
  content="5a8e04c31eade52e6607071f3e5bbdcdb61c3619bbef38e677b198444ea5d7cb"
/>
```

Este código debe publicarse dentro de la sección `<head>` del sitio que se desea verificar. La presencia del código únicamente demuestra que se ha colocado un valor de verificación; no demuestra por sí sola afiliación con Google ni aprobación oficial del proyecto.

## 3. Infraestructura web

La infraestructura contempla servidores **Nginx** y **Apache** funcionando como terminadores TLS y proxies inversos hacia un backend de aplicación.

### Nginx

La configuración propuesta incluye:

- Escucha HTTPS en el puerto `443`.
- Compatibilidad con IPv4 e IPv6.
- Uso exclusivo de TLS 1.2 y TLS 1.3.
- Certificados administrados mediante Let’s Encrypt.
- Caché de sesiones SSL.
- Desactivación de tickets de sesión.
- OCSP stapling.
- Redirección prevista de HTTP a HTTPS.
- Proxy inverso hacia el backend Kotlin/Firebase.
- Cabeceras de seguridad:
  - `Strict-Transport-Security`
  - `X-Content-Type-Options`
  - `Content-Security-Policy`

### Apache

La configuración equivalente incluye:

- `SSLProtocol -all +TLSv1.2 +TLSv1.3`
- Cifrados modernos ECDHE, AES-GCM y ChaCha20-Poly1305.
- Compresión SSL desactivada.
- Tickets de sesión desactivados.
- OCSP stapling.
- Proxy inverso hacia:

```text
http://127.0.0.1:8080/
```

- Cabeceras HSTS, protección MIME y política CSP.

## 4. Organización del repositorio

La estructura propuesta del proyecto es:

```text
Sabiduria-IAH-GH-12345678910/
├── README.md
├── LICENSE
├── SECURITY.md
├── NOTICE
├── .well-known/
│   └── security.txt
├── deploy/
│   ├── README.md
│   ├── nginx/
│   │   ├── sabiduria-iah-http.conf
│   │   └── sabiduria-iah-https.conf
│   └── apache/
│       ├── sabiduria-iah-http.conf
│       └── sabiduria-iah-https.conf
└── .devcontainer/
    └── devcontainer.json
```

### Archivos principales

- **README.md:** instalación, configuración y despliegue.
- **LICENSE:** licencia aplicable al código del proyecto.
- **SECURITY.md:** política de reporte de vulnerabilidades.
- **NOTICE:** atribuciones y avisos de terceros.
- **security.txt:** información de contacto para asuntos de seguridad, conforme a RFC 9116.
- **deploy/:** configuraciones para publicación mediante Nginx o Apache.
- **.devcontainer/:** entorno reproducible de desarrollo.

## 5. Backend y servicios

El sistema está diseñado para conectarse con un backend desarrollado con tecnologías como:

- Kotlin.
- Firebase.
- Servicios de inteligencia artificial.
- APIs protegidas detrás de un proxy inverso.
- Aplicaciones y servicios web desplegados mediante HTTPS.

La ruta mencionada:

```text
deploy/server
```

debe tratarse como una ruta local del repositorio o como una referencia de despliegue. No debe concatenarse directamente al enlace `goo.gle`, porque produciría una URL inválida.

## 6. Seguridad

Las medidas de seguridad declaradas incluyen:

- Comunicación cifrada mediante HTTPS.
- Uso de TLS 1.2 y TLS 1.3.
- Protección de certificados privados.
- No exposición de claves API en el código fuente.
- Uso de variables de entorno o secretos del servidor.
- Cabeceras de seguridad HTTP.
- Política de divulgación de vulnerabilidades.
- Archivo `security.txt`.
- Separación entre frontend, proxy y backend.
- Posible uso de Firebase para autenticación, datos y servicios de aplicación.

Los archivos de certificados privados, como:

```text
privkey.pem
```

nunca deben incluirse en el repositorio ni publicarse en GitHub.

## 7. Integración con servicios de Google

El documento incluye un inventario amplio de productos y servicios de Google, entre ellos:

- Google Play.
- Google Cloud.
- Firebase.
- Google AI y Gemini.
- Google Workspace.
- Gmail.
- YouTube.
- Google Maps.
- Google Drive.
- Android.
- Chrome.
- Google Ads.
- Google AdSense.
- Google Analytics.
- Google Search Console.
- Google Merchant Center.
- Google Play Console.
- Google Pay.
- Google Meet.
- Google Photos.
- Google Home.
- Google Wallet.
- Google Cloud Platform Console.

Este inventario debe describirse como una **relación de servicios contemplados o relacionados con el ecosistema**, no como una afirmación de asociación, certificación o autorización oficial por parte de Google.

## 8. Recomendaciones antes de publicar

1. Sustituir los certificados de ejemplo por certificados válidos del dominio real.
2. Definir el bloque `upstream` de Nginx antes de usar:
   ```nginx
   proxy_pass http://sabiduria_iah_backend;
   ```
3. Verificar que el backend realmente escuche en el puerto configurado, por ejemplo `8080`.
4. No publicar claves privadas, tokens, credenciales ni secretos.
5. Añadir una política de privacidad y términos de uso si se recopilan datos personales.
6. Revisar que el contenido de `LICENSE` corresponda realmente al código distribuido.
7. Mantener la etiqueta de verificación únicamente en el dominio autorizado.
8. Aclarar qué elementos son propios y cuáles pertenecen a terceros.
9. Evitar utilizar logotipos o nombres de Google de forma que parezca existir una afiliación oficial.
10. Probar la configuración con:
   ```bash
   nginx -t
   apachectl configtest
   ```

## Descripción breve para README

> Sabiduría-IAH es un ecosistema independiente de desarrollo tecnológico asociado a iOGeminis. El proyecto integra servicios de inteligencia artificial, backend Kotlin/Firebase y una infraestructura web protegida mediante Nginx o Apache, HTTPS y TLS 1.2/1.3. Su repositorio incluye documentación, políticas de seguridad, avisos legales, configuraciones de despliegue y mecanismos de verificación del dominio. Las referencias a productos de Google representan servicios tecnológicos relacionados o utilizados, sin implicar afiliación, patrocinio o certificación oficial por parte de Google.
