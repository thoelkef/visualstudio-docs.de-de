---
title: "Ausführen eines Komponententests als 64-Bit-Prozess | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 36a33e9be37255e6bcf199e612a44f65ca243a1e
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Ausführen eines Komponententest als 64-Bit-Prozess
Wenn Sie über einen 64-Bit-Computer verfügen, können Sie Komponententests ausführen und Code Coverage-Informationen als 64-Bit-Prozess erfassen.  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>Ausführen eines Komponententest als 64-Bit-Prozess  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>So führen Sie einen Komponententest als 64-Bit-Prozess aus  
  
1.  Wenn Ihr Code oder Ihre Tests als 32-Bit/X86 kompiliert wurden, aber Sie diese als ein 64-Bit-Prozess ausführen möchten, kompilieren Sie sie als **Beliebige CPU** oder optional als **64-Bit**.  
  
    > [!TIP]
    >  Maximale Flexibilität erhalten Sie, wenn Sie die Testprojekte mit der Konfiguration **Beliebige CPU** kompilieren. Die Ausführung ist dann auf 32- und auf 64-Bit-Agents möglich. Das Kompilieren von Testprojekten mit der **64-Bit**-Konfiguration bietet keinen Vorteil.  
  
2.  Wählen Sie im Visual Studio-Menü **Test**, wählen Sie dann **Einstellungen** und anschließend **Prozessorarchitektur** aus. Wählen Sie **x64** zum Ausführen der Tests als 64-Bit-Prozess aus.  
  
     \- oder –  
  
     Geben Sie `<TargetPlatform>x64</TargetPlatform>` in einer RUNSETTINGS-Datei. Ein Vorteil dieser Methode ist, dass Sie Gruppen von Einstellungen in verschiedenen Dateien angeben und schnell zwischen verschiedenen Einstellungen wechseln können. Sie können auch die Einstellungen zwischen Projektmappen kopieren. Weitere Informationen hierzu finden Sie unter [Configure unit tests by using a .runsettings file (Konfigurieren von Komponententests mithilfe einer .runsettings-Datei)](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## <a name="see-also"></a>Siehe auch

[Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)  
[Komponententest für Code](../test/unit-test-your-code.md)  
