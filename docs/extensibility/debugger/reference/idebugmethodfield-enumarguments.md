---
title: "IDebugMethodField::EnumArguments | Microsoft Docs"
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
  - "IDebugMethodField::EnumArguments"
helpviewer_keywords: 
  - "IDebugMethodField::EnumArguments-Methode"
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für den Typ jedes Arguments, das zum Aufrufen der Methode benötigt wird.  
  
## Syntax  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Parameter  
 `ppParams`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste der Argumenttypen darstellt.  Gibt einen NULL\-Wert zurück, wenn keine Argumente vorhanden sind.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn keine Argumente vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jedes Element ist ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt, das die Typen der einzelnen Parameter darstellt.  Rufen Sie die [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)\-Methode auf, um Informationen über den Typ jedes Parameters abzurufen.  
  
 Wenn der Name des Parameters mit dem Typ benötigt wird, und rufen Sie dann die [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)