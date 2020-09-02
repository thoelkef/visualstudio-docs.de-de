---
title: 'Idebugpropertyfield:: getpropertygetter | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6c1a9f712555de6f4b8400f828bf18aca13c779d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164869"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Methode ab, die die Eigenschaft abruft.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetPropertyGetter(   
   IDebugMethodField** ppField  
);  
```  
  
```cpp#  
int GetPropertyGetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 vorgenommen Gibt ein [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt zurück, das die Methode darstellt, mit der die Eigenschaft abgerufen wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Zum Abrufen der Methode, mit der die-Eigenschaft festgelegt wird, ruft [getpropertysetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) die-Methode auf.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugpropertyfield](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [Getpropertysetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
