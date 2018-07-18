---
title: Dia2dump-Beispiel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5559d1ac2a03eaeb1dca57531cd2f19831851d3b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457825"
---
# <a name="dia2dump-sample"></a>Dia2dump-Beispiel
Dia2dump-Beispiel mit Visual Studio installiert ist und die Quelldatei dia2dump.cpp enthält. Die kompilierte ausführbare Datei ausgeführt wird, von der Befehlszeile aus und zeigt den Inhalt von einem gesamten Programmdatenbankdatei (.pdb).  
  
### <a name="to-install-the-sample"></a>So installieren Sie das Beispiel  
  
1.  Stellen Sie sicher, dass Ihr System alle in der Visual Studio-Setup-Startseite beschriebenen Installationsanforderungen erfüllt.  
  
2.  Installieren von Visual Studio, und befolgen Sie alle Setup- und Anweisungen für diese enthaltenen Beispiele.  
  
#### <a name="to-build-the-sample"></a>So erstellen Sie das Beispiel  
  
1.  Öffnen Sie die Datei Dia2dump.sln in Visual Studio. (Falls erforderlich, Visual Studio zuerst das Dia2dump-Projekt aktualisieren hilft Ihnen.)  
  
2.  In den Eigenschaftenseiten des Projekts in der **C/C++-** &#124; **allgemeine** &#124; **Zusätzliche Includeverzeichnisse** -Eigenschaft, geben Sie die `..\DIA SDK\include` Verzeichnis. Damit wird sichergestellt, dass der Compiler die dia2.h-Datei nicht finden kann.  
  
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