---
title: Debuggen eines datengebundenen ActiveX-Steuerelements | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6945d1ccf72385b4d2fbe76736668e84b804e446
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686756"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debuggen eines datengebundenen ActiveX-Steuerelements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie ein ActiveX-Steuerelement entwickeln, das an ein Datenquellen-Steuerelement gebunden werden soll, können Sie Ihre eigene Containeranwendung erstellen und diesen Container zum Debuggen des ActiveX-Steuerelements verwenden.  
  
 Sie können beispielsweise eine auf Dialogfeldern basierende MFC-Anwendung erstellen und das datengebundene Steuerelement sowie ein Datenquellen-Steuerelement in das Dialogfeld einfügen. Sie können diese MFC-Anwendung für Laufzeittests und als ausführbare Containerdatei zum Debuggen des datengebundenen ActiveX-Steuerelements verwenden.  
  
## <a name="using-the-test-container"></a>Verwendung des Testcontainers  
 Falls Sie einen Container benötigen, der auf einfache Weise für die Unterstützung unterschiedlicher Steuerelement- bzw. Containerschnittstellen modifiziert werden kann, verwenden Sie den ActiveX-Testcontainer als ausführbare Anwendung für die Debugsitzung. Klicken Sie im Menü **Container** des ActiveX-Testcontainers auf **Optionen**, um mehrere Schnittstellen zu aktivieren. Weitere Informationen finden Sie unter [Testen von Eigenschaften und Ereignisse mit Test Container](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 Falls während des Debuggens Sprünge in den Containercode erforderlich sind, verwenden Sie die Debugversion des Containers oder die Debugversion des ActiveX-Testcontainers. Weitere Informationen finden Sie unter [TSTCON-Beispiel: ActiveX-Steuerelementtestcontainer](https://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)   
 [ActiveX-Steuerelemente](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
