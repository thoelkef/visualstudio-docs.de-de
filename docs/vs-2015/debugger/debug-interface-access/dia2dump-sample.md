---
title: Dia2dump-Beispiel | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197590"
---
# <a name="dia2dump-sample"></a>Dia2dump-Beispiel
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Dia2dump-Beispiel wird mit Visual Studio installiert und enthält die Dia2dump. cpp-Quelldatei. Die kompilierte ausführbare Datei wird von der Befehlszeile aus ausgeführt und zeigt den Inhalt einer gesamten Programm Datenbankdatei (. pdb) an.  
  
### <a name="to-install-the-sample"></a>So installieren Sie das Beispiel  
  
1. Stellen Sie sicher, dass Ihr System alle Setup Anforderungen erfüllt, die auf der Visual Studio-Setup-Startseite beschrieben werden  
  
2. Installieren Sie Visual Studio, und befolgen Sie alle Setup-und Installationsanweisungen für die enthaltenen Beispiele.  
  
#### <a name="to-build-the-sample"></a>So erstellen Sie das Beispiel  
  
1. Öffnen Sie die Datei Dia2dump. sln in Visual Studio. (Bei Bedarf unterstützt Visual Studio zunächst das Upgrade des Dia2dump-Projekts.)  
  
2. Geben Sie auf den Eigenschaften Seiten des Projekts in der Eigenschaft **C/C++** &#124; **Allgemeine** &#124; **zusätzliche include-Verzeichnisse** das `..\DIA SDK\include` Verzeichnis an. Dadurch wird sichergestellt, dass der Compiler die Datei "dia2. h" finden kann.  
  
3. Klicken Sie im Menü **Build** auf **Projektmappe neu erstellen**.  
  
4. Schließen Sie Visual Studio.  
  
#### <a name="to-run-the-sample"></a>So führen Sie das Beispiel aus  
  
1. Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dia2dump. cpp-Quelldatei](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Vorgehensweise: Problembehandlung bei nicht erfolgreichen Visual Studio-Projektupgrades](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
