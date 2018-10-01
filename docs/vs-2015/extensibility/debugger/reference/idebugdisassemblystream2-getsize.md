---
title: IDebugDisassemblyStream2::GetSize | Microsoft-Dokumentation
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
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d91f08406bac9800fe716fc123495ae74418bfef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514943"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDisassemblyStream2::GetSize](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2-getsize).  
  
Ruft die Größe in Anweisungen dieses Streams Disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

