---
title: IDebugField::GetType | Microsoft-Dokumentation
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
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4c0209830694cc6256974e8f6a66f0b67eb4803
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176396"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft den Typ des Felds ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppType`  
 [out] Gibt den Feldtyp, wie eine andere [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

