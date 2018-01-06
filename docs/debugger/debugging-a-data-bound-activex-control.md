---
title: Debuggen eines datengebundenen ActiveX-Steuerelements | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 32cbb7bee21b54c932e0c369c46c3b2c3dacd898
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-a-data-bound-activex-control"></a>Debuggen eines datengebundenen ActiveX-Steuerelements
Wenn Sie ein ActiveX-Steuerelement entwickeln, das an ein Datenquellen-Steuerelement gebunden werden soll, können Sie Ihre eigene Containeranwendung erstellen und diesen Container zum Debuggen des ActiveX-Steuerelements verwenden.  
  
 Sie können beispielsweise eine auf Dialogfeldern basierende MFC-Anwendung erstellen und das datengebundene Steuerelement sowie ein Datenquellen-Steuerelement in das Dialogfeld einfügen. Sie können diese MFC-Anwendung für Laufzeittests und als ausführbare Containerdatei zum Debuggen des datengebundenen ActiveX-Steuerelements verwenden.  
  
## <a name="using-the-test-container"></a>Verwendung des Testcontainers  
 Falls Sie einen Container benötigen, der auf einfache Weise für die Unterstützung unterschiedlicher Steuerelement- bzw. Containerschnittstellen modifiziert werden kann, verwenden Sie den ActiveX-Testcontainer als ausführbare Anwendung für die Debugsitzung. Klicken Sie in der ActiveX-Testcontainers auf **Optionen** aus der **Container** Menü, um verschiedene Schnittstellen zu aktivieren. Weitere Informationen finden Sie unter [Testen von Eigenschaften und Ereignisse mit Test Container](/cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Falls während des Debuggens Sprünge in den Containercode erforderlich sind, verwenden Sie die Debugversion des Containers oder die Debugversion des ActiveX-Testcontainers. Weitere Informationen finden Sie unter [TSTCON-Beispiel: Testcontainer für ActiveX-Steuerelement](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Siehe auch  
 [COM und ActiveX-Debugging](../debugger/com-and-activex-debugging.md)   
 [ActiveX-Steuerelemente](/cpp/mfc/activex-controls)