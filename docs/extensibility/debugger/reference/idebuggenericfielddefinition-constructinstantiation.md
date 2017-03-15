---
title: "IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ConstructInstantiation"
  - "IDebugGenericFieldDefinition::ConstructInstantiation"
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt eine Instanz des angegebenen Felds ein Array von Typargumenten.  
  
## Syntax  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```c#  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### Parameter  
 `cArgs`  
 \[in\]  Die Anzahl der Argumente im `ppArgs` Array.  
  
 `ppArgs`  
 \[in\]  Array, das die Typargumente enthält.  Die Typargumente müssen die geschlossenen Typen \(nicht generische oder vollständig instanziiertes Generika\) sein.  
  
 `ppConstructedField`  
 \[out\]  Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle zurück, die das neue Feld darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Einschränkungen werden nicht überprüft.  
  
## Siehe auch  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)