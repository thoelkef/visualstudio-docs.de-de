---
title: "Gewusst wie: Implementieren Sie suchen und Ersetzen Sie Mechanismus | Microsoft Docs"
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
  - "legacy - Editoren [Visual Studio SDK] Suchen und ersetzen"
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Implementieren Sie suchen und Ersetzen Sie Mechanismus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio bietet zwei Möglichkeiten zum Implementieren von Suche bzw. ersetzt.  Eine Möglichkeit besteht darin, ein Bild Text der Shell zu übergeben und können diese Suchvorgänge, das Hervorheben und Ersetzen von Text bearbeiten.  Dies ermöglicht es Benutzern, mehrere Textabschnitte anzugeben.  Alternativ kann ein VSPackage diese Funktion selbst steuern.  In beiden Fällen müssen Sie die Shell über das aktuelle Ziel und Zielen für alle geöffneten Dokumente benachrichtigen.  
  
### Um die Suche zu implementieren und ersetzen Sie  
  
1.  Implementieren Sie die Schnittstelle in einem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> der Objekte, die von der Rahmen von Eigenschaften <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> oder <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>zurückgegeben werden.  Wenn Sie einen benutzerdefinierten Editor erstellen, sollten Sie diese Schnittstelle als Teil der benutzerdefinierten Editor\-Klasse implementieren.  
  
2.  Verwenden Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A>\-Methode, um die Optionen angeben, die der Editor unterstützt und anzugeben, ob das Bild Text suchen implementiert.  
  
     Wenn der Text Editor Bild Suche unterstützt, implementieren Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     Andernfalls <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> implementieren und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Wenn Sie das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>\-Methode implementieren, können Sie die suchenden Aufgaben vereinfachen, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>\-Schnittstelle aufrufen.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>