---
title: "Gewusst wie: Verwenden von GetGlobalService | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dienste, GetGlobalService"
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Gewusst wie: Verwenden von GetGlobalService
In einigen Fällen müssen Sie möglicherweise einen Dienst eines Tool\- oder Steuerelementcontainer ab, der nicht positioniert wurde. Andernfalls handelt es positioniert wurde mit einem Dienstanbieter, der nicht im Dienst auskennt, den Sie verwenden möchten.  Beispielsweise können Sie mit dem Aktivitätsprotokoll aus einem Steuerelement schreiben.  Weitere Informationen über diese und andere Szenarios finden Sie unter [Gewusst wie: Problembehandlung bei Services](../extensibility/how-to-troubleshoot-services.md).  
  
 Sie können die meisten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Dienste abrufen, indem Sie die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>\-Methode aufrufen.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> beruht auf einem zwischengespeicherten Dienstanbieter, das das erste Mal ein beliebiges VSPackage initialisiert wird, das von <xref:Microsoft.VisualStudio.Shell.Package> abgeleitet ist, wird positioniert.  Sie müssen sicherstellen, dass diese Bedingung erfüllt ist, oder für einen Dienst vorbereitet sein. Andernfalls NULL  
  
 Glücklicherweise <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Regel ordnungsgemäß funktioniert.  
  
-   Wenn ein VSPackage eine Dienst bereitstellt, die nur einen anderen VSPackage bekannt ist, wird ein VSPackage, das den Dienst anfordert, positioniert, bevor ein VSPackage, das den Dienst bereitstellt, geladen werden.  
  
-   Wenn ein Toolfenster von VSPackages erstellt wird, wird ein VSPackage positioniert, bevor das Toolfenster erstellt wird.  
  
-   Wenn ein Steuerelementcontainer über ein Toolfenster gehostet wird, das von einem VSPackage erstellt wird, wird ein VSPackage positioniert, bevor der Steuerelementcontainer erstellt wird.  
  
### Um einen Dienst aus ein Tool\- oder Steuerelementcontainer abrufen  
  
-   Fügen Sie diesen Code im Konstruktor oder im Toolfenster im Steuerelementcontainer ein:  
  
     [!code-vb[UseGetGlobalService#1](../misc/codesnippet/VisualBasic/how-to-use-getglobalservice_1.vb)]
     [!code-cs[UseGetGlobalService#1](../misc/codesnippet/CSharp/how-to-use-getglobalservice_1.cs)]  
  
     Dieser Code ruft ein SVsActivityLog\-Dienst und wandelt es in eine Schnittstelle um <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> , die verwendet werden kann, um auf den Aktivitätsprotokoll zu schreiben.  Ein entsprechendes Beispiel finden Sie unter [Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
## Siehe auch  
 [Gewusst wie: Problembehandlung bei Services](../extensibility/how-to-troubleshoot-services.md)   
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)