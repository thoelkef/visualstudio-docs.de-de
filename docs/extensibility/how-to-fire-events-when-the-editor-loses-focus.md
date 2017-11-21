---
title: "Vorgehensweise: Ereignisse auszulösen, wenn der Editor den Fokus verliert. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a566d52dc1aabb9895e2f1f9751fdb37ae016d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Vorgehensweise: Ereignisse auszulösen, wenn der Editor den Fokus verliert.
Manchmal ist es erforderlich sind, wenn Sie ein Editor den Fokus auf den Fensterrahmen verliert. Beispielsweise müssen Sie möglicherweise Code aus einem Fenster des Code extrahieren, nachdem der Editor nicht mehr darauf ausgerichtet ist. Das folgende Verfahren beschreibt die Schritte befolgen, um die Benachrichtigung des Editors verlieren des Fokus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Ein Ereignis als Antwort auf einen Editor verlieren des Fokus ausgelöst werden.  
  
1.  Auswahlereignisse überwachen, indem Sie erhalten eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> -Sitzungsobjekts <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> und Bereitstellen Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> Objekt.  
  
3.  Der Aufruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, suchen Sie nach `elementid==SEID_WindowFrame`.  
  
4.  Testen der `varValueNew` -Parameter für zwei Dinge:  
  
    1.  Der Fensterrahmen, den Sie suchen.  
  
    2.  Der Punkt, an dem das Programm die Auswahl dieser Fensterrahmen verliert.