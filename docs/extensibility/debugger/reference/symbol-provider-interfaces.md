---
title: Symbol Anbieterschnittstellen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ecc2d37c85e20ce000dc7998e62afc4541614a83
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934704"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
Im folgenden sind die Symbol Behandeln von Schnittstellen für die [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Diskussion  
 Diese Schnittstellen werden zum Auswerten von Variablen in einer Aufrufliste im Unterbrechungsmodus verwendet. Sie sind nur für common Language Runtime Symbol-Anbieter (SP) implementiert.  
  
|Interface|Implementiert von|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Die Adresse eines Elements darstellt.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Stellt die Adresse eines Elements, das den Zugriff auf die Prozess-ID.|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Stellt ein Array Symbol oder Arraytyp dar.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Stellt eine Klasse Symbol oder ein Klassentyp dar.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Stellt einen COM+-Symbol-Anbieter mit Methoden, die spezifisch für verwalteten Code dar.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Stellt einen COM+-Symbol-Anbieter mit Methoden, die auf verwalteten Code beziehen, und erweitert die **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Stellt ein Symbol oder ein Typ, der ein Container für andere Symbole oder Typen ist.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Stellt ein benutzerdefiniertes Attribut, das auf ein Symbol zugeordnet werden kann.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Stellt eine Abfrage für die benutzerdefinierten Attribute für eine Methode oder einen Typ dar.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Bietet Zugriff auf benutzerdefinierte Attribute auf ein Symbol.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Die Basisschnittstelle für alle Typen, die zur Laufzeit bestimmt werden kann.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Stellt ein dynamisches Feld für eine [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Objekt.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Stellt einen Enumerationstyp dar.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Erweitert die Typen der verfügbaren Felder zur Unterstützung von Generika mit verwaltetem Code.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Die Basisklasse für alle Felder; Stellt eine Beschreibung eines Symbols oder einen Typ dar.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Stellt die Definition eines Felds für einen generischen Typ von verwaltetem Code dar.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Stellt eine Instanz eines Felds für einen generischen Typ von verwaltetem Code.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Stellt einen Parameter für einen generischen Typ von verwaltetem Code.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Stellt eine Methode dar.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Stellt einen Debug-Optionaler Modifizierer.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Stellt einen Zeiger.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Stellt einen primitiven Typ Enumeration-Wert aus einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Stellt eine Eigenschaft einer Klasse von verwaltetem Code, die Get oder gesetzt werden kann.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Stellt einen symbolanbieter, der Symbole und Typen bereitstellt.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Stellt einen symbolanbieter mit direktem Zugriff auf Metadaten und Core-Symbol-Schnittstellen dar.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Stellt die Möglichkeit, ein Feld erstellen, die einen Typ darstellt.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Erweitert die **IDebugTypeFieldBuilder** Arraytypen erstellen können.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Stellt eine Auflistung von [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekte.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Stellt eine Auflistung von [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) Objekte.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Stellt eine Auflistung von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekte.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)