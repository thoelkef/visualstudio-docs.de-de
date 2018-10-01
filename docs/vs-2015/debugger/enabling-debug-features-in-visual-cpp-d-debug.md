---
title: Aktivieren von Debugfunktionen in Visual C++ (-D_DEBUG) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67de755105f30ee4a88daeef26bc29bc9841ae39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513654"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Aktivieren von Debugfunktionen in Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [aktivieren Debuggen Funktionen in Visual C++ (-D_DEBUG)](https://docs.microsoft.com/visualstudio/debugger/enabling-debug-features-in-visual-cpp-d-debug).  
  
In [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], Debugfunktionen, z. B. Assertionen sind beim Kompilieren des Programms mit dem Symbol **_DEBUG** definiert. Sie können definieren, **_DEBUG** auf zwei Arten:  
  
-   Geben Sie **#define _DEBUG** in Ihrem Quellcode, oder  
  
-   Geben Sie die **/D_DEBUG** -Compileroption. (Wenn Sie Ihr Projekt in Visual Studio mit einem Assistenten erstellen **/D_DEBUG** wird in der Debugkonfiguration automatisch definiert.)  
  
 Wenn **_DEBUG** wird definiert, kompiliert der Compiler Codeabschnitte enthaltender **#ifdef _DEBUG** und `#endif`.  
  
 Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die MFC-Headerdateien bestimmt die richtige Version der MFC-Bibliothek zur Verknüpfung mit auf der Grundlage der Symbole, die Sie, wie z. B. definiert haben **_DEBUG** und **_UNICODE**. Weitere Informationen finden Sie unter [MFC-Bibliotheksversionen](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)



