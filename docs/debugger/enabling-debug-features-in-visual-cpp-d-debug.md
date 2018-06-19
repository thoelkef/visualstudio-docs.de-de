---
title: Aktivieren von Debugfeatures in Visual C++ (-D_DEBUG) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5298879d93bf4e86df7610d5891e73bdbb67c4a1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472577"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Aktivieren von Debugfeatures in Visual C++ (/D_DEBUG)
In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], Debugfunktionen, z. B. Assertionen aktiviert werden, wenn Sie das Programm mit dem Symbol Kompilieren **_DEBUG** definiert. Sie können definieren, **_DEBUG** auf zwei Arten:  
  
-   Geben Sie **#define _DEBUG** im Quellcode, oder  
  
-   Geben Sie die **/D_DEBUG** -Compileroption. (Wenn Sie Ihr Projekt in Visual Studio mit einem Assistenten erstellen **/D_DEBUG** ist in der Debugkonfiguration automatisch definiert.)  
  
 Wenn **_DEBUG** wird definiert, kompiliert der Compiler Codeabschnitte enthaltender **#ifdef _DEBUG** und `#endif`.  
  
 Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die MFC-Headerdateien bestimmt die richtige Version der MFC-Bibliothek zu verknüpfen basierend auf der definierten Symbole, z. B. **_DEBUG** und **_UNICODE**. Weitere Informationen finden Sie unter [MFC-Bibliotheksversionen](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)