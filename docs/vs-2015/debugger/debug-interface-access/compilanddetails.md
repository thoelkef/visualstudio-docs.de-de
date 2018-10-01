---
title: CompilandDetails | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c385d82dfc9a4223610000642b82b8cffe4a7109
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512693"
---
# <a name="compilanddetails"></a>CompilandDetails
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CompilandDetails](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/compilanddetails).  
  
Compiland-Informationen zwischen Symbole mit aufgeteilt ist eine `SymTagCompiland` Tag (niedrige Detail) und ein `SymTagCompilandDetails` Tag (hohe Detail). `SymTagCompilandDetails` erfordert zusätzliche Symbole werden geladen. Sie bietet jedoch eine Fülle von Informationen zu der Kompiliereinheit, die nicht verfügbar ist eine `SymTagCompiland` Symbol.  
  
## <a name="properties"></a>Eigenschaften  
 Die folgende Tabelle zeigt die Eigenschaften, die für diesen Symboltyp gültig sind.  
  
|Eigenschaft|Datentyp|Beschreibung|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Back-End-Build-Nummer des Compilers.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Anzahl der Back-End-Hauptversion des Compilers.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Back-End-Nebenversionsnummer des Compilers.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Der Name des Compilers, die diese Kompiliereinheit (nur in DIA-SDK Version 8.0 oder höher) erstellt.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Wenn bei der Kompilierung bearbeiten und Fortfahren aktiviert wurden.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Front-End-Build-Nummer des Compilers.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Anzahl der Front-End-Hauptversion des Compilers.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Front-End-Nebenversionsnummer des Compilers.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Wenn diese Kompiliereinheit Debuginformationen (nur in DIA-SDK Version 8.0 oder höher) hat.|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Wenn diese Kompiliereinheit verwalteten Code (nur in DIA-SDK-Version 8.0 oder höher) enthält.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Wenn der Kompiliereinheit kompiliert wurde, mit der [/GS (Puffer-Sicherheitsüberprüfung)](http://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) Compilerschalter (nur in DIA-SDK Version 8.0 oder höher).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Wenn Kompiliereinheit aus Common Intermediate Language (CIL) Code in systemeigenen Code konvertiert wurde.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Benutzerdefinierte Typen (UDT) ausgerichtet wurden einige Speichergrenze (nur in DIA-SDK Version 8.0 oder höher) angegeben.|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Wenn Kompiliereinheit kompiliert wurde, mit der [/hotpatch (Erstellen eines Hotpatch-fähigen Abbildes)](http://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) Compilerschalter (nur in DIA-SDK-Version 8.0 oder höher).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Wenn Kompiliereinheit kompiliert wurde, mit der [/LTCG (Link-Time Code Generation)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) Compilerschalter (nur in DIA-SDK Version 8.0 oder höher).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|True, wenn Kompiliereinheit ein Microsoft Intermediate Language (MSIL)-Modul (nur in DIA-SDK-Version 8.0 oder höher).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Quellcodesprache.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol für die Kompiliereinheit.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Die ID des lexikalischen übergeordneten Symbols.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plattform, die unter dem der Kompiliereinheit kompiliert wurde (eines der [CV_CPU_TYPE_e-Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md) Werte).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index-ID des Symbols.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagCompilandDetails` (eines der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Werte).|  
  
## <a name="remarks"></a>Hinweise  
 Compiler stammen, sind häufig in einem Formular als ein zweiphasiges Compiler bezeichnet. In einigen Compilerversionen wird jedem Durchlauf durch ein separates Programm behandelt. Diese werden als Front-End- und Back-End-Compiler, daher die Symboleigenschaften für Back-End und Front-End-Versionsnummern bezeichnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)



