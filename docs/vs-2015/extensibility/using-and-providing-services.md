---
title: Verwenden und Bereitstellen von Diensten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f58e29797e9a7760aa0f48c68868199f51b3c92
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177437"
---
# <a name="using-and-providing-services"></a>Verwenden und Bereitstellen von Diensten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet es sich um einen bestimmten Satz von Schnittstellen für einen anderen VSPackage zu nutzen. Z. B. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bietet die <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service jedem VSPackage lädt. Dieser Dienst stellt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> -Schnittstelle, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages können anbieten von Diensten, die Ihre eigenen durch die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle...  
  
 Visual Studio bietet wichtige Dienste wie z. B. Folgendes an:  
  
|IDE-Dienst|Beschreibung|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Bietet Zugriff auf IDE Umgang mit grundlegenden Funktionen, die VSPackages und der Registrierung services.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Bietet grundlegende fensterverwaltungsfunktionalität und UI-bezogene Funktionen in der IDE, z. B. die Fähigkeit zum Erstellen von Tools und Dokumentfenstern.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet grundlegende Lösung bezogenen Funktionen, z.B. die Möglichkeit, Projekte auflisten, neue Projekte erstellen und Überwachen von Projekt wird geändert.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)  
 Zeigt die wichtigen Elemente von Visual Studio-Dienst.  
  
 [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)  
 Behandelt das anfordern (nutzen) eines Diensts.  
  
 [Vorgehensweise: Bereitstellen eines Diensts](../extensibility/how-to-provide-a-service.md)  
 Erläutert, wie Sie einen Dienst bereitstellen.  
  
 [Vorgehensweise: Bereitstellen eines asynchronen Visual Studio-Diensts](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Erläutert, wie einen asynchronen Dienst bereitstellen.  
  
 [Vorgehensweise: Problembehandlung bei Diensten](../extensibility/how-to-troubleshoot-services.md)  
 Behandelt häufige Probleme und Lösungen dafür bietet.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
