---
title: "IDebugPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortPicker-Schnittstelle"
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt eine benutzerdefinierte Benutzeroberfläche zum Auswählen des Ports dar.  
  
## Syntax  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von den Anschlusslieferanten implementiert.  Ein Port lieferant definiert die Anschluss\-Auswahl, indem er es als CLSID verfügbar macht und die `metricPortPickerCLSID` sich am Metriken CLSID verfügbar gemacht wird.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugPortPicker`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zeigt das angegebene Dialogfeld an, das es dem Benutzer ermöglicht, einen Port auszuwählen.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Legt den Dienstanbieter festgelegt.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll