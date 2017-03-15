---
title: "Dia2dump-Beispiel | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "Beispielanwendungen [DIA-SDK]"
  - "Dia2dump-Beispiel [DIA-SDK]"
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Dia2dump-Beispiel
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Dia2dump\-Beispiel wird zusammen mit Visual Studio installiert und die Dia2dump.cpp\-Quelldatei enthält.  Die kompilierte ausführbare Datei kann von der Befehlszeile ausgeführt und zeigt den Inhalt einer kompletten Programmdatenbankdatei \(.pdb\) an.  
  
### So installieren Sie das Beispiel  
  
1.  Vergewissern Sie sich, dass im gesamten System Rüstanforderungen erfüllt, die in der Visual Studio\-Setup\- startseite beschrieben werden.  
  
2.  Installieren Sie Visual Studio, und befolgen Sie alles Setup\- und Installationsanweisungen für die enthaltenen Beispiele.  
  
#### So erstellen Sie das Beispiel  
  
1.  Öffnen Sie die Dia2dump.sln\-Datei in Visual Studio.  Gegebenenfalls \(Visual Studio Ihnen hilft, zuerst das Dia2dump\-Projekt zu aktualisieren.\)  
  
2.  In den Projekteigenschaftenseiten in **C\/C\+\+** &#124; **Allgemein** &#124; **Zusätzliche Includeverzeichnisse**\-Eigenschaft geben das `fest. DIA \ SDK \ Include` Verzeichnis an.  Dadurch wird sichergestellt, dass der Compiler die dia2.h\-Datei finden kann.  
  
3.  Klicken Sie im Menü **Erstellen** auf **Projektmappe neu erstellen**.  
  
4.  Schließen Sie Visual Studio.  
  
#### So führen Sie das Beispiel aus  
  
1.  Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:  
  
    ```  
    dia2dump filename  
    ```  
  
## Siehe auch  
 [Quelldatei Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Gewusst wie: Problembehandlung bei nicht erfolgreichen Visual Studio\-Projektupgrades](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)