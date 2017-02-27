---
title: "Ausf&#252;hren eines Komponententest als 64-Bit-Prozess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Komponententests, Erstellen"
  - "Komponententests, Ausführen"
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 25
---
# Ausf&#252;hren eines Komponententest als 64-Bit-Prozess
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie einen 64\-Bit\-Computer verwenden, können Sie Komponententests und Informationen zur Codeabdeckung als 64\-Bit\-Prozess ausgeführt.  
  
## Ausführen eines Komponententests als 64\-Bit\-Prozess  
  
#### So führen Sie einen Komponententest als 64\-Bit\-Prozess aus  
  
1.  Wenn der Code oder Test als 32\-Bit\-\/x86\-Prozess kompiliert wurde, nun aber als 64\-Bit\-Prozess ausgeführt werden soll, kompilieren Sie ihn mit **Any CPU** oder optional mit **64\-Bit** neu.  
  
    > [!TIP]
    >  Maximale Flexibilität erhalten Sie, wenn Sie die Testprojekte mit der Konfiguration **Any CPU** kompilieren.  Die Ausführung ist dann auf 32\- und auf 64\-Bit\-Agents möglich.  Das Kompilieren von Testprojekten mit der **64\-Bit**\-Konfiguration bietet keinen Vorteil.  
  
2.  Vom Visual Studio\-Menü wählen Sie **Test** aus, und wählen Sie **Einstellungen** und wählen Sie dann **Prozessorarchitektur** aus.  Wählen **x64**, um die Tests als 64\-Bit\-Prozess zu machen.  
  
     – oder –  
  
     Geben Sie `<TargetPlatform>x64</TargetPlatform>` in um eine RUNSETTINGS\-Datei an.  Ein Vorteil dieser Methode ist, dass Sie Gruppen von Einstellungen in verschiedenen Dateien angeben und zwischen verschiedenen Einstellungen schnell wechseln können.  Sie können Einstellungen zwischen Projektmappen auch kopieren.  Weitere Informationen finden Sie unter [Konfigurieren von Komponententests mithilfe einer .runsettings\-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## Siehe auch  
 [Ausführen von Komponententests mit dem Test\-Explorer](../test/run-unit-tests-with-test-explorer.md)   
 [Komponententest für Code](../test/unit-test-your-code.md)   
 [Angeben von Testeinstellungen für Visual Studio\-Tests](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)