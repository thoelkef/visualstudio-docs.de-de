---
title: Aktivieren von Debugfunktionen in Visual C++ (-D_DEBUG) | Microsoft-Dokumentation
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
ms.openlocfilehash: 772467caf74a381fc2ef5cc74e8e31bf2ff0503c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949616"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Aktivieren von Debugfunktionen in Visual C++ (/D_DEBUG)
In [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], Debugfunktionen, z. B. Assertionen sind beim Kompilieren des Programms mit dem Symbol **_DEBUG** definiert. Sie können definieren, **_DEBUG** auf zwei Arten:  
  
- Geben Sie **#define _DEBUG** in Ihrem Quellcode, oder  
  
- Geben Sie die **/D_DEBUG** -Compileroption. (Wenn Sie Ihr Projekt in Visual Studio mit einem Assistenten erstellen **/D_DEBUG** wird in der Debugkonfiguration automatisch definiert.)  
  
  Wenn **_DEBUG** wird definiert, kompiliert der Compiler Codeabschnitte enthaltender **#ifdef _DEBUG** und `#endif`.  
  
  Die Debugkonfiguration eines MFC-Programms muss mit einer Debugversion der MFC-Bibliothek verknüpft werden. Die MFC-Headerdateien bestimmt die richtige Version der MFC-Bibliothek zur Verknüpfung mit auf der Grundlage der Symbole, die Sie, wie z. B. definiert haben **_DEBUG** und **_UNICODE**. Weitere Informationen finden Sie unter [MFC-Bibliotheksversionen](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)