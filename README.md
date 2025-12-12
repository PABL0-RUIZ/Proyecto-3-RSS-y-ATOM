# Memoria de la Actividad – Generación de Canales RSS/Atom (RA3)

## Grupo X: *Noticias TechBox y EduSys*

**Integrantes del grupo:**
- **Enrique** – Rol: Desarrollador del feed RSS  
- **Pablo** – Rol: Desarrollador del feed Atom  
- **Javi** – Rol: Coordinación y Pruebas con Agregador  

---

## 1. Descripción del Proyecto

El proyecto consiste en la creación de dos canales de sindicación de contenido: uno en **RSS 2.0** y otro en **Atom 1.0**. El tema elegido por el grupo fueron **noticias tecnológicas** centradas en hardware, software y formación.

El grupo acordó crear tres noticias comunes para ambos feeds:
1. Lanzamiento del nuevo servidor NAS compacto.  
2. Publicación de la actualización 3.2 del panel de control web.  
3. Nuevo curso gratuito de administración Linux.

Cada miembro del equipo asumió un rol: Enrique desarrolló el archivo RSS, Pablo creó el Atom y Javi comprobó la coherencia entre ambos, además de realizar las pruebas en un agregador de noticias.

---

## 2. Desarrollo del Trabajo

---

### 2.1 Rol RSS – Enrique Ros

**Tareas realizadas:**

Para crear el archivo `feed_rss.xml`, utilicé la estructura de RSS 2.0 con el elemento raíz `<rss>` y el espacio de nombres Atom para incluir el enlace `atom:link` que apunta al propio feed. Dentro del `<channel>`, añadí los elementos obligatorios y recomendados:  
- `<title>`  
- `<link>`  
- `<description>`  
- `<language>`  
- `<pubDate>`  
- `<lastBuildDate>`  
- `<category>`  
- `<atom:link>`  

Después incorporé las tres noticias dentro de elementos `<item>`, cada una con:  
- `<title>`  
- `<link>`  
- `<description>`  
- `<pubDate>` en formato RFC 822  
- `<guid>`  
- `<author>`  
- `<category>`

```xml
<item>
  <title>Lanzamiento del nuevo servidor NAS compacto</title>
  <link>http://midominio.com/articulos/nas-compacto</link>
  <description>El fabricante TechBox presenta un NAS doméstico de bajo consumo con soporte para RAID 1 y aplicaciones de contenedor.</description>
  <pubDate>Mon, 01 Dec 2025 09:00:00 GMT</pubDate>
  <guid>http://midominio.com/articulos/nas-compacto</guid>
</item>

```

**Validación del RSS:**

El archivo se validó con W3C Feed Validator, revisando sintaxis XML, formato de fechas y estructura RSS 2.0.
No presentaba errores estructurales.


**Reflexión individual:**

Crear el RSS me permitió comprender bien los requisitos estrictos del formato, especialmente respecto a las fechas RFC 822. La estructura es simple pero rígida, y se debe ser cuidadoso con la sintaxis XML. Resulta un formato fácil de leer y generar.

---

### 2.2 Rol Atom – Pablo

**Tareas realizadas:**

Para crear el archivo `feed_atom.xml`, utilicé la estructura de Atom 1.0 con el elemento raíz `<feed>` y el espacio de nombres `xmlns="http://www.w3.org/2005/Atom"`. Dentro del `<feed>`, añadí los elementos obligatorios y recomendados:
- `<title>`
- `<subtitle>`
- `<id>`
- `<updated>`
- `<author>`
- `<link>` con `rel="self"` (apuntando al propio feed)
- `<link>` con `rel="alternate"` (apuntando al sitio web)
- `<category>` para cada tema

Después incorporé las tres noticias dentro de elementos `<entry>`, cada una con:
- `<title>`
- `<id>`
- `<link>` con `rel="alternate"` y `type="text/html"`
- `<updated>` en formato ISO 8601
- `<published>` en formato ISO 8601
- `<category>`
- `<summary>`
- `<author>`

```xml
<entry>
  <title>Lanzamiento del nuevo servidor NAS compacto</title>
  <id>http://midominio.com/articulos/nas-compacto</id>
  <link href="http://midominio.com/articulos/nas-compacto" rel="alternate" type="text/html"/>
  <updated>2025-12-01T09:00:00Z</updated>
  <published>2025-12-01T09:00:00Z</published>
  <category term="Hardware"/>
  <summary>El fabricante TechBox presenta un NAS doméstico de bajo consumo con soporte para RAID 1 y aplicaciones de contenedor. Ideal para copias de seguridad locales.</summary>
  <author>
    <name>Marta López</name>
  </author>
</entry>
```

**Validación del Atom:**

El archivo se validó con W3C Feed Validator, revisando sintaxis XML, formato de fechas ISO 8601 y estructura Atom 1.0. La validación fue exitosa sin errores estructurales.

**Reflexión individual:**

Crear el feed Atom me permitió apreciar la mayor riqueza semántica de este formato en comparación con RSS.
Atom es más estricto y estructurado, requiriendo fechas en formato ISO 8601 y siendo más explícito con los tipos de enlaces (`rel="self"`, `rel="alternate"`).
La estructura es más compleja que RSS pero también más expresiva y coherente. Destacaría la obligatoriedad de elementos como `<id>` y `<updated>` que hacen el feed más robusto y preciso.
Aunque requiere más atención al detalle, resulta un formato más moderno y completo.

---

### 2.3 Rol Coordinador/Agregador – Nombre Apellido 3

**Tareas realizadas:**

*[Explica cómo se coordinaron los contenidos entre RSS y Atom, cómo revisaste ambos archivos, y cómo preparaste la prueba con el agregador.]*

**Pruebas en agregador:**

*[Indica qué agregador usaste (Feedly, Inoreader...), cómo subiste los feeds (GitHub Pages, servidor local...), y qué resultados obtuviste.]*

- ![Captura: Feed RSS en el agregador](evidencias/agregador_rss.png)
- ![Captura: Feed Atom en el agregador](evidencias/agregador_atom.png)

**Reflexión individual:**

*[Comenta la utilidad de los agregadores, qué diferencias notaste en la presentación entre RSS y Atom, si el agregador aportó alguna funcionalidad extra.]*

---

## 3. Conclusión del Grupo

Este proyecto nos ha permitido comprender en profundidad los mecanismos de sindicación de contenidos y su relevancia en la distribución de información en la web. Hemos aprendido que tanto RSS como Atom son estándares complementarios que persiguen el mismo objetivo: facilitar la agregación y consumo de contenidos actualizados sin necesidad de visitar múltiples sitios web.

**Aprendizajes clave:**

La principal diferencia entre RSS y Atom radica en su filosofía de diseño. RSS 2.0 es más simple y flexible, con fechas en formato RFC 822 y una estructura menos rígida, lo que facilita su creación pero puede generar inconsistencias. Atom 1.0, por su parte, es más estricto y semánticamente rico, utilizando formato ISO 8601 para fechas y siendo más explícito en la definición de enlaces y relaciones entre elementos. Esta mayor precisión de Atom lo hace más robusto, aunque requiere mayor atención al detalle.

**Utilidad de la sindicación:**

Vemos la sindicación de contenidos especialmente útil en escenarios como:
- Agregación de noticias y blogs para consumo centralizado
- Notificaciones automáticas de actualizaciones en sitios web
- Distribución de podcasts y contenido multimedia
- Integración de contenidos entre diferentes plataformas y servicios
- Seguimiento eficiente de múltiples fuentes de información sin visitar cada sitio individualmente

**Experiencia de trabajo en equipo:**

Trabajar con roles divididos resultó muy productivo. La división permitió que cada miembro se especializara en un aspecto concreto (RSS, Atom, coordinación), profundizando en los detalles técnicos de cada formato. La coordinación fue fundamental para mantener coherencia entre ambos feeds y asegurar que las tres noticias fueran idénticas en contenido. Las pruebas con el agregador demostraron que ambos formatos funcionan correctamente y son interpretados de manera similar por las herramientas modernas, validando nuestro trabajo.

En definitiva, esta actividad nos ha dotado de conocimientos prácticos sobre tecnologías de sindicación que siguen siendo relevantes en el ecosistema web actual, especialmente en aplicaciones de agregación de contenidos, sistemas de notificaciones y distribución automatizada de información.

---

## 4. Evidencias

- **validacion_rss.png** – Captura del feed RSS validado correctamente.
- **validacion_atom.png** – Captura del feed Atom validado correctamente.
- **agregador_rss.png** – Visualización del feed RSS en el agregador.
- **agregador_atom.png** – Visualización del feed Atom en el agregador.

> Las imágenes se encuentran en la carpeta `/capturas/` incluida en el ZIP.
