---
title: "Sicherheit und lokalisierte Satellitenassemblys | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assemblys [Visual Studio], Sicherheit"
  - "Codesignatur, Assemblys"
  - "Schlüsselpaare für Assemblys mit starkem Namen"
  - "Lokalisierung, Satellitenassemblys"
  - "Satellitenassemblys, Lokalisiert"
  - "Sicherheit [Visual Studio], Assemblys"
  - "Assemblys mit starken Namen, Lokalisiert"
  - "Assemblys mit starken Namen, Überlegungen zur Sicherheit"
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Sicherheit und lokalisierte Satellitenassemblys
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn für die Hauptassembly starke Namen verwendet werden, müssen Satellitenassemblys mit demselben privaten Schlüssel signiert werden wie die Hauptassembly.  Wenn das aus einem privaten und einem öffentlichen Schlüssel bestehende Schlüsselpaar für die Hauptassembly und die Satellitenassemblys nicht übereinstimmt, werden die Ressourcen nicht geladen.  Weitere Informationen zum Signieren von Assemblys finden Sie unter [Gewusst wie: Signieren einer Assembly mit einem starken Namen](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md).  
  
 In der Regel müssen Sie die Signierung mit dem privaten Schlüssel entweder von der Signierungsgruppe Ihrer Organisation oder von einer externen Signierungsorganisation anfordern.  Der Grund hierfür liegt darin, dass der private Schlüssel vertraulich behandelt werden muss und der Zugriff daher auf wenige Personen beschränkt ist.  Während der Entwicklung können Sie verzögertes Signieren verwenden.  Weitere Informationen finden Sie unter [Verzögertes Signieren einer Assembly](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
## Siehe auch  
 [Überlegungen zur Assemblysicherheit](../Topic/Assembly%20Security%20Considerations.md)   
 [Key Security Concepts](../Topic/Key%20Security%20Concepts.md)   
 [Einführung in internationale Anwendungen basierend auf .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)