---
title: "Makros f&#252;r die Berichterstellung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.macros"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_RPTFn-Makro"
  - "_RPTn-Makro"
  - "CRT, Berichterstellung von Makros"
  - "Debuggen [CRT], Berichterstellung von Makros"
  - "Makros, CRT-Berichtmakros"
  - "Makros, Debuggen mit"
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Makros f&#252;r die Berichterstellung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe der in **CRTDBG.H** definierten Makros **\_RPTn** und **\_RPTFn** lassen sich Codefolgen ersetzen, in denen `printf`\-Anweisungen zum Debuggen verwendet werden.  Da diese Makros automatisch aus dem Releasebuild entfernt werden, wenn **\_DEBUG** nicht definiert ist, müssen sie nicht in **\#ifdef**\-Blöcke eingeschlossen werden.  
  
|Makro|Beschreibung|  
|-----------|------------------|  
|**\_RPT0**, **\_RPT1**, **\_RPT2**, **\_RPT3**, **\_RPT4**|Gibt eine Meldungszeichenfolge und 0 \(null\) bis vier Argumente aus.  Bei \_RPT1 bis **\_RPT4** fungiert die Meldungszeichenfolge als printf\-Formatzeichenfolge für die Argumente.|  
|**\_RPTF0**, **\_RPTF1**, **,\_RPTF2**, **\_RPTF4**|Identisch mit **\_RPTn**. Bei diesen Makros wird jedoch zusätzlich der Name der Datei und die Zeilennummer ausgegeben, in der sich das Makro befindet.|  
  
 Betrachten Sie das folgende Beispiel:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Durch diesen Code werden die Werte von `someVar` und `otherVar` in **stdout** ausgegeben.  Sie können den folgenden Aufruf von `_RPTF2` verwenden, um dieselben Werte und zusätzlich Dateinamen und Zeilennummer auszugeben:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Wenn Sie für eine bestimmte Anwendung Debugberichte benötigen, die mit den Makros aus der C\-Laufzeitbibliothek nicht erstellt werden können, können Sie selbst ein geeignetes Makro schreiben.  Beispielsweise könnten Sie in eine der Headerdateien mit dem folgenden Beispiel vergleichbaren Code einfügen, durch den ein Makro mit dem Namen **ALERT\_IF2** definiert wird:  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Durch einen Aufruf von **ALERT\_IF2** könnten dann alle Funktionen des **printf**\-Codes am Anfang dieses Themas ausgeführt werden:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Da benutzerdefinierte Makros problemlos geändert werden können, um bedarfsabhängig mehr oder auch weniger Informationen an bestimmte Ziele zu senden, kann sich dieser Ansatz insbesondere bei steigenden Debuganforderungen als nützlich erweisen.  
  
## Siehe auch  
 [CRT\-Debugverfahren](../debugger/crt-debugging-techniques.md)