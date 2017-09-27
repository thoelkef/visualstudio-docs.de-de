---
title: IDebugField::GetSize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
caps.latest.revision: 11
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
ms.openlocfilehash: 5f025b96c3a37cd55d8bc148d04196a862f7e7bc
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Diese Methode ruft die Größe eines Felds in Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwSize`  
 [out] Gibt die Größe zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Alle Felder verfügen über einen Typ und alle Typen verfügen über eine Größe. Beispielsweise verfügt über ein Feld vom Typ Byte einer Größe von 1 Byte.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
