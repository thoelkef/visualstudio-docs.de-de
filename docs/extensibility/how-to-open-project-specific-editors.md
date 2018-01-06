---
title: "Vorgehensweise: Öffnen von Editoren projektspezifische | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 66ac0837649b42dc238eac57829c713b2bf83e3a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-project-specific-editors"></a>Vorgehensweise: Öffnen von Editoren projektspezifische
Wenn eine Elementdatei, die von einem Projekt geöffnet wird, auf den bestimmten Editor für dieses Projekt systemintern gebunden ist, muss das Projekt zu die Datei mit einem projektspezifischen-Editor öffnen. Die Datei kann nicht auf den Mechanismus der IDE für die Auswahl eines Editors delegiert werden. Anstatt einen standard-Bitmap-Editor, können Sie z. B. diese projektspezifische Editoroption verwenden, an einem bestimmten Bitmap-Editor, der Informationen in der Datei, die dem Projekt eindeutig ist, erkennt.  
  
 Ruft die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode, wenn es feststellt, dass eine Datei von einem bestimmten Projekt geöffnet werden soll. Weitere Informationen finden Sie unter [Anzeigen von Dateien mithilfe des Befehls der geöffneten Datei](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Verwenden Sie die folgenden Richtlinien zum Implementieren der `OpenItem` Methode, um Ihr Projekt eine Datei mit einem projektspezifischen-Editor zu öffnen.  
  
### <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>So implementieren Sie die OpenItem-Methode mit einem projektspezifischen-editor  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode (RDT_EditLock), um zu bestimmen, ob die Datei (dokumentdatenobjekt) bereits geöffnet ist.  
  
    > [!NOTE]
    >  Weitere Informationen zu Dokumentdaten und Ansicht-Dokumentobjekte, finden Sie unter [Dokumentdaten und Dokumentenansicht in benutzerdefinierte Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md).  
  
2.  Wenn die Datei bereits geöffnet ist, diesem die Datei durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> -Methode und die Angabe des Werts IDO_ActivateIfOpen für die `grfIDO` Parameter.  
  
     Wenn die Datei geöffnet wurde, und das Dokument von einem anderen Projekt als dem aufrufenden Projekt gehört, wird eine Warnung für den Benutzer angezeigt werden, die der Editor geöffnet, die aus einem anderen Projekt ist. Das Fenster wird dann eingeblendet.  
  
3.  Wenn der Textpuffer (dokumentdatenobjekt) bereits geöffnet ist, und Sie einer anderen Ansicht anfügen möchten, sind Sie verantwortlich für diese Sicht einbinden. Die empfohlene Vorgehensweise zum Instanziieren einer Ansicht (dokumentansichtsobjekts) aus dem Projekt lautet wie folgt:  
  
    1.  Rufen Sie `QueryService` auf die <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> Dienst um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> Schnittstelle.  
  
    2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Methode zum Erstellen einer Instanz der Ansichtsklasse Dokument.  
  
4.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> Methode, dabei werden Ihre dokumentansichtsobjekts.  
  
     Diese Methode sites des dokumentansichtsobjekts in einem Dokumentfenster angezeigt.  
  
5.  Führen Sie die entsprechenden Aufrufe von der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Methoden.  
  
     An diesem Punkt sollte die Sicht vollständig initialisiert und ist bereit, die geöffnet werden.  
  
6.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> -Methode zum Anzeigen und öffnen Sie die Ansicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Vorgehensweise: Öffnen Sie die Standard-Editoren](../extensibility/how-to-open-standard-editors.md)   
 [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)