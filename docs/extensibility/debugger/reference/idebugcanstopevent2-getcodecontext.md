---
title: IDebugCanStopEvent2::GetCodeContext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05cd4729635042d67f063bbba412c19a4a2f89f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818340"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
Ruft ab, der Codekontext, der den Speicherort der dieses Ereignis beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppCodeContext`  
 [out] Gibt die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) Objekt, das den aktuellen Speicherort darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Für die meisten Laufzeitfehler-Architekturen kann ein Codekontext als Adresse im Stream Ausführung eines Programms auf eine bestimmte Anweisung betrachtet werden.  
  
 Rufen Sie den Dokumentenkontext, der auf die Quellcodezeilen ausgerichtet ist, rufen Sie die [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)