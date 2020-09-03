---
title: Verwenden von und Bereitstellen von Diensten | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177437"
---
# <a name="using-and-providing-services"></a>Verwenden und Bereitstellen von Diensten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet einen bestimmten Satz von Schnittstellen für ein anderes VSPackage, das verwendet werden soll. Beispielsweise [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bietet den <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Dienst einem beliebigen VSPackage, das er lädt. Dieser Dienst stellt die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle bereit, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages können eigene Dienste anbieten, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle verwenden.  
  
 Visual Studio bietet wichtige Dienste wie die folgenden:  
  
|IDE-Dienst|Beschreibung|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Bietet Zugriff auf IDE-Dienste, die mit den grundlegenden Funktionen, VSPackages und der Registrierung in Zusammenhang stehen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Bietet grundlegende Fenster Funktionen und UI-bezogene Funktionen in der IDE, z. b. die Möglichkeit zum Erstellen von Tools und Dokument Fenstern.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet grundlegende Funktionen für die Lösung, z. b. die Möglichkeit, Projekte aufzulisten, neue Projekte zu erstellen und Projektänderungen zu überwachen.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)  
 Stellt die wichtigen Elemente eines Visual Studio-Dienstanbieter dar.  
  
 [Gewusst wie: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)  
 Erläutert, wie ein Dienst angefordert (genutzt) wird.  
  
 [Gewusst wie: Bereitstellen eines Diensts](../extensibility/how-to-provide-a-service.md)  
 Erläutert, wie Sie einen Dienst bereitstellen.  
  
 [Gewusst wie: Bereitstellen eines asynchronen Visual Studio-Diensts](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Erläutert, wie ein asynchroner Dienst bereitgestellt wird.  
  
 [Gewusst wie: Problembehandlung bei Diensten](../extensibility/how-to-troubleshoot-services.md)  
 Erläutert häufige Probleme und stellt Ihnen Lösungen vor.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
