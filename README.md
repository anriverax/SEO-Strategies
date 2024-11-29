# SEO-Strategies

## 1. Reducir el tamaño de las imágenes
### Herramientas para compresión

- Online:
  - TinyPNG
  - ImageOptim

- CLI/Automatización:
  - Sharp: Una biblioteca Node.js para optimización y transformación de imágenes.
  - Imagemin: Otra herramienta poderosa para optimizar imágenes en tus proyectos.

Consejos
- Usa formatos modernos como WebP o AVIF para reducir el tamaño del archivo sin pérdida significativa de calidad. Estos formatos tienen mejor compresión en comparación con JPG o PNG.
- Elige una resolución adecuada al propósito (por ejemplo, no uses imágenes de 3000x3000px si solo las necesitas de 600x400px).

## 2. Carga diferida (Lazy Loading)

Implementa lazy loading para cargar imágenes únicamente cuando sean visibles en el viewport del usuario. Esto mejora el tiempo de carga inicial de la página.

```bash
import React from "react";

const LazyImage = ({ src, alt, className }: { src: string; alt: string; className?: string }) => {
  return (
    <img
      src={src}
      alt={alt}
      className={className}
      loading="lazy" // habilita la carga diferida
    />
  );
};

export default LazyImage;
```

## 3. Usar atributos correctos para SEO

Agregar los atributos y configuraciones adecuadas puede mejorar el rendimiento SEO:

- Alt text: Describe el contenido de la imagen, útil para accesibilidad y SEO.
- Título: Opcional, pero puede agregar contexto adicional.
- Formato adecuado: Asegúrate de que el formato sea soportado por todos los navegadores relevantes.

```bash
<img src="optimized-image.webp" alt="Descripción clara de la imagen" title="Título opcional de la imagen" />
```

## 4. Implementar imágenes responsivas
Usa el atributo srcset para que el navegador cargue automáticamente la versión más adecuada de la imagen según el tamaño de pantalla.

```bash
<img 
  src="image-600px.jpg" 
  srcset="image-400px.jpg 400w, image-800px.jpg 800w" 
  sizes="(max-width: 600px) 100vw, 50vw" 
  alt="Descripción de la imagen" 
/>
```

## 5. Servir imágenes desde una CDN

Utilizar una Red de Distribución de Contenidos (CDN) mejora significativamente la carga, especialmente para usuarios ubicados lejos del servidor principal. Servicios como Cloudinary, Imgix, o ImageKit pueden ser una gran opción.

## 6. Optimización en Next.js (opcional)

Si estás usando Next.js, puedes aprovechar su componente Image para optimización automática.

```bash
import Image from 'next/image';

const MyComponent = () => {
  return (
    <Image 
      src="/path-to-image.webp" 
      alt="Descripción clara de la imagen" 
      width={600} 
      height={400} 
      priority // si es una imagen importante para el SEO (ej. portada)
    />
  );
};

export default MyComponent;
```

#### Ventajas:

- Comprime las imágenes automáticamente.
- Implementa lazy loading de forma predeterminada.
- Genera diferentes tamaños de imágenes para diferentes dispositivos.

## 7. Auditar imágenes con Lighthouse

Puedes verificar el rendimiento y las optimizaciones necesarias con la pestaña Lighthouse del navegador:

- Ve a Lighthouse en las herramientas de desarrollo.
- Ejecuta un reporte de "Performance".
- Identifica las recomendaciones bajo "Reduce image load times" o "Serve images in next-gen formats".

8. Cacheo de imágenes
Configura los encabezados HTTP para almacenar en caché imágenes y evitar que se vuelvan a descargar en cada visita:

```bash
Cache-Control: max-age=31536000, immutable
```

## 8. Metaetiqueta

- Title
  - Una de las partes más importantes para SEO. Incluye la palabra clave principal al inicio.
  - El título debe ser corto y preciso (idealmente entre 50-60 caracteres). Un título muy largo puede cortarse en los resultados de búsqueda.
  - Asegúrar que cada página tenga un H1 único y relevante con tus palabras clave.
  - Subtítulos (H2, H3, etc.): Organiza tu contenido con subtítulos que incluyan palabras clave relacionadas.
- Description
  - La descripción debe tener máximo 160 caracteres. Google suele cortar cualquier texto adicional.
- Caninical
  - Debe de ser la url de la página actual a la que se está accediendo.
- MetaKeywords
  - El uso de meta keywords está obsoleto para los motores de búsqueda como Google (ya no las utilizan para posicionamiento). Puedes eliminarlas o mantenerlas si son necesarias para otros motores de búsqueda secundarios.
  - Sugerencia: Si decides mantenerlas, reduce su extensión a unas 10-15 palabras clave para mejorar claridad y relevancia.

## Mejoras adicionales

### 1. Metaetiquetas para Redes Sociales

Estas etiquetas son útiles para mejorar la presentación de la página al compartirse en plataformas como Facebook, Twitter y LinkedIn.

```bash
<meta property="og:title" content="title" />
<meta property="og:description" content="description" />
<meta property="og:url" content="url-de-la-pagina-que-se-comparte" />
<meta property="og:type" content="website" />
<meta property="og:image" content="url-de-la-imagen" />
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="title" />
<meta name="twitter:description" content="description" />
<meta name="twitter:image" content="url-de-la-imagen" />
```

### 2. Hreflang para Sitios Multilingües

Si el sitio está disponible en varios idiomas, se pueden añadir etiquetas hreflang para informar a los motores de búsqueda de las versiones disponibles.

```bash
<link rel="alternate" hreflang="en" href="https://abposus.com/" />
<link rel="alternate" hreflang="es" href="https://abposus.com/es/" />
```

## schema.org

El uso de datos estructurados ayuda a los motores de búsqueda a entender mejor tu contenido. Puedes implementar JSON-LD para describir tu página.

```bash
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Name Solutions",
  "url": "https://url.com/",
  "logo": "https://url.com/logo.png",
  "description": "Boost your business, the perfect point of sale system.",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 POS Street",
    "addressLocality": "City",
    "addressRegion": "State",
    "postalCode": "12345",
    "addressCountry": "US"
  },
  "telephone": "+1-800-123-4567"
}
</script>
```
Esto puede ayudar a que Google muestre rich snippets en los resultados de búsqueda.








