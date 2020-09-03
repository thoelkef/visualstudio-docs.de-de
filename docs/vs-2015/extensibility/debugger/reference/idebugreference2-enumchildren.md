---
title: 'IDebugReference2:: enumchildren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4df5ad26db3ad519f162c62150d822ae2bc4b687
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182486"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Eine Liste ausgewählter untergeordneter Elemente eines Verweises erhalten. Für zukünftige Verwendung reserviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGREF_INFO_FLAGS        dwFields,  
   DWORD                      dwRadix,  
   DBG_ATTRIB_FLAGS           dwAttribFilter,  
   LPCOLESTR                  pszNameFilter,  
   DWORD                      dwTimeout,  
   IEnumDebugReferenceInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGREF_INFO_FLAGS     dwFields,  
   uint                         dwRadix,  
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,  
   string                       pszNameFilter,  
   uint                         dwTimeout,  
   out IEnumDebugReferenceInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 in Eine Kombination von Flags aus der [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Enumeration, die angibt, welche Felder in den aufgelisteten [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen ausgefüllt werden sollen.  
  
 `dwRadix`  
 in Der zum Formatieren numerischer Informationen zu verwendende Basis.  
  
 `dwAttribFilter`  
 in Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Enumeration, die als Filter in Kombination mit dem-Parameter verwendet wird, `pszNameFilter` um auszuwählen, welche Strukturen aufgelistet werden sollen.  
  
 `pszNameFilter`  
 in Eine Zeichenfolge, die einen Filter angibt, z. b. "MYX", der in Kombination mit dem-Parameter verwendet wird, `dwAttribFilter` um die aufzuzählenden Strukturen auszuwählen.  
  
 `dwTimeout`  
 in Maximale Zeit in Millisekunden, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden `INFINITE` Sie, um unbegrenzt zu warten.  
  
 `ppEnum`  
 vorgenommen Gibt ein [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) -Objekt zurück, das eine Liste der angeforderten untergeordneten Eigenschaften enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
