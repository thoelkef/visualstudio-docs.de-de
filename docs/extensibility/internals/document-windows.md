---
title: Dokument Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708519"
---
# <a name="document-windows"></a>Dokumentfenster
In Visual Studio ist ein *Dokumentfenster* ein gerahmtes untergeordnetes Fenster, das einem MDI-Fenster (Multiple Document Interface) zugeordnet ist. Dokumentfenster werden in der Regel für die Anzeige und Änderung von Quellcode oder Text verwendet, können aber auch andere Funktionstypen hosten. Dokumentfenster:

- Kann in separaten horizontalen oder vertikalen Registerkartengruppen in der übergeordneten MDI organisiert werden, sodass mehrere Dateien gleichzeitig angezeigt werden können.

- Kann in beliebiger Reihenfolge im übergeordneten MDI angedockt werden.

- Kann frei schweben.

- Sind in Tab-Reihenfolge mit anderen MDI-Fenstern verknüpft.

  Die Befehle zum Gruppieren, Andocken und Floating finden Sie im Kontextmenü für eine Registerkarte Dokumentfenster.

  Weitere Informationen zum Fensterverhalten in Visual Studio finden Sie unter Anpassen von [Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="document-window-implementation"></a>Dokumentfensterimplementierung
 Dokumentfenster werden durch Implementieren eines Editors erstellt. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle erstellt Dokumentfenster als Teil der Instanziierung eines Editors. Weitere Informationen finden Sie [unter Legacy-Schnittstellen im Editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015).

> [!NOTE]
> Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> Schnittstelle, um Rückwärts- und Vorwärtsnavigationspunkte in einem Fenster bereitzustellen. Der Texteditor verwendet Textmarkierungen, um Navigationspunkte im Dokument zu identifizieren.

## <a name="the-running-document-table"></a>Die Tabelle "Laufendes Dokument"
 Die IDE verwendet die Tabelle "Dokument ausführen" (RDT), um den Status jedes Dokumentfensters nachzuverfolgen. Die RDT ist der Mechanismus, über den Dokumentfenster über Ereignisse benachrichtigt werden, z. B. wenn eine Projektmappe geschlossen wird oder wenn eine Datei bearbeitet wurde. Weitere Informationen finden Sie unter Ausführen der [Dokumenttabelle](../../extensibility/internals/running-document-table.md).

## <a name="see-also"></a>Weitere Informationen
- [Verzögertes Laden von Dokumenten](../../extensibility/internals/delayed-document-loading.md)
