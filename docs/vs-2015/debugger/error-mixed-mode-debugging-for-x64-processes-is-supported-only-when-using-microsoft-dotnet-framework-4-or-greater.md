---
title: 'Fehler: Im gemischten Modus Debuggen für X64 Prozesse wird nur unterstützt, wenn Microsoft .NET Framework, Version 4 oder höher | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 190a6e890ce31ce2aa66ff474bb9e4b1976a6c46
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824000"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Fehler: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um gemischten systemeigenen und verwalteten Code in einem 64-Bit-Prozess zu debuggen, benötigen Sie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4. Das Debuggen von 64-Bit-Prozessen im gemischten Modus wird erst ab [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 unterstützt.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Führen Sie einen der folgenden Schritte aus:  
  
  - Aktualisieren Sie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] auf Version 4.  

  - Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten der Remotetools auf dem Gerät](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
