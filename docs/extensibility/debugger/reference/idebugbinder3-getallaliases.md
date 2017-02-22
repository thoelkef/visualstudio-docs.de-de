---
title: "IDebugBinder3::GetAllAliases | Microsoft Docs"
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
  - "IDebugBinder3::GetAllAliases"
helpviewer_keywords: 
  - "IDebugBinder3::GetAllAliases-Methode"
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft eine Liste der Aliase vom Programm abgerufen.  
  
## Syntax  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```c#  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### Parameter  
 `uRequest`  
 \[in\]  Die maximale Anzahl der zurückzugebenden Alias \(gibt die Länge des Arrays an, das in `ppAliases`übergeben wird\).  
  
 `ppAliases`  
 \[in, out\]  Mit Aliasnamen auszufüllende Array \(wenn dies ein NULL\-Wert ist und `uRequest` 0 ist, wird die Anzahl der Aliase, die zurückgegeben werden können, um `puFetched`zurückgegeben\).  
  
 `puFetched`  
 \[out\]  Gibt die Anzahl der abgerufenen Alias zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)