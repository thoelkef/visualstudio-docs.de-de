---
title: "IDebugMethodField::EnumParameters | Microsoft Docs"
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
  - "IDebugMethodField::EnumParameters"
helpviewer_keywords: 
  - "IDebugMethodField::EnumParameters-Methode"
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für die Parameter der Methode.  
  
## Syntax  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Parameter  
 `ppParams`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste der Parameter für die Methode darstellt. Andernfalls gibt einen NULL\-Wert zurück, wenn keine Parameter vorhanden sind.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine Parameter vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt, das verschiedene Typen von Parametern darstellt.  Rufen Sie die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)\-Methode für jedes Objekt auf, um genau zu bestimmen, welche Art von Parametern das Objekt darstellt.  
  
 Ein Parameter enthält den Variablennamen und den Typ.  Der erste Parameter in eine Klassenmethode ist in der Regel der „this“ \- Zeiger.  
  
 Wenn nur die Typen der Parameter erforderlich ist, rufen Sie die [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)