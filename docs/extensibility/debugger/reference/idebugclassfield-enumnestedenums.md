---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ea28f2a455d3528f083ba2acb2e9e4ad8989319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103028"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Erstellt einen Enumerator für die geschachtelte Enumeratoren dieser Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der geschachtelten Enumerationen darstellt. Gibt einen null-Wert zurück, wenn keine geschachtelten Enumerationen vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück oder gibt "S_FALSE" zurück, wenn keine geschachtelten Enumeratoren vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jedes Element der Enumeration ist ein [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) -Objekt, das eine geschachtelten Enumeration beschreibt.  
  
 Eine Enumeration, die innerhalb einer Klasse deklariert wird eine geschachtelten Enumeration betrachtet. Angenommen, dies liegt vor:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 Die `EnumNestedEnums` Methodenrückgabewert würde eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt, das eine enthält [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) Objekt, das darstellt der `NestedEnum` Enumeration.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)