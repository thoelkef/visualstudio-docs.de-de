---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 915cf272a592628f6d25ebf04edd4309bceccfb3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007788"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Diese Methode ruft Informationen über ein Feld erweitert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidExtendedInfo`  
 [in] Wählt die Informationen zurückgegeben werden. Gültige Werte sind:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`guidConstantValue`|Der Wert als eine Folge von Bytes.|  
|`guidConstantType`|Der Typ als eine Typsignatur.|  
  
 `prgBuffer`  
 [out] Gibt den erweiterten Informationen zurück.  
  
 `pdwLen`  
 [in, out] Gibt die Größe der erweiterten Informationen, in Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Derzeit gibt diese Methode auf, nur den Typ oder Wert einer Konstante. Der Aufrufer muss im zurückgegebenen Puffers freigeben `prgBuffer` durch Aufrufen von COM `CoTaskMemFree` Funktion (C++) oder <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)