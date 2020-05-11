---
title: Nutzung und Bereitstellung von Diensten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698740"
---
# <a name="using-and-providing-services"></a>Verwenden und Bereitstellen von Diensten
Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet einen bestimmten Satz von Schnittstellen für ein anderes VSPackage zu verbrauchen. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bietet den <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Dienst beispielsweise für jedes zu ladende VSPackage an. Dieser Dienst <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> stellt die Schnittstelle bereit, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).

 VSPackages kann eigene Dienste über <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> die Schnittstelle anbieten.

 Visual Studio bietet wichtige Dienste, z. B. die folgenden:

|IDE-Dienst|BESCHREIBUNG|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Bietet Zugriff auf IDE-Dienste, die sich mit grundlegenden Funktionen, VSPackages und der Registrierung befassen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Bietet grundlegende Fenster und UI-bezogene Funktionen in der IDE, z. B. die Möglichkeit, Tools und Dokumentfenster zu erstellen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet grundlegende lösungsbezogene Funktionen, z. B. die Möglichkeit, Projekte aufzuzählen, neue Projekte zu erstellen und Projektänderungen zu überwachen.|

## <a name="in-this-section"></a>In diesem Abschnitt
- [Service Essentials](../extensibility/internals/service-essentials.md) Stellt die wichtigen Elemente eines Visual Studio-Dienstes vor.

- [Gewusst wie: Erhalten Sie einen Service](../extensibility/how-to-get-a-service.md) Erläutert, wie ein Dienst anfordert (verbraucht) wird.

- [Gewusst wie: Bereitstellen eines Dienstes](../extensibility/how-to-provide-a-service.md) Erläutert, wie ein Dienst bereitzustellen ist.

- [Gewusst wie: Bereitstellen eines asynchronen Visual Studio-Dienstes](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Erläutert, wie ein asynchroner Dienst bereitzustellen ist.

- [Gewusst wie: Troubleshoot Services](../extensibility/how-to-troubleshoot-services.md) Erläutert häufige Probleme und stellt Lösungen für diese vor.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
