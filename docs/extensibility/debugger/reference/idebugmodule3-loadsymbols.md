---
title: "IDebugModule3::LoadSymbols | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::LoadSymbols"
helpviewer_keywords: 
  - "IDebugModule3::LoadSymbols"
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModule3::LoadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Lädt die Symbole für das aktuelle Modul.  
  
## Syntax  
  
```cpp#  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```c#  
int LoadSymbols();  
```  
  
## Rückgabewert  
 Wenn die Methode erfolgreich ausgeführt, gibt sie `S_OK`zurück.  Bei einem Fehler wird ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Diese Methode lädt die Symbole vom aktuellen Suchpfad der geändert werden kann \(mithilfe der [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)\-Methode aufruft\).  
  
 Diese Methode ist über die [ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)\-Methode vorgezogen.  
  
## Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)