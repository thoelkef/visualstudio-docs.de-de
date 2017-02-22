---
title: "IDebugBinder3::FindAlias | Microsoft Docs"
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
  - "IDebugBinder3::FindAlias"
helpviewer_keywords: 
  - "IDebugBinder3::FindAlias-Methode"
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode sucht einen Alias, wenn ein Name.  Dies findet alle Aliase im Programm.  
  
## Syntax  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### Parameter  
 `pcstrName`  
 \[in\]  Name des Alias.  
  
 `ppAlias`  
 \[out\]  Alias hat \(sofern vorhanden\), dargestellt durch die [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)\-Schnittstelle.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls gibt `S_FALSE` zurück \(falls Alias nicht gefunden\) oder ein Fehlercode.  
  
## Hinweise  
 Diese Methode initialisiert das Zielobjekt NULL, bevor sie aufgerufen wird. Testen Sie anschließend einen NULL\-Wert für diese anschließend, um zu bestimmen, ob der Alias gefunden wurde.  
  
## Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)