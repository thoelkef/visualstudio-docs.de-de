---
title: IDebugExtendedField::IsClosedType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b3c1badda9933c97761d3bf209380ba0c822b7f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002794"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Bestimmt, ob das Feld einen geschlossenen Typ darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn das Feld einen geschlossenen Typ ist, gibt `S_OK`ist, andernfalls gibt `S_FALSE`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)