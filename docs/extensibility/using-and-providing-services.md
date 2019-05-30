---
title: Verwenden und Bereitstellen von Diensten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c9b0dbf2122b5a76d557cdd70da27660b886041
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337041"
---
# <a name="using-and-providing-services"></a>Verwenden und Bereitstellen von Diensten
Ein Dienst ist ein Vertrag zwischen zwei VSPackages. Ein VSPackage bietet es sich um einen bestimmten Satz von Schnittstellen für einen anderen VSPackage zu nutzen. Z. B. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bietet die <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service jedem VSPackage lädt. Dieser Dienst stellt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> -Schnittstelle, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).

 VSPackages können anbieten von Diensten, die Ihre eigenen durch die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle...

 Visual Studio bietet wichtige Dienste wie z. B. Folgendes an:

|IDE-Dienst|Beschreibung|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Bietet Zugriff auf IDE Umgang mit grundlegenden Funktionen, die VSPackages und der Registrierung services.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Bietet grundlegende fensterverwaltungsfunktionalität und UI-bezogene Funktionen in der IDE, z. B. die Fähigkeit zum Erstellen von Tools und Dokumentfenstern.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Bietet grundlegende Lösung bezogenen Funktionen, z.B. die Möglichkeit, Projekte auflisten, neue Projekte erstellen und Überwachen von Projekt wird geändert.|

## <a name="in-this-section"></a>In diesem Abschnitt
- [Dienstgrundlagen](../extensibility/internals/service-essentials.md) zeigt die wichtigen Elemente von Visual Studio-Dienst.

- [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md) wird erläutert, wie Sie anfordern (nutzen) eines Diensts.

- [Vorgehensweise: Geben Sie einen Dienst](../extensibility/how-to-provide-a-service.md) wird erläutert, wie Sie einen Dienst bereitstellen.

- [Vorgehensweise: Geben Sie ein asynchroner Dienst für Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) wird erläutert, wie einen asynchronen Dienst bereitstellen.

- [Vorgehensweise: Problembehandlung bei Services](../extensibility/how-to-troubleshoot-services.md) behandelt häufige Probleme und Lösungen dafür bietet.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)