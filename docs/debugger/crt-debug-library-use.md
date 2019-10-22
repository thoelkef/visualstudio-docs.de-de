---
title: Verwendung der CRT-Debugbibliothek | Microsoft-Dokumentation
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7e58f65f174c549f6992e9218d7ad692634e20d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72435886"
---
# <a name="crt-debug-library-use"></a>Verwenden der CRT-Debugbibliothek
Die C-Laufzeitbibliothek bietet umfassende Debugunterstützung. Wenn Sie eine der CRT-Debugbibliotheken verwenden möchten, müssen Sie eine Verknüpfung mit [/Debug](/cpp/build/reference/debug-generate-debug-info) herstellen und die Kompilierung mit **/MDD**, **/MTD**oder **/ldd**durchführen.

## <a name="remarks"></a>Hinweise
 Die Hauptdefinitionen und Makros für CRT-Debugverfahren befinden sich in der Headerdatei Crtdbg.h.

 Die Funktionen in den CRT-Debugbibliotheken werden mit Debuginformationen ([/Z7, /Zd, /Zi, /ZI (Debuginformationsformat)](/cpp/build/reference/z7-zi-zi-debug-information-format)) und ohne Optimierung kompiliert. Einige der Funktionen enthalten Assertionen, um die an sie übergebenen Parameter zu überprüfen. Außerdem ist Quellcode enthalten. Mit diesem Quellcode können Sie in die CRT-Funktionen springen, um sicherzustellen, dass sie erwartungsgemäß funktionieren, und fehlerhafte Parameter oder Speicherzustände suchen. (Einige CRT-Laufzeittechnologien sind jedoch proprietär und beinhalten daher keinen Quellcode für Ausnahmebehandlung, Gleitkomma- und einige andere Routinen.)

 Weitere Informationen zum Verwenden der verschiedenen Laufzeitbibliotheken finden Sie unter [C-Laufzeitbibliotheken](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Siehe auch

- [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (Laufzeitbibliothek verwenden)](/cpp/build/reference/md-mt-ld-use-run-time-library)