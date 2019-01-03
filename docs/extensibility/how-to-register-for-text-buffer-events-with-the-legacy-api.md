---
title: 'Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3eb5706cea2ec0e79ed29812beb94d39a117c61d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886006"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der legacy-API
Wenn Sie den Textpuffer mithilfe der legacy-API zugreifen, sollten Sie für Text-pufferereignisse, wie im folgenden Verfahren dargestellt registrieren.  
  
## <a name="to-advise-text-buffer-events"></a>Anweisen, Text-Puffer-Ereignisse  
  
1.  Von einem Zeiger auf eine der Schnittstellen auf <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, rufen Sie `QueryInterface` für einen Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> -Methode und übergeben Sie die Schnittstellen-ID der Ereignisse für die Sie registrieren möchten.  
  
     Wenn Sie für registrieren möchten z. B. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, klicken Sie dann in einer Schnittstelle-ID des IID_IVsTextLinesEvents übergeben.  
  
     Das Textpuffer gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle für das entsprechende Objekt.  
  
3.  Rufen Sie diesen Zeiger mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> Methode und übergeben eines Zeigers für Ihre Implementierung der die Schnittstelle für die Sie registrieren z. B., möchten die `IVsTextLinesEvents` Schnittstelle.  
  
     Die Umgebung gibt ein Cookie, das Sie, zum Beenden der Überwachung auf Ereignisse verwenden können durch Aufrufen der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Text-Puffer-Ereignisse in der legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md)