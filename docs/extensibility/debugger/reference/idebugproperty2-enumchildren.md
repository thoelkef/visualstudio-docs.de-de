---
title: "IDebugProperty2::EnumChildren | Microsoft Docs"
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
  - "IDebugProperty2::EnumChildren"
helpviewer_keywords: 
  - "IDebugProperty2::EnumChildren"
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste der untergeordneten Elemente der Eigenschaft ab.  
  
## Syntax  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### Parameter  
 `dwFields`  
 \[in\]  Eine Kombination von Flags aus der [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)\-Enumeration, die angibt, welche Felder in den aufgelisteten [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen gefüllt werden sollen.  
  
 `dwRadix`  
 \[in\]  Gibt die beim Formatieren numerischer Daten an alle Basis verwendet werden soll.  
  
 `guidFilter`  
 \[in\]  GUID des Filters verwendet `dwAttribFilter` mit den Parametern `pszNameFilter` und auswählen können, die `DEBUG_PROPERTY_INFO` untergeordnete Elemente aufgelistet werden sollen.  Zum Beispiel `guidFilterLocals` Filter für lokale Variablen.  
  
 `dwAttribFilter`  
 \[in\]  Eine Kombination von Flags aus der [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)\-Enumeration, die angibt, welcher Typ der aufzulistenden Objekte, z. B. `DBG_ATTRIB_METHOD` für alle Methoden, die untergeordnete Elemente dieser Eigenschaft sind.  Wird in Verbindung mit den `guidFilter` und `pszNameFilter`\-Parametern.  
  
 `pszNameFilter`  
 \[in\]  Der Name des Filters, die mit den `guidFilter` und `dwAttribFilter`\-Parametern auswählen, die `DEBUG_PROPERTY_INFO` untergeordnete Elemente aufgelistet werden sollen.  Zum Beispiel“ diesen Parameter auf „MyX durch Festlegen von Filtern für alle untergeordneten Elemente mit dem Namen „MyX“.  
  
 `dwTimeout`  
 \[in\]  Bevor der Rückgabe dieser Methode gibt die maximale Zeit in Millisekunden an, zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)\-Objekt zurück, das eine Liste mit untergeordneten Eigenschaften enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)