---
title: "SymTagEnum | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SymTagEnum-Enumeration"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt den Typ des Symbols.  
  
## Syntax  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## Elements  
 `SymTagNull`  
 Gibt an, dass das Symbol kein Typ.  
  
 `SymTagExe`  
 Gibt an, dass das Symbol einer EXE\-Datei.  Es gibt nur einen `SymTagExe` Symbol pro Symbol speichern.  Es dient als im globalen Gültigkeitsbereich und verfügt nicht über eine übergeordnete lexikalische.  
  
 `SymTagCompiland`  
 Die Kompiliereinheit Kennnummer für jede Komponente Kompiliereinheit des Symbolspeichers bereit.  Für systemeigene Anwendungen `SymTagCompiland` Symbole entsprechen den Objektdateien verknüpft, in das Bild.  Für einige Arten von Bildern von Microsoft Intermediate Language \(MSIL\) gibt es eine Kompiliereinheit pro Klasse.  
  
 `SymTagCompilandDetails`  
 Gibt an, dass das Symbol der Kompiliereinheit erweiterten Attribute enthält.  Diese Eigenschaften erfordern Kompiliereinheit Symbole laden.  
  
 `SymTagCompilandEnv`  
 Gibt an, dass das Symbol einer Umgebungszeichenfolge für der Kompiliereinheit definiert ist.  
  
 `SymTagFunction`  
 Gibt an, dass das Symbol einer Funktion ist.  
  
 `SymTagBlock`  
 Gibt an, dass das Symbol eines geschachtelten Blockes.  
  
 `SymTagData`  
 Gibt an, dass das Symbol Daten.  
  
 `SymTagAnnotation`  
 Gibt an, dass das Symbol für eine Code\-Anmerkung.  Kinder dieses Symbols sind Konstante Datenzeichenfolgen \(`SymTagData`, `LocIsConstant`, `DataIsConstant`\).  Die meisten Clients ignorieren dieses Symbol.  
  
 `SymTagLabel`  
 Gibt an, dass das Symbol einer Bezeichnung.  
  
 `SymTagPublicSymbol`  
 Gibt an, dass das Symbol einer öffentlichen Symbol.  Für systemeigene Anwendungen ist dieses Symbol die externe COFF\-Symbol das Bild verknüpfen aufgetreten.  
  
 `SymTagUDT`  
 Gibt an, dass das Symbol eines benutzerdefinierten Typs \(Struktur, Union oder Klasse\).  
  
 `SymTagEnum`  
 Gibt an, dass das Symbol einer Enumeration ist.  
  
 `SymTagFunctionType`  
 Gibt an, dass das Symbol einen Signaturtyp Funktion.  
  
 `SymTagPointerType`  
 Gibt an, dass das Symbol ein Zeigertyp ist.  
  
 `SymTagArrayType`  
 Gibt an, dass das Symbol eines Arraytyps.  
  
 `SymTagBaseType`  
 Gibt an, dass das Symbol einen Basistyp.  
  
 `SymTagTypedef`  
 Gibt an, dass das Symbol ist ein `typedef`, d. h. einen Alias für einen anderen Typ.  
  
 `SymTagBaseClass`  
 Gibt an, dass das Symbol einer Basisklasse eines benutzerdefinierten Typs.  
  
 `SymTagFriend`  
 Gibt an, dass das Symbol ein Freund eines benutzerdefinierten Typs.  
  
 `SymTagFunctionArgType`  
 Gibt an, dass das Symbol ein Funktionsargument ist.  
  
 `SymTagFuncDebugStart`  
 Gibt an, dass das Symbol die Endposition des Prolog\-Code der Funktion.  
  
 `SymTagFuncDebugEnd`  
 Gibt an, dass das Symbol die Anfangsposition des Epilog der Funktionscode.  
  
 `SymTagUsingNamespace`  
 Gibt an, dass das Symbol einen Namespacenamen im aktuellen Gültigkeitsbereich aktiv ist.  
  
 `SymTagVTableShape`  
 Gibt an, dass das Symbol eine virtuelle Tabellenbeschreibung.  
  
 `SymTagVTable`  
 Gibt an, dass das Symbol eine virtuelle Tabelle Zeiger ist.  
  
 `SymTagCustom`  
 Gibt an, dass das Symbol ein benutzerdefiniertes Symbol ist und nicht von stark interpretiert  
  
 `SymTagThunk`  
 Gibt an, dass das Symbol ein Thunk für den Datenaustausch zwischen 16 und 32\-Bit\-Code verwendet.  
  
 `SymTagCustomType`  
 Gibt an, dass das Symbol benutzerdefinierte Compiler Symbol.  
  
 `SymTagManagedType`  
 Gibt an, dass das Symbol in den Metadaten.  
  
 `SymTagDimension`  
 Gibt an, dass das Symbol eines mehrdimensionalen Arrays von FORTRAN.  
  
 `SymTagCallSite`  
 Gibt an, dass das Symbol die Aufrufsite darstellt.  
  
 `SymTagInlineSite`  
 Gibt an, dass das Symbol die Inline\-Website darstellt.  
  
 `SymTagBaseInterface`  
 Gibt an, dass das Symbol einer Basisschnittstelle.  
  
 `SymTagVectorType`  
 Gibt an, dass das Symbol ein Vektor ist.  
  
 `SymTagMatrixType`  
 Gibt an, dass das Symbol eines Matrix\-Typs.  
  
 `SymTagHLSLType`  
 Gibt an, dass das Symbol ein High Level Shader Language\-Typ.  
  
## Hinweise  
 Alle Symbole in eine Datei haben eine identifizierende Tag, der den Symboltyp angibt.  
  
 Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) Methode.  
  
 Die Werte in dieser Enumeration werden für die folgenden Methoden zum Einschränken der Suche auf einen bestimmten Symboltyp übergeben:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Anforderungen  
 Header: dia2.idl  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)