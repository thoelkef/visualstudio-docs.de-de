---
title: "Verwenden der CRT-Debugbibliothek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "/DEBUG (Linkeroption) [C++]"
  - "/LDd (Compilerfunktion) [C++]"
  - "/MDd-Compileroption [C++]"
  - "/MTd-Compileroption [C++]"
  - "crtdbg.h (Datei)"
  - "Debugbibliothek"
  - "DEBUG (Linkeroption) [C++]"
  - "Debuggen [CRT], CRT-Debugbibliothek"
  - "LDd (Compilerfunktion) [C++]"
  - "Bibliotheken, CRT-Debugbibliothek"
  - "MDd-Compileroption [C++]"
  - "MTd-Compileroption [C++]"
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Verwenden der CRT-Debugbibliothek
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die C\-Laufzeitbibliothek bietet umfassende Debugunterstützung.  Um eine der CRT\-Debugbibliotheken verwenden zu können, müssen eine Verknüpfung mit [\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info) und eine Kompilierung mit **\/MDd**, **\/MTd** oder **\/LDd** durchgeführt werden.  
  
## Hinweise  
 Die Hauptdefinitionen und Makros für CRT\-Debugverfahren befinden sich in der Headerdatei **Crtdbg.h**.  
  
 Die Funktionen in den CRT\-Debugbibliotheken werden mit Debuginformationen \(["\/Z7", "\/Zd", "\/Zi", "\/ZI" \(Debuginformationsformat\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\) und ohne Optimierung kompiliert.  Einige der Funktionen enthalten Assertionen, um die an sie übergebenen Parameter zu überprüfen. Außerdem ist Quellcode enthalten.  Mit diesem Quellcode können Sie in die CRT\-Funktionen springen, um sicherzustellen, dass sie erwartungsgemäß funktionieren, und fehlerhafte Parameter oder Speicherzustände suchen. \(Einige CRT\-Laufzeittechnologien sind jedoch proprietär und beinhalten daher keinen Quellcode für Ausnahmebehandlung, Gleitkomma\- und einige andere Routinen.\)  
  
 Sie haben beim Installieren von Visual C\+\+ die Möglichkeit, den Quellcode der C\-Laufzeitbibliothek auf der Festplatte zu installieren.  Wenn Sie den Quellcode nicht installieren, benötigen Sie die CD\-ROM, um in die einzelnen CRT\-Funktionen zu springen.  
  
 Weitere Informationen zum Verwenden der verschiedenen Laufzeitbibliotheken finden Sie unter [C\-Laufzeitbibliotheken](/visual-cpp/c-runtime-library/crt-library-features).  
  
## Siehe auch  
 [CRT\-Debugverfahren](../debugger/crt-debugging-techniques.md)   
 [\/MD, \/MT, \/LD \(Laufzeitbibliothek verwenden\)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library)