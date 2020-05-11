---
title: Speichern eines benutzerdefinierten Dokuments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705615"
---
# <a name="saving-a-custom-document"></a>Speichern eines benutzerdefinierten Dokuments
Die Umgebung verarbeitet die Befehle **Speichern**, **Speichern unter**und **Speichern aller** Befehle. Wenn ein Benutzer im Menü Datei auf **Speichern**, **Speichern unter** **oder Speichern von Allen** im Menü **Datei** klickt oder die Projektmappe schließt, was zu einem Speichern aller führt, tritt der folgende Vorgang auf.

 ![Kunden-Editor speichern](../../extensibility/internals/media/private.gif "Privat") Speichern, Speichern unter und Speichern aller Befehlsbehandlungen für einen benutzerdefinierten Editor

 Dieser Prozess wird in den folgenden Schritten beschrieben:

1. Für die Befehle **Speichern** und **Speichern** <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> unter verwendet die Umgebung den Dienst, um das aktive Dokumentfenster und damit die zu speichernden Elemente zu bestimmen. Sobald das aktive Dokumentfenster bekannt ist, findet die Umgebung den Hierarchiezeiger und die Elementkennung (itemID) für das Dokument in der laufenden Dokumenttabelle. Weitere Informationen finden Sie unter Ausführen der [Dokumenttabelle](../../extensibility/internals/running-document-table.md).

     Für den Befehl Alle speichern verwendet die Umgebung die Informationen in der Tabelle des ausgeführten Dokuments, um die Liste aller zu speichernden Elemente zu kompilieren.

2. Wenn die Lösung <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> einen Anruf empfängt, wird die Durchlaufensmenge durch den Satz ausgewählter Elemente durchlaufen (d. h. die mehrfachen Auswahlen, die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> vom Dienst verfügbar gemacht werden).

3. Bei jedem Element in der Auswahl verwendet die Lösung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> den Hierarchiezeiger, um die Methode aufzurufen, um zu bestimmen, ob der Menübefehl Speichern aktiviert werden soll. Wenn ein oder mehrere Elemente verschmutzt sind, ist der Befehl Speichern aktiviert. Wenn die Hierarchie einen Standard-Editor verwendet, delegiert die Hierarchie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> die Abfrage nach schmutzigem Status an den Editor, indem sie die Methode aufruft.

4. Bei jedem ausgewählten Element, das verschmutzt ist, verwendet <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> die Lösung den Hierarchiezeiger, um die Methode für die entsprechenden Hierarchien aufzurufen.

     Bei einem benutzerdefinierten Editor ist die Kommunikation zwischen dem Dokumentdatenobjekt und dem Projekt privat. Daher werden alle besonderen Persistenzbedenken zwischen diesen beiden Objekten behandelt.

    > [!NOTE]
    > Wenn Sie Ihre eigene Persistenz implementieren, müssen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Methode aufrufen, um Zeit zu sparen. Diese Methode überprüft, ob das Speichern der Datei sicher ist (z. B. ist die Datei nicht schreibgeschützt).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)
