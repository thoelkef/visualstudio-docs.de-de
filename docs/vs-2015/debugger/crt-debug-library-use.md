---
title: Verwenden der CRT-Debugbibliothek | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51534d226f3ae0f8726bb818423bf0a9b788fd8c
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "58956075"
---
# <a name="crt-debug-library-use"></a>Verwenden der CRT-Debugbibliothek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die C-Laufzeitbibliothek bietet umfassende Debugunterstützung. Um eine der CRT-Debugbibliotheken verwenden zu können, müssen Sie eine Verknüpfung mit [/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) und kompilieren Sie mit **/MDd**, **/MTd**, oder **"/ LDD"**.  
  
## <a name="remarks"></a>Hinweise  
 Die Hauptdefinitionen und Makros für CRT-Debugverfahren befinden sich in der Headerdatei Crtdbg.h.  
  
 Die Funktionen in den CRT-Debugbibliotheken werden mit Debuginformationen ([/Z7, /Zd, /Zi, /ZI (Debuginformationsformat)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) und ohne Optimierung kompiliert. Einige der Funktionen enthalten Assertionen, um die an sie übergebenen Parameter zu überprüfen. Außerdem ist Quellcode enthalten. Mit diesem Quellcode können Sie in die CRT-Funktionen springen, um sicherzustellen, dass sie erwartungsgemäß funktionieren, und fehlerhafte Parameter oder Speicherzustände suchen. (Einige CRT-Laufzeittechnologien sind jedoch proprietär und beinhalten daher keinen Quellcode für Ausnahmebehandlung, Gleitkomma- und einige andere Routinen.)  
  
 Sie haben beim Installieren von Visual C++ die Möglichkeit, den Quellcode der C-Laufzeitbibliothek auf der Festplatte zu installieren. Wenn Sie den Quellcode nicht installieren, benötigen Sie die CD-ROM, um in die einzelnen CRT-Funktionen zu springen.  
  
 Weitere Informationen zum Verwenden der verschiedenen Laufzeitbibliotheken finden Sie unter [C-Laufzeitbibliotheken](http://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Siehe auch  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (Laufzeitbibliothek verwenden)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
