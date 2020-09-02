---
title: 'Idebugfield:: getextendedinfo | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3de21bc984a36db87f8ce1567f4ff7d97212c40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547558"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode erhält erweiterte Informationen zu einem Feld.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Wählt die Informationen aus, die zurückgegeben werden sollen. Gültige Werte sind:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`guidConstantValue`|Der-Wert als Bytefolge.|  
|`guidConstantType`|Der Typ als Typsignatur.|  
  
 `prgBuffer`  
 vorgenommen Gibt die erweiterten Informationen zurück.  
  
 `pdwLen`  
 [in, out] Gibt die Größe der erweiterten Informationen in Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Derzeit gibt diese Methode nur den Typ oder den Wert einer Konstanten zurück. Der Aufrufer muss den in zurückgegebenen Puffer `prgBuffer` durch Aufrufen der com- `CoTaskMemFree` Funktion (C++) oder <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (c#) freigeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
