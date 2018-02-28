---
title: "Makros für die Berichterstellung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5af21a708a05bfdc0338ca1c5b2bc038e192eb4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="macros-for-reporting"></a>Makros für die Berichterstellung
Sie können die **_RPTn**, und **_RPTFn** Makros, die in CRTDBG.H definiert. H, ersetzen Sie die Verwendung von `printf` Anweisungen für das Debuggen. Diese Makros automatisch dem Releasebuild entfernt erstellen, wenn **_DEBUG** nicht definiert ist, daher keine Notwendigkeit zum Einschließen in besteht **#ifdef**s.  
  
|Makro|Beschreibung|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Gibt eine Meldungszeichenfolge und 0 (null) bis vier Argumente aus. Bei _RPT1 bis **_RPT4**, fungiert die Meldungszeichenfolge als Printf-Style-Formatzeichenfolge für die Argumente.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Identisch mit **_RPTn**, aber diese Makros auch ausgegeben werden die Namen und die Zeilennummer Dateinummer in der sich das Makro befindet.|  
  
 Betrachten Sie das folgende Beispiel:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Dieser Code gibt die Werte der `someVar` und `otherVar` auf **"stdout"**. Sie können den folgenden Aufruf von `_RPTF2` verwenden, um dieselben Werte und zusätzlich Dateinamen und Zeilennummer auszugeben:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Wenn Sie für eine bestimmte Anwendung Debugberichte benötigen, die mit den Makros aus der C-Laufzeitbibliothek nicht erstellt werden können, können Sie selbst ein geeignetes Makro schreiben. In einem der Headerdateien ein, z. B. Sie konnte vergleichbaren Code Folgendes verwenden, um ein Makro definieren aufgerufen **ALERT_IF2**:  
  
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
  
 Ein Aufruf von **ALERT_IF2** konnte ausgeführt werden, die Funktionen des die **Printf** Code am Anfang dieses Themas:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Da benutzerdefinierte Makros problemlos geändert werden können, um bedarfsabhängig mehr oder auch weniger Informationen an bestimmte Ziele zu senden, kann sich dieser Ansatz insbesondere bei steigenden Debuganforderungen als nützlich erweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)