---
title: "IDebugContainerField::EnumFields | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugContainerField::EnumFields"
helpviewer_keywords: 
  - "IDebugContainerField::EnumFields-Methode"
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für die Felder des Containers.  
  
## Syntax  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### Parameter  
 `dwKindFilter`  
 \[in\]  Eine Kombination von [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md) Konstanten, die die Felder auswählen, die aufgelistet werden sollen.  arten Feld speichern können, z. B. Klasse oder Primitive oder bestimmte Informationen, z. B. lokale Variablen, Parameter oder „this“ \- Zeiger beschreiben.  
  
 `dwModifiersFilter`  
 \[in\]  Eine Kombination von [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Konstanten, die die Felder auswählen, die aufgelistet werden sollen.  Feld modifizierer Zugriffsberechtigungen können, z. B. öffentliches oder privates oder Speicherinformationen, wie ein virtuelles, statisch sein oder endgültige.  
  
 `pszNameFilter`  
 \[in\]  Der Name des Felds, die aufgelistet werden sollen.  Dies kann ein NULL\-Wert sein, wenn alle Felder zurückgegeben werden sollen.  
  
 `nameMatch`  
 \[in\]  Ein Wert aus der [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)\-Enumeration, die steuert, ob das Suchen, ist oder nicht zwischen Groß\- und Kleinschreibung unterschieden.  
  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)\-Objekt zurück, das die Liste der Felder darstellt.  Gibt einen NULL\-Wert zurück, wenn keine Felder vorhanden sind.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK oder S\_FALSE zurück, wenn keine Felder vorhanden sind.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 `dwKindFilter`, `dwModifiersFilter`und `pszNameFilter`\-Parameter können kombiniert werden, z. B. um alle öffentlichen virtuellen Methoden auszuwählen, die „MyMethod“ benannt werden.  
  
## Siehe auch  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)