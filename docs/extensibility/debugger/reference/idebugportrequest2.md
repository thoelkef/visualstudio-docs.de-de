---
title: "IDebugPortRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2"
helpviewer_keywords: 
  - "IDebugPortRequest2-Schnittstelle"
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle beschreibt einen Anschluss.  Diese Beschreibung wird verwendet, um den Anschlusslieferanten einem Port hinzufügen.  
  
## Syntax  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle in der Regel bei dem Abrufen eines Anschlusses Debuggen von einem Anschlusslieferanten.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird in [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) übergeben, um einen Anschluss Debuggen zu erstellen.  Ein Aufruf von [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) gibt diese Schnittstelle zurück und stellt die Anforderung dar, die verwendet wird, um den Port an erster Stelle zu erstellen.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugPortRequest2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ruft den Namen des Anschlusses ab, die erstellt werden soll.|  
  
## Hinweise  
 Ein Debuggen Modul in der Regel interagiert nicht mit einem Anschlusslieferanten. Es wird keine Verwendung für diese Schnittstelle verfügen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)