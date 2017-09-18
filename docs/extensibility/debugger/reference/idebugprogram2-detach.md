---
title: "IDebugProgram2::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Detach"
helpviewer_keywords: 
  - "IDebugProgram2::Detach"
ms.assetid: 5e8d88b0-a8d4-4746-88c0-ad332ee73f33
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Trennt eine Debug\- Modul vom Programm.  
  
## Syntax  
  
```cpp#  
HRESULT Detach(   
   void   
);  
```  
  
```c#  
int Detach();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein getrenntes Programm weiterhin ausgeführt wird. Es ist jedoch nicht mehr Teil der Debugsitzung.  Nicht mehr Ereignisse Debuggen des Programms werden gesendet, sobald das Debugmodul getrennt wird.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)