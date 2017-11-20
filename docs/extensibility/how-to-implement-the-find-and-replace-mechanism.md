---
title: 'Vorgehensweise: Implementieren von Suchen und Ersetzen Sie Mechanismus | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c12e300a3537d1927710b0a4c3550ec3f5fd762
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Vorgehensweise: Implementieren von Suchen und Ersetzen Sie Mechanismus
Visual Studio bietet zwei Möglichkeiten zum Implementieren von Suchen/Ersetzen. Eine Möglichkeit besteht darin textimages an die Shell übergeben, und lassen Sie ihn suchen, Hervorhebung und Ersetzen von Text zu behandeln. Dadurch können Benutzer mehrere unzusammenhängende angeben. Alternativ kann das VSPackage selbst gesteuert werden. In beiden Fällen müssen Sie die Befehlsshell über das aktuelle Ziel und die Ziele für alle geöffneten Dokumente benachrichtigen.  
  
### <a name="to-implement-findreplace"></a>Zum Implementieren von Suchen/Ersetzen  
  
1.  Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> Schnittstelle auf einem der vom Frame-Eigenschaften zurückgegebenen Objekte <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> oder <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Wenn Sie einen benutzerdefinierten Editor erstellen, sollten Sie diese Schnittstelle als Teil der benutzerdefinierten Editor-Klasse implementieren.  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> Methode, um die Optionen angeben, die der Editor unterstützt und um anzugeben, ob Text Image Suche implementiert.  
  
     Der Editor unterstützt Image Textsuche, implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     Andernfalls implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Wenn Sie implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> Methoden, können Sie Ihre suchen Aufgaben vereinfachen, durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>