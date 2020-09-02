---
title: CV_CFL_LANG | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699358"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt die Quell Codesprache der Anwendung oder des verknüpften Moduls an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
  
## <a name="elements"></a>Elemente  
 CV_CFL_C  
 Die Anwendungs Sprache lautet C.  
  
 CV_CFL_CXX  
 Die Anwendungs Sprache ist C++.  
  
 CV_CFL_FORTRAN  
 Die Anwendungs Sprache ist "Fortran".  
  
 CV_CFL_MASM  
 Die Anwendungs Sprache ist der Microsoft-Makro Assembler.  
  
 CV_CFL_PASCAL  
 Die Anwendungs Sprache ist Pascal.  
  
 CV_CFL_BASIC  
 Die Anwendungs Sprache ist "Basic".  
  
 CV_CFL_COBOL  
 Die Anwendungs Sprache ist COBOL.  
  
 CV_CFL_LINK  
 Die Anwendung ist ein vom Linker generiertes Modul.  
  
 CV_CFL_CVTRES  
 Die Anwendung ist ein Ressourcen Modul, das mit dem Tool CVTRES konvertiert wird.  
  
 CV_CFL_CVTPGD  
 Die Anwendung ist ein mit dem cvtpgd-Tool generiertes Pogo-optimiertes Modul.  
  
 CV_CFL_CSHARP  
 Die Anwendungs Sprache ist c#.  
  
 CV_CFL_VB  
 Die Anwendungs Sprache ist Visual Basic.  
  
 CV_CFL_ILASM  
 Die Anwendungs Sprache ist eine zwischensprachenassembly (d. h. CLR-Assembly (Common Language Runtime)).  
  
 CV_CFL_JAVA  
 Die Anwendungs Sprache ist Java.  
  
 CV_CFL_JSCRIPT  
 Die Anwendungs Sprache ist "JScript".  
  
 CV_CFL_MSIL  
 Die Anwendungs Sprache ist eine unbekannte Microsoft Intermediate Language (MSIL), möglicherweise ein Ergebnis der Verwendung des Schalters [/LTCG (Link-Zeit Code Generierung)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) .  
  
 CV_CFL_HLSL  
 Die Anwendungs Sprache ist eine hochstufige Shader-Sprache.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
