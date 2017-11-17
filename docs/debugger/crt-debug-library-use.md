---
title: Verwenden der CRT-Debugbibliothek | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
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
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2774eacfb0472145edb84d5c3becf77513ee986
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="crt-debug-library-use"></a>Verwenden der CRT-Debugbibliothek
Die C-Laufzeitbibliothek bietet umfassende Debugunterstützung. Um eine der CRT-Debugbibliotheken verwenden zu können, müssen Sie eine Verknüpfung mit [/DEBUG](/cpp/build/reference/debug-generate-debug-info) und kompilieren Sie mit **/MDd**, **/MTd**, oder **"/ LDD"**.  
  
## <a name="remarks"></a>Hinweise  
 Die Hauptdefinitionen und Makros für CRT-Debugverfahren befinden sich in der Headerdatei Crtdbg.h.  
  
 Die Funktionen in den CRT-Debugbibliotheken werden mit Debuginformationen kompiliert (["/ Z7", / Zd, / Zi, / Zi (Debuginformationsformat)](/cpp/build/reference/z7-zi-zi-debug-information-format)) und ohne Optimierung. Einige der Funktionen enthalten Assertionen, um die an sie übergebenen Parameter zu überprüfen. Außerdem ist Quellcode enthalten. Mit diesem Quellcode können Sie in die CRT-Funktionen springen, um sicherzustellen, dass sie erwartungsgemäß funktionieren, und fehlerhafte Parameter oder Speicherzustände suchen. (Einige CRT-Laufzeittechnologien sind jedoch proprietär und beinhalten daher keinen Quellcode für Ausnahmebehandlung, Gleitkomma- und einige andere Routinen.)  
  
 Sie haben beim Installieren von Visual C++ die Möglichkeit, den Quellcode der C-Laufzeitbibliothek auf der Festplatte zu installieren. Wenn Sie den Quellcode nicht installieren, benötigen Sie die CD-ROM, um in die einzelnen CRT-Funktionen zu springen.  
  
 Weitere Informationen zu den verschiedenen Laufzeitbibliotheken können, finden Sie unter [C-Laufzeitbibliotheken](/cpp/c-runtime-library/crt-library-features).  
  
## <a name="see-also"></a>Siehe auch  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)   
 [/ MD, / MT, / ld (Laufzeitbibliothek verwenden)](/cpp/build/reference/md-mt-ld-use-run-time-library)