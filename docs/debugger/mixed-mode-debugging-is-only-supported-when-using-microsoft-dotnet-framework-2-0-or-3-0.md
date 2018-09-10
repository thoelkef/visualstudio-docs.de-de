---
title: Debuggen im gemischten Modus wird nur unterstützt, wenn Microsoft .NET Framework 2.0 oder 3.0 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9d51a0ca72840b20e23eaaa9db3a82382a3fa012
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284067"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Debuggen im gemischten Modus wird nur bei Verwendung von Microsoft .NET Framework, Version 2.0 oder 3.0, unterstützt
Ältere Versionen von Microsoft .NET Framework 2.0 bieten keine Unterstützung für das Debuggen im gemischten Modus von 64-Bit-Prozessen. Dies bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu nativem Code oder von nativem Code zu verwaltetem Code wechseln können.  
  
 Sie können Folgendes tun, um dieses Problem zu umgehen:  
  
-   Aktualisieren Sie das Projekt, um Microsoft .NET Framework 2.0 oder 3.0 zu verwenden.  
  
-   Debuggen Sie den verwalteten und den nativen Code in separaten Debugsitzungen.  
  
-   Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>So ändern Sie das Betriebssystem in 32-Bit (Visual Basic oder C#)  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften** im Kontextmenü die Option.  
  
2.  Klicken Sie in den Eigenschaftenseiten auf die **Kompilieren** oder **Debuggen** Registerkarte.  
  
3.  Klicken Sie auf **Plattform**, und wählen Sie dann **X86** aus der Liste der Plattformen.  
  
     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Sie müssen zum Ausführen auf einem 32-Bit-Prozess auswählen **Win32**, nicht **"anycpu"**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>So ändern Sie das Betriebssystem in 32-Bit (C/C++)  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften** im Kontextmenü die Option.  
  
     Klicken Sie in den Eigenschaftenseiten auf **Plattform**, und wählen Sie dann **Win32** aus der Liste der Plattformen.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Finden Sie unter [Einrichten von SQL-Debugging](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)