---
title: Makros für die Berichterstellung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c92424275a1dff69863b81fbf8567fbc4b84499
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905554"
---
# <a name="macros-for-reporting"></a>Makros für die Berichterstellung
Für das Debuggen, können Sie die **_RPTn** und **_RPTFn** in CRTDBG.H definierten Makros. H, ersetzen Sie die Verwendung von `printf` Anweisungen. Sie müssen nicht in inclose **#ifdef**s, da sie nicht mehr automatisch in Ihrer Version angezeigt erstellen, wenn **_DEBUG** ist nicht definiert.

|Makro|Beschreibung|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Gibt eine Meldungszeichenfolge und 0 (null) bis vier Argumente aus. Bei _RPT1 bis **_RPT4** fungiert die Meldungszeichenfolge als printf-Formatzeichenfolge für die Argumente.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Identisch mit **_RPTn**. Bei diesen Makros wird jedoch zusätzlich der Name der Datei und die Zeilennummer ausgegeben, in der sich das Makro befindet.|

 Betrachten Sie das folgende Beispiel:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Durch diesen Code werden die Werte von `someVar` und `otherVar` in **stdout** ausgegeben. Sie können den folgenden Aufruf von `_RPTF2` verwenden, um dieselben Werte und zusätzlich Dateinamen und Zeilennummer auszugeben:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Unter Umständen, dass eine bestimmte Anwendung Debugberichte, die mit der C-Laufzeitbibliothek den Makros keine bereitstellen. In diesen Fällen können Sie ein Makro, das speziell dazu entwickelt, Ihre eigenen Anforderungen anpassen schreiben. Beispielsweise könnten Sie in eine der Headerdateien mit dem folgenden Beispiel vergleichbaren Code einfügen, durch den ein Makro mit dem Namen **ALERT_IF2** definiert wird:

```cpp
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

 Ein Aufruf von **ALERT_IF2** möglich, dass alle Funktionen von der **Printf** Code:

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Sie können ganz einfach ein benutzerdefiniertes Makro, um mehr oder weniger Informationen an verschiedenen Ziele melden ändern. Dieser Ansatz ist besonders nützlich, da es sich bei steigenden Debuganforderungen.

## <a name="see-also"></a>Siehe auch
- [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)
