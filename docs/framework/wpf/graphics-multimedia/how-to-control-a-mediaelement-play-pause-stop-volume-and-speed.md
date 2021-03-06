---
title: 'Cómo: Controlar un MediaElement (Reproducir, Pausar, Detener, Volumen y Velocidad)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: beeddc658f16d8b52142a8a79f9c61e4f7070b01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561396"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Cómo: Controlar un MediaElement (Reproducir, Pausar, Detener, Volumen y Velocidad)
En el ejemplo siguiente se muestra cómo controlar la reproducción de medios mediante un <xref:System.Windows.Controls.MediaElement>. En el ejemplo se crea un reproductor multimedia simple que permite reproducir, pausar, detener y avanzar o retroceder en el medio así como ajustar la proporción de volumen y la velocidad.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente crea la interfaz de usuario.  
  
> [!NOTE]
>  El <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propiedad de <xref:System.Windows.Controls.MediaElement> debe establecerse en `Manual` para poder interactivamente detener, pausar y reproducir el archivo multimedia.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Ejemplo  
 El código siguiente implementa la funcionalidad de los controles de interfaz de usuario de ejemplo. El <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, y <xref:System.Windows.Controls.MediaElement.Stop%2A> métodos se usan para reproducir, pausar y detener el elemento multimedia respectivamente. Cambiar el <xref:System.Windows.Controls.MediaElement.Position%2A> propiedad de la <xref:System.Windows.Controls.MediaElement> permite omitir de los medios. Por último, el <xref:System.Windows.Controls.MediaElement.Volume%2A> y <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> propiedades se utilizan para ajustar la velocidad de reproducción y el volumen de los medios.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Vea también  
 [Controlar un control MediaElement mediante un guión gráfico](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)
