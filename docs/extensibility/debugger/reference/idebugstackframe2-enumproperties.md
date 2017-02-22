---
title: "IDebugStackFrame2::EnumProperties | Microsoft Docs"
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
  - "IDebugStackFrame2::EnumProperties"
helpviewer_keywords: 
  - "IDebugStackFrame2::EnumProperties"
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2::EnumProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für die Eigenschaften, die dem Stapelrahmen, z. B. lokale Variablen zugeordnet sind.  
  
## Syntax  
  
```cpp#  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### Parameter  
 `dwFieldSpec`  
 \[in\]  Eine Kombination von Flags aus der [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)\-Enumeration, die angibt, welche Felder in den aufgelisteten [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen gefüllt werden sollen.  
  
 `nRadix`  
 \[in\]  Die Basis verwendet werden soll, wenn alle numerischen Daten formatiert werden.  
  
 `refiid`  
 \[in\]  Ein GUID eines Filters verwendet, um den [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen aufgelistet werden sollen, z. B. `guidFilterLocals`auszuwählen.  
  
 `dwTimeout`  
 \[in\]  Maximale Zeit in Millisekunden, bevor der Rückgabe dieser Methode zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
 `pcelt`  
 \[out\]  Gibt die Anzahl der aufgelisteten Eigenschaften zurück.  Dies entspricht dem die [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)\-Methode aufgerufen wird.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)\-Objekt zurück, das eine Liste der gewünschten Eigenschaften enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Da diese Methode alle ausgewählten mit ermöglicht es einem einzelnen Aufruf Eigenschaften abgerufen werden sollen, ist jedoch schneller als die [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) und [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)\-Methoden nacheinander, aufgerufen wird.  
  
## Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)