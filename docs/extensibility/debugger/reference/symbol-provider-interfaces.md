---
title: Symbol Anbieterschnittstellen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 798334058a89199e1e40e023e0b7f46d13c36997
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131300"
---
# <a name="symbol-provider-interfaces"></a>Symbol-Anbieter-Schnittstellen
Im folgenden sind die Behandlung von Schnittstellen mit Symbol für die [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Diskussion  
 Diese Schnittstellen werden zum Auswerten von Variablen in einer Aufrufliste im Unterbrechungsmodus. Sie sind nur für common Language Runtime Symbol-Anbieter (SP) implementiert.  
  
|Interface|Implementiert durch|Beschreibung|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Stellt die Adresse eines Elements dar.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Stellt die Adresse eines Elements, das Bereitstellen des Zugriffs auf die Prozess-ID|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Stellt eine Array-Symbol oder Arraytyp.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Stellt eine Klasse Symbol oder Klassentyp dar.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Stellt einen COM+-Symbol-Anbieter mit Methoden, die an verwalteten Code spezifisch sind.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Stellt einen COM+-Symbol-Anbieter mit Methoden, die auf verwalteten Code beziehen und erweitert die **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Stellt ein Symbol oder ein Typ, der einen Container für andere Symbole oder Typen handelt.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Stellt ein benutzerdefiniertes Attribut, das ein Symbol zugeordnet werden kann.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Stellt eine Abfrage für benutzerdefinierte Attribute auf eine Methode oder generischen Typ dar.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Bietet Zugriff auf die benutzerdefinierten Attribute auf ein Symbol an.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Die Basisschnittstelle für jeden Typ, der zur Laufzeit bestimmt werden kann.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Stellt ein dynamisches Feld für eine [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Objekt.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Stellt einen Enumerationstyp.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Erweitert die Typen der verfügbaren Felder zur Unterstützung von verwaltetem Code Generika.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Die Basisklasse für alle Felder; Stellt eine Beschreibung eines Symbols oder einen Typ dar.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Stellt die Definition eines Felds für einen generischen Typ für verwalteten Code dar.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Stellt eine Instanz eines Felds für einen generischen Typ mit verwaltetem Code.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Stellt einen Parameter für einen generischen Typ für verwalteten Code dar.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Stellt eine Methode dar.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Stellt einen Debug-Optionaler Modifizierer.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Stellt einen Zeiger.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Stellt einen primitiven Typ Enumerationswert aus einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Stellt eine Eigenschaft einer verwalteten Code-Klasse, die Get oder gesetzt werden kann.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Stellt einen Symbol-Anbieter, der Symbole und Typen bereitstellt.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Stellt einen Symbol-Anbieter mit direktem Zugriff auf Metadaten und Core Symbol Schnittstellen dar.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Stellt die Möglichkeit zum Erstellen eines Felds, das einen Typ darstellt.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Erweitert die **IDebugTypeFieldBuilder** Arraytypen erstellen können.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Stellt eine Auflistung von [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekte.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Stellt eine Auflistung von [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) Objekte.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Stellt eine Auflistung von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekte.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)