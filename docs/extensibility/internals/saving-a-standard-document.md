---
title: Speichern eines Dokuments Standard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45fa2c5acfad8195ed2853d7e21413b77262a6b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="saving-a-standard-document"></a>Speichern eines Dokuments Standard
Die Umgebung ist für die speichern, speichern unter, und speichern Sie alle Befehle. Wenn ein Benutzer wählt **speichern**, **speichern unter**, oder **alle speichern** aus der **Datei** Menü oder schließt die Projektmappe, wodurch eine  **Speichern Sie alle**, der folgende Prozess tritt.  
  
 ![Standard-Editor](../../extensibility/internals/media/public.gif "öffentliche")  
Speichern Sie, speichern unter, und speichern Sie alle befehlsbehandelung für einen standard-editor  
  
 Dabei werden in den folgenden Schritten beschrieben:  
  
1.  Wenn die **speichern** und **speichern unter** Befehle aktiviert sind, verwendet der umgebungs der <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service, um zu bestimmen, das aktive Fenster, und daher welche Elemente gespeichert werden soll. Nachdem das aktive Fenster bekannt ist, sucht die Umgebung für das Dokument in der Dokumenttabelle der ausgeführten Hierarchie Zeiger und Element-ID (ItemID). Weitere Informationen finden Sie unter [Document-Tabelle ausgeführt](../../extensibility/internals/running-document-table.md).  
  
     Wenn die **alle speichern** Befehl ausgewählt ist, wird die Umgebung verwendet die Informationen in der Dokumenttabelle der ausgeführten kompilieren Sie die Liste aller Elemente zu speichern.  
  
2.  Wenn empfängt die Lösung eine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufrufen, wird die Gruppe von ausgewählten Elementen durchlaufen (d. h. die Mehrfachauswahl von verfügbar gemacht werden die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Service).  
  
3.  Für jedes Element in der Auswahl, die Lösung verwendet den Hierarchie-Zeiger zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Methode, um zu bestimmen, ob die **speichern** Menübefehl aktiviert werden soll. Wenn ein oder mehrere Elemente geändert, sind die **speichern** Befehl ist aktiviert. Wenn die Hierarchie ein standard-Editors verwendet wird, klicken Sie dann die Hierarchie-Delegaten, die für Abfragen modifizierte Status in den Editor durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> Methode.  
  
4.  Für jedes ausgewählte Element, das geändert wurde, verwendet die Lösung den Hierarchie-Zeiger zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> -Methode für die entsprechenden Hierarchien.  
  
     Es ist üblich, für die Hierarchie auf einen standard-Editor verwenden, um das Dokument zu bearbeiten. In diesem Fall die Dokumentdaten-Objekt für diesen Editor zu unterstützen, sollte die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle. Nach dem Empfang der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> -Methodenaufruf, informiert das Projekt sollte Editors, die durch Aufrufen des Dokuments gespeichert wurde die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> Methode für das Dokument-Datenobjekt. Der Editor können die Umgebung, behandeln die **speichern unter** (Dialogfeld), durch den Aufruf `Query Service` für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> Schnittstelle. Dies gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle. Der Editor muss dann rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> -Methode, die Übergabe eines Zeigers auf des Editors <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Implementierung mithilfe von der `pPersistFile` Parameter. Die Umgebung führt den Speichervorgang, und bietet die **speichern unter** Dialogfeld für den Editor. Die Umgebung ruft dann wieder in den Editor mit <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Wenn der Benutzer versucht, ein unbenanntes Dokument (d. h. ein bisher nicht gespeicherten Dokument) gespeichert ist, wird ein Befehl Speichern unter tatsächlich ausgeführt.  
  
6.  Für den Befehl Speichern unter zeigt die Umgebung das Dialogfeld Speichern unter, der Benutzer einen Dateinamen aufgefordert.  
  
     Wenn der Name der Datei wurde geändert, und klicken Sie dann die Hierarchie verantwortlich ist für des Dokumentframe aktualisiert Informationen durch Aufrufen zwischengespeicherte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
 Wenn die **speichern unter** Befehl verschiebt den Speicherort des Dokuments, die Hierarchie ist empfindlich gegenüber der Speicherort des Dokuments, und die Hierarchie ist verantwortlich für die Übergabe des Besitzes des Fensters geöffneten Dokument an einer anderen Hierarchie. Dies geschieht beispielsweise, wenn das Projekt verfolgt nach, ob die Datei eine interne oder externe Datei (Verschiedenes) in Bezug auf das Projekt. Verwenden Sie wie folgt vor, um den Besitzer einer Datei zum Projekt verschiedene Dateien zu ändern.  
  
## <a name="changing-file-ownership"></a>Dateibesitz ändern  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>So ändern Sie Dateibesitz dem Projekt verschiedene Dateien  
  
1.  Abfrage-Dienst für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> Schnittstelle.  
  
     Ein Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> wird zurückgegeben.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) Methode, um das Dokument an die neue Hierarchie übertragen. Diese Methode wird von die Hierarchie Ausführen den Befehl Speichern unter aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)