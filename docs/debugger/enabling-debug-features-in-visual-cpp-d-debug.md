---
title: Aktivieren von Debugfeatures in Visual C++ (-D_DEBUG) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
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
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b762f34df693ac3b5992d0b1e9c2ba4fa6fb8cb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Aktivieren von Debugfunktionen in Visual C++ (/D_DEBUG)
In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], Debugfunktionen, z. B. Assertionen aktiviert werden, wenn Sie das Programm mit dem Symbol Kompilieren **_DEBUG** definiert. Sie können definieren, **_DEBUG** auf zwei Arten:  
  
-   Geben Sie **#define _DEBUG** im Quellcode, oder  
  
-   Geben Sie die **/D_DEBUG** -Compileroption. (Wenn Sie Ihr Projekt in Visual Studio mit einem Assistenten erstellen **/D_DEBUG** ist in der Debugkonfiguration automatisch definiert.)  
  
 Wenn **_DEBUG** wird definiert, kompiliert der Compiler Codeabschnitte enthaltender **#ifdef _DEBUG** und `#endif`.  
  
 Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die MFC-Headerdateien bestimmt die richtige Version der MFC-Bibliothek zu verknüpfen basierend auf der definierten Symbole, z. B. **_DEBUG** und **_UNICODE**. Weitere Informationen finden Sie unter [MFC-Bibliotheksversionen](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)