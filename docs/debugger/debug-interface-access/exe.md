---
title: "Exe | Microsoft Docs"
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
  - "DLL-Datei"
  - "EXE-Symbol"
  - "EXE-Dateien"
  - "Ausführbare Dateien, EXE-Symbol"
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Exe ist das einzige Symbol entweder ohne ein lexikalisches oder Klassen übergeordnetes Element, da es den globalen Bereich der EXE\- oder DLL\-Datei darstellt.  Es gibt nur ein Symbol mit dem `SymTagExe` Datei pro Tag.  Die [IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)\-Methode gibt das Symbol zurück.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften angegeben, die auf das Symbol für diesen Typ gültig sind.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Alter dieser ausführbaren Datei.|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` dieser ausführbaren Datei.|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` ,  wenn die Symboldatei, die dieser ausführbaren Datei zugeordnet ist \(C enthält nur DIA SDK in v8.0 oder höher\).|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` ,  wenn privaten Symbole der Symboldatei entfernt wurden, die dieser ausführbaren Datei zugeordnet ist \(nur DIA SDK in v8.0 oder höher\).|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Ziel\-CPU Wert, der angibt [CV\_CPU\_TYPE\_e Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md) \(einer der Werte\).|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Name der EXE\-Datei.|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Die Signatur der ausführbaren Datei.|  
|[IDiaSymbol::get\_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Vollständiger Pfad der .exe\-das .pdb oder die DBG\-Datei Datei.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagExe` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Siehe auch  
 [IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)