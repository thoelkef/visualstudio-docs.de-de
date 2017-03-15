---
title: "Ausw&#228;hlen einer Strategie f&#252;r das Debug-Modul-Implementierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, Implementierungsstrategien"
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Ausw&#228;hlen einer Strategie f&#252;r das Debug-Modul-Implementierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Debug\-, um die Architektur der Durchführungsstrategie des Moduls \(DE\) zu bestimmen.  Das Debugmodul kann es sich um gedebuggt werden prozessintern erstellt, das prozessinterne Debuggen auf den Manager der Visual Studio\-Sitzung \(SDM\) oder prozessextern Programm zu allen beidem.  Die folgenden Richtlinien sollten Sie mit diesen drei Strategien auszuwählen.  
  
## Richtlinien  
 Obwohl es möglich ist, um DE gedebuggt werden soll und SDM auf das Programm prozessextern sein, gibt es normalerweise keinen Grund.  Aufrufe über Prozessgrenzen sind relativ langsam.  
  
 Debuggen von Modulen sind bereits für die Win32\-systemeigene Laufzeitumgebung und für die Common Language Runtime\-Umgebung bereitgestellt.  Wenn Sie DE für jede dieser Umgebung verwenden möchten, müssen Sie DE erstellen, das mit dem SDM prozessintern ist.  
  
 Andernfalls können Sie zwischen dem Erstellen DEs auswählen, das für das SDM prozessintern oder dem zu debuggenden Programm kann prozessintern werden.  Es ist wichtig, zu beachten, dass die Ausdrucksauswertung DEs allgemeinen Zugriff auf das Programm symbolspeicher erforderlich ist und ob der Symbolspeicher in den Speicher für den Schnellzugriff geladen werden kann.  Betrachten Sie auch Folgendes:  
  
-   Wenn es nur wenige Aufrufe zwischen der Ausdrucksauswertung und dem Symbolspeicher gibt, oder wenn der Symbolspeicher in den SDM speicherbereich gelesen werden kann, erstellen Sie DE, das dem SDM prozessintern ist.  Sie müssen die CLSID des Debugmoduls um SDM zurückgegeben werden, wenn es an das Programm angefügt werden.  Das SDM verwendet dieses CLSID, um eine prozessinterne Instanz DEs zu erstellen.  
  
-   Wenn DE das Programm aufrufen muss, um den Symbolspeicher zuzugreifen, erstellen Sie DE, das dem Programm prozessintern ist.  In diesem Fall erstellt das Programm die Instanz DEs.  
  
## Siehe auch  
 [Visual Studio\-Debugger\-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)