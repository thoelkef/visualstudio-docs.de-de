---
title: 'IDebugThread2:: cansetnextstatement | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3e98603a39d820b5565836bd2620f8a27def76f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153071"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bestimmt, ob der aktuelle Anweisungs Zeiger auf den angegebenen Stapel Rahmen festgelegt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CanSetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int CanSetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 Für zukünftige Verwendung reserviert. Legen Sie auf einen NULL-Wert fest. Wenn dies ein NULL-Wert ist, verwenden Sie den aktuellen Stapel Rahmen.  
  
 `pCodeContext`  
 in Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das den Code Speicherort beschreibt, der ausgeführt werden soll, und seinen Kontext.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn diese Methode zurückgibt `S_OK` , wird die [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) -Methode aufgerufen, um die nächste Anweisung tatsächlich festzulegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
