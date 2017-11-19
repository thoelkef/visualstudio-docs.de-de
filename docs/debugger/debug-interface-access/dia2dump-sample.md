---
title: Dia2dump-Beispiel | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a3166065680c193875c451626846a090e50cbc1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="dia2dump-sample"></a>Dia2dump-Beispiel
Dia2dump-Beispiel mit Visual Studio installiert ist und die Quelldatei dia2dump.cpp enthält. Die kompilierte ausführbare Datei ausgeführt wird, von der Befehlszeile aus und zeigt den Inhalt von einem gesamten Programmdatenbankdatei (.pdb).  
  
### <a name="to-install-the-sample"></a>So installieren Sie das Beispiel  
  
1.  Stellen Sie sicher, dass Ihr System alle in der Visual Studio-Setup-Startseite beschriebenen Installationsanforderungen erfüllt.  
  
2.  Installieren von Visual Studio, und befolgen Sie alle Setup- und Anweisungen für diese enthaltenen Beispiele.  
  
#### <a name="to-build-the-sample"></a>So erstellen Sie das Beispiel  
  
1.  Öffnen Sie die Datei Dia2dump.sln in Visual Studio. (Falls erforderlich, Visual Studio zuerst das Dia2dump-Projekt aktualisieren hilft Ihnen.)  
  
2.  In den Eigenschaftenseiten des Projekts in der **C/C++-** &#124; **Allgemeine** &#124; **Zusätzliche Includeverzeichnisse** -Eigenschaft, geben Sie die `..\DIA SDK\include` Verzeichnis. Damit wird sichergestellt, dass der Compiler die dia2.h-Datei nicht finden kann.  
  
3.  Auf der **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.  
  
4.  Schließen Sie Visual Studio.  
  
#### <a name="to-run-the-sample"></a>So führen Sie das Beispiel aus  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster, und geben Sie Folgendes ein:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Quelldatei Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Übertragung, Migration und Upgrade der Visual Studio-Projekte](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)