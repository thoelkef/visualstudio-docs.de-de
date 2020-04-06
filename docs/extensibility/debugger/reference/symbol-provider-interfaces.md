---
title: Symbolanbieter-Schnittstellen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7929ba36c76f0db1cabab087afe3590de509efff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715849"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
Im Folgenden sind die SymbolHandling [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]Interfaces für die .

## <a name="discussion"></a>Diskussion
 Diese Schnittstellen werden verwendet, um Variablen in einer Aufrufliste während des Unterbrechungsmodus auszuwerten. Sie werden nur für Common Language Runtime Symbol Provider (SP) implementiert.

|Schnittstelle|Implementiert von|BESCHREIBUNG|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Stellt die Adresse eines Elements dar.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Stellt die Adresse eines Elements dar und bietet Zugriff auf die Prozess-ID.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Stellt ein Arraysymbol oder einen Arraytyp dar.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Stellt ein Klassensymbol oder einen Klassentyp dar.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Stellt einen COM+-Symbolanbieter mit Methoden dar, die für verwalteten Code spezifisch sind.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Stellt einen COM+-Symbolanbieter mit Methoden dar, die für verwalteten Code spezifisch sind, und erweitert den **IDebugComPlusSymbolProvider**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Stellt ein Symbol oder einen Typ dar, der ein Container für andere Symbole oder Typen ist.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Stellt ein benutzerdefiniertes Attribut dar, das einem Symbol zugeordnet werden kann.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Stellt eine Abfrage für benutzerdefinierte Attribute für eine Methode oder einen Typ dar.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Bietet Zugriff auf benutzerdefinierte Attribute für ein Symbol.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Die Basisschnittstelle für jeden Typ, der zur Laufzeit bestimmt werden kann.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Stellt ein dynamisches Feld für ein [IDebugBinder-Objekt](../../../extensibility/debugger/reference/idebugbinder.md) dar.|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Stellt einen Enumerationstyp dar.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|Erweitert die Typen der verfügbaren Felder, um generische Genegene für verwalteten Code zu unterstützen.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Die Basisklasse für alle Felder; stellt eine Beschreibung eines Symbols oder Typs dar.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Stellt die Definition eines Felds für einen generischen Codetyp für verwalteten Code dar.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Stellt eine Instanz eines Felds für einen generischen Codetyp für verwalteten Code dar.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Stellt einen Parameter für einen generischen Codetyp für verwalteten Code dar.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Stellt eine Methode dar.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Stellt einen optionalen Debugmodifizierer dar.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Stellt einen Zeiger dar.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Stellt einen primitiven Typenumerationswert aus einer [IDebugField-Schnittstelle](../../../extensibility/debugger/reference/idebugfield.md) dar.|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Stellt eine Eigenschaft einer verwalteten Codeklasse dar, die ab- oder festgelegt werden kann.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Stellt einen Symbolanbieter dar, der Symbole und Typen bereitstellt.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Stellt einen Symbolanbieter mit direktem Zugriff auf Metadaten und Kernsymbolschnittstellen dar.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Stellt die Möglichkeit dar, ein Feld zu erstellen, das einen Typ darstellt.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Erweitert den **IDebugTypeFieldBuilder,** um Arraytypen erstellen zu können.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Stellt eine Auflistung von [IDebugAddress-Objekten](../../../extensibility/debugger/reference/idebugaddress.md) dar.|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Stellt eine Auflistung von [IDebugCustomAttribute-Objekten](../../../extensibility/debugger/reference/idebugcustomattribute.md) dar.|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Stellt eine Auflistung von [IDebugField-Objekten](../../../extensibility/debugger/reference/idebugfield.md) dar.|

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
