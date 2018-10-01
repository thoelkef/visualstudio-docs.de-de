---
title: IDebugProperty2::GetPropertyInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1f4b3e08f81262de7bfb56f4f479dbe38ac6b64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523863"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProperty2::GetPropertyInfo](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2-getpropertyinfo).  
  
Ruft die [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) -Struktur, die eine Eigenschaft beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp#  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 [in] Eine Kombination von Werten aus der [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Enumeration, der angibt, welche Felder sind in ausgefüllt werden, müssen die `pPropertyInfo` Struktur.  
  
 `nRadix`  
 [in] Die Basis bei der Formatierung von numerischen Informationen verwendet werden.  
  
 `dwTimeout`  
 [in] Gibt die maximale Zeit in Millisekunden, warten Sie vor der Rückgabe dieser Methode an. Verwendung `INFINITE` für Warten ohne Timeout.  
  
 `rgpArgs`  
 [in, out] Für die zukünftige Verwendung reserviert. Legen Sie auf einen null-Wert.  
  
 `dwArgCount`  
 [in] Für die zukünftige Verwendung reserviert. Legen Sie auf 0 (null).  
  
 `pPropertyInfo`  
 [out] Ein [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) -Struktur, die mit der Beschreibung der Eigenschaft gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)

