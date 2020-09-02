---
title: 'Idebugpointerobject:: GetBytes | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ef0c01d86259b6ec8c23f2874244b018a74febc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188588"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Wert ab, auf den als eine Reihe von aufeinander folgenden Bytes gezeigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwStart`  
 in Ein Offset (in Bytes) vom Anfang des Objekts, auf das verwiesen wird.  
  
 `dwCount`  
 in Die Anzahl der abzurufenden bytes.  
  
 `pBytes`  
 [in, out] Ein Array, das mit dem Wert als Folge von aufeinander folgenden Bytes gefüllt wird, beginnend mit dem angegebenen Offset aus dem Objekt, auf das verwiesen wird.  
  
 `pdwBytes`  
 vorgenommen Gibt die Anzahl der tatsächlich abgerufenen Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird verwendet, wenn der Zeiger, der durch dieses [idebugpointerobject](../../../extensibility/debugger/reference/idebugpointerobject.md) dargestellt wird, auf einen primitiven Typ oder ein einfaches Array primitiver Typen zeigt (d. h. ein Array, das durch eine einfache Bytefolge dargestellt werden kann).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugpointerobject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
