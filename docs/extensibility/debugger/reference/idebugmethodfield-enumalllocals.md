---
title: "IDebugMethodField::EnumAllLocals | Microsoft Docs"
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
  - "IDebugMethodField::EnumAllLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumAllLocals-Methode"
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für alle lokalen Variablen, einschließlich der Methode, die intern von einem Compiler generiert wurden.  
  
## Syntax  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Parameter  
 `pAddress`  
 \[in\]  Ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekt, das eine Adresse innerhalb der Methode, zeigenden auf einen bestimmten Bereich oder Kontext darstellt.  
  
 `ppLocals`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste aller lokalen Variablen im angegebenen Bereich darstellt. Andernfalls gibt einen NULL\-Wert zurück. Dies gibt an, dass keine lokalen Variablen angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine lokalen Variablen vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Nur die Variablen, die innerhalb des Blocks definiert werden, die mit der angegebenen Adresse, werden aufgezählt.  Diese Methode schließt alle vom Compiler generierten lokalen Variablen.  Wenn alle erforderlichen die lokalen Variablen sind, die explizit in der Quelle definiert wurden, rufen Sie die [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)\-Methode auf.  
  
 Eine Methode kann die mehrere Kontexte oder Blöcke enthalten.  
  
## Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)