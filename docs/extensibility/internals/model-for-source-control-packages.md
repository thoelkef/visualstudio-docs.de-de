---
title: Modell für Quellcodeverwaltungspakete | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707070"
---
# <a name="model-for-source-control-packages"></a>Modell für Quellcodeverwaltungspakete
Das folgende Modell stellt ein Beispiel für eine Quellcodeverwaltungsimplementierung dar. Im Modell werden die Schnittstellen angezeigt, die Sie implementieren müssen, sowie die Umgebungsdienste, die Sie aufrufen müssen. Wie alle Dienste rufen Sie tatsächlich die Methoden einer bestimmten Schnittstelle auf, die Sie über den Dienst erhalten. Die Namen der Klassen werden identifiziert, um die Art und Weise, wie die Quellcodeverwaltung durchgeführt wird, leichter zu erkennen.

 ![SCC&#95;TUP-Beispiele](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Beispiel-Quellcodeverwaltungsprojekt

## <a name="interfaces"></a>Schnittstellen
 Sie können die Quellcodeverwaltung für Ihre neuen Projekttypen in Visual Studio mithilfe der Liste der in der folgenden Tabelle gezeigten Schnittstellen implementieren.

|Schnittstelle|Zweck|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Wird von Projekten und Editoren aufgerufen, bevor sie Dateien speichern oder ändern (schmutzige Dateien). Auf diese Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> wird über den Dienst zugegriffen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Wird von Projekten aufgerufen, um die Berechtigung zum Hinzufügen, Entfernen oder Umbenennen einer Datei oder eines Verzeichnisses anzufordern. Diese Schnittstelle wird auch von Projekten aufgerufen, um die Umgebung zu informieren, wenn eine genehmigte Aktion zum Hinzufügen, Entfernen oder Umbenennen abgeschlossen ist. Auf sie wird <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> über den Dienst zugegriffen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Wird von einer Entität implementiert, die sich registriert, um benachrichtigt zu werden, wenn Projekte eine Datei oder ein Verzeichnis hinzufügen, umbenennen oder entfernen. Um sich für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>Ereignisbenachrichtigung zu registrieren, rufen Sie an.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Wird von Projekten aufgerufen, um sich beim Quellcodeverwaltungspaket zu registrieren und Informationen zum Quellcodeverwaltungsstatus zu erhalten. Auf diese Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> wird über den Dienst zugegriffen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Wird vom Projekt implementiert, um auf Quellcodeverwaltungsanforderungen für Informationen zu Dateien zu reagieren und die für die Projektdatei erforderlichen Quellcodeverwaltungseinstellungen abzufragen.|

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
