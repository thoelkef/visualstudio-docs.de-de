---
title: Compilanddetails | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 34349bf096d8bb98ae4b3de7c7a922b8d28bc4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703000"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Compiland-Informationen werden zwischen Symbolen mit einem `SymTagCompiland` Tag (niedriges Detail) und einem `SymTagCompilandDetails` Tag (hoher Detail) aufgeteilt. `SymTagCompilandDetails` erfordert das Laden zusätzlicher Symbole. Sie bietet jedoch eine Fülle von Informationen über die Kompilierungen, die nicht mit einem Symbol verfügbar ist `SymTagCompiland` .  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die für diesen Symboltyp gültig sind.  
  
|Eigenschaft|Datentyp|BESCHREIBUNG|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Die Back-End-Buildnummer des Compilers.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Die Hauptversionsnummer für das Back-End des Compilers.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Die Back-End-neben Versionsnummer des Compilers.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Der Name des Compilers, der diese Kompilierungen erstellt hat (nur in Dia SDK v 8.0 oder höher).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` , wenn Bearbeiten und fortfahren bei der Kompilierung aktiviert wurde.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Die Front-End-Buildnummer des Compilers.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Front-End-Hauptversionsnummer des Compilers.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Front-End-neben Versionsnummer des Compilers.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Wenn kompiliert wird, werden Debuginformationen (nur in Dia SDK v 8.0 oder höher) erstellt.|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Wenn kompiliert wird, enthält Sie verwalteten Code (nur in Dia SDK v 8.0 oder höher).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` , wenn die Kompilierung mit dem Compilerschalter [/GS (Buffer Security Check)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) kompiliert wurde (nur in Dia SDK v 8.0 oder höher).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` , wenn kompiliert und aus Common Intermediate Language (CIL)-Code in nativen Code konvertiert wurden.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` , wenn benutzerdefinierte Typen (User-Defined Types, UDT) an einer bestimmten Speichergrenze ausgerichtet wurden (nur in Dia SDK v 8.0 oder höher).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` , wenn kompiliert und mit dem Compilerschalter [/hotpatch (Create Hotpatchable Image)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) kompiliert wurde (nur in Dia SDK v 8.0 oder höher).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` , wenn kompiliert und mit dem [Compilerschalter/LTCG (Link-Time Code Generation)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) kompiliert wurde (nur in Dia SDK v 8.0 oder höher).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE, wenn kompiliert und ein MSIL-Modul (Microsoft Intermediate Language) ist (nur in Dia SDK v 8.0 oder höher).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Quellcodesprache.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für das kompiand.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID des übergeordneten lexikalischen Symbols.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plattform, auf der kompiliert wird (einer der [CV_CPU_TYPE_e Enumerationswerte](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompilandDetails` (einen der [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationswerte) zurück.|  
  
## <a name="remarks"></a>Bemerkungen  
 Compiler sind häufig in einer Form enthalten, die als zwei-Pass-Compiler bezeichnet wird. in einigen Compilerversionen wird jeder Durchlauf von einem separaten Programm behandelt. Diese werden als Front-End-bzw. Back-End-Compiler bezeichnet und somit als Symbol Eigenschaften für Back-End-und Front-End-Versionsnummern bezeichnet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
