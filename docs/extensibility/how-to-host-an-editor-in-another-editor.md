---
title: "Gewusst wie: Hosten ein Editors in einem anderen Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "legacy - Editoren [Visual Studio SDK], hosten ein geschachteltes-Editors"
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Hosten ein Editors in einem anderen Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual Studio können Sie Editor innere Ausnahme des Hosts, indem Sie das Projekt bei einer Fenster als übergeordnetes Fenster angeben.  Dazu legen Sie die Parameter <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> auf dem Rahmen des untergeordneten Fensters ab.  
  
### So installieren Sie den Fensterrahmen zum Hosten eines Editor  
  
1.  Legen Sie einen gehosteter Editor als Editor festlegen, indem Sie einen Bereich des untergeordneten Fensters erstellen.  
  
     Dieser Bereich befindet, auf dem der Text des Editors wird.  
  
2.  Wiederherstellen des Hosting mit dem Editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> oder der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>\-Methode erstellt.  
  
3.  Legen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> und <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2>\-Eigenschaften in der Implementierung des Fensterrahmens gehosteten Editors fest, indem Sie diese Eigenschaften als Parameter an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>\-Methode erzeugt haben.  
  
     Wenn Sie diese Parameter abrufen müssen, führen Sie diese Eigenschaften auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>\-Methode.  
  
4.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>\-Methode für den enthaltenen Editor an.  
  
     Der Editor wird im gehosteten enthaltenden Bereich des Editors.  
  
## Robuste Programmierung  
 **Anwendungs\-Designer** in Visual Studio Team Edition for Architects ist ein Beispiel für einen Editor fensterrahmens, der einen anderen Editor fungiert.  Die **Anwendungs\-Designer** Hosts andere Designer im rechten Bereich angezeigt.  Ein Designerbereich \(oder **Eigenschaften** Seite\) für jeden der enthaltenen Designer wird zum enthaltenden Fensterrahmen hinzugefügt.