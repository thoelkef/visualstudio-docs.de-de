---
title: COM-Servern und-Containern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a495b90f68d0a12d9fb34babf28aca073580f2aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788003"
---
# <a name="com-server-and-container-debugging"></a>Debuggen von COM-Servern und -Containern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

COM-Anwendungen führen eine Reihe von Aufgaben durch, die nicht direkt vom Programmierer gesteuert werden können. Zu den Bereichen, in denen ein unerwartetes Verhalten auftreten kann, gehören beispielsweise die Kommunikation zwischen DLLs, die Verwendungshäufigkeit von Objekten sowie Zwischenablageoperationen. In einem solchen Fall sollten Sie zunächst die Problemursache ermitteln.  
  
 Der Visual Studio-Debugger unterstützt das Springen über und in Container und Server. Dies schließt die Möglichkeit ein, Remoteprozeduraufrufe zu überspringen.  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Debuggen eines COM-Server und der Container in der gleichen Projektmappe  
 COM-Server und -Container können mithilfe von zwei Projekten in derselben Projektmappe gedebuggt werden. Sie legen die geeigneten Haltepunkte pro Projekt fest und beginnen dann mit dem Debuggen. Wenn der Container einen Server aufruft und auf einen Haltepunkt trifft, wartet der Container so lange, bis der Servercode wieder verfügbar ist (d. h., bis der Debugvorgang beendet ist).  
  
 Das Debuggen eines COM-Containers ist vergleichbar mit dem Debuggen eines Standardprogramms. Hiervon ausgenommen ist jedoch das Debuggen eines Ereignisses, durch das ein Rückruf generiert wird (z. B. das Ziehen von Daten über die Containeranwendung). In diesem Fall müssen Sie einen Haltepunkt in der Rückruffunktion setzen.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Debuggen einer Serveranwendung ohne Containerinformationen  
 Wenn Sie keine Debuginformationen besitzen oder diese für Ihre Containeranwendung nicht verwenden möchten, besteht das Debuggen der Serveranwendung aus drei Schritten:  
  
1.  Debuggen Sie den Server wie eine normale Anwendung.  
  
2.  Legen Sie die gewünschten Haltepunkte fest.  
  
3.  Starten Sie die Containeranwendung.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Debuggen einer Server- und Domänenisolationsanwendung (SDI)  
 Wenn Sie eine SDI-Serveranwendung Debuggen, müssen Sie angeben `/Embedding` oder `/Automation` in die **Befehlszeilenargumente** -Eigenschaft in der *Projekt* Eigenschaftenseiten-Dialogfeld für C/C++, c# oder Visual Basic-Projekte.  
  
 Mithilfe dieser Befehlszeilenargumente kann die Serveranwendung vom Debugger wie von einem Container aus gestartet werden. Das Starten des Containers im Programm-Manager oder Datei-Manager bewirkt dann, dass der Container die im Debugger gestartete Instanz des Servers verwendet.  
  
 Für den Zugriff auf die *Projekt* im Dialogfeld Eigenschaftenseiten, mit der rechten Maustaste in des Projekts im Projektmappen-Explorer, und wählen Sie dann Eigenschaften aus dem Kontextmenü. Die Eigenschaft Befehlszeilenargumente wird angezeigt, wenn Sie die Kategorie Konfigurationseigenschaften erweitern und dann auf die Seite Debuggen klicken.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)



