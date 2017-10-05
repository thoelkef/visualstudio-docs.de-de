---
title: IDebugThread2::CanSetNextStatement | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 8ffa88255d8f61e8908a6ec33e04e56a03ab6405
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Bestimmt, ob für der aktuellen Anweisungszeiger auf den angegebenen Stapelrahmen festgelegt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 Für die zukünftige Verwendung reserviert. Legen Sie auf einen null-Wert. Ist dies ein null-Wert, verwenden Sie den aktuellen Stapelrahmen.  
  
 `pCodeContext`  
 [in] Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das den Speicherort der Code ausgeführt werden soll beschreibt und seines Kontexts.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Methode zurückgibt `S_OK`, rufen Sie anschließend die [nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) Methode, um tatsächlich auf die nächste Anweisung festlegen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [Nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
