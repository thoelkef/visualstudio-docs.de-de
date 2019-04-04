---
title: 'Vorgehensweise: Implementieren von Suchen und Ersetzen Sie Mechanismus | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a42df69a7c51b7eb7ef44cf137d8449cf1421ae2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959566"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Vorgehensweise: Implementieren von Suchen und Ersetzen Sie Mechanismus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
