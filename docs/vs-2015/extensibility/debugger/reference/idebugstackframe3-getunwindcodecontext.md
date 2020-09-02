---
title: 'IDebugStackFrame3:: getunwindcodecontext | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5a3fdaf9ca21841a43041f0ad5c1dc7b1507085
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546888"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Code Kontext zurück, der einen Speicherort darstellt, wenn ein Stapel Entladevorgang aufgetreten ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```csharp  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppCodeContext`  
 vorgenommen Gibt ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt zurück, das den Code Kontext Speicherort darstellt, wenn eine Stapel Entladung aufgetreten ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Obwohl diese Methode möglicherweise einen Code Kontext für den Speicherort nach einer Stapel Entladung zurückgibt, bedeutet dies nicht unbedingt, dass die Stapel Entladung tatsächlich im aktuellen Stapel Rahmen auftreten kann.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
