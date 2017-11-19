---
title: IDebugField::GetExtendedInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetExtendedInfo
helpviewer_keywords: IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5b52c5634b4b34edf11ddb8a56317cc237063bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Diese Methode ruft Informationen zu einem Feld erweitert.  
  
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
 [in] Wählt die Informationen zurückgegeben werden sollen. Gültige Werte sind:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`guidConstantValue`|Der Wert als eine Folge von Bytes.|  
|`guidConstantType`|Der Typ als eine Typsignatur.|  
  
 `prgBuffer`  
 [out] Gibt den erweiterten Informationen zurück.  
  
 `pdwLen`  
 [in, out] Gibt die Größe der erweiterten Informationen in Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Derzeit gibt diese Methode nur den Typ oder den Wert einer Konstante. Der Aufrufer muss im zurückgegebenen Puffers freigeben `prgBuffer` durch den Aufruf von COM `CoTaskMemFree` Funktion (C++) oder <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)