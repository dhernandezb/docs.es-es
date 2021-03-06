---
title: 'Cómo: Usar un diccionario de recursos en el ámbito de aplicación'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dictionaries [WPF], resource
- resource dictionaries [WPF], application-scope
- application-scope resource dictionaries
ms.assetid: 53857682-bd2c-4f2c-8f25-1307d0b451a2
ms.openlocfilehash: 081ce8d350995d5321acbb24d220bed229ff17ae
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43801363"
---
# <a name="how-to-use-an-application-scope-resource-dictionary"></a>Cómo: Usar un diccionario de recursos en el ámbito de aplicación
En este ejemplo se muestra cómo definir y usar un diccionario de recursos personalizado de ámbito de la aplicación.  
  
## <a name="example"></a>Ejemplo  
 <xref:System.Windows.Application> expone un almacén de ámbito de la aplicación para los recursos compartidos: <xref:System.Windows.Application.Resources%2A>. De forma predeterminada, el <xref:System.Windows.Application.Resources%2A> propiedad se inicializa con una instancia de la <xref:System.Windows.ResourceDictionary> tipo. Utilice esta instancia cuando obtenga y establezca las propiedades de ámbito de la aplicación mediante <xref:System.Windows.Application.Resources%2A>. Para obtener más información, consulte [Cómo: obtener y establecer un recurso de ámbito de la aplicación](https://msdn.microsoft.com/library/39e0420c-c9fc-47dc-8956-fdd95b214095).
  
 Si tiene varios recursos que establecen mediante <xref:System.Windows.Application.Resources%2A>, en su lugar, puede usar un diccionario de recursos personalizado para almacenar esos recursos y establecer <xref:System.Windows.Application.Resources%2A> con él en su lugar. A continuación muestra cómo declarar un diccionario de recursos personalizado mediante XAML.
  
 [!code-xaml[HOWTOResourceDictionaries#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MyResourceDictionary.xaml#1)]  
  
 Intercambio de diccionarios de recursos completo mediante <xref:System.Windows.Application.Resources%2A> le permite admitir temas del ámbito de aplicación, donde cada tema se encapsula mediante un diccionario de recursos único. En el ejemplo siguiente se muestra cómo establecer <xref:System.Windows.ResourceDictionary>.  
  
 [!code-xaml[HOWTOResourceDictionaries#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/App.xaml#2)]  
  
 La siguiente muestra cómo puede obtener los recursos del ámbito de la aplicación desde el diccionario de recursos expuesto por <xref:System.Windows.Application.Resources%2A> en XAML.  
  
 [!code-xaml[HOWTOResourceDictionaries#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml#4)]  
  
 A continuación, se muestra cómo puede obtener también los recursos en el código.  
  
 [!code-csharp[HOWTOResourceDictionaries#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToResourceDictionaries/CSharp/MainWindow.xaml.cs#3)]
 [!code-vb[HOWTOResourceDictionaries#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToResourceDictionaries/VB/MainWindow.xaml.vb#3)]  
  
 Existen dos consideraciones al usar <xref:System.Windows.Application.Resources%2A>. Primero, el diccionario *clave* es un objeto, por lo que debe usar exactamente la misma instancia del objeto al establecer y obtener un valor de propiedad. (Tenga en cuenta que la clave distingue mayúsculas de minúsculas cuando se utiliza una cadena). Segundo, el diccionario *valor* es un objeto, por lo que tendrá que convertir el valor al tipo deseado al obtener un valor de propiedad.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.ResourceDictionary>  
 <xref:System.Windows.Application.Resources%2A>  
 [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Diccionarios de recursos combinados](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)
