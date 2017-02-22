---
title: "Verwendung und Bereitstellung von Diensten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Beispiele [Visual Studio SDK], Dienste"
  - "Visual Studio, Dienste"
  - "Dienste"
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
caps.handback.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
---
# Verwendung und Bereitstellung von Diensten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet einen bestimmten Satz von Schnittstellen für einen anderen VSPackage nutzen. Z. B. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet die <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service alle VSPackage lädt. Dieser Service bietet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> \-Schnittstelle, die zum Schreiben in die Protokolldatei für die Aktivität verwendet werden kann. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages bieten Dienste ihre eigenen durch Verwendung der <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle...  
  
 Visual Studio bietet wichtige Dienste wie den folgenden:  
  
|IDE\-Dienst|Beschreibung|  
|-----------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Bietet Zugriff auf IDE Umgang mit grundlegenden Funktionen, die VSPackages und die Registrierung Dienste.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Enthält grundlegende Windowing und UI\-bezogene Funktionen in der IDE, z. B. die Möglichkeit zum Erstellen von Tools und Dokumentfenster.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Stellt grundlegende Lösung\-Funktionen, z. B. die Möglichkeit, Projekte auflisten, neue Projekte erstellen und überwachen Sie Projekt bereit.|  
  
## In diesem Abschnitt  
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)  
 Stellt die wichtigen Elemente der Visual Studio\-Dienst.  
  
 [Gewusst wie: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)  
 Beschreibt, wie Sie anfordern \(nutzen\) eines Diensts.  
  
 [Gewusst wie: Bereitstellen ein Diensts](../extensibility/how-to-provide-a-service.md)  
 Erläutert, wie ein Dienst zur Verfügung.  
  
 [Gewusst wie: Bereitstellen einen asynchronen Visual Studio\-Dienst](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Erläutert, wie einen asynchronen Dienst bereitstellen.  
  
 [Gewusst wie: Problembehandlung bei Services](../extensibility/how-to-troubleshoot-services.md)  
 Erläutert allgemeine Probleme und Lösungen werden dargestellt.  
  
## Verwandte Abschnitte  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)