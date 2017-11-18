---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress::GetAddress
helpviewer_keywords: IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ed14b69dbc116514b191aadf58d209b4d39e458
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Gibt eine Struktur, die beschreibt ein Objekt und dessen Speicherort innerhalb des Bereichs oder den Container zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 [in, out] Ein [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) -Struktur, die von dieser Methode ausgefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur übergeben wird, um diese Methode, die dann sie sich mit den entsprechenden Informationen voll ist. Wie diese Informationen interpretiert wird, hängt von der Art der Informationen zurückgegeben und der Symbol-Handler selbst ab. Finden Sie unter [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Weitere Details.  
  
## <a name="see-also"></a>Siehe auch  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)