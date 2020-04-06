---
title: Speichern eines Standarddokuments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705554"
---
# <a name="saving-a-standard-document"></a>Speichern eines Standarddokuments
Die Umgebung verarbeitet die Befehle Speichern, Speichern unter und Speichern aller Befehle. Wenn ein Benutzer im Menü **Datei** **"Speichern**", **Speichern unter**" oder **"Alle speichern"** auswählt oder die Projektmappe schließt, tritt **der**folgende Vorgang ein.

 ![Standard-Editor](../../extensibility/internals/media/public.gif "Öffentlich") Speichern, Speichern unter und Speichern Aller Befehlsbehandlungfürstand für einen Standard-Editor

 Dieser Prozess wird in den folgenden Schritten beschrieben:

1. Wenn die Befehle **Speichern** und **Speichern unter** <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> ausgewählt sind, verwendet die Umgebung den Dienst, um das aktive Dokumentfenster und damit die zu speichernden Elemente zu bestimmen. Sobald das aktive Dokumentfenster bekannt ist, findet die Umgebung den Hierarchiezeiger und die Elementkennung (itemID) für das Dokument in der laufenden Dokumenttabelle. Weitere Informationen finden Sie unter Ausführen der [Dokumenttabelle](../../extensibility/internals/running-document-table.md).

    Wenn der Befehl **Alle** speichern ausgewählt ist, verwendet die Umgebung die Informationen in der Tabelle des ausgeführten Dokuments, um die Liste aller zu speichernden Elemente zu kompilieren.

2. Wenn die Lösung <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> einen Anruf empfängt, wird die Durchlaufensmenge durch den Satz ausgewählter Elemente durchlaufen (d. h. die mehrfachen Auswahlen, die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> vom Dienst verfügbar gemacht werden).

3. Bei jedem Element in der Auswahl verwendet die Lösung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> den Hierarchiezeiger, um die Methode aufzurufen, um zu bestimmen, ob der Menübefehl **Speichern** aktiviert werden soll. Wenn ein oder mehrere Elemente verschmutzt sind, ist der Befehl **Speichern** aktiviert. Wenn die Hierarchie einen Standard-Editor verwendet, delegiert die Hierarchie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> die Abfrage nach schmutzigem Status an den Editor, indem sie die Methode aufruft.

4. Bei jedem ausgewählten Element, das verschmutzt ist, verwendet <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> die Lösung den Hierarchiezeiger, um die Methode für die entsprechenden Hierarchien aufzurufen.

    Es ist üblich, dass die Hierarchie einen Standardeditor verwendet, um das Dokument zu bearbeiten. In diesem Fall sollte das Dokumentdatenobjekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> für diesen Editor die Schnittstelle unterstützen. Nach Dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Empfang des Methodenaufrufs sollte das Projekt den Editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> darüber informieren, dass das Dokument durch Aufrufen der Methode für das Dokumentdatenobjekt gespeichert wird. Der Editor kann der Umgebung erlauben, das Dialogfeld <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> **Speichern** unter zu behandeln, indem er die Schnittstelle aufruft. `Query Service` Dadurch wird ein Zeiger <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> auf die Schnittstelle zurückgegeben. Der Editor muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> dann die Methode aufrufen und einen <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Zeiger über `pPersistFile` den Parameter an die Implementierung des Editors übergeben. Die Umgebung führt dann den Vorgang Speichern aus und stellt das Dialogfeld **Speichern** unter für den Editor bereit. Die Umgebung ruft dann mit <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>an den Editor zurück.

5. Wenn der Benutzer versucht, ein unbenanntes Dokument (d. h. ein zuvor nicht gespeichertes Dokument) zu speichern, wird tatsächlich ein Befehl Speichern unter ausgeführt.

6. Für den Befehl Speichern unter zeigt die Umgebung das Dialogfeld Speichern unter an und fordert den Benutzer zur Eingabe eines Dateinamens auf.

    Wenn sich der Name der Datei geändert hat, ist die Hierarchie für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>Aktualisierung der zwischengespeicherten Informationen des Dokumentrahmens durch Aufrufen (VSFPROPID_MkDocument) verantwortlich.

   Wenn der Befehl **Speichern unter** die Position des Dokuments verschiebt und die Hierarchie für den Dokumentspeicherort sensibel ist, ist die Hierarchie für die Übergabe des Besitzes des geöffneten Dokumentfensters an eine andere Hierarchie verantwortlich. Dies tritt z. B. auf, wenn das Projekt nachverfolgt, ob es sich bei der Datei um eine interne oder eine externe Datei (Verschiedene Datei) in Bezug auf das Projekt handelt. Gehen Sie wie folgt vor, um den Besitz einer Datei in das Projekt Verschiedene Dateien zu ändern.

## <a name="changing-file-ownership"></a>Ändern des Dateibesitzes

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>So ändern Sie den Dateibesitz in das Projekt Verschiedene Dateien

1. Abfragedienst für <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> die Schnittstelle.

     Ein Zeiger <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> auf wird zurückgegeben.

2. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> Sie`pszMkDocumentNew` `punkWindowFrame`die Methode ( , ) auf, um das Dokument in die neue Hierarchie zu übertragen. Die Hierarchie, die den Befehl Speichern unter ausführt, ruft diese Methode auf.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)
