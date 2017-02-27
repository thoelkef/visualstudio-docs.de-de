---
title: "IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::SetRegistryRoot"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::SetRegistryRoot-Methode"
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode legt den Registrierungsstamm fest.  Wird für paralleles Debuggen.  
  
## Syntax  
  
```cpp#  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```c#  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### Parameter  
 `ustrRegistryRoot`  
 \[in\]  Der neue Registrierungsstamm.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der angegebene Registrierungsstamm wird in der Regel festgelegt, wenn sich die Ausdrucksauswertung zuerst instanziiert wird und für den Registrierungsschlüssel für eine bestimmte Version von Visual Studio wird \(HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*X.Y*, wo *X.Y* eine Versionsnummer ist\).  
  
## Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)