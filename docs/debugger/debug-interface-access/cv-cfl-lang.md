---
title: CV_CFL_LANG | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745337"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Gibt die Quell Codesprache der Anwendung oder des verknüpften Moduls an.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Elements
CV_CFL_C Anwendungs Sprache ist C.

CV_CFL_CXX Anwendungs Sprache ist C++.

CV_CFL_FORTRAN Anwendungs Sprache ist Fortran.

CV_CFL_MASM Anwendungs Sprache ist der Microsoft-Makro Assembler.

CV_CFL_PASCAL Anwendungs Sprache ist Pascal.

CV_CFL_BASIC Anwendungs Sprache ist "Basic".

CV_CFL_COBOL Anwendungs Sprache ist COBOL.

CV_CFL_LINK-Anwendung ist ein vom Linker generiertes Modul.

CV_CFL_CVTRES-Anwendung ist ein Ressourcen Modul, das mit dem CVTRES-Tool konvertiert wurde.

Die CV_CFL_CVTPGD-Anwendung ist ein mit dem cvtpgd-Tool generiertes Pogo-optimiertes Modul.

CV_CFL_CSHARP Anwendungs Sprache ist C#.

CV_CFL_VB Anwendungs Sprache ist Visual Basic.

Die CV_CFL_ILASM-Anwendungs Sprache ist eine zwischensprachenassembly (d. h. CLR-Assembly (Common Language Runtime)).

CV_CFL_JAVA Anwendungs Sprache ist Java.

CV_CFL_JSCRIPT Anwendungs Sprache ist JScript.

Die CV_CFL_MSIL-Anwendungs Sprache ist eine unbekannte Microsoft Intermediate Language (MSIL), möglicherweise ein Ergebnis der Verwendung des Schalters " [/LTCG (Link-Zeit Code Generierung)](/cpp/build/reference/ltcg-link-time-code-generation) ".

CV_CFL_HLSL Anwendungs Sprache ist eine allgemeine Shader-Sprache.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
