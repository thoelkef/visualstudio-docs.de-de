---
title: IDebugProperty2::EnumChildren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3045c79926efc367b187f88727b5841852dadfb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823588"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Liste der untergeordneten Elemente der Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
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
  
```csharp  
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
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 [in] Eine Kombination von Flags aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, der angibt, welche Felder in den aufgelisteten [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Strukturen sind gefüllt werden soll.  
  
 `dwRadix`  
 [in] Gibt an, die Basis bei der Formatierung von numerischen Informationen verwendet werden.  
  
 `guidFilter`  
 [in] GUID des Filters verwendet wird, mit der `dwAttribFilter` und `pszNameFilter` Parameter auswählen, welche `DEBUG_PROPERTY_INFO` untergeordnet sind, aufgelistet werden sollen. Z. B. `guidFilterLocals` Filter für lokale Variablen.  
  
 `dwAttribFilter`  
 [in] Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Enumeration, der angibt, welche Objekttypen aufgelistet, z. B. `DBG_ATTRIB_METHOD` für alle Methoden, die untergeordneten Elemente dieser Eigenschaft sein können. In Kombination mit verwendet die `guidFilter` und `pszNameFilter` Parameter.  
  
 `pszNameFilter`  
 [in] Der Name des Filters verwendet wird, mit der `guidFilter` und `dwAttribFilter` Parameter auswählen, welche `DEBUG_PROPERTY_INFO` untergeordnet sind, aufgelistet werden sollen. Dieser Parameter z. B. festlegen "MyX" Filter, für alle untergeordneten Elemente mit dem Namen "MyX."  
  
 `dwTimeout`  
 [in] Gibt die maximale Zeit in Millisekunden, warten Sie vor der Rückgabe dieser Methode an. Verwendung `INFINITE` für Warten ohne Timeout.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) -Objekt, das eine Liste der untergeordneten Eigenschaften enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)

