---
title: Dokument Fenster | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d29d64090320a8f62491209773145c024564efa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186634"
---
# <a name="document-windows"></a>Dokumentfenster
Ein *Dokument Fenster* in Visual Studio ist ein untergeordnetes Fenster, das einem MDI-Fenster (Multiple Document Interface) zugeordnet ist. Dokument Fenster werden in der Regel zum Anzeigen und Ändern von Quellcode oder Text verwendet, Sie können jedoch auch andere funktionale Typen hosten. Dokument Fenster:

- Kann in separaten horizontalen oder vertikalen Registerkarten Gruppen im übergeordneten MDI organisiert werden, sodass mehrere Dateien gleichzeitig angezeigt werden können.

- Kann in beliebiger Reihenfolge in der übergeordneten MDI angedockt werden.

- Kann frei in den Umlauf gebracht werden.

- Sind in der Aktivier Reihenfolge mit anderen MDI-Fenstern verknüpft.

  Die Befehle zum Gruppieren, Andocken und unverankerten finden Sie im Kontextmenü für eine Dokument Fenster-Registerkarte.

  Weitere Informationen zum Fenster Verhalten in Visual Studio finden Sie unter [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Dokument Fenster Implementierung
 Dokument Fenster werden erstellt, indem ein Editor implementiert wird. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>-Schnittstelle erstellt Dokument Fenster als Teil der Instanziierung eines Editors. Weitere Informationen finden Sie unter [Legacy Schnittstellen im Editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Um Navigationspunkte rückwärts und vorwärts in einem Fenster bereitzustellen, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation>-Schnittstelle. Der Text-Editor verwendet Textmarker zur Identifizierung von Navigationspunkten im Dokument.

## <a name="the-running-document-table"></a>Die laufende Dokument Tabelle
 Die IDE verwendet die laufende dokumententabelle (RDT), um den Status jedes Dokument Fensters zu verfolgen. Der RDT ist der Mechanismus, über den Dokument Fenster über Ereignisse benachrichtigt werden, z. b. Wenn eine Projekt Mappe geschlossen wird oder wenn eine Datei bearbeitet wurde. Weitere Informationen finden Sie unter [Ausführen der Dokument Tabelle](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Siehe auch
- [Verzögerte Dokument Ladevorgänge](../../extensibility/internals/delayed-document-loading.md)