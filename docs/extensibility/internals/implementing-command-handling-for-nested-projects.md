---
title: Implementieren der Befehls Behandlung für in der Liste eingefügte Projekte Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 628fde153441104e4bb504253d96235270b4b8fb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727079"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementieren der Befehlsbehandlung für geschachtelte Projekte
Die IDE kann Befehle übergeben, die über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> übergeben werden, und die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstellen an die an das Projekt übergebenen Projekte, oder übergeordnete Projekte können die Befehle filtern oder außer Kraft setzen.

> [!NOTE]
> Es können nur Befehle gefiltert werden, die normalerweise von dem übergeordneten Projekt behandelt werden. Befehle wie **Build** **und bereit** Stellung, die von der IDE verarbeitet werden, können nicht gefiltert werden.

 In den folgenden Schritten wird der Prozess zum Implementieren der Befehls Behandlung beschrieben.

## <a name="procedures"></a>Verfahren

#### <a name="to-implement-command-handling"></a>So implementieren Sie die Befehls Behandlung

1. Wenn der Benutzer ein geclustertes Projekt oder einen Knoten in einem geclusterte Projekt auswählt:

   1. Die IDE Ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>-Methode auf.

      \- oder -

   2. Wenn der Befehl in einem Hierarchie Fenster (z. b. einem Kontextmenü Befehl in Projektmappen-Explorer) stammt, ruft die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>-Methode für das übergeordnete Element des Projekts auf.

2. Das übergeordnete Projekt kann Parameter untersuchen, die an `QueryStatus`, z. b. `pguidCmdGroup` und `prgCmds`, übermittelt werden, um zu bestimmen, ob das übergeordnete Projekt die Befehle filtern soll. Wenn das übergeordnete Projekt zum Filtern von Befehlen implementiert ist, sollte Folgendes festgelegt werden:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Dann sollte das übergeordnete Projekt `S_OK` zurückgeben.

    Wenn das übergeordnete Projekt den Befehl nicht filtert, sollte nur `S_OK` zurückgegeben werden. In diesem Fall leitet die IDE automatisch den Befehl an das untergeordnete Projekt weiter.

    Das übergeordnete Projekt muss den Befehl nicht an das untergeordnete Projekt weiterleiten. Die IDE führt diese Aufgabe aus.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)