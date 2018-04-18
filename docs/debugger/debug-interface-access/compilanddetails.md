---
title: CompilandDetails | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16f9239028cada1108092af3bc5a511964f89c6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="compilanddetails"></a>CompilandDetails
Symbole mit Kompiliereinheit Informationen aufgeteilt ist ein `SymTagCompiland` Tag (wenig Details) und ein `SymTagCompilandDetails` Tag (hohe Detail). `SymTagCompilandDetails` erfordert zusätzliche Symbole laden. Sie bietet jedoch eine Fülle von Informationen zu den Kompiliereinheit, die nicht mit verfügbar ist ein `SymTagCompiland` Symbol.  
  
## <a name="properties"></a>Eigenschaften  
 Die folgende Tabelle zeigt die Eigenschaften, die für diesen Symboltyp gültig sind.  
  
|Eigenschaft|Datentyp|Beschreibung|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Back-End-Build-Nummer des Compilers.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Back-End-Hauptversionsnummer des Compilers.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Back-End-Nebenversionsnummer des Compilers.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Der Name des Compilers, die diese Kompiliereinheit (nur in DIA-SDK 8.0 oder höher) erstellt.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Wenn bei der Kompilierung bearbeiten und Fortfahren aktiviert wurden.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Front-End-Build-Nummer des Compilers.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Front-End-Hauptversionsnummer des Compilers.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Front-End-Nebenversionsnummer des Compilers.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Wenn diese Kompiliereinheit Debuginformationen (nur in DIA-SDK 8.0 oder höher) verfügt.|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Wenn diese Kompiliereinheit verwalteten Code (nur in DIA-SDK 8.0 oder höher) enthält.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Wenn der Kompiliereinheit kompiliert wurde, mit der [/GS (Puffer-Sicherheitsüberprüfung)](/cpp/build/reference/gs-buffer-security-check) Compilerschalter (nur in DIA-SDK 8.0 oder höher).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Wenn Kompiliereinheit aus Common Intermediate Language (CIL) Code in systemeigenen Code konvertiert wurde.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Benutzerdefinierte Typen (UDT) ausgerichtet wurden einige Arbeitsspeicher-Grenze (nur in DIA-SDK 8.0 oder höher) angegeben.|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Wenn Kompiliereinheit kompiliert wurde, mit der [/hotpatch (Erstellen eines Hotpatch-fähigen Abbildes)](/cpp/build/reference/hotpatch-create-hotpatchable-image) Compilerschalter (nur in DIA-SDK 8.0 oder höher).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Wenn Kompiliereinheit kompiliert wurde, mit der [/LTCG (Link-Time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation) Compilerschalter (nur in DIA-SDK 8.0 oder höher).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|"True", wenn Kompiliereinheit ein Microsoft Intermediate Language (MSIL)-Modul (nur in DIA-SDK 8.0 oder höher) ist.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Quellcodesprache.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die Kompiliereinheit.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Die ID des übergeordneten lexikalischen Symbols.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plattform, auf denen der Kompiliereinheit kompiliert wurde (eines der [CV_CPU_TYPE_e-Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md) Werte).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompilandDetails` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|  
  
## <a name="remarks"></a>Hinweise  
 Compiler werden oft in einem Formular als ein Compiler zwei Durchläufen bezeichnet; In einigen Versionen werden von Compilern wird jedem Durchlauf durch ein separates Programm behandelt. Diese werden als Front-End- und Back-End-Compiler, daher die Symboleigenschaften für Front-End- und Back-End-Versionsnummern bezeichnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)