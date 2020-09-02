---
title: 'Idebugpropertyfield:: getpropertysetter | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8484aa4041e00b9decce73dc9e19e22aa106e9df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164857"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Methode ab, die die-Eigenschaft festlegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetPropertySetter(   
   IDebugMethodField** ppField  
);  
```  
  
```csharp  
int GetPropertySetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppField`  
 vorgenommen Gibt ein [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt zurück, das die Methode darstellt, die die-Eigenschaft festlegt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Um die Methode abzurufen, die die Eigenschaft abruft, können Sie die [getpropertygetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) -Methode aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugpropertyfield](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [Idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
