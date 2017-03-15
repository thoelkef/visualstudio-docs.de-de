---
title: "Gewusst wie: &#214;ffnen von Editoren projektspezifische | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Öffnen einen projektspezifische-Editor-Projekttypen"
  - "Editoren [Visual Studio SDK] projektspezifische Editoren öffnen"
  - "Projekte [Visual Studio SDK] Öffnen von Ordnern"
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Gewusst wie: &#214;ffnen von Editoren projektspezifische
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn eine Elementdatei, die von einem Projekt geöffnet wird, tatsächlich um bestimmten Editor für dieses Projekt gebunden ist, muss das Projekt die Datei öffnen, indem Sie einen projektspezifischen Editor verwendet wird.  Die Datei kann nicht auf den Mechanismus der IDE zum Auswählen eines Editors unten delegiert werden.  Anstatt einen Standardwert bitmap\-Editor zu verwenden, können Sie diese projektspezifische Editoroption verwenden, um einen bestimmten Bitmap\-Editor anzugeben, der Informationen in der Datei erkennt, die für das Projekt eindeutig ist.  
  
 Die IDE ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>\-Methode auf, wenn es ermittelt, dass eine Datei durch ein bestimmtes Projekt geöffnet werden soll.  Weitere Informationen finden Sie unter [Anzeigen von Dateien mit dem Befehl Datei öffnen](../extensibility/internals/displaying-files-by-using-the-open-file-command.md).  Verwenden Sie die folgenden Richtlinien, um die `OpenItem`\-Methode implementieren, um das Projekt zu haben eine Datei öffnen, indem Sie einen projektspezifischen Editor verwenden.  
  
### So implementieren OpenItem\-Methode mit einem projektspezifischen Editor  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>\-Methode \(RDT\_EditLock\) an, um festzustellen, ob die Datei \(Dokumenten das angegebene Channeldatenobjekt\) bereits geöffnet ist.  
  
    > [!NOTE]
    >  Weitere Informationen über die Dokumente und Dokumentdaten Objekte finden Sie unter [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Wenn die Datei bereits geöffnet ist, erneuern Sie die Datei, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>\-Methode aufrufen und einen Wert von IDO\_ActivateIfOpen für den `grfIDO`\-Parameter angeben.  
  
     Wenn die Datei geöffnet ist und das Dokument von einem Projekt anderes als das aufrufende Projekt gehört, wird eine Warnung angezeigt, die der Editor geöffnet wird, der von einem anderen Projekt befindet.  Das Fenster Datei überzogen wird.  
  
3.  Wenn der Textpuffer \(Dokumenten das angegebene Channeldatenobjekt\) bereits geöffnet, und Sie möchten eine andere Ansicht auf diesen Typ ist anfügen, müssen Sie für das Haken in dieser Ansicht verantwortlich.  Die empfohlene Vorgehensweise zum Instanziieren einer Ansicht für die Dokumente \(\) aus dem Projekt, lautet wie folgt:  
  
    1.  Aufruf `QueryService` auf dem <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> Dienst, um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2>\-Schnittstelle abzurufen.  
  
    2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>\-Methode aufgerufen, um eine Instanz der ansichtsklasse Dokumente zu erstellen.  
  
4.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>\-Methode auf und die Dokumente Objekt angeben.  
  
     Sites dieser Methode das Objekt die Dokumente in einem Dokumentfenster.  
  
5.  Führen Sie die entsprechenden Aufrufe an <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Methods.  
  
     An diesem Punkt sollte die Ansicht vollständig initialisiert werden, und es kann geöffnet werden soll.  
  
6.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>\-Methode auf, um die Ansicht anzuzeigen und zu öffnen.  
  
## Siehe auch  
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Gewusst wie: Öffnen Sie die Standard\-Editoren](../extensibility/how-to-open-standard-editors.md)   
 [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)