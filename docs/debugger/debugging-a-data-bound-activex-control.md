---
title: "Debuggen eines datengebundenen ActiveX-Steuerelements | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
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
  - "ActiveX-Steuerelemente, Debuggen"
  - "Steuerelemente [Visual Studio], ActiveX"
  - "Datengebundene Steuerelemente, ActiveX"
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen eines datengebundenen ActiveX-Steuerelements
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie ein ActiveX\-Steuerelement entwickeln, das an ein Datenquellen\-Steuerelement gebunden werden soll, können Sie Ihre eigene Containeranwendung erstellen und diesen Container zum Debuggen des ActiveX\-Steuerelements verwenden.  
  
 Sie können beispielsweise eine auf Dialogfeldern basierende MFC\-Anwendung erstellen und das datengebundene Steuerelement sowie ein Datenquellen\-Steuerelement in das Dialogfeld einfügen.  Sie können diese MFC\-Anwendung für Laufzeittests und als ausführbare Containerdatei zum Debuggen des datengebundenen ActiveX\-Steuerelements verwenden.  
  
## Verwendung des Testcontainers  
 Falls Sie einen Container benötigen, der auf einfache Weise für die Unterstützung unterschiedlicher Steuerelement\- bzw. Containerschnittstellen modifiziert werden kann, verwenden Sie den ActiveX\-Testcontainer als ausführbare Anwendung für die Debugsitzung.  Klicken Sie im Menü **Container** des ActiveX\-Testcontainers auf **Optionen**, um mehrere Schnittstellen zu aktivieren.  Weitere Informationen finden Sie unter [Testen der Eigenschaften und Ereignisse mit Test Container](/visual-cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Falls während des Debuggens Sprünge in den Containercode erforderlich sind, verwenden Sie die Debugversion des Containers oder die Debugversion des ActiveX\-Testcontainers.  Weitere Informationen finden Sie unter [TSTCON Sample: ActiveX Control Test Container](http://msdn.microsoft.com/de-de/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## Siehe auch  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)   
 [ActiveX\-Steuerelemente](/visual-cpp/mfc/activex-controls)