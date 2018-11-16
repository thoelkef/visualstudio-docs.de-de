---
title: Aktivieren von Debugfunktionen in Visual C++ (-D_DEBUG) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf560bcde09b9d2e3c2bee689c92c9900c6e2af5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760600"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Aktivieren von Debugfunktionen in Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], Debugfunktionen, z. B. Assertionen sind beim Kompilieren des Programms mit dem Symbol **_DEBUG** definiert. Sie können definieren, **_DEBUG** auf zwei Arten:  
  
- Geben Sie **#define _DEBUG** in Ihrem Quellcode, oder  
  
- Geben Sie die **/D_DEBUG** -Compileroption. (Wenn Sie Ihr Projekt in Visual Studio mit einem Assistenten erstellen **/D_DEBUG** wird in der Debugkonfiguration automatisch definiert.)  
  
  Wenn **_DEBUG** wird definiert, kompiliert der Compiler Codeabschnitte enthaltender **#ifdef _DEBUG** und `#endif`.  
  
  Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die MFC-Headerdateien bestimmt die richtige Version der MFC-Bibliothek zur Verknüpfung mit auf der Grundlage der Symbole, die Sie, wie z. B. definiert haben **_DEBUG** und **_UNICODE**. Weitere Informationen finden Sie unter [MFC-Bibliotheksversionen](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)



