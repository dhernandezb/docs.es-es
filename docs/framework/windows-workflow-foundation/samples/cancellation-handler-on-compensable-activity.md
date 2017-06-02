---
title: "Controlador de cancelaci&#243;n en una actividad compensable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Controlador de cancelaci&#243;n en una actividad compensable
En este ejemplo se muestra el uso de un controlador de cancelación en un objeto <xref:System.Activities.Statements.CompensableActivity>.  
  
 Este ejemplo incluye dos escenarios que muestran el uso de la cancelación de <xref:System.Activities.Statements.CompensableActivity>. El primero contiene una actividad compensable raíz que contiene tres actividades compensables secundarias.Dos actividades secundarias terminan de ejecutar sus cuerpos de actividad correctamente.Cuando el cuerpo de la tercera actividad secundaria se ejecuta, encuentra una excepción que se controla cancelando el proceso de la tercera actividad, tras lo cual se activa la cancelación de la actividad raíz.La lógica de la actividad raíz de este ejemplo es compensar las otras dos actividades secundarias que se completaron anteriormente.  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
  
```  
  
 El segundo escenario muestra cómo ejecutar <xref:System.Activities.Statements.TryCatch> en paralelo con <xref:System.Activities.Statements.Delay>, que finaliza antes de la bifurcación <xref:System.Activities.Statements.TryCatch>.La condición de la realización se establece en `true` una vez finalizada la primera bifurcación, lo que causa la cancelación de la otra bifurcación.  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
  
```  
  
### Para configurar, compilar y ejecutar el ejemplo  
  
1.  Abra CompensationCancellation.sln con [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Compile el ejemplo presionando CTRL\+MAYÚS\+B o seleccione "Compilar solución" en el menú Compilar.  
  
3.  Ejecute el ejemplo presionando F5 o seleccione "Iniciar depuración" en el menú Depurar.También, puede presionar Ctrl\+F5 o seleccionar "Iniciar sin depurar" en el menú Depurar.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo.Compruebe el siguiente directorio \(valor predeterminado\) antes de continuar.  
>   
>  `<>InstallDrive:\WF_WCF_Samples`  
>   
>  Si no existe este directorio, vaya a la página de [ejemplos de Windows Communication Foundation \(WCF\) y Windows Workflow Foundation \(WF\) Samples para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los ejemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] y [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<unidadDeInstalación>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`  
  
## Vea también