---
title: "Gewusst wie: &#214;ffnen Sie die Standard-Editoren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] öffnen"
  - "Projekte [Visual Studio SDK], öffnen die standard-Editoren"
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Gewusst wie: &#214;ffnen Sie die Standard-Editoren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Erstellen eines standardmäßigen Editor öffnen, können Sie die IDE einen standardmäßigen Editor für einen Dateityp festlegen, anstatt einen projektspezifischen Editor für die Datei anzugeben.  
  
 Führen Sie die folgenden Schritte aus, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>\-Methode zu implementieren.  Dadurch wird eine Projektdatei in einem standardmäßigen Editor.  
  
### So implementieren OpenItem\-Methode mit einem standardmäßigen Editor  
  
1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> \(`RDT_EditLock`\) an, um festzustellen, ob das angegebene Channeldatenobjekt die Datei bereits geöffnet ist.  
  
2.  Wenn die Datei bereits geöffnet ist, erneuern Sie die Datei, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>\-Methode aufrufen und einen Wert von `IDO_ActivateIfOpen` für den `grfIDO`\-Parameter angeben.  
  
     Wenn die Datei geöffnet ist und das Dokument von einem anderen Projekt als das aufrufende Projekt gehört, empfängt das Projekt eine Warnung aus, die der Editor geöffnet wird, der von einem anderen Projekt befindet.  Das Fenster Datei überzogen wird.  
  
3.  Wenn das Dokument nicht oder nicht in der Tabelle Dokument geöffnet ist, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>\-Methode \(`OSE_ChooseBestStdEditor`\) an, um einen standardmäßigen Editor für die Datei zu öffnen.  
  
     Wenn Sie die Methode aufrufen, führt die IDE die folgenden Aufgaben aus:  
  
    1.  Die IDE überprüft den untergeordneten Unterschlüssel Verleger {guidEditorType} \/Extensions in der Registrierung, zu welchem Editor die Datei öffnen und die höchste Priorität für das diese Vorgehensweise hat.  
  
    2.  Nachdem die IDE festgestellt hat, welcher Editor die Datei öffnen kann, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>an.  Die Implementierung des Editors dieser Methode gibt Informationen zurück, die erforderlich ist, damit die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> Website und das neu geöffnete Dokument aufruft.  
  
    3.  Schließlich wird die IDE das Dokument, indem die übliche Dauerhaftigkeit Oberfläche, wie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>verwendet.  
  
    4.  Wenn die IDE vorher festgestellt hat, dass die Hierarchie oder das Element Hierarchien verfügbar ist, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A>\-Methode auf das Projekt, kontext\- Projektniveau einen Zeiger <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> abgerufen, um den Hintergrund mit dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>\-Methodenaufruf übergeben werden soll.  
  
4.  Geben Sie einen <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Zeiger zur IDE zurück, wenn die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> auf das Projekt aufruft, wenn Sie den Editor Kontext des Projekts abrufen lassen möchten.  
  
     Die Ausführung dieses Schritts können die zusätzliche Dienste des angebots Projekt auf Editor.  
  
     Wenn das Dokument der Dokumente oder ansichts\- Objekt erfolgreich in einem Fensterrahmen positioniert wurde, wird das Objekt mit den Daten initialisiert, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>aufruft.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Gewusst wie: Öffnen von Editoren projektspezifische](../extensibility/how-to-open-project-specific-editors.md)   
 [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Anzeigen von Dateien mit dem Befehl Datei öffnen](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)