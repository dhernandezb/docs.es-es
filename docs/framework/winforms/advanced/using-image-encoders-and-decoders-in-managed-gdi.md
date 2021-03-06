---
title: Usar codificadores y descodificadores de imagen en la interfaz GDI+ administrada
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524506"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Usar codificadores y descodificadores de imagen en la interfaz GDI+ administrada
El <xref:System.Drawing> espacio de nombres proporciona la <xref:System.Drawing.Image> y <xref:System.Drawing.Bitmap> clases para almacenar y manipular imágenes. Mediante el uso de codificadores de imágenes en [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], puede escribir imágenes de la memoria en el disco. Mediante el uso de descodificadores de imágenes en [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], puede cargar imágenes desde el disco en la memoria. Un codificador convierte los datos en un <xref:System.Drawing.Image> o <xref:System.Drawing.Bitmap> objeto en un formato de archivo de disco designado. Un descodificador traduce los datos en un archivo de disco para el formato requerido por la <xref:System.Drawing.Image> y <xref:System.Drawing.Bitmap> objetos.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tiene integrados codificadores y descodificadores que admiten los siguientes tipos de archivo:  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] También tiene descodificadores integrados que admiten los siguientes tipos de archivo:  
  
-   WMF  
  
-   EMF  
  
-   ICONO  
  
 Los temas siguientes describen los codificadores y descodificadores con más detalle:  
  
## <a name="in-this-section"></a>En esta sección  
 [Enumerar los codificadores instalados](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 Describe cómo enumerar los codificadores disponibles en un equipo.  
  
 [Enumerar los descodificadores instalados](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 Describe cómo enumerar los descodificadores disponibles en un equipo.  
  
 [Determinar los parámetros admitidos por un codificador](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Describe cómo mostrar el <xref:System.Drawing.Imaging.EncoderParameters> admitidos por un codificador.  
  
 [Convertir una imagen BMP en una imagen PNG](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 Describe cómo guardar una imagen en un formato de imagen distinto.  
  
 [Establecer el nivel de compresión de imágenes JPEG](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 Describe cómo cambiar el nivel de calidad de una imagen.  
  
## <a name="reference"></a>Referencia  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [About GDI+ Managed Code](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md) (Acerca del código administrado de GDI+)  
  
 [Imágenes, mapas de bits y metarchivos](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
