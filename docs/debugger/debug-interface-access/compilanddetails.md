---
title: "CompilandDetails | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CompilandDetails-Symbol"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Informationen Kompiliereinheits werden zwischen Symbole mit einem `SymTagCompiland`\-Tag \(sowohl Basisfunktionalität\) und einen Tag `SymTagCompilandDetails` aufgeteilt \(hohes Detail\).  `SymTagCompilandDetails` erfordert zusätzliche Symbole laden.  Allerdings stellt er eine Füllzustand von Informationen über die Kompiliereinheit, die keinem `SymTagCompiland` Symbol verfügbar ist.  
  
## Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften angegeben, die auf das Symbol für diesen Typ gültig sind.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Hinter buildnummer des Compilers verfügbar.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Hinter hauptversionsnummer des Compilers verfügbar.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Hinter nebenversionsnummer des Compilers verfügbar.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Name des Compilers, der diese Kompiliereinheit hat \(DIA nur SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|Bearbeiten und Fortfahren`TRUE` ,  wenn bei der Kompilierung aktiviert wurden.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Front\-End Buildnummer des Compilers verfügbar.|  
|[IDiaSymbol::get\_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Front\-End Hauptversionsnummer des Compilers verfügbar.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Front\-End Nebenversionsnummer des Compilers verfügbar.|  
|[IDiaSymbol::get\_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` ,  wenn diese Kompiliereinheit Debuginformationen \(DIA nur SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` ,  wenn diese Kompiliereinheit verwalteten Code enthält \(nur DIA SDK in v8.0 oder höher\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` ,  wenn die Kompiliereinheit mit dem [\/GS \(Puffer\-Sicherheitsüberprüfung\)](/visual-cpp/build/reference/gs-buffer-security-check) Compilerschalter kompiliert wurde \(DIA nur SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` ,  wenn Kompiliereinheit vom allgemeinen Code der CIL \(Intermediate Language\) in systemeigenen Code konvertiert wurde.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` ,  wenn benutzerdefinierte Typen \(UDT\) zu einer bestimmten Speicher Grenze ausgerichtet wurden \(DIA nur SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` ,  wenn Kompiliereinheit mit dem [\/hotpatch \(Erstellen eines Hotpatch\-fähigen Abbildes\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) Compilerschalter kompiliert wurde \(DIA nur SDK in v8.0 oder höher\).|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` ,  wenn Kompiliereinheit mit dem [\/LTCG \(Code zur Verknüpfungszeit generieren\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) Compilerschalter kompiliert wurde \(DIA nur SDK in V8.0 oder höher\).|  
|[IDiaSymbol::get\_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE, wenn ein Modul Kompiliereinheit Microsoft Intermediate Language \(MSIL\) ist nur in v8.0 \(DIA SDK oder höher\).|  
|[IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Quellcode Entwicklungssprache.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die Kompiliereinheit.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des lexikalischen Elementen Symbols.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plattform, auf der die Kompiliereinheit kompiliert wurde \(einer der [CV\_CPU\_TYPE\_e Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md)\-Werte\).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompilandDetails` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Hinweise  
 Compiler stammen häufig in eine Form, die als in zwei Durchläufen Compiler bekannt ist. Compiler in einigen Versionen wird jede Durchlauf durch ein separates Programm behandelt.  Diese werden als Front\-End und Sprachcompiler Hinter Eigenschaft daher die Symbol, Hinter\- und Eigenschaften für die Versionsnummern Front\-End.  
  
## Siehe auch  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)