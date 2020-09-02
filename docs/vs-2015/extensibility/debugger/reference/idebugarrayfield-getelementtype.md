---
title: 'Idebugarrayfield:: GetElementType | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ae24c2449d9bd26895647fc8f7b026291c4288
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68142979"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Typ des Elements im Array ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppType`  
 vorgenommen Gibt ein [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) -Objekt zurück, das den Typ des Elements beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Das [idebugarrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md) -Objekt geht davon aus, dass alle Elemente des Arrays denselben Typ haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugarrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
