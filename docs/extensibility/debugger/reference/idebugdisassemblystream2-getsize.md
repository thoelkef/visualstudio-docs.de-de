---
title: IDebugDisassemblyStream2::GetSize | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 434a53803dcc08a5d4b07b531b56e913d5311d1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934794"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Ruft die Größe in Anweisungen dieses Streams Disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pnSize`  
 [out] Gibt die Größe in Anweisungen zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der von dieser Methode zurückgegebene Wert kann verwendet werden, ein Array von zuweisen [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Strukturen, die dann an die [lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)