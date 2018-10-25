---
title: 'Vorgehensweise: Debuggen eines lokal gehosteten WCF-Diensts | Microsoft-Dokumentation'
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
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 255ca0f7d472060d110135536d76de99dc46a18e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872121"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Gewusst wie: Debuggen eines lokal gehosteten WCF-Diensts
Ein *lokal gehosteter Dienst* ist ein WCF-Dienst, der nicht innerhalb von IIS, der WCF-Diensthost ausgeführt werden kann oder die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Die einfachste Möglichkeit zum Debuggen eines lokal gehosteten WCFS ist so konfigurieren Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Starten von sowohl Client-als auch bei der Auswahl **Debuggen starten** auf die **Debuggen** Menü.  
  
 Wenn der WCF-Dienst in einem Prozess lokal gehostet wird, der nicht auf diese Weise gestartet werden kann, z. B. ein NT-Dienst, kann diese Methode nicht verwendet werden. Verwenden Sie stattdessen eine der folgenden Methoden:  
  
-   Fügen Sie den Debugger manuell an den Hostprozess an. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     - oder -  
  
-   Starten Sie das Debuggen des Clients, und führen Sie einen Einzelschritt in einen Aufruf des Diensts aus. Dazu muss das Debuggen in der Datei app.config aktiviert werden. Weitere Informationen [Einschränkungen beim WCF-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>So starten Sie sowohl Client als auch Host in Visual Studio  
  
1. Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe, in der sowohl das Client- als auch das Serverprojekt enthalten ist.  
  
2. Konfigurieren Sie die Lösung zum Starten von sowohl Client-als auch des Serverprozesses, bei der Auswahl **starten** auf die **Debuggen** Menü.  
  
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