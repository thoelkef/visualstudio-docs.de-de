---
title: 'Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 94f2e781c316f3891fdef0c324d54fa2f9742222
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API
Wenn Sie den Textpuffer mithilfe der legacy-API zugreifen, sollten Sie für Ereignisse des Text-Puffer wie im folgenden Verfahren gezeigt registrieren.  
  
### <a name="to-advise-text-buffer-events"></a>Um Text Puffer Ereignisse darüber zu informieren.  
  
1.  Von einem Zeiger auf eine der Schnittstellen auf <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, rufen Sie `QueryInterface` für einen Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> Methode und übergeben der Schnittstellen-ID der Ereignisse, die für die Sie registrieren möchten.  
  
     Angenommen, Sie registrieren möchten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, klicken Sie dann in einer Schnittstelle-ID des IID_IVsTextLinesEvents übergeben.  
  
     Die Textpuffer gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle für das entsprechende Objekt.  
  
3.  Rufen Sie mithilfe der this-Zeiger der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> -Methode auf und übergibt einen Zeiger auf Ihre Implementierung die Ereignisschnittstelle, die für die Sie registrieren z. B., möchten die `IVsTextLinesEvents` Schnittstelle.  
  
     Die Umgebung gibt ein Cookie, mit denen Sie können dann beenden Überwachen von Ereignissen durch Aufrufen der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Text-Puffer-Ereignisse in die Legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md)