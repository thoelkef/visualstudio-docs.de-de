---
title: "Ein standardisiertes Dokument speichern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] standard Dokumente speichern"
  - "Projekte [Visual Studio SDK] standard Dokumente speichern"
  - "Dauerhaftigkeit, speichern die Standarddokumente"
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Ein standardisiertes Dokument speichern
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Umgebung verarbeitet die Speichern, Speichern unter, und speichert alle Befehle.  Wenn ein Benutzer **Speichern**, **Speichern unter**oder **Alle speichern** aus dem Menü **Datei** auswählt oder schließt, wird die Lösung, mit dem Ergebnis **Alle speichern**, der folgende Prozess auf.  
  
 ![Standard&#45;Editor](../../extensibility/internals/media/public.png "Public")  
Speichern, Speichern unter, und speichern Sie alle Befehls Klassenbehandlung für einen standardmäßigen Editor  
  
 Dieser Vorgang wird in den folgenden Schritten einzeln aufgeführt:  
  
1.  Wenn die **Speichern** und **Speichern unter** Befehle ausgewählt ist, wird die Umgebung den <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Dienst, um das aktive Dokumentfenster und somit bestimmen, welche Elemente gespeichert werden sollen.  Sobald das aktive Dokumentfenster bekannt ist, durchsucht die Umgebung den Hierarchien zeiger\- und Elementbezeichner \(itemID\) für das Dokument in der Tabelle Dokumente.  Weitere Informationen finden Sie unter [Dokumenttabelle der ausgeführten](../../extensibility/internals/running-document-table.md).  
  
     Wenn der **Alle speichern** Befehl aktiviert ist, wird die Umgebung die Informationen in der Tabelle der Dokumente, um die Liste aller Elemente zu kompilieren, um zu speichern.  
  
2.  Wenn die Projektmappe <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> einen Aufruf empfängt, wird sie durch den Satz von ausgewählten Elementen durch \(d. h. die Mehrfachauswahl verfügbar gemacht <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> vom Dienst\).  
  
3.  Bei jedem Element in der Auswahl, wird die Projektmappe den Zeiger Hierarchien, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A>\-Methode aufrufen, um zu bestimmen, ob der **Save** Menübefehl aktiviert werden soll.  Wenn eine oder mehrere Elemente geändert wurden, wird der Befehl aktiviert **Save** .  Wenn die Hierarchie einen standardmäßigen Editor verwendet, delegiert die Hierarchie Abfragen für geänderten Status in den Editor, indem sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A>\-Methode aufruft.  
  
4.  Bei jedem ausgewählten Element, das geändert wurde, wird die Projektmappe den Zeiger Hierarchien, um die Hierarchien auf den entsprechenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>\-Methode aufrufen.  
  
     Es ist üblich, sodass die Hierarchie einen standardmäßigen Editor verwendet, um das Dokument zu bearbeiten.  In diesem Fall sollte das Dokument das angegebene Channeldatenobjekt für diesen Editor verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>\-Schnittstelle unterstützen.  Nach dem Empfang des <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> methodenaufrufs, sollte das Projekt den Editor informieren, dass das Dokument gespeichert wird, indem die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A>\-Methode für das Dokument das angegebene Channeldatenobjekt aufruft.  Der Editor kann der Umgebung ermöglichen, um das Dialogfeld **Speichern unter** zu behandeln, indem er `Query Service` für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>\-Schnittstelle aufruft.  Dies gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>\-Schnittstelle zurück.  Der Editor muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>\-Methode aufrufen und einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Implementierung des Editors mithilfe des `pPersistFile`\-Parameters übergeben.  Die Umgebung verhält sich der Speichervorgang aus und stellt das **Speichern unter** Dialogfeld für den Editor bereit.  Die Aufrufe der Umgebung anschließend wieder in den Editor mit <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Wenn der Benutzer versucht, ein unberechtigtes Dokument \(d. h. ein zuvor nicht gespeicherten Dokument\) zu speichern, dann wird eine Befehl Speichern unter tatsächlich ausgeführt.  
  
6.  Bei der Befehl Speichern unter, sind die Umgebungen das Dialogfeld Speichern unter an und fordert den Benutzer zur Eingabe eines Dateinamens aufgefordert.  
  
     Wenn der Name der Datei geändert wurde, dann wird die Hierarchie für die Aktualisierung der zwischengespeicherten Informationen der Dokumente Skinframes zuständig, indem sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>\(VSFPROPID\_MkDocument\) aufruft.  
  
 Wenn der **Speichern unter** Befehl den Speicherort des Dokuments verschoben wird und die Hierarchie zum Dokumentspeicherort vertraulich ist, ist die Hierarchie für die Übergebung vom Besitzer des Fensters des geöffneten Dokuments zu einer anderen Hierarchie verantwortlich.  Dies tritt beispielsweise auf, wenn das Projekt nachverfolgt, ob die Datei eine interne oder externe Datei \(andere Datei\) in Bezug auf das Projekt befindet.  Führen Sie die folgenden Schritte aus, um den Besitz einer Datei zum Projekt Verschiedene Dateien zu ändern.  
  
## Ändern Datei\-Besitz  
  
#### So fügen Sie dem Projekt Verschiedene Dateien besitz Datei ändern  
  
1.  Abfragen\-Dienst für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager>\-Schnittstelle.  
  
     Ein Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> wird zurückgegeben.  
  
2.  Rufen Sie die Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> \(`pszMkDocumentNew`, `punkWindowFrame`\) an das Dokument an die neue Hierarchie zu übertragen.  Die Hierarchie, die das Befehl ausführt, ruft diese Methode auf.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)