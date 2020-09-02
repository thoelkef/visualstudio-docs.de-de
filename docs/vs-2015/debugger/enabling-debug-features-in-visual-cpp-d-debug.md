---
title: Aktivieren von Debugfunktionen in Visual C++ (-D_DEBUG) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cffa8592c2048c6c6b39eee5c4ca654c41448933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686704"
---
# <a name="enabling-debug-features-in-visual-c-d_debug"></a>Aktivieren von Debugfeatures in Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie das Programm mit definiertem **_DEBUG**-Symbol kompilieren, aktivieren Sie damit die Debugfunktion in [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], (z.B. Assertionen). Sie können **_DEBUG** auf zwei Arten definieren:  
  
- Geben Sie im Quellcode **#define _DEBUG** an, oder  
  
- Geben Sie die **/D_DEBUG**-Compileroption an. (Wenn Sie das Projekt in Visual Studio mit Assistenten erstellen, wird **/D_DEBUG** automatisch in der Debugkonfiguration definiert.)  
  
  Wenn **_DEBUG** definiert wird, kompiliert der Compiler Codeabschnitte, die in **#ifdef _DEBUG** und `#endif` eingeschlossen sind.  
  
  Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die korrekte MFC-Bibliotheksversion, mit der verknüpft werden soll, wird auf der Grundlage der definierten Symbole, z.B. **_DEBUG** und **_UNICODE**, von den MFC-Headerdateien bestimmt. Einzelheiten dazu finden Sie unter [Versionen der MFC-Bibliothek](https://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugging von nativem Code](../debugger/debugging-native-code.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
