---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumNestedEnums
helpviewer_keywords: IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7667e21f57f3fc2844800e498d9519ddf9929f85
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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