---
title: Speichern eines Standarddokuments | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c13e2af373025cc264f9bec34f426fb8f9b75d66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267513"
---
# <a name="saving-a-standard-document"></a>Speichern eines Standarddokuments
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Umgebung verarbeitet die speichern, speichern unter, und speichern Sie alle Befehle. Wenn ein Benutzer auswählt **speichern**, **speichern unter**, oder **alle speichern** aus der **Datei** Menü oder schließt die Projektmappe, wodurch eine  **Speichern Sie alle**, der folgende Prozess durchgeführt.  
  
 ![Standard-Editor](../../extensibility/internals/media/public.gif "öffentliche")  
Speichern Sie, speichern und Klassenbehandlung für ein standard-Editor-Befehl Alle speichern  
  
 Dieser Prozess wird in den folgenden Schritten beschrieben:  
  
1.  Wenn die **speichern** und **speichern** Befehle aktiviert sind, ist die Umgebung verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service, um zu bestimmen, das das aktive Fenster, und somit welche Elemente gespeichert werden soll. Nachdem das aktive Dokumentfenster bekannt ist, sucht die Umgebung für das Dokument in der ausgeführten Dokumententabelle Hierarchie Zeiger und Elementbezeichner (Element-ID). Weitere Informationen finden Sie unter [Running Document Table](../../extensibility/internals/running-document-table.md).  
  
     Wenn die **Alles speichern** Befehl aktiviert ist, wird die Umgebung verwendet die Informationen in der ausgeführten Dokumententabelle, um die Liste der zu speichernden alle Elemente zu kompilieren.  
  
2.  Wenn die Lösung empfängt eine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufrufen, wird der Satz von ausgewählten Elementen durchlaufen (, also die Mehrfachauswahl von verfügbar gemacht werden die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Service).  
  
3.  Die Lösung verwendet für jedes Element in der Auswahl den Hierarchie Zeiger aufrufen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Methode, um zu bestimmen, ob die **speichern** Menübefehl aktiviert werden soll. Wenn eine oder mehrere Elemente geändert, und klicken Sie dann die **speichern** Befehl ist aktiviert. Wenn die Hierarchie ein standard-Editors verwendet wird, klicken Sie dann die Hierarchie-Delegaten, die für Abfragen dirty-Status in den Editor durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> Methode.  
  
4.  Für jedes ausgewählte Element, das geändert wurde, verwendet die Lösung den Hierarchie Zeiger zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Methode auf die entsprechenden Hierarchien.  
  
     Es ist üblich, für die Hierarchie mit einem standard-Editor zum Bearbeiten des Dokuments. In diesem Fall die Daten des Objekts, für Editor unterstützen soll die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Schnittstelle. Bei Empfang der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> -Methodenaufruf, das Projekt sollte darüber zu informieren den Editor, das das Dokument durch Aufrufen gespeichert wird der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> Methode für das dokumentendatenobjekt. Der Editor können die Umgebung, Behandeln der **speichern unter** Dialogfeld durch Aufrufen von `Query Service` für die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> Schnittstelle. Gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle. Der Editor müssen Sie die Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> Methode auf und übergibt einen Zeiger auf die Anmerkung der Redaktion <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Implementierung von der `pPersistFile` Parameter. Die Umgebung anschließend den Speichervorgang ausgeführt, und die **speichern** im Dialogfeld für den Editor. Die Umgebung ruft dann wieder in den Editor mit <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Wenn der Benutzer versucht, ein unbenanntes Dokument (d. h. ein zuvor nicht gespeicherte Dokument) gespeichert ist, klicken Sie dann ein Befehl Speichern unter tatsächlich erfolgt.  
  
6.  Für den Befehl Speichern unter zeigt die Umgebung das Dialogfeld Speichern unter, der Benutzer zum Eingeben eines Dateinamens aufgefordert.  
  
     Wenn der Name der Datei wurde geändert, und klicken Sie dann die Hierarchie verantwortlich ist für Informationen durch Aufrufen des Dokument-Frames aktualisieren zwischengespeicherte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
 Wenn die **speichern** Befehl verschiebt die Position des Dokuments und die Hierarchie ist anfällig für den Speicherort des Dokuments, und die Hierarchie für die Übergabe des Besitzes der geöffneten Dokumentfenster an einer anderen Hierarchie verantwortlich ist. Dies geschieht beispielsweise, wenn das Projekt verfolgt nach, ob die Datei eine interne oder externe Datei (sonstige) in Bezug auf das Projekt. Verwenden Sie wie folgt vor, um den Besitz einer Datei auf das Projekt verschiedene Dateien zu ändern.  
  
## <a name="changing-file-ownership"></a>Ändern der Dateibesitz  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>So ändern Sie den Besitzer auf das Projekt verschiedene Dateien  
  
1.  Dienst für die Abfrage die <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> Schnittstelle.  
  
     Ein Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> zurückgegeben wird.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) Methode, um das Dokument an die neue Hierarchie übertragen. Diese Methode wird von die Hierarchie Ausführen den Befehl Speichern unter aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)

