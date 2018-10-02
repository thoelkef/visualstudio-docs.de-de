---
title: 'Vorgehensweise: Auslösen der Ereignisse aus, wenn der Editor den Fokus verliert. | Microsoft-Dokumentation'
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
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2462e41470b72c63f5c96a69d2776af2a640c372
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513507"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Vorgehensweise: Auslösen der Ereignisse aus, wenn der Editor den Fokus verliert.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [wie: Auslösen Ereignisse bei der Editor verliert den Fokus](https://docs.microsoft.com/visualstudio/extensibility/how-to-fire-events-when-the-editor-loses-focus).  
  
Manchmal ist es notwendig zu wissen, wenn Sie ein Editor den Fokus auf den Fensterrahmen verliert. Beispielsweise müssen Sie Code aus einem Codefenster zu extrahieren, nachdem der Editor nicht mehr darauf ausgerichtet ist. Das folgende Verfahren enthält die Schritte zum Empfangen von Benachrichtigungen über den Editor den Fokus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Zum Auslösen eines Ereignisses als Reaktion auf einen Editor den Fokus  
  
1.  Auswahlereignisse überwachen, durch Abrufen einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> -Sitzungsobjekts <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> und Bereitstellen Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> Objekt.  
  
3.  Der Aufruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, suchen Sie nach `elementid==SEID_WindowFrame`.  
  
4.  Testen der `varValueNew` Parameter für zwei Dinge:  
  
    1.  Der Fensterrahmen, die, den Sie suchen.  
  
    2.  Der Punkt, an dem das Programm die Auswahl auf, das diesem Fensterrahmen verliert.

