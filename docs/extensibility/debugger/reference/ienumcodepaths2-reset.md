---
title: "IEnumCodePaths2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2::Reset"
helpviewer_keywords: 
  - "IEnumCodePaths2::Reset"
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumCodePaths2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Setzt die Enumeration auf das erste Element zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf der [Weiter](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)\-Methode das erste Element der Enumeration zurück.  
  
## Siehe auch  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)