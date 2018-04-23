---
title: Debuggen eines datengebundenen ActiveX-Steuerelements | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df11571bb1e37d458fd647ce1524f67432617b8f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
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