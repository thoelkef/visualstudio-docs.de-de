---
title: "IDebugComPlusSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider-Schnittstelle"
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt einen Anbieter COM\+\-Symbol mit Methoden, die für den verwalteten Code vorgesehen sind.  
  
## Syntax  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## Hinweise für Implementierer  
 Obwohl es sich nicht um eine Trennung zwischen Schnittstellen, die einen Ausdrucksauswertung \(EE\) nützlich sind und denen gibt, die noch nicht über eine Debug\- Modul \(DE\) verwendet wird, sind die folgenden Methoden: interest wahrscheinlich nur developers DE AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols und UpdateSymbols.  
  
## Methoden  
 Zusätzlich zu den Methoden der [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Bestimmt, ob die Programmdebuginformationen Symbole für das angegebene Modul der angegebene Bezeichner der Anwendungsdomäne geladen werden.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Erstellt einen Typ aus dem angegebenen Typ.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Ordnet eine Position des Dokuments im angegebenen Modul auf ein Array von Adressen zu Debuggen.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Ruft Typinformationen über das angegebene Adresse Debuggen der angegebenen Array ab.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Ruft den Namen der angegebenen Assembly sein Modul und Anwendungsdomäne ab.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Ruft die Klassen mit dem angegebenen Attribut ab, die in der angegebenen Programmiersprache implementiert werden.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Ruft die Klassen mit dem angegebenen Attribut in einem angegebenen Modul ab.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Ruft den Einstiegspunkt der Anwendung ab.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Ruft die Adresse innerhalb einer angegebenen Funktion ab, die den Zeilenoffset darstellt.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Ruft das Lay\-out von lokalen Variablen für eine Gruppe von Methoden ab.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Gibt den Namen zurück, der dem angegebenen Scheinangegebenen das Metadatenobjekt zugeordnet ist.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Ruft die Programmdebuginformationen Symbole mit dem angegebenen übergeordneten Attribut für das angegebene Modul ab.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Ruft den durch nicht verwalteten Code ab Symbolreader verwendet werden soll.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Ruft den Typ des Symbols auf einen bestimmten Adresse Debuggen in Punkt ab oder legt diese fest.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Bestimmt, ob die Funktion an der angegebenen Adresse Debuggen deaktiviert ist.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Bestimmt, ob das Feature Debuggen an der angegebenen Adresse als veraltet betrachtet wird.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Bestimmt, ob die Codeausführung an der angegebenen Debugger adresse ausgeblendet ist.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Lädt die angegebenen Debuggen von Symbolen im Arbeitsspeicher.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Lädt die angegebenen Symbole Debuggen der Datenstrom.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Ersetzt Standardsymbole durch die Programmdebuginformationen die derzeit im angegebenen Stream.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Entlädt die Programmdebuginformationen Symbole für das angegebene Modul aus dem Arbeitsspeicher entladen.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aktualisiert die Programmdebuginformationen Symbole im Arbeitsspeicher mit denen der angegebene Stream.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll