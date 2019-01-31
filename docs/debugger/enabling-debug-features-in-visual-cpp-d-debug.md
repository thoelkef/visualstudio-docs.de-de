---
title: Aktivieren von Debugfunktionen in Visual C++ (-D_DEBUG) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2c18dfec1f6d1581f926fa24d006b3761c2f6fce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976247"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Aktivieren von Debugfunktionen in Visual C++ (/D_DEBUG)
Wenn Sie das Programm mit definiertem **_DEBUG**-Symbol kompilieren, aktivieren Sie damit die Debugfunktion in [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], (z.B. Assertionen). Sie können **_DEBUG** auf zwei Arten definieren:  
  
- Geben Sie im Quellcode **#define _DEBUG** an, oder  
  
- Geben Sie die **/D_DEBUG**-Compileroption an. (Wenn Sie das Projekt in Visual Studio mit Assistenten erstellen, wird **/D_DEBUG** automatisch in der Debugkonfiguration definiert.)  
  
  Wenn **_DEBUG** definiert wird, kompiliert der Compiler Codeabschnitte, die in **#ifdef _DEBUG** und `#endif` eingeschlossen sind.  
  
  Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die korrekte MFC-Bibliotheksversion, mit der verknüpft werden soll, wird auf der Grundlage der definierten Symbole, z.B. **_DEBUG** und **_UNICODE**, von den MFC-Headerdateien bestimmt. Einzelheiten dazu finden Sie unter [Versionen der MFC-Bibliothek](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)