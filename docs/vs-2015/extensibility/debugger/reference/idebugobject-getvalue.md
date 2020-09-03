---
title: 'Idebugobject:: GetValue | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de6e6888cfce338ebcee90e722f07e900ce25d0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180531"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Wert des-Objekts als aufeinander folgende Reihe von Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pValue`  
 [in, out] Ein Array, das mit einer aufeinanderfolgenden Reihe von Bytes gefüllt ist, die den Wert des-Objekts darstellen.  
  
 `nSize`  
 in Die maximale Anzahl der abzurufenden bytes.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Rufen Sie die Gesamtzahl der Bytes ab, die durch Aufrufen der [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) -Methode abgerufen werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
