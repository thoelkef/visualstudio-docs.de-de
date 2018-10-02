---
title: 'Vorgehensweise: Debuggen eines lokal gehosteten WCF-Diensts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1e87af205a88e84942eb4958876c2030a175065
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524369"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Gewusst wie: Debuggen eines lokal gehosteten WCF-Diensts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Debuggen eines WCF-Diensts für selbstgehostete](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-a-self-hosted-wcf-service).  
  
Ein *lokal gehosteter Dienst* ist ein WCF-Dienst, der nicht innerhalb von IIS, der WCF-Diensthost ausgeführt werden kann oder die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server. Die einfachste Möglichkeit zum Debuggen eines lokal gehosteten WCFS ist so konfigurieren Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zum Starten von sowohl Client-als auch bei der Auswahl **Debuggen starten** auf die **Debuggen** Menü.  
  
 Wenn der WCF-Dienst in einem Prozess lokal gehostet wird, der nicht auf diese Weise gestartet werden kann, z. B. ein NT-Dienst, kann diese Methode nicht verwendet werden. Verwenden Sie stattdessen eine der folgenden Methoden:  
  
-   Fügen Sie den Debugger manuell an den Hostprozess an. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     - oder -  
  
-   Starten Sie das Debuggen des Clients, und führen Sie einen Einzelschritt in einen Aufruf des Diensts aus. Dazu muss das Debuggen in der Datei app.config aktiviert werden. Weitere Informationen [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>So starten Sie sowohl Client als auch Host in Visual Studio  
  
1.  Erstellen Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe, in der sowohl das Client- als auch das Serverprojekt enthalten ist.  
  
2.  Konfigurieren Sie die Lösung zum Starten von sowohl Client-als auch des Serverprozesses, bei der Auswahl **starten** auf die **Debuggen** Menü.  
  
    1.  In **Projektmappen-Explorer**, mit der rechten Maustaste in des Namens der Projektmappe.  
  
    2.  Klicken Sie auf **Startprojekte**.  
  
    3.  In der **Lösung \<Name > Eigenschaften** wählen Sie im Dialogfeld **mehrere Startprojekte**.  
  
    4.  In der **mehrere Startprojekte** Raster in der Zeile, die die dem Serverprojekt entspricht, klicken Sie auf **Aktion** , und wählen Sie **starten**.  
  
    5.  Klicken Sie auf die Zeile, in das Clientprojekt entspricht, auf **Aktion** , und wählen Sie **starten**.  
  
    6.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)   
 [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md)   
 [Gewusst wie: Ausführen eines Einzelschritts in WCF-Dienste](../debugger/how-to-step-into-wcf-services.md)



