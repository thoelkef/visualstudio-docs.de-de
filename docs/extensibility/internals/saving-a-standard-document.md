---
title: Speichern eines Standard Dokuments | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df93813d339a45689845b82fe4f5a185301b6c74
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724098"
---
# <a name="saving-a-standard-document"></a>Speichern eines Standarddokuments
Die Umgebung verarbeitet die Befehle "Speichern", "Speichern unter" und "Alle speichern". Wenn ein Benutzer " **Speichern**", " **Speichern**unter" oder " **Alle speichern** " im Menü "Datei" auswählt oder die Projekt **Mappe** schließt, was zu " **Alles speichern**" führt, wird der folgende Vorgang ausgeführt.

 ![Standard-Editor](../../extensibility/internals/media/public.gif "Öffentlich") Speichern, speichern unter und Speichern der gesamten Befehls Behandlung für einen Standard Editor

 Dieser Vorgang wird in den folgenden Schritten beschrieben:

1. Wenn die Befehle " **Speichern** " und " **Speichern** unter" ausgewählt sind, verwendet die Umgebung den <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>-Dienst, um das aktive Dokument Fenster zu bestimmen, und damit die Elemente, die gespeichert werden sollen. Sobald das aktive Dokument Fenster bekannt ist, findet die Umgebung den Hierarchie Zeiger und den Element Bezeichner (Itemid) für das Dokument in der aktiven Dokument Tabelle. Weitere Informationen finden Sie unter [Ausführen der Dokument Tabelle](../../extensibility/internals/running-document-table.md).

    Wenn der Befehl **Alle speichern** ausgewählt ist, kompiliert die Umgebung die Informationen in der ausgelaufenden dokumententabelle, um die Liste aller zu speichernden Elemente zu kompilieren.

2. Wenn die Lösung einen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>-Befehl empfängt, durchläuft Sie den Satz ausgewählter Elemente (d. h. die Mehrfachauswahl, die vom <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>-Dienst verfügbar gemacht wird).

3. Bei jedem Element in der Auswahl verwendet die Projekt Mappe den Hierarchie Zeiger, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>-Methode aufzurufen, um zu bestimmen, ob der Menübefehl **Speichern** aktiviert werden soll. Wenn ein oder mehrere Elemente geändert werden, ist der Befehl **Speichern** aktiviert. Wenn in der Hierarchie ein Standard-Editor verwendet wird, delegiert die Hierarchie die Abfrage des geänderten Status an den Editor, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>-Methode aufgerufen wird.

4. Bei jedem ausgewählten Element, das geändert wird, verwendet die Projekt Mappe den Hierarchie Zeiger, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>-Methode in den entsprechenden Hierarchien aufzurufen.

    Es ist üblich, dass die Hierarchie einen Standard Editor verwendet, um das Dokument zu bearbeiten. In diesem Fall sollte das Dokument Datenobjekt für diesen Editor die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>-Schnittstelle unterstützen. Beim Empfang des <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Methoden Aufrufs sollte das Projekt den Editor darüber informieren, dass das Dokument durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>-Methode für das Dokument Datenobjekt gespeichert wird. Der Editor kann der Umgebung ermöglichen, das Dialogfeld **Speichern** unter zu behandeln, indem `Query Service` für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>-Schnittstelle aufgerufen wird. Dadurch wird ein Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>-Schnittstelle zurückgegeben. Der Editor muss dann die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>-Methode aufrufen und mithilfe des `pPersistFile`-Parameters einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Implementierung des Editors übergeben. Die Umgebung führt dann den Speichervorgang aus und stellt das Dialogfeld **Speichern** unter für den Editor bereit. Die Umgebung ruft dann mit <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> zurück an den Editor.

5. Wenn der Benutzer versucht, ein Unbenanntes Dokument (d. h. ein zuvor nicht gespeichertes Dokument) zu speichern, wird tatsächlich ein Befehl "Speichern unter" ausgeführt.

6. Für den Befehl "Speichern unter" zeigt die Umgebung das Dialogfeld Speichern unter an, in dem der Benutzer aufgefordert wird, einen Dateinamen zu erhalten.

    Wenn sich der Name der Datei geändert hat, ist die Hierarchie für die Aktualisierung der zwischengespeicherten Informationen des Dokument Frames zuständig, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (VSFPROPID_MkDocument) aufgerufen wird.

   Wenn der Befehl **Speichern** unter den Speicherort des Dokuments verschiebt und die Hierarchie für den Speicherort des Dokuments sensibel ist, ist die Hierarchie dafür verantwortlich, den Besitz des geöffneten Dokument Fensters an eine andere Hierarchie zu übergeben. Dies ist z. b. der Fall, wenn das Projekt nachverfolgt, ob es sich um eine interne oder externe Datei (sonstige Datei) im Zusammenhang mit dem Projekt handelt. Verwenden Sie das folgende Verfahren, um den Besitz einer Datei in das Projekt "sonstige Dateien" zu ändern.

## <a name="changing-file-ownership"></a>Ändern des Datei Besitzes

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>So ändern Sie den Dateibesitz in das Projekt "sonstige Dateien"

1. Abfragedienst für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>-Schnittstelle.

     Ein Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> wird zurückgegeben.

2. Um das Dokument in die neue Hierarchie zu übertragen, können Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew` `punkWindowFrame`)-Methode aufzurufen. Diese Methode wird von der Hierarchie aufgerufen, die den Befehl Speichern unter ausführt.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)