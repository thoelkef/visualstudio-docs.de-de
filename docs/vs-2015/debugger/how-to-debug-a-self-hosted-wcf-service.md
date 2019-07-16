---
title: 'Vorgehensweise: Debuggen eines lokal gehosteten WCF-Diensts | Microsoft-Dokumentation'
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
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e58acc6323f396f9b0755e84b369ce0fdf413c08
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185169"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Vorgehensweise: Debuggen eines lokal gehosteten WCF-Diensts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein *lokal gehosteter Dienst* ist ein WCF-Dienst, der nicht innerhalb von IIS, WCF-Diensthost oder [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server ausgeführt wird. Der einfachste Weg zum Debuggen eines lokal gehosteten WCFs besteht darin, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] für das Starten sowohl von Client als auch Server zu konfigurieren, wenn Sie im Menü **Debuggen** den Befehl **Debuggen starten** auswählen.  
  
 Wenn der WCF-Dienst in einem Prozess lokal gehostet wird, der nicht auf diese Weise gestartet werden kann, z. B. ein NT-Dienst, kann diese Methode nicht verwendet werden. Verwenden Sie stattdessen eine der folgenden Methoden:  
  
- Fügen Sie den Debugger manuell an den Hostprozess an. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     \- oder -  
  
- Starten Sie das Debuggen des Clients, und führen Sie einen Einzelschritt in einen Aufruf des Diensts aus. Dazu muss das Debuggen in der Datei app.config aktiviert werden. Weitere Informationen [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>So starten Sie sowohl Client als auch Host in Visual Studio  
  
1. Erstellen Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektmappe, in der sowohl das Client- als auch das Serverprojekt enthalten ist.  
  
2. Konfigurieren Sie die Projektmappe zum Starten sowohl des Client- als auch des Serverprozesses, wenn Sie im Menü **Debuggen** den Befehl **Starten** auswählen.  
  
    1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Namen der Projektmappe.  
  
    2. Klicken Sie auf **Startprojekte festlegen**.  
  
    3. Wählen Sie im Dialogfeld **Eigenschaften der Projektmappe \<Name>** die Option **Mehrere Startprojekte** aus.  
  
    4. Wechseln Sie im Raster **Mehrere Startprojekte** zu der Zeile, die dem Serverprojekt entspricht, klicken Sie auf **Aktion**, und wählen Sie **Starten** aus.  
  
    5. Klicken Sie in der Zeile, die dem Clientprojekt entspricht, auf **Aktion**, und wählen Sie **Starten** aus.  
  
    6. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)   
 [Einschränkungen beim WCF-Debuggen](../debugger/limitations-on-wcf-debugging.md)   
 [Vorgehensweise: Ausführen eines Einzelschritts in WCF-Diensten](../debugger/how-to-step-into-wcf-services.md)
