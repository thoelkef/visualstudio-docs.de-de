---
title: Verwendung und Bereitstellung von Diensten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 351b5b5c0ab32ab7e8267864eddaae10459a23bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138339"
---
# <a name="using-and-providing-services"></a>Verwenden und die Bereitstellung von Diensten
Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet es sich um einen bestimmten Satz von Schnittstellen für einen anderen VSPackage zu nutzen. Beispielsweise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet die <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service alle VSPackage lädt. Dieser Dienst stellt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> -Schnittstelle, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages bieten Dienste eigene durch Verwendung der <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle...  
  
 Visual Studio bietet wichtige Dienste, z. B. Folgendes an:  
  
|IDE-Dienst|Beschreibung|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Bietet Zugriff auf IDE Umgang mit Grundfunktionen, VSPackages und die Registrierung Dienste.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Stellt grundlegende fensterverwaltungsfunktionalität und UI-bezogene Funktionen in der IDE, z. B. die Fähigkeit zum Erstellen von Tools und Dokumentfenster bereit.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Stellt grundlegende Lösung bezogenen Funktionen, z. B. das Aufzählen von Projekten, neue Projekte erstellen und überwachen projektänderungen bereit.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)  
 Zeigt die wichtigen Elemente eines Visual Studio-Diensts an.  
  
 [Gewusst wie: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)  
 Erläutert, wie anfordern (nutzen) eines Diensts.  
  
 [Gewusst wie: Bereitstellen eines Diensts](../extensibility/how-to-provide-a-service.md)  
 Erläutert, wie ein Dienst zur Verfügung.  
  
 [Gewusst wie: Bereitstellen eines asynchronen Visual Studio-Diensts](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Erläutert, wie einen asynchrone Dienst bereit.  
  
 [Gewusst wie: Problembehandlung bei Diensten](../extensibility/how-to-troubleshoot-services.md)  
 Beschreibt allgemeine Probleme, und informiert über Lösungen für sie.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)