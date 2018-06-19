---
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5fb55fb6f9a90cf39120be408428524f64463d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116951"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Legt den Wert einer Eigenschaft aus einer angegebenen Zeichenfolge fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszValue`  
 [in] Eine Zeichenfolge mit dem Wert, der festgelegt werden.  
  
 `nRadix`  
 [in] Eine Basis interpretieren alle numerischen Daten verwendet werden sollen. Dies kann 0 versucht, die die Basis automatisch zu bestimmen sein.  
  
 `dwTimeout`  
 [in] Gibt die maximale Zeit in Millisekunden, bis vor der Rückgabe dieser Methode. Verwendung `INFINITE` zum unendlichen Warten angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird Fehlercode zurückgegeben. Die folgende Tabelle zeigt weitere mögliche Werte.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Die Zeichenfolge konnte nicht in einem Eigenschaftswert konvertiert werden, oder der Eigenschaftswert konnte nicht festgelegt werden.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Die Eigenschaft ist schreibgeschützt.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)