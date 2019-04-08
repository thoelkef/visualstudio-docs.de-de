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
ms.openlocfilehash: afc89dc2b70191524830926d108a5de81fbbb647
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947337"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt die Quellcodesprache der Anwendung oder des verknüpften Modul an.  
  
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
 Anwendungssprache ist C#.  
  
 CV_CFL_VB  
 Anwendungssprache ist Visual Basic.  
  
 CV_CFL_ILASM  
 Anwendungssprache ist zwischensprachenassembly (d. h. Common Language Runtime (CLR)-Assembly).  
  
 CV_CFL_JAVA  
 Anwendungssprache ist Java.  
  
 CV_CFL_JSCRIPT  
 Anwendungssprache ist Jscript.  
  
 CV_CFL_MSIL  
 Sprache der Anwendung ist ein Unbekannter Microsoft Intermediate Language (MSIL), möglicherweise ein Ergebnis der Verwendung der [/LTCG (Link-Time Code Generation)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) wechseln.  
  
 CV_CFL_HLSL  
 Anwendungssprache ist High Level Shader Language.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
