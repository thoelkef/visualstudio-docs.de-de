---
title: Implementieren der Befehlsbehandlung für verschachtelte Projekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707600"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementieren der Befehlsbehandlung für geschachtelte Projekte
Die IDE kann Befehle übergeben, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> über die und die Schnittstellen an verschachtelte Projekte übergeben werden, oder übergeordnete Projekte können die Befehle filtern oder überschreiben.

> [!NOTE]
> Nur Befehle, die normalerweise vom übergeordneten Projekt verarbeitet werden, können gefiltert werden. Befehle wie **Build** und **Deploy,** die von der IDE verarbeitet werden, können nicht gefiltert werden.

 Die folgenden Schritte beschreiben den Prozess zum Implementieren der Befehlsbehandlung.

## <a name="procedures"></a>Prozeduren

#### <a name="to-implement-command-handling"></a>So implementieren Sie die Befehlsbehandlung

1. Wenn der Benutzer ein verschachteltes Projekt oder einen Knoten in einem verschachtelten Projekt auswählt:

   1. Die IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ruft die Methode auf.

      – oder –

   2. Wenn der Befehl in einem Hierarchiefenster stammt, z. B. einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> Kontextmenübefehl im Projektmappen-Explorer, ruft die IDE die Methode auf dem übergeordneten Projekt auf.

2. Das übergeordnete Projekt kann Parameter `QueryStatus`untersuchen, `pguidCmdGroup` die `prgCmds`an übergeben werden sollen, z. B. und , um zu bestimmen, ob das übergeordnete Projekt die Befehle filtern soll. Wenn das übergeordnete Projekt zum Filtern von Befehlen implementiert ist, sollte Folgendes festgelegt werden:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Dann sollte das `S_OK`übergeordnete Projekt zurückkehren.

    Wenn das übergeordnete Projekt den Befehl nicht `S_OK`filtert, sollte es einfach zurückgeben. In diesem Fall leitet die IDE den Befehl automatisch an das untergeordnete Projekt weiter.

    Das übergeordnete Projekt muss den Befehl nicht an das untergeordnete Projekt weiterleiten. Die IDE führt diese Aufgabe aus.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
