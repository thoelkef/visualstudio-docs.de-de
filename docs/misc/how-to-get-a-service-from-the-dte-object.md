---
title: "Gewusst wie: Abrufen eines Diensts vom DTE-Objekt | Microsoft Docs"
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
  - "Dienste, des DTE-Objekts"
ms.assetid: c26a51d4-86f0-454b-9625-5443e55eec7d
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Gewusst wie: Abrufen eines Diensts vom DTE-Objekt
Ein Dienst kann von jedem Programm abgerufen werden, das über [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Zugriff auf das <xref:EnvDTE.DTEClass>\-Objekt verfügt.  Beispielsweise können Sie den Assistenten aus einem Dienst <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> vom DTE\-Objekt zugreifen.  Sie können diesen Dienst verwenden, um zum Aktivitätsprotokoll zu schreiben.  Weitere Informationen finden Sie unter [Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
 Das DTE\-Objekt implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, die Sie verwenden können, um für einen Dienst aus verwaltetem Code abfragen, indem Sie <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>verwenden.  
  
### Um einen Dienst vom DTE\-Objekt abrufen  
  
1.  Der folgende Code erstellt <xref:Microsoft.VisualStudio.Shell.ServiceProvider> vom DTE\-Objekt und ruft <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> mit dem Typ des <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Dienstes an.  Der Dienst wird auf die Schnittstelle umgewandelt <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>, die verwendet wird, um einen Eintrag im Aktivitätsprotokoll zu schreiben.  Weitere Informationen abou, wie zum Aktivitätsprotokoll finden Sie unter schreibt [Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
     [!code-cs[GetAServiceFromTheDTEObject#1](../misc/codesnippet/CSharp/how-to-get-a-service-from-the-dte-object_1.cs)]
     [!code-vb[GetAServiceFromTheDTEObject#1](../misc/codesnippet/VisualBasic/how-to-get-a-service-from-the-dte-object_1.vb)]  
  
## Siehe auch  
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)