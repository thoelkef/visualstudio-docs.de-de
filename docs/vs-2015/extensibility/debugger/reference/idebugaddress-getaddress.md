---
title: IDebugAddress::GetAddress | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf2888a476c631fd17b8f97971deecfc699bfd57
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734336"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt eine Struktur, die beschreibt ein Objekt und seinen Speicherort in seinem Bereich oder den Container zurück.  
  
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
 [in, out] Ein [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) -Struktur, die von dieser Methode angegeben ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur an diese Methode, die es sich die entsprechenden Informationen dann füllt übergeben wird. Wie diese Informationen interpretiert werden, hängt von der Art von Informationen zurückgegeben, und der Symbol-Handler selbst ab. Finden Sie unter [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Weitere Details.  
  
## <a name="see-also"></a>Siehe auch  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

