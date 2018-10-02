---
title: IDebugComPlusSymbolProvider | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d10dc52dfdf628caed5439a969ba5ce3d2377ceb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523780"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugComPlusSymbolProvider](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcomplussymbolprovider).  
  
Stellt einen COM+-Symbol-Anbieter mit Methoden, die spezifisch für verwalteten Code dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Obwohl es keine Trennung zwischen Schnittstellen, die für eine ausdrucksauswertung (EE) nützlich sind, und diejenigen, die von einer Debug-Engine (DE) verwendet werden sollen ist, die folgenden Methoden wahrscheinlich nur DE Entwickler interessieren: AreSymbolsLoaded, GetAddressesInModuleFromPosition GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols und UpdateSymbols.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den Methoden für die [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Bestimmt, ob die Debugsymbole für das angegebene Modul mit dem angegebenen Bezeichner der Anwendungsdomäne geladen wurden.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Erstellt einen vom angegebenen primitiven Typs.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Ordnet eine Dokumentposition im angegebenen Modul in ein Array von Debug-Adressen an.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Ruft die Typinformationen über das angegebene Array, wenn die debugadresse.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Ruft den Namen der Assembly bei Angabe der Modul- und Domäne ab.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Ruft ab, die Klassen mit dem angegebenen Attribut an, die in der angegebenen Programmiersprache implementiert werden.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Ruft die Klassen mit dem angegebenen Attribut in einem bestimmten Modul ab.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Ruft den Einstiegspunkt der Anwendung ab.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Ruft die Adresse in einer Funktion, die den Offset der angegebenen Zeile darstellt.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Ruft das Layout von lokalen Variablen für einen Satz von Methoden ab.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Gibt den Namen der angegebenen Token, die die Metadaten-Objekt zugeordnet.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Ruft die Debugsymbole, mit dem angegebenen übergeordneten Attribut für das angegebene Modul ab.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Ruft ab den Symbolreader von nicht verwaltetem Code verwendet werden.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Ruft ab, um ein Symboltyp, wenn die debugadresse.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Bestimmt, ob die Funktion an der angegebenen Debug-Adresse gelöscht wird.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Bestimmt, ob die Funktion an der angegebenen Debug-Adresse als veraltet angesehen wird.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Bestimmt, ob der Code unter der Adresse angegebenen Debugger ausgeblendet ist.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Lädt die angegebenen Debug-Symbole im Arbeitsspeicher.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Lädt Debugsymbole ab, der den Datenstrom angegeben ist.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Ersetzt die aktuelle Debugsymbole mit den Angaben in den angegebenen Datenstrom.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Entlädt die Debugsymbolen für das angegebene Modul aus dem Arbeitsspeicher.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualisiert die Debugsymbole im Arbeitsspeicher mit den angegebenen Datenstream.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

