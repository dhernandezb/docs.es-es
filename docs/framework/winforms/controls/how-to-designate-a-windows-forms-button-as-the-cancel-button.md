---
title: 'Cómo: Definir un botón de formularios Windows Forms como el botón Cancelar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: efe68ec8e5c34607bb8f865b5d0c7919a0377ab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530876"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Cómo: Definir un botón de formularios Windows Forms como el botón Cancelar
En cualquier formulario Windows Forms, puede designar un <xref:System.Windows.Forms.Button> que sea el botón Cancelar del control. Cada vez que el usuario presiona la tecla ESC, sin tener en cuenta que otro control en el formulario tiene el foco, se hace clic en un botón de cancelación. Habitualmente, este botón se programa para permitir que el usuario salga rápidamente de una operación sin confirmar ninguna acción.  
  
### <a name="to-designate-the-cancel-button"></a>Para designar el botón Cancelar  
  
1.  Establezca el formulario <xref:System.Windows.Forms.Form.CancelButton%2A> propiedad correspondientes <xref:System.Windows.Forms.Button> control.  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Información general sobre el control Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Maneras de seleccionar un control Button de formularios Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Responder a clics de botones en Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Designar un botón de Windows Forms como botón para aceptar](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Botón (control)](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
