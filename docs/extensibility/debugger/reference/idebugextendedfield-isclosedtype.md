---
title: IDebugExtendedField::IsClosedType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ad1498f0f169e10bcc58cdc0f5e041096766e87c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Bestimmt, ob das Feld einen geschlossenen darstellt.  
  
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
 Wenn das Feld ein geschlossener Typ ist, gibt `S_OK`ist, andernfalls gibt `S_FALSE`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)