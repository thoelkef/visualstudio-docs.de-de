---
title: Debuggen eines datengebundenen ActiveX-Steuerelements | Microsoft-Dokumentation
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b5b3d5a58c87988c950328a8b0136986b3a149f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852417"
---
# <a name="debugging-a-data-bound-activex-control"></a>Debuggen eines datengebundenen ActiveX-Steuerelements
Wenn Sie ein ActiveX-Steuerelement entwickeln, das an ein Datenquellen-Steuerelement gebunden werden soll, können Sie Ihre eigene Containeranwendung erstellen und diesen Container zum Debuggen des ActiveX-Steuerelements verwenden.

 Sie können beispielsweise eine auf Dialogfeldern basierende MFC-Anwendung erstellen und das datengebundene Steuerelement sowie ein Datenquellen-Steuerelement in das Dialogfeld einfügen. Sie können diese MFC-Anwendung für Laufzeittests und als ausführbare Containerdatei zum Debuggen des datengebundenen ActiveX-Steuerelements verwenden.

## <a name="using-the-test-container"></a>Verwendung des Testcontainers
 Falls Sie einen Container benötigen, der auf einfache Weise für die Unterstützung unterschiedlicher Steuerelement- bzw. Containerschnittstellen modifiziert werden kann, verwenden Sie den ActiveX-Testcontainer als ausführbare Anwendung für die Debugsitzung. Klicken Sie im Menü **Container** des ActiveX-Testcontainers auf **Optionen**, um mehrere Schnittstellen zu aktivieren. Weitere Informationen finden Sie unter [Testen von Eigenschaften und Ereignisse mit Test Container](/cpp/mfc/testing-properties-and-events-with-test-container).

 Falls während des Debuggens Sprünge in den Containercode erforderlich sind, verwenden Sie die Debugversion des Containers oder die Debugversion des ActiveX-Testcontainers. Weitere Informationen finden Sie unter [TSTCON-Beispiel: ActiveX-Steuerelementtestcontainer](https://msdn.microsoft.com/library/72fa40ef-27d3-400c-813f-10b03236e600).

## <a name="see-also"></a>Siehe auch
- [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)
- [ActiveX-Steuerelemente](/cpp/mfc/activex-controls)