---
title: "IDebugEnumField::GetStringFromValue | Microsoft Docs"
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
  - "IDebugEnumField::GetStringFromValue"
helpviewer_keywords: 
  - "IDebugEnumField::GetStringFromValue-Methode"
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft der Name aus dem angegebenen konstanten Wert der Enumeration handeln.  
  
## Syntax  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```c#  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### Parameter  
 `value`  
 \[in\]  Der Wert, der den Namen der Enumerationskonstante abruft.  
  
 `pbstrValue`  
 \[out\]  Gibt den Namen der Enumerationskonstante zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls gibt `S_FALSE` , wenn der Wert über keinen zugeordneten Namen zurück oder gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn mehr als einen Namen vorhanden ist, der mit demselben Wert zugeordnet wird, wird der Vorname, der in der Enumeration definiert ist, zurückgegeben.  
  
## Siehe auch  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)