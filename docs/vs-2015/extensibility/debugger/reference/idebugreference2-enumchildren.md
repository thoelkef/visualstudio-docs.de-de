---
title: IDebugReference2::EnumChildren | Microsoft-Dokumentation
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182486"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Liste der ausgewählten, untergeordneten Elemente eines Verweises. Zur künftigen Verwendung reserviert.  
  
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
 [in] Eine Kombination von Flags aus der [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Enumeration, der angibt, welche Felder in den aufgelisteten [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Strukturen sind gefüllt werden soll.  
  
 `dwRadix`  
 [in] Die Basis bei der Formatierung von numerischen Informationen verwendet werden.  
  
 `dwAttribFilter`  
 [in] Eine Kombination von Flags aus der [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) -Enumeration, der verwendet wird, als Filter in Kombination mit der `pszNameFilter` Parameter auswählen, welche Strukturen sind, aufgelistet werden sollen.  
  
 `pszNameFilter`  
 [in] Eine Zeichenfolge, die Angabe eines Filters, wie z. B. "MyX", verwendet in Kombination mit der `dwAttribFilter` Parameter an, wählen Sie die Strukturen aufgelistet werden sollen.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, die vor der Rückgabe dieser Methode gewartet. Verwendung `INFINITE` für Warten ohne Timeout.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) -Objekt, das eine Liste der angeforderten untergeordneten Eigenschaften enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
