---
title: 'Fehler: Im gemischten Modus Debuggen für X64 Prozesse wird nur unterstützt, wenn Microsoft .NET Framework, Version 4 oder höher | Microsoft-Dokumentation'
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
- vs.debug.error.interop_unsupported_x64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82440d378e34c5808e9bcb250172f6c1abfbfdf6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239238"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Fehler: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um gemischten systemeigenen und verwalteten Code in einem 64-Bit-Prozess zu debuggen, benötigen Sie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4. Das Debuggen von 64-Bit-Prozessen im gemischten Modus wird erst ab [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 unterstützt.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Führen Sie einen der folgenden Schritte aus:  
  
    -   Aktualisieren Sie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] auf Version 4.  
  
    -   Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



