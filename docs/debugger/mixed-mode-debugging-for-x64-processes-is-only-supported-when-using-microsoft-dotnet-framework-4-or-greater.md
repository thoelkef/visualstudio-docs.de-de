---
title: Im gemischten Modus Debuggen für X64 Prozesse wird nur unterstützt, wenn Microsoft.NET Framework 4 oder höher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6d58713da9a4c809d5f9c3db6f7157a699a467f
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284093"
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
  
2.  Klicken Sie in den Eigenschaftenseiten auf die **Kompilieren** oder **Debuggen** Registerkarte.  
  
3.  Klicken Sie auf **Plattform** , und wählen Sie aus der Liste der Plattformen X86.  
  
     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Sie müssen zum Ausführen auf einem 32-Bit-Prozess auswählen **Win32**, nicht **"anycpu"**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>So ändern Sie die Plattform in 32-Bit (C/C++)  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Eigenschaften**.  
  
2.  Klicken Sie in den Eigenschaftenseiten auf **Plattform** , und wählen Sie Win32 aus der Liste der Plattformen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Finden Sie unter [Einrichten von SQL-Debugging](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)