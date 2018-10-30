---
title: CV_CFL_LANG | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63426af550894df0e9796babaec91ff5758bbf1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909907"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Gibt die Quellcodesprache der Anwendung oder des verknüpften Modul an.  
  
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
 CV_CFL_C  
 Anwendungssprache ist C.  
  
 CV_CFL_CXX  
 Anwendungssprache ist C++.  
  
 CV_CFL_FORTRAN  
 Anwendungssprache ist FORTRAN.  
  
 CV_CFL_MASM  
 Anwendungssprache ist Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Sprache der Anwendung wird die Pascal-Schreibweise.  
  
 CV_CFL_BASIC  
 Anwendungssprache ist BASIC.  
  
 CV_CFL_COBOL  
 Anwendungssprache ist COBOL.  
  
 CV_CFL_LINK  
 Anwendung ist ein vom Linker generierte Modul.  
  
 CV_CFL_CVTRES  
 Anwendung ist ein Ressourcenmodul CVTRES Tool konvertiert.  
  
 CV_CFL_CVTPGD  
 Anwendung ist ein Modul mit CVTPGD-Tool generierte PGO optimiert.  
  
 CV_CFL_CSHARP  
 Anwendungssprache ist c#.  
  
 CV_CFL_VB  
 Anwendungssprache ist Visual Basic.  
  
 CV_CFL_ILASM  
 Anwendungssprache ist zwischensprachenassembly (d. h. Common Language Runtime (CLR)-Assembly).  
  
 CV_CFL_JAVA  
 Anwendungssprache ist Java.  
  
 CV_CFL_JSCRIPT  
 Anwendungssprache ist Jscript.  
  
 CV_CFL_MSIL  
 Sprache der Anwendung ist ein Unbekannter Microsoft Intermediate Language (MSIL), möglicherweise ein Ergebnis der Verwendung der [/LTCG (Link-Time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation) wechseln.  
  
 CV_CFL_HLSL  
 Anwendungssprache ist High Level Shader Language.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)