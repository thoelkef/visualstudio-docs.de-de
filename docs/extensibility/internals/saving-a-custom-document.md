---
title: Speichern eines benutzerdefinierten Dokuments | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf67335b6a12b966eb148b3f8dcaf16339e2a29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724075"
---
# <a name="saving-a-custom-document"></a>Speichern eines benutzerdefinierten Dokuments
Die Umgebung verarbeitet die Befehle " **Speichern**", " **Speichern**unter" und " **Alle speichern** ". Wenn ein Benutzer auf " **Speichern**", " **Speichern**unter" **oder "Alles speichern** " im Menü "Datei" klickt oder die Projekt **Mappe** schließt, was zu "Alles speichern" führt, wird der folgende Vorgang ausgeführt.

 ![Speichern des Kunden-Editors](../../extensibility/internals/media/private.gif "Private") Speichern, speichern unter und Speichern der gesamten Befehls Behandlung für einen benutzerdefinierten Editor

 Dieser Vorgang wird in den folgenden Schritten beschrieben:

1. Für die Befehle " **Speichern** " und " **Speichern** unter" verwendet die Umgebung den <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>-Dienst, um das aktive Dokument Fenster zu bestimmen, und damit die Elemente, die gespeichert werden sollen. Sobald das aktive Dokument Fenster bekannt ist, findet die Umgebung den Hierarchie Zeiger und den Element Bezeichner (Itemid) für das Dokument in der aktiven Dokument Tabelle. Weitere Informationen finden Sie unter [Ausführen der Dokument Tabelle](../../extensibility/internals/running-document-table.md).

     Für den Befehl Alle speichern verwendet die Umgebung die Informationen in der laufenden dokumententabelle, um die Liste aller zu speichernden Elemente zu kompilieren.

2. Wenn die Lösung einen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>-Befehl empfängt, durchläuft Sie den Satz ausgewählter Elemente (d. h. die Mehrfachauswahl, die vom <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>-Dienst verfügbar gemacht wird).

3. Bei jedem Element in der Auswahl verwendet die Projekt Mappe den Hierarchie Zeiger, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>-Methode aufzurufen, um zu bestimmen, ob der Menübefehl speichern aktiviert werden soll. Wenn ein oder mehrere Elemente geändert werden, ist der Befehl speichern aktiviert. Wenn in der Hierarchie ein Standard-Editor verwendet wird, delegiert die Hierarchie die Abfrage des geänderten Status an den Editor, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>-Methode aufgerufen wird.

4. Bei jedem ausgewählten Element, das geändert wird, verwendet die Projekt Mappe den Hierarchie Zeiger, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>-Methode in den entsprechenden Hierarchien aufzurufen.

     Im Fall eines benutzerdefinierten Editors ist die Kommunikation zwischen dem Dokument Datenobjekt und dem Projekt privat. Daher werden alle besonderen Persistenzprobleme zwischen diesen beiden Objekten behandelt.

    > [!NOTE]
    > Wenn Sie Ihre eigene Persistenz implementieren, achten Sie darauf, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>-Methode aufzurufen, um Zeit zu sparen. Mit dieser Methode wird überprüft, ob die Datei sicher gespeichert werden kann (z. b. wenn die Datei nicht schreibgeschützt ist).

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)