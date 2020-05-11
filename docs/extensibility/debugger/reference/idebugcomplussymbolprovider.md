---
title: IDebugComPlusSymbolAnbieter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733478"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Stellt einen COM+-Symbolanbieter mit Methoden dar, die für verwalteten Code spezifisch sind.

## <a name="syntax"></a>Syntax

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Obwohl es keine Trennung zwischen Schnittstellen gibt, die für einen Ausdrucksevaluator (EE) nützlich sind, und solchen, die von einem Debugmodul (DE) verwendet werden sollen, interessieren die folgenden Methoden wahrscheinlich nur DE-Entwickler: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols und UpdateSymbols.

## <a name="methods"></a>Methoden
 Zusätzlich zu den Methoden auf der [IDebugSymbolProvider-Schnittstelle](../../../extensibility/debugger/reference/idebugsymbolprovider.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Bestimmt, ob die Debugsymbole für das angegebene Modul geladen werden, das den Anwendungsdomänenbezeichner erhält.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Erstellt einen Typ aus dem angegebenen primitiven Typ.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Ordnet eine Dokumentposition im angegebenen Modul einem Array von Debugadressen zu.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Ruft Typinformationen über das angegebene Array mit der Debugadresse ab.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Ruft den Namen der Assembly mit dem Modul und der Anwendungsdomäne ab.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Ruft die Klassen mit dem angegebenen Attribut ab, die in der angegebenen Programmiersprache implementiert sind.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Ruft die Klassen mit dem angegebenen Attribut in einem bestimmten Modul ab.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Ruft den Anwendungseinstiegspunkt ab.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Ruft die Adresse innerhalb einer Funktion ab, die den angegebenen Zeilenversatz darstellt.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Ruft das Layout lokaler Variablen für eine Reihe von Methoden ab.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Gibt den Namen zurück, der dem angegebenen Token zugeordnet ist, da sein Metadatenobjekt angegeben ist.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Ruft die Debugsymbole mit dem angegebenen übergeordneten Attribut für das angegebene Modul ab.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Ruft den Symbolleser ab, der von nicht verwaltetem Code verwendet werden soll.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Ruft einen Symboltyp mit der Debugadresse ab.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Bestimmt, ob die Funktion an der angegebenen Debugadresse gelöscht wird.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Bestimmt, ob die Funktion an der angegebenen Debugadresse als veraltet betrachtet wird.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Bestimmt, ob der Code an der angegebenen Debuggeradresse ausgeblendet ist.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Lädt die angegebenen Debugsymbole in den Arbeitsspeicher.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Lädt Debugsymbole, die dem Datenstrom gegeben sind.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Ersetzt die aktuellen Debugsymbole durch die Symbole im angegebenen Datenstrom.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Entlädt die Debugsymbole für das angegebene Modul aus dem Speicher.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualisiert die Debugsymbole im Speicher mit denen des angegebenen Datenstroms.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
