---
title: "Das Debugging im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt. | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 193d469666d9aaa012187500de063470df77c823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Das Debugging im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt.
Visual Studio unterstützt kein Debugging im gemischten Modus für verwalteten und nativen Code in IA64-Prozessen. Dies bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu nativem Code oder von nativem Code zu verwaltetem Code wechseln können.  
  
### <a name="workarounds"></a>Problemumgehung  
  
-   Debuggen Sie den verwalteten und den nativen Code in separaten Debugsitzungen.  
  
     - oder -   
  
     Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>So ändern Sie die Plattform in 32-Bit (Visual Basic oder C#)  
  
1.  In **Projektmappen-Explorer**Sie mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Eigenschaften** im Kontextmenü.  
  
2.  Klicken Sie auf den Eigenschaftenseiten auf die **Kompilieren** oder **Debuggen** Registerkarte.  
  
3.  Klicken Sie auf **Plattform** , und wählen Sie aus der Liste der Plattformen X86.  
  
     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Unter 32-Bit-Prozess ausführen möchten, müssen Sie auswählen **Win32**, nicht **"anycpu"**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>So ändern Sie die Plattform in 32-Bit (C/C++)  
  
1.  In **Projektmappen-Explorer**Sie mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Eigenschaften** im Kontextmenü.  
  
2.  Klicken Sie auf den Eigenschaftenseiten auf **Plattform** und wählen Sie Win32 aus der Liste der Plattformen,  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)