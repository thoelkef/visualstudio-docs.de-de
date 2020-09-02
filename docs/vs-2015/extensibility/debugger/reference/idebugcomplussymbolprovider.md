---
title: Idebugcomplussymbolprovider | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b70701aa9c4b339749554601e2a565c17697c6a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186514"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Stellt einen com+-Symbol Anbieter mit Methoden dar, die für verwalteten Code spezifisch sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Es gibt zwar keine Trennung Zwischenschnitt stellen, die für eine Ausdrucks Auswertung (EE) nützlich sind, und diejenigen, die von einer Debug-Engine (de) verwendet werden sollen. die folgenden Methoden interessieren sich wahrscheinlich nur für Entwickler: aresymbolsloaded, getaddressesinmodulefromposition, getentrypoint, getfunctionlineoffset, getlocalvariablelayout, isfunctionstale, loadsymbols, loadsymbolsfromstream, replacesymbols, unloadsymbols und updatesymbols.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Bestimmt, ob die Debugsymbole für das angegebene Modul geladen werden, wenn der Anwendungs Domänen Bezeichner angegeben ist.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Erstellt einen Typ aus dem angegebenen primitiven Typ.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Ordnet eine Dokument Position im angegebenen Modul einem Array von debugadressen zu.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Ruft Typinformationen über das angegebene Array ab, wenn die zugehörige debugadresse angegeben ist.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Ruft den Namen der Assembly ab, bei der das Modul und die Anwendungsdomäne angegeben sind.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Ruft die Klassen mit dem angegebenen Attribut ab, das in der angegebenen Programmiersprache implementiert ist.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Ruft die Klassen mit dem angegebenen Attribut in einem angegebenen Modul ab.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Ruft den Einstiegspunkt der Anwendung ab.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Ruft die Adresse innerhalb einer Funktion ab, die den angegebenen Zeilen Offset darstellt.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Ruft das Layout von lokalen Variablen für einen Satz von Methoden ab.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Gibt den Namen zurück, der dem angegebenen Token bei Angabe seines Metadatenobjekts zugeordnet ist.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Ruft die Debugsymbole mit dem angegebenen übergeordneten Attribut für das angegebene Modul ab.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Ruft den Symbol Reader ab, der von nicht verwaltetem Code verwendet werden soll.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Ruft bei angegebener debugadresse einen Symboltyp ab.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Bestimmt, ob die Funktion an der angegebenen debugadresse gelöscht wird.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Bestimmt, ob die Funktion an der angegebenen debugadresse als veraltet eingestuft wird.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Bestimmt, ob der Code an der angegebenen debuggeradresse ausgeblendet ist.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Lädt die angegebenen Debugsymbole in den Arbeitsspeicher.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Lädt Debugsymbole, wenn der Datenstrom angegeben wird.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Ersetzt die aktuellen Debugsymbole durch die im angegebenen Datenstream.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Entlädt die Debugsymbole für das angegebene Modul aus dem Arbeitsspeicher.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualisiert die Debugsymbole im Speicher mit den angegebenen Datenströmen.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
