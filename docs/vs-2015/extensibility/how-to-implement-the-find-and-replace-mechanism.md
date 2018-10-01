---
title: 'Vorgehensweise: Implementieren Sie suchen und Ersetzen Sie Mechanismus | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eaae77979fc15954b4480a038c791a15bd95ab65
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511071"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Vorgehensweise: Implementieren Sie suchen und Ersetzen Sie Mechanismus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Implementieren der suchen und Ersetzen Sie dies Mechanismus](https://docs.microsoft.com/visualstudio/extensibility/how-to-implement-the-find-and-replace-mechanism).  
  
Visual Studio bietet zwei Möglichkeiten zum Implementieren von Suchen/Ersetzen. Eine Möglichkeit ist, übergeben ein TEXTIMAGE an die Shell, und laden, damit sie die Suche, Hervorhebung und Ersetzen von Text zu behandeln. Dadurch können Benutzer mehrere Textabschnitte angegeben. Alternativ kann das VSPackage selbst gesteuert werden. In beiden Fällen müssen Sie die Shell über das aktuelle Ziel und die Ziele für alle geöffneten Dokumente benachrichtigen.  
  
### <a name="to-implement-findreplace"></a>Zum Implementieren der Suchen/Ersetzen  
  
1.  Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> Schnittstelle auf eines der Objekte, die von den Frameeigenschaften zurückgegebenen <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> oder <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Wenn Sie einen benutzerdefinierten Editor erstellen, sollten Sie diese Schnittstelle als Teil der benutzerdefinierten Editor-Klasse implementieren.  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> Methode, um die Optionen angeben, die Ihr Editor unterstützt und um anzugeben, ob die Suche nach einer Zeichenfolge Image implementiert.  
  
     Wenn Ihr Editor unterstützt die Suche nach einer Zeichenfolge Image, implementieren Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     Implementieren Sie anderenfalls <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Wenn Sie implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> Methoden, Sie können Ihre suchen Aufgaben vereinfachen, durch den Aufruf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>

