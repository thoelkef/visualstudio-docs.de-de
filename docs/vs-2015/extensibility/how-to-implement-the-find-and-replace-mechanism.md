---
title: 'Vorgehensweise: Implementieren des Mechanismus zum Suchen und ersetzen | Microsoft-Dokumentation'
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
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548695"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Vorgehensweise: Implementieren von „Suchen und Ersetzen“
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio bietet zwei Möglichkeiten zum Implementieren von suchen/ersetzen. Eine Möglichkeit besteht darin, ein Textbild an die Shell zu übergeben und das suchen, hervorheben und Ersetzen von Text zu behandeln. Dadurch können Benutzer mehrere Text spannen angeben. Alternativ kann das VSPackage diese Funktionalität selbst steuern. In beiden Fällen müssen Sie die Shell über das aktuelle Ziel und die Ziele für alle geöffneten Dokumente benachrichtigen.  
  
### <a name="to-implement-findreplace"></a>So implementieren Sie "Suchen/Ersetzen"  
  
1. Implementieren Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> Schnittstelle für eines der-Objekte, die von den Frame Eigenschaften oder zurückgegeben werden <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> . Wenn Sie einen benutzerdefinierten Editor erstellen, sollten Sie diese Schnittstelle als Teil der benutzerdefinierten Editor-Klasse implementieren.  
  
2. Verwenden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> Sie die-Methode, um die Optionen anzugeben, die der Editor unterstützt, und um anzugeben, ob die Textbild Suche implementiert wird.  
  
     Wenn der Editor das Suchen von Text Bildern unterstützt, implementieren Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> .  
  
     Implementieren Sie andernfalls <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> .  
  
3. Wenn Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> Methoden und implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> , können Sie die Suchaufgaben vereinfachen, indem Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> Schnittstelle aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
