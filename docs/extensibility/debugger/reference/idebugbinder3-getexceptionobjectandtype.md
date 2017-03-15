---
title: "IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType"
helpviewer_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType-Methode"
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft die Ausnahme ab, die einem Objekt zugeordnet ist \(sofern zutreffend\).  
  
## Syntax  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### Parameter  
 `ppException`  
 \[out\]  Gibt das Objekt zurück, das die Ausnahme darstellt.  
  
 `ppField`  
 \[out\]  Gibt das Objekt zurück, das ein bestimmtes Feld darstellt, das die Ausnahme verursacht hat \(dies ist ein NULL\-Wert.\)  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
> [!NOTE]
>  Um sicherzustellen, dass es eine Ausnahme vorhanden sind, überprüfen Sie den Wert, der von `ppException`zurückgegeben wird: wenn ein NULL\-Wert ist, wird keine Ausnahme mit diesem Objekt verknüpft.  
  
## Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)