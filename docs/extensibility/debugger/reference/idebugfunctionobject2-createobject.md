---
title: "IDebugFunctionObject2::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::CreateObject"
  - "CreateObject"
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt ein Objekt, das Einstellungen eines angegebenen Auswertungs\-Flags des Konstruktors und einen Timeoutwert verwendet.  
  
## Syntax  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### Parameter  
 `pConstructor`  
 \[in\]  Ein [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)\-Objekt, das den Konstruktor des zu erstellenden Objekts darstellt.  
  
 `dwArgs`  
 \[in\]  Die Anzahl von Parametern im `pArg` Array.  Stellt die Anzahl von Parametern dar, die an den Konstruktor übergeben werden.  
  
 `pArgs`  
 \[in\]  Ein Array [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekten, das die Parameter darstellt, der an den Konstruktor übergeben.  
  
 `dwEvalFlags`  
 \[in\]  Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)\-Enumeration, die angeben, wie die Evaluierung ausgeführt werden soll.  
  
 `dwTimeout`  
 \[in\]  Maximale Zeit in Millisekunden, bevor der Rückgabe dieser Methode zu warten.  **INFINITE** verwenden, um unbegrenzt zu warten.  
  
 `ppObject`  
 \[out\]  Gibt ein **IDebugObject zurück,** das **das** neu erstellte Objekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Rufen Sie diese Methode auf, um ein Objekt, das eine Instanz einer Klasse darstellt oder anderen komplexen Typ erstellen, der einen Konstruktor erfordert, die einen Parameter handelt.  
  
## Siehe auch  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)