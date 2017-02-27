---
title: "IDebugEngine2::SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::SetLocale"
helpviewer_keywords: 
  - "IDebugEngine2::SetLocale"
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt das Gebietsschema des Debugmoduls fest \(DE\).  
  
## Syntax  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### Parameter  
 `wLangID`  
 \[in\]  Gibt das Gebietsschema Sprachen angezeigt.  Beispielsweise 1033 für Englisch.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird vom Debugbuild Manager der Sitzung \(SDM\) aufgerufen, um die regionalen Einstellungen der IDE weiterzugeben, dass Zeichenfolgen, die durch DE zurückgegeben werden, ordnungsgemäß lokalisiert werden.  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)