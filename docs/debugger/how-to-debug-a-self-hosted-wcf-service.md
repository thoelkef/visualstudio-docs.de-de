---
title: "Gewusst wie: Debuggen eines lokal gehosteten WCF-Diensts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen, WCF"
  - "WCF, Debuggen"
  - "WCF, Lokal gehosteter Dienst"
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Gewusst wie: Debuggen eines lokal gehosteten WCF-Diensts
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein *lokal gehosteter Dienst* ist ein WCF\-Dienst, der nicht innerhalb von IIS, WCF\-Diensthost oder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server ausgeführt wird.  Der einfachste Weg zum Debuggen eines lokal gehosteten WCFs besteht darin, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] für das Starten sowohl von Client als auch Server zu konfigurieren, wenn Sie im Menü **Debuggen** den Befehl **Debuggen starten** auswählen.  
  
 Wenn der WCF\-Dienst in einem Prozess lokal gehostet wird, der nicht auf diese Weise gestartet werden kann, z. B. ein NT\-Dienst, kann diese Methode nicht verwendet werden.  Verwenden Sie stattdessen eine der folgenden Methoden:  
  
-   Fügen Sie den Debugger manuell an den Hostprozess an.  Weitere Informationen finden Sie unter [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     \- oder \-  
  
-   Starten Sie das Debuggen des Clients, und führen Sie einen Einzelschritt in einen Aufruf des Diensts aus.  Dazu muss das Debuggen in der Datei app.config aktiviert werden.  Weitere Informationen finden Sie unter [Einschränkungen beim WCF\-Debugging](../debugger/limitations-on-wcf-debugging.md).  
  
### So starten Sie sowohl Client als auch Host in Visual Studio  
  
1.  Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektmappe, in der sowohl das Client\- als auch das Serverprojekt enthalten ist.  
  
2.  Konfigurieren Sie die Projektmappe zum Starten sowohl des Client\- als auch des Serverprozesses, wenn Sie im Menü **Debuggen** den Befehl **Starten** auswählen.  
  
    1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf den Namen der Projektmappe.  
  
    2.  Klicken Sie auf **Startprojekte festlegen**.  
  
    3.  Wählen Sie im Dialogfeld **Eigenschaften für \<Name\> der Projektmappe** die Option **Mehrere Startprojekte** aus.  
  
    4.  Wechseln Sie im Raster **Mehrere Startprojekte** zur Zeile, die dem Serverprojekt entspricht, klicken Sie auf **Aktion**, und wählen Sie **Starten** aus.  
  
    5.  Klicken Sie in der Zeile, die dem Clientprojekt entspricht, auf **Aktion**, und wählen Sie **Starten** aus.  
  
    6.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Debuggen von WCF\-Diensten](../debugger/debugging-wcf-services.md)   
 [Einschränkungen beim WCF\-Debugging](../debugger/limitations-on-wcf-debugging.md)   
 [Gewusst wie: Ausführen eines Einzelschritts in WCF\-Dienste](../debugger/how-to-step-into-wcf-services.md)