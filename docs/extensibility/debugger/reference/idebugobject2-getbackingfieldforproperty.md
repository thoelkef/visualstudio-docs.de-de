---
title: "IDebugObject2::GetBackingFieldForProperty | Microsoft Docs"
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
  - "IDebugObject2::GetBackingFieldForProperty"
helpviewer_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty-Methode"
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Feld oder die Variable \(sofern vorhanden\) ab, die diese Eigenschaft unterstützen, die durch dieses Objekt dargestellt wird.  
  
## Syntax  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### Parameter  
 `ppObject`  
 \[out\]  Ein [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)\-Objekt, das das dahinter liegende Feld beschreibt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)\-Objekt stellt eine Eigenschaft Klassen von verwaltetem Code. h. eine Methode mit einem get\- und\/oder einem set\-Accessor dar.  Solche Eigenschaften müssen im Allgemeinen eine Variable, um den Wert, der von der Eigenschaft bearbeitet wird.  Diese Variable wird als das dahinter liegende Feld.  Wenn kein dahinter liegende Feld für das Objekt vorhanden ist, stellen Sie sicher, einen NULL\-Wert zurückzugeben: einige Aufrufer den Rückgabewert nicht unbedingt beachten, sondern stattdessen überprüfen, um zu ermitteln, ob ein NULL\-Wert in `ppObject`zurückgegeben wurde.  
  
## Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)