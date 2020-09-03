---
title: 'Idebugclassfield:: enumnetstedclasses | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7745eea3f5b3264016a25defd696a9b85f2e9fb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191073"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für die Klassen, die in dieser Klasse eingefügt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der geschiesteten Klassen darstellt. Gibt einen NULL-Wert zurück, wenn keine Unterklassen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine Unterklassen vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Jedes Element der-Enumeration ist ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das eine geschsted-Klasse beschreibt.  
  
 Eine geschachtelte Klasse ist eine Klasse, die in einer anderen Klasse definiert ist. Beispiel:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Die [ienumdebugfields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Enumeration enthält ein Objekt, das die- `NestedClass` Klasse darstellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
