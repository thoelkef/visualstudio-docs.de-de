---
title: Aktivieren von Debuggingfunktionen in C++ Projekten (-D_DEBUG) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 7f772b74a42b9704f1fd77c731022ddb44774c68
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430679"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Aktivieren von Debuggingfunktionen in C++ Projekten (/D_DEBUG)
Wenn Sie das Programm mit definiertem **_DEBUG**-Symbol kompilieren, aktivieren Sie damit die Debugfunktion in [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], (z.B. Assertionen). Sie können **_DEBUG** auf zwei Arten definieren:

- Geben Sie im Quellcode **#define _DEBUG** an, oder

- Geben Sie die **/D_DEBUG**-Compileroption an. (Wenn Sie das Projekt in Visual Studio mit Assistenten erstellen, wird **/D_DEBUG** automatisch in der Debugkonfiguration definiert.)

  Wenn **_DEBUG** definiert wird, kompiliert der Compiler Codeabschnitte, die in **#ifdef _DEBUG** und `#endif` eingeschlossen sind.

  Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die korrekte MFC-Bibliotheksversion, mit der verknüpft werden soll, wird auf der Grundlage der definierten Symbole, z.B. **_DEBUG** und **_UNICODE**, von den MFC-Headerdateien bestimmt. Einzelheiten dazu finden Sie unter [Versionen der MFC-Bibliothek](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Siehe auch
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)