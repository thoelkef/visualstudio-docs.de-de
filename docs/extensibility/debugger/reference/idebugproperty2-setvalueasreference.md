---
title: "IDebugProperty2::SetValueAsReference | Microsoft Docs"
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
  - "IDebugProperty2::SetValueAsReference"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsReference-Methode"
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Wert dieser Eigenschaft auf den Wert des angegebenen Verweises ab.  
  
## Syntax  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```c#  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### Parameter  
 `rgpArgs`  
 \[in\]  Ein Array setzer Eigenschaft zu verwaltetem Code zu übergebenden Argumente.  Wenn der Eigenschaftensetter keine Argumente akzeptiert, oder wenn dieses Objekt nicht [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) eines solchen Eigenschaftensetter verweist, muss `rgpArgs` ein NULL\-Wert sein.  Dieser Parameter ist in der Regel ein NULL\-Wert.  
  
 `dwArgCount`  
 \[in\]  Die Anzahl der Argumente im `rgpArgs` Array.  
  
 `pValue`  
 \[in\]  Ein Verweis in Form eines [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Objekts auf den Wert, mit dem diese Eigenschaft festzulegen.  
  
 `dwTimeout`  
 \[in\]  Wie lange dauert von den Wert in Millisekunden festgelegt werden soll.  Ein typischer Wert ist `INFINITE`.  Dies wirkt sich auf die Zeit, die eine Auswertung annehmen kann.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode, in der Regel einen der folgenden Werte zurück:  
  
|Fehler|Beschreibung|  
|------------|------------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Das Festlegen des Werts aus einem Verweis wird nicht unterstützt.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Der Wert kann nicht festgelegt werden, da diese Eigenschaft eine Methode verweist.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Der Wert ist schreibgeschützt und kann nicht festgelegt werden.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)