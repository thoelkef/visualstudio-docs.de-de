---
title: "Symbol-Provider-Schnittstellen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbol-Handler-Schnittstellen"
  - "Symbol für Ereignishandler, Schnittstellen"
  - "Symbol für Ereignishandler Auswerten von Variablen"
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Symbol-Provider-Schnittstellen
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Im Folgenden werden die Symbol\-Behandlungs\-Schnittstellen für [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## Erörterung  
 Diese Schnittstellen werden verwendet, um Variablen in einer Aufrufliste, die während des Unterbrechungsmodus auszuwerten.  Sie werden nur für Common Language Runtime\-Symbol Textanbieter \(SP\) implementiert.  
  
|Schnittstelle|Vorbei implementiert|Beschreibung|  
|-------------------|--------------------------|------------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Stellt die Adresse eines Elements dar.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Stellt die Adresse eines Elements dar und ermöglicht den Zugriff auf Prozessnummer|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Stellt ein Array oder einen Arraytyp Symbol dar.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Stellt ein Symbol für Klassen oder \- Klassentyp dar.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Stellt einen Anbieter COM\+\-Symbol mit Methoden, die für den verwalteten Code vorgesehen sind.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Stellt einen Anbieter COM\+\-Symbol mit Methoden, die für den verwalteten Code beziehen und erweitert das **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Stellt ein Symbol oder einen Typ dar, die ein Container für andere Symbole oder Typen handelt.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Stellt ein benutzerdefiniertes Attribut dar, das auf ein Symbol angefügt werden kann.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Stellt eine Abfrage für benutzerdefinierte Attribute auf eine Methode oder einen Typ dar.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Bietet Zugriff auf benutzerdefinierte Attribute auf ein Symbol.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Die Basisschnittstelle für jeden Typ, der zur Laufzeit bestimmt werden kann.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Stellt ein dynamisches Feld für ein [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)\-Objekt dar.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Stellt einen Enumerationstyp dar.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Erweitert die Typen der verfügbaren Feldern, um einen verwalteten Code generika zu unterstützen.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Die Basisklasse für alle Felder. stellt eine Beschreibung eines Symbols oder des Typs dar.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Stellt die Definition eines Felds für einen verwalteten Code generischen Typ dar.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Stellt eine Instanz eines Felds für einen verwalteten Code generischen Typ dar.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Stellt einen Parameter für einen generischen Typ von verwaltetem Code dar.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Stellt eine Methode dar.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Stellt einen Debugbuild optionaler Modifizierer dar.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Stellt einen Zeiger dar.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Stellt einen Typ enumerationswert aus einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle dar.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Stellt eine Eigenschaft einer verwalteten Codeklasse dar, die abgerufen oder festgelegt werden kann.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Stellt ein Symbol für, der Symbole und Typen bereitstellt.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Stellt einen Anbieter Symbol mit direkten Zugriff auf die Metadaten und zu den wichtigsten Schnittstellen Symbol.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Bietet die Möglichkeit, ein Feld zu erstellen, das einen Typ darstellt.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Erweitert das **IDebugTypeFieldBuilder,** um in der Lage zu sein, Arraytypen zu erstellen.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Stellt eine Auflistung von [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekten dar.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Stellt eine Auflistung von [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)\-Objekten dar.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Stellt eine Auflistung von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekten dar.|  
  
## Siehe auch  
 [API\-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)