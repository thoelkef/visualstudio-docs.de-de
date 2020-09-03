---
title: 'Idebugclassfield:: enumberstedenums | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84f60b9b0c882883c930657df59530f1c5107a22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191059"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für die unter aufgefügten Enumeratoren dieser Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der geschiesteten Enumerationen darstellt. Gibt einen NULL-Wert zurück, wenn keine unter aufgefügten Enumerationen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK zurückgegeben, oder es wird S_FALSE zurückgegeben, wenn keine unter-Enumeratoren vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Jedes Element der-Enumeration ist ein [idebugenumfield](../../../extensibility/debugger/reference/idebugenumfield.md) -Objekt, das eine geschsted-Enumeration beschreibt.  
  
 Eine Enumeration, die innerhalb einer Klasse deklariert wird, wird als geschachtelte Enumeration betrachtet. Angenommen, dies liegt vor:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 Die- `EnumNestedEnums` Methode gibt ein [ienumdebugfields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das ein [idebugenumfield](../../../extensibility/debugger/reference/idebugenumfield.md) -Objekt enthält, das die- `NestedEnum` Enumeration darstellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [Ienumdebug-Felder](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
