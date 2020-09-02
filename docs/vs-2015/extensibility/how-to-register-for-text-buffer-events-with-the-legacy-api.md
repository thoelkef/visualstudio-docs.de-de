---
title: 'Gewusst wie: Registrieren für Text Puffer Ereignisse mit der Legacy-API | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204093"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Vorgehensweise: Registrieren für Textpufferereignisse mit der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie mit der Legacy-API auf den Text Puffer zugreifen, sollten Sie sich für Text Puffer Ereignisse registrieren, wie im folgenden Verfahren gezeigt.  
  
### <a name="to-advise-text-buffer-events"></a>So informieren Sie Text Puffer Ereignisse  
  
1. Bei einem Zeiger auf eine der Schnittstellen in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> , wird `QueryInterface` für einen Zeiger auf aufgerufen <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Nennen <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> Sie die-Methode, und übergeben Sie die Schnittstellen-ID der Ereignisse, die Sie registrieren möchten.  
  
     Wenn Sie z. b. für registrieren möchten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> , übergeben Sie eine Schnittstellen-ID IID_IVsTextLinesEvents.  
  
     Der Text Puffer gibt einen Zeiger auf die- <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle für das entsprechende Verbindungspunkt Objekt zurück.  
  
3. Verwenden Sie diesen Zeiger, um die-Methode aufzurufen <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> und einen Zeiger auf die Implementierung der Ereignis Schnittstelle zu übergeben, für die Sie sich registrieren möchten, z. b. die- `IVsTextLinesEvents` Schnittstelle.  
  
     Die Umgebung gibt ein Cookie zurück, das Sie verwenden können, um das lauschen an Ereignissen zu überwachen, indem Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> Methode aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Textpufferereignisse in der Legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md)
