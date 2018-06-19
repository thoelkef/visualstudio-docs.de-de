---
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1eab7e30715032500719ee371011a600d2e9552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109739"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Stellt einen COM+-Symbol-Anbieter mit Methoden, die an verwalteten Code spezifisch sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Es gibt zwar keine Trennung zwischen Schnittstellen, die eine ausdrucksauswertung (EE) sind und solchen, die von einem Debugging-Modul (DE) verwendet werden sollen, die folgenden Methoden wahrscheinlich DE Entwickler nur interessieren: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols und UpdateSymbols.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) diese Schnittstelle implementiert, die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Bestimmt, ob es sich bei die Debugsymbolen für das angegebene Modul mit dem angegebenen Bezeichner der Anwendungsdomäne geladen werden.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Erstellt einen Typ aus der angegebenen primitiven Typs.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Ordnet eine Dokumentposition im angegebenen Modul in ein Array der Debug-Adressen an.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Ruft die Typinformationen über das angegebene Array, wenn seine Adresse Debuggen.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Ruft den Namen der Assembly bei Angabe seiner Domäne Modul- und Anwendungsdomänennamen ab.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Ruft die Klassen mit dem angegebenen Attribut an, die in der angegebenen Programmiersprache implementiert werden.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Ruft die Klassen mit dem angegebenen Attribut in einem bestimmten Modul ab.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Ruft den Einstiegspunkt der Anwendung ab.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Ruft die Adresse innerhalb einer Funktion, die den Offset für die jeweilige Zeile darstellt.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Ruft das Layout der lokalen Variablen für einen Satz von Methoden ab.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Gibt den Namen, die dem angegebenen Token erhält ihr Metadatenobjekt zugeordnet.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Ruft den Debugsymbolen mit dem angegebenen übergeordneten Attribut für das angegebene Modul ab.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Ruft ab die Symbolreaders von nicht verwaltetem Code verwendet werden.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Ruft ab, wenn seine Adresse Debug-Symboltyp.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Bestimmt, ob die Funktion bei der die angegebene Debug-Adresse gelöscht wird.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Bestimmt, ob die Funktion bei der die angegebene Debug-Adresse als veraltet angesehen wird.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Bestimmt, ob der Code bei der Adresse angegebenen Debugger ausgeblendet ist.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Lädt die angegebene Debug-Symbole im Arbeitsspeicher.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Lädt Symbole erhält den Datenstrom für das Debuggen.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Ersetzt die aktuellen Debugsymbolen zu denjenigen in dem angegebenen Datenstream.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Wird die Debugsymbolen für das angegebene Modul aus dem Arbeitsspeicher entladen.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualisiert den Debugsymbolen im Arbeitsspeicher mit den angegebenen Datenstream.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll