---
title: "IDebugAlias::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugAlias::GetICorDebugValue-Methode"
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine verwaltete Codeschnittstelle, die den Wert dieser Alias darstellt ab.  
  
## Syntax  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### Parameter  
 `ppUnk`  
 \[Out\] `IUnknown` Schnittstelle, die den Wert dieser Alias darstellt. Diese Schnittstelle kann abgefragt werden, für die `ICorDebugValue` Schnittstelle.  
  
## Rückgabewert  
 Bei erfolgreicher Ausführung gibt S\_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Diese Methode gilt nur für verwaltete Werte \(die `ICorDebugValue` steht eine Schnittstelle in der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] und ist definiert der [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK in der Datei cordebug.idl\).  
  
## Siehe auch  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)