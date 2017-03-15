---
title: "IDebugMethodField::EnumStaticLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumStaticLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumStaticLocals-Methode"
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für statische lokale Variablen der Methode.  
  
## Syntax  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Parameter  
 `ppLocals`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste der statischen lokalen Variablen darstellt.  Gibt einen NULL\-Wert zurück, wenn keine statischen lokalen Variablen vorhanden sind.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine statischen lokalen Variablen vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt, das verschiedene Typen von statischen lokalen Variablen darstellt.  Rufen Sie die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)\-Methode für jedes Objekt auf, um genau zu bestimmen, welche Art von statische lokale Variable das Objekt darstellt.  
  
## Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)