---
title: Im gemischten Modus Debuggen für X64 Prozesse wird nur unterstützt, wenn Microsoft.NET Framework 4 oder höher | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 189e5c622d19ce3e122e01bfbe4b886bd2a830b7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063386"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework-Versionen bereits als 4 bieten keine Unterstützung ist für das Debuggen im gemischten Modus von X64 verarbeitet. Das bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu nativem Code oder von nativem Code zu verwaltetem Code wechseln können.  
  
### <a name="workarounds"></a>Problemumgehung  
  
- Aktualisieren Sie das Projekt, um Microsoft .NET Framework 4 oder höher zu verwenden.  
  
     – oder –  
  
     Debuggen Sie den verwalteten und den systemeigenen Code in separaten Debugsitzungen.  
  
     – oder –  
  
     Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>So ändern Sie die Plattform in 32-Bit (Visual Basic oder C#)  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2. Klicken Sie auf den Eigenschaftenseiten auf die Registerkarte **Kompilieren** oder auf die Registerkarte **Debuggen**.  
  
3. Klicken Sie auf **Plattform**, und wählen Sie x86 aus der Liste der Plattformen aus.  
  
     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Wählen Sie **Win32** anstelle von **AnyCPU** aus, wenn Sie die Ausführung in einem 32-Bit-Prozess wünschen.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>So ändern Sie die Plattform in 32-Bit (C/C++)  
  
1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
2. Klicken Sie auf den Eigenschaftenseiten auf **Plattform**, und wählen Sie Win32 aus der Liste der Plattformen aus.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Finden Sie unter [Einrichten von SQL-Debugging](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)
