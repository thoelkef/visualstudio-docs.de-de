---
title: IDebugField::Equal | Microsoft-Dokumentation
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
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8973f82c2237bb606fa9dba84b1d3135adddde80
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735966"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode vergleicht dieses Feld mit dem angegebenen Feld hinsichtlich ihrer Gleichheit.  
  
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
 [in] Das Feld, in dieses Objekt verglichen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück, wenn die Felder identisch sind, `S_OK`. Gibt zurück, wenn die Felder unterscheiden, `S_FALSE.` wird, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

