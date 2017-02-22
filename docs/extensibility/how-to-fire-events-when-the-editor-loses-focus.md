---
title: "Gewusst wie: Ereignisse auszul&#246;sen, wenn der Editor den Fokus verliert. | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - auslösen Ereignisse Fokus"
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Ereignisse auszul&#246;sen, wenn der Editor den Fokus verliert.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Manchmal ist es erforderlich zu wissen, wann ein Editor Fokus auf dem Fensterrahmen verliert.  Beispielsweise müssen Sie eventuell Code aus einem Codefenster extrahieren, nachdem der Editor nicht mehr dafür verwendet wird.  Im folgenden Verfahren werden die Schritte, um zu verfolgen, um eine Benachrichtigung des verlierenden Fokus des Editors zu empfangen.  
  
### Um ein Ereignis als Reaktion auf einen verlierenden Fokus des Editors auslösen  
  
1.  Bildschirm\-Auswahl von Ereignissen durch ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>\-Objekt aus <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>erhalten.  
  
2.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> und stellen Sie es auf das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>\-Objekt bereit.  
  
3.  Im Aufruf des <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, suchen Sie nach `elementid==SEID_WindowFrame`.  
  
4.  Testen Sie den `varValueNew`\-Parameter für zwei Dinge:  
  
    1.  Nach der Fensterrahmen, den Sie suchen.  
  
    2.  Der Punkt, an dem das Programm die Auswahl auf dieses Fensterrahmen verliert.