---
title: 'Gewusst wie: Auslösen von Ereignissen, wenn der Editor den Fokus verliert | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204195"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Vorgehensweise: Auslösen von Ereignissen, wenn der Editor den Fokus verliert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Manchmal müssen Sie wissen, wann ein Editor den Fokus auf den Fensterrahmen verliert. Beispielsweise müssen Sie möglicherweise Code aus einem Code Fenster extrahieren, nachdem der Editor nicht mehr darauf fokussiert ist. Das folgende Verfahren enthält die Schritte, die Sie befolgen müssen, um die Benachrichtigung zu erhalten, dass der Editor den Fokus verliert  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>So lösen Sie ein Ereignis in Reaktion auf einen Editor aus, der den Fokus verliert  
  
1. Überwachen Sie die Auswahl Ereignisse, indem Sie ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> Objekt von abrufen <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>Geben Sie ein, und stellen Sie das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> Objekt bereit.  
  
3. Suchen Sie in Ihrem-Befehl nach <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> `elementid==SEID_WindowFrame` .  
  
4. Testen Sie den `varValueNew` Parameter auf zwei Dinge:  
  
    1. Der gesuchte Fensterrahmen.  
  
    2. Der Punkt, an dem das Programm die Auswahl an diesem Fensterrahmen verliert.
