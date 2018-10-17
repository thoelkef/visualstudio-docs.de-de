---
title: 'Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76b782e688c567eb3888b2dbc890a360d22e3014
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232244"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie den Textpuffer mithilfe der legacy-API zugreifen, sollten Sie für Text-pufferereignisse, wie im folgenden Verfahren dargestellt registrieren.  
  
### <a name="to-advise-text-buffer-events"></a>Anweisen, Text-Puffer-Ereignisse  
  
1.  Von einem Zeiger auf eine der Schnittstellen auf <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, rufen Sie `QueryInterface` für einen Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> -Methode und übergeben Sie die Schnittstellen-ID der Ereignisse für die Sie registrieren möchten.  
  
     Wenn Sie für registrieren möchten z. B. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, klicken Sie dann in einer Schnittstelle-ID des IID_IVsTextLinesEvents übergeben.  
  
     Das Textpuffer gibt einen Zeiger auf die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle für das entsprechende Objekt.  
  
3.  Rufen Sie diesen Zeiger mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> Methode und übergeben eines Zeigers für Ihre Implementierung der die Schnittstelle für die Sie registrieren z. B., möchten die `IVsTextLinesEvents` Schnittstelle.  
  
     Die Umgebung gibt ein Cookie, das Sie, zum Beenden der Überwachung auf Ereignisse verwenden können durch Aufrufen der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Textpufferereignisse in der Legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md)

