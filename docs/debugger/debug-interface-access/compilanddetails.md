---
title: Compilanddetails | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b72a5ae53c336877c68cc9b164cf787017dacbe2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745419"
---
# <a name="compilanddetails"></a>CompilandDetails
Compiland-Informationen werden zwischen Symbolen mit einem `SymTagCompiland` Tag (niedriges Detail) und einem `SymTagCompilandDetails` Tag (sehr detailliert) aufgeteilt. `SymTagCompilandDetails` das Laden zusätzlicher Symbole erfordert. Sie bietet jedoch eine Fülle von Informationen über die Kompilierungen, die nicht mit einem `SymTagCompiland` Symbol verfügbar ist.

## <a name="properties"></a>Eigenschaften
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die für diesen Symboltyp gültig sind.

|property|Datentyp|Beschreibung|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Die Back-End-Buildnummer des Compilers.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Die Hauptversionsnummer für das Back-End des Compilers.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Die Back-End-neben Versionsnummer des Compilers.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Der Name des Compilers, der diese Kompilierungen erstellt hat (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE`, wenn Bearbeiten und fortfahren bei der Kompilierung aktiviert wurde.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Die Front-End-Buildnummer des Compilers.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Front-End-Hauptversionsnummer des Compilers.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Front-End-neben Versionsnummer des Compilers.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE`, wenn diese Kompilierung über Debuginformationen verfügt (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE`, wenn dieser kompiliert und verwalteten Code enthält (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`, wenn die Kompilierung mit dem Compilerschalter [/GS (Buffer Security Check)](/cpp/build/reference/gs-buffer-security-check) kompiliert wurde (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE`, wenn kompiliert und aus Common Intermediate Language (CIL)-Code in systemeigenen Code konvertiert wurden.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE`, wenn benutzerdefinierte Typen (User-Defined Types, UDT) an einer bestimmten Speichergrenze ausgerichtet wurden (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE`, wenn die Kompilierung mit dem Compilerschalter [/hotpatch (Create Hotpatchable Image)](/cpp/build/reference/hotpatch-create-hotpatchable-image) kompiliert wurde (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE`, wenn die Kompilierung mit dem [Compilerschalter/LTCG (Link-Time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation) kompiliert wurde (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE, wenn kompiliert und ein MSIL-Modul (Microsoft Intermediate Language) ist (nur in Dia SDK v 8.0 oder höher).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Quellcodesprache.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für das kompiand.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des übergeordneten lexikalischen Symbols.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plattform, auf der kompiliert wurde (einer der [CV_CPU_TYPE_e-Enumerationswerte](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompilandDetails` zurück (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte).|

## <a name="remarks"></a>Hinweise
 Compiler sind häufig in einer Form enthalten, die als zwei-Pass-Compiler bezeichnet wird. in einigen Compilerversionen wird jeder Durchlauf von einem separaten Programm behandelt. Diese werden als Front-End-bzw. Back-End-Compiler bezeichnet und somit als Symbol Eigenschaften für Back-End-und Front-End-Versionsnummern bezeichnet.

## <a name="see-also"></a>Siehe auch
- [Compiland](../../debugger/debug-interface-access/compiland.md)
- [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)