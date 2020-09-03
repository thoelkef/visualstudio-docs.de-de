---
title: 'Idebugcontainerfield:: EnumFields | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 485de4bdc9ff5b17c056c0db4e2930f5c6986fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205299"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator für die Felder des Containers.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Eine Kombination aus [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Konstanten, die die aufzuzählenden Felder auswählen. Feldtypen können Speichertypen beschreiben, z. b. Klasse oder primitiv, oder bestimmte Informationen, wie z. b. local, Parameter oder "This"-Zeiger.  
  
 `dwModifiersFilter`  
 in Eine Kombination aus [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Konstanten, die die aufzuzählenden Felder auswählen. Feldmodifizierer können Zugriffsberechtigungen sein, z. b. Public oder private, oder Speicherinformationen, wie z. b. Virtual, static oder Final.  
  
 `pszNameFilter`  
 in Der Name des Felds, das aufgelistet werden soll. Dies kann ein NULL-Wert sein, wenn alle Felder zurückgegeben werden sollen.  
  
 `nameMatch`  
 in Ein Wert aus der [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) Enumeration, der steuert, ob bei der Suche die Groß-/Kleinschreibung beachtet wird.  
  
 `ppEnum`  
 vorgenommen Gibt ein [ienumdebug Fields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt zurück, das die Liste der Felder darstellt. Gibt einen NULL-Wert zurück, wenn keine Felder vorhanden sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird S_OK oder S_FALSE zurückgegeben, wenn keine Felder vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die `dwKindFilter` `dwModifiersFilter` Parameter, und `pszNameFilter` können kombiniert werden, um z. b. Alle öffentlichen virtuellen Methoden mit dem Namen "MyMethod" auszuwählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Idebugcontainerfield](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [Ienumdebug-Felder](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
