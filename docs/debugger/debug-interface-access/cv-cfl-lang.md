---
title: "CV_CFL_LANG | Microsoft Docs"
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
  - "CV_CFL_LANG-Enumeration"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt die Quellcodesprache der Anwendung oder des verknüpften Moduls an.  
  
## Syntax  
  
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
  
## Elements  
 CV\_CFL\_C  
 Anwendungssprache ist C.  
  
 CV\_CFL\_CXX  
 Anwendungssprache ist C\+\+.  
  
 CV\_CFL\_FORTRAN  
 Anwendungssprache FORTRAN ist.  
  
 CV\_CFL\_MASM  
 Anwendungssprache ist Microsoft Macro Assembler.  
  
 CV\_CFL\_PASCAL  
 Anwendungssprache ist Pascal.  
  
 CV\_CFL\_BASIC  
 Anwendungssprache ist GRUNDLEGEND.  
  
 CV\_CFL\_COBOL  
 Anwendungssprache COBOL ist.  
  
 CV\_CFL\_LINK  
 Anwendung ist ein Linker\-generiertes Modul.  
  
 CV\_CFL\_CVTRES  
 Anwendung ist ein Ressourcenmodul, das mit CVTRES\-Tool konvertiert wird.  
  
 CV\_CFL\_CVTPGD  
 Anwendung ist ein POGO optimiertes Modul, das mit CVTPGD\-Tool generiert wird.  
  
 CV\_CFL\_CSHARP  
 Anwendungssprache ist C\#.  
  
 CV\_CFL\_VB  
 Anwendungssprache ist Visual Basic.  
  
 CV\_CFL\_ILASM  
 Anwendungssprache ist Intermediate Language\-Assembly \(das heißt, Assembly der CLR \(Common Language Runtime\)\).  
  
 CV\_CFL\_JAVA  
 Anwendungssprache ist Java.  
  
 CV\_CFL\_JSCRIPT  
 Anwendungssprache ist JScript.  
  
 CV\_CFL\_MSIL  
 Anwendungssprache ist eine unbekannte Microsoft Intermediate Language \(MSIL\), möglicherweise ein Ergebnis von der Anwendung [\/LTCG \(Code zur Verknüpfungszeit generieren\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) des Schalters.  
  
 CV\_CFL\_HLSL  
 Anwendungssprache ist High\-Level Shader Language.  
  
## Hinweise  
 Die Werte in dieser Enumeration werden von einem Aufruf der [IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)