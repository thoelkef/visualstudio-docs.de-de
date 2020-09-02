---
title: 'Idebugfield:: Equal | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa630a6f2084f7ff79a9c89b685658cf694fcab9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547311"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode vergleicht dieses Feld mit dem angegebenen Feld auf Gleichheit.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pField`  
 in Das Feld, das mit diesem verglichen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Felder identisch sind, wird zurückgegeben `S_OK` . Wenn die Felder verschieden sind, wird zurückgegeben `S_FALSE.` , andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
