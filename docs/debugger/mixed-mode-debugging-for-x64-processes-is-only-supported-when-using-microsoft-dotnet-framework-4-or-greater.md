---
title: "Im gemischten Modus Debuggen für X64 Prozesse wird nur unterstützt, wenn Microsoft.NET Framework 4 oder höher | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 37d5c52192c30ccc3b34bfa609c3f6a7ffb99566
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
.NET Framework-Versionen vor Version 4 bieten keine Unterstützung für das Debuggen im gemischten Modus von x64-Prozessen. Das bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu systemeigenem Code oder von systemeigenem Code zu verwaltetem Code wechseln können.  
  
### <a name="workarounds"></a>Problemumgehung  
  
-   Aktualisieren Sie das Projekt, um Microsoft .NET Framework 4 oder höher zu verwenden.  
  
     - oder -   
  
     Debuggen Sie den verwalteten und den nativen Code in separaten Debugsitzungen.  
  
     - oder -   
  
     Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>So ändern Sie die Plattform in 32-Bit (Visual Basic oder C#)  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf den Eigenschaftenseiten auf die **Kompilieren** oder **Debuggen** Registerkarte.  
  
3.  Klicken Sie auf **Plattform** , und wählen Sie aus der Liste der Plattformen X86.  
  
     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Unter 32-Bit-Prozess ausführen möchten, müssen Sie auswählen **Win32**, nicht **"anycpu"**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>So ändern Sie die Plattform in 32-Bit (C/C++)  
  
1.  In **Projektmappen-Explorer**Sie mit der rechten Maustaste des Projekts, und klicken Sie auf **Eigenschaften**.  
  
2.  Klicken Sie auf den Eigenschaftenseiten auf **Plattform** und wählen Sie Win32 aus der Liste der Plattformen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Finden Sie unter [Einrichten von SQL-Debuggen](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)