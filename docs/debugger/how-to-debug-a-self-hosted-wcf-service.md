---
title: 'Vorgehensweise: Debuggen eines lokal gehosteten WCFS Diensts | Microsoft Docs'
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
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e64f764153106c252ba1a9586bfd0a33f4e239f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Gewusst wie: Debuggen eines lokal gehosteten WCF-Diensts
Ein *lokal gehosteter Dienst* ist ein WCF-Dienst, der nicht innerhalb von IIS, WCF-Diensthost ausgeführt werden kann oder der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Die einfachste Möglichkeit zum Debuggen eines lokal gehosteten WCFS ist so konfigurieren Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Starten sowohl Client-als auch bei der Auswahl **Debuggen** auf die **Debuggen** Menü.  
  
 Wenn der WCF-Dienst in einem Prozess lokal gehostet wird, der nicht auf diese Weise gestartet werden kann, z. B. ein NT-Dienst, kann diese Methode nicht verwendet werden. Verwenden Sie stattdessen eine der folgenden Methoden:  
  
-   Fügen Sie den Debugger manuell an den Hostprozess an. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     – oder –  
  
-   Starten Sie das Debuggen des Clients, und führen Sie einen Einzelschritt in einen Aufruf des Diensts aus. Dazu muss das Debuggen in der Datei app.config aktiviert werden. Weitere Informationen [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>So starten Sie sowohl Client als auch Host in Visual Studio  
  
1.  Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe, in der sowohl das Client- als auch das Serverprojekt enthalten ist.  
  
2.  Konfigurieren Sie die Projektmappe, um sowohl Client als auch für Serverprozesse zu starten, wenn Sie die Option **starten** auf die **Debuggen** Menü.  
  
    1.  In **Projektmappen-Explorer**, mit der rechten Maustaste in des Namens der Projektmappe.  
  
    2.  Klicken Sie auf **Startprojekte festlegen**.  
  
    3.  In der **Lösung \<Name > Eigenschaften** wählen Sie im Dialogfeld **mehrere Startprojekte**.  
  
    4.  In der **mehrere Startprojekte** Raster, in der Zeile, die dem Serverprojekt entspricht klicken Sie auf **Aktion** , und wählen Sie **starten**.  
  
    5.  Klicken Sie auf die Zeile, die dem Clientprojekt entspricht, auf **Aktion** , und wählen Sie **starten**.  
  
    6.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von WCF-Diensten](../debugger/debugging-wcf-services.md)   
 [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md)   
 [Gewusst wie: Ausführen eines Einzelschritts in WCF-Dienste](../debugger/how-to-step-into-wcf-services.md)