---
title: Das Debugging im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt. | Microsoft-Dokumentation
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
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b1c35a2801c79b4775b1e58b8c8c3c74c194fd5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262677"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Das Debugging im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio unterstützt kein Debugging im gemischten Modus für verwalteten und nativen Code in IA64-Prozessen. Dies bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu nativem Code oder von nativem Code zu verwaltetem Code wechseln können.  
  
### <a name="workarounds"></a>Problemumgehung  
  
-   Debuggen Sie den verwalteten und den nativen Code in separaten Debugsitzungen.  
  
     – oder –  
  
     Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>So ändern Sie die Plattform in 32-Bit (Visual Basic oder C#)  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste auf das Projekt, und klicken Sie dann **Eigenschaften** im Kontextmenü die Option.  
  
2.  Klicken Sie in den Eigenschaftenseiten auf die **Kompilieren** oder **Debuggen** Registerkarte.  
  
3.  Klicken Sie auf **Plattform** , und wählen Sie aus der Liste der Plattformen X86.  
  
     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Sie müssen zum Ausführen auf einem 32-Bit-Prozess auswählen **Win32**, nicht **"anycpu"**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>So ändern Sie die Plattform in 32-Bit (C/C++)  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste auf das Projekt, und klicken Sie dann **Eigenschaften** im Kontextmenü die Option.  
  
2.  Klicken Sie in den Eigenschaftenseiten auf **Plattform** und wählen Sie Win32 aus der Liste der Plattformen  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)



