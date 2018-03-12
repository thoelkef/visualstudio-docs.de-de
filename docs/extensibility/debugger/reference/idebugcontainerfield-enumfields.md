---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a262d2f4aa90bc9ae638fb6cfbfe8af605f2446a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Erstellt einen Enumerator für die Felder des Containers.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwKindFilter`  
 [in] Eine Kombination von [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Konstanten, die die Felder aufgelistet werden sollen. Feld Arten können Speichertypen, z. B. Klasse oder Primitiv oder bestimmte Informationen, z. B. lokale, Parameter oder "this" Zeiger beschreiben.  
  
 `dwModifiersFilter`  
 [in] Eine Kombination von [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Konstanten, die die Felder aufgelistet werden sollen. Feldmodifizierern können Zugriffsberechtigungen, z. B. öffentlichen oder privaten Speicherinformationen, z. B. virtuelle, statischen oder den abschließenden sein.  
  
 `pszNameFilter`  
 [in] Der Name des Felds aufgelistet werden sollen. Dies kann ein null-Wert sein, wenn alle Felder sind, zurückgegeben werden.  
  
 `nameMatch`  
 [in] Ein Wert aus der [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) -Enumeration, der steuert, ob die Suche Groß-/Kleinschreibung beachtet wird, oder nicht.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der Felder darstellt. Gibt einen null-Wert zurück, wenn keine Felder vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK oder "S_FALSE" zurück, wenn keine Felder vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die `dwKindFilter`, `dwModifiersFilter`, und `pszNameFilter` Parameter können kombiniert werden, z. B. um alle öffentliche virtuelle Methoden, die mit dem Namen "MyMethod" auszuwählen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)