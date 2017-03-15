---
title: "Gewusst wie: &#214;ffnen von Editoren f&#252;r ge&#246;ffnete Dokumente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] für geöffnete Dokumente öffnen"
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Gewusst wie: &#214;ffnen von Editoren f&#252;r ge&#246;ffnete Dokumente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bevor ein Projekt ein Dokumentfenster geöffnet wird, muss das Projekt zuerst ermitteln, ob die Datei bereits im Dokumentfenster für einen anderen Editor geöffnet ist.  Die Datei kann entweder als öffnen in einem projektspezifischen Editor oder einem der Standardwert editoren, die mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]registriert werden.  
  
## Wenn Sie einen projektspezifischen Editor öffnen  
 Führen Sie die folgenden Schritte aus, um einen projektspezifischen Editor für eine Datei zu öffnen, die bereits geöffnet ist.  
  
#### So fügen Sie einen projektspezifischen Editor für eine offene Datei öffnen  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>\-Methode auf.  
  
     Dieses Rückkehraufruf des Dokuments Zeiger, um Hierarchien der Hierarchie " \- Element und dem Fensterrahmen, falls erforderlich.  
  
2.  Wenn das Dokument geöffnet ist, muss das Projekt untersuchen, um festzustellen, ob nur ein Dokument das angegebene Channeldatenobjekt vorhanden ist oder wenn die Dokumente auch ein Objekt vorhanden ist.  
  
    -   Wenn ein Objekt vorhanden ist und die Dokumente für diese Ansicht einer anderen Hierarchie oder Hierarchien element ist, verwendet das Projekt den Zeiger auf den Fensterrahmen der Ansicht, um das vorhandene Fenster wieder aufzukommen.  
  
    -   Wenn ein Objekt vorhanden ist und die Dokumente für diese Ansicht der gleichen Hierarchie und Hierarchien " \- Element wurde, kann das Projekt eine zweite Ansicht öffnen, wenn es an das zugrunde liegende Dokument das angegebene Channeldatenobjekt angefügt werden kann.  Andernfalls sollte das Projekt den Zeiger auf den Fensterrahmen der Ansicht verwenden, um das vorhandene Fenster wieder aufzukommen.  
  
    -   Wenn nur das Dokument das angegebene Channeldatenobjekt vorhanden ist, muss das Projekt bestimmen, ob das Dokument das angegebene Channeldatenobjekt für die Ansicht verwendet werden kann.  Wenn das Dokument das angegebene Channeldatenobjekt kompatibel ist, führen Sie die Schritte aus, die in [Wenn Sie einen projektspezifischen Editor öffnen](../extensibility/how-to-open-project-specific-editors.md)erläutert werden.  
  
     Wenn das Dokument das angegebene Channeldatenobjekt nicht kompatibel ist, sollte ein Fehler angezeigt werden, der angibt, dass die Datei gerade verwendet wird.  Dieser Fehler wird in den flüchtigen Fällen, z. B. nur angezeigt, wenn eine Datei gleichzeitig ein Benutzer versucht, die Datei zu öffnen kompiliert wird, indem Sie einen anderen als den Editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kern text\-editor verwendet.  Der Kern text\-editor das angegebene Channeldatenobjekt Dokumenten kann mit dem Compiler freigeben.  
  
3.  Wenn das Dokument nicht geöffnet ist, weil kein Dokument oder das angegebene Channeldatenobjekt die Dokumente Objekt vorhanden ist, führen Sie die Schritte in [Wenn Sie einen projektspezifischen Editor öffnen](../extensibility/how-to-open-project-specific-editors.md)ab.  
  
## Erstellen eines standardmäßigen Editor öffnen  
 Führen Sie die folgenden Schritte aus, um einen standardmäßigen Editor für eine Datei zu öffnen, die bereits geöffnet ist.  
  
#### So fügen Sie einen standardmäßigen Editor für eine offene Datei öffnen  
  
1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> auf.  
  
     Diese Methode überprüft zuerst, dass das Dokument noch nicht durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>geöffnet ist.  Wenn das Dokument bereits geöffnet ist, wird ihr Editorfenster erneuert.  
  
2.  Wenn das Dokument nicht geöffnet ist, führen Sie die Schritte in [Gewusst wie: Öffnen Sie die Standard\-Editoren](../extensibility/how-to-open-standard-editors.md)ab.  
  
## Siehe auch  
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Gewusst wie: Öffnen von Editoren projektspezifische](../extensibility/how-to-open-project-specific-editors.md)   
 [Gewusst wie: Öffnen Sie die Standard\-Editoren](../extensibility/how-to-open-standard-editors.md)