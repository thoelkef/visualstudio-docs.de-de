---
title: "Visual Studio-Bibliothek, &#220;bersicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Bibliothek, Übersicht"
ms.assetid: 48910975-7202-462f-a656-de67a4f8b14d
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Visual Studio-Bibliothek, &#220;bersicht
Visual Studio\-Bibliothek ist ein Satz von auf Vorlagen basierendem C\+\+\-Klassen für die Vereinfachung der Erstellung von VSPackages in systemeigenem C\+\+.  Visual Studio\-Bibliothek schließt vollständigen Quellcode, als Satz von C\+\+\-Headerdateien ein.  Die Headerdateien werden in *Pfad SDK\-Installations Visual Studio*\\ VisualStudioIntegration \\ \\. \\ \\ Quelle CPP \(Common VSL \\ Include \\ installiert.  
  
> [!NOTE]
>  Visual Studio\-Bibliothek stützt sich auf die Active Template Library \(ATL\) für die Unterstützung von COM\-Objekten.  Weitere Informationen finden Sie unter [Einführung in ATL](/visual-cpp/atl/introduction-to-atl).  
  
 Visual Studio\-Bibliothek unterstützt Komponententest für seinen eigenen Code und den Code.  Bei einigen Komponententests sind enthalten:  
  
-   Visual Studio\-Bibliotheks von Komponententests werden in *Pfad SDK\-Installations Visual Studio*\\ VisualStudioIntegration Common \\ \\. \\ \\. \\ VSL CPP Quelle UnitTest \\ installiert.  
  
-   Die Basisklassen für Komponententests für Code sind in *Pfad SDK\-Installations Visual Studio*\\ \\ VisualStudioIntegration CPP Common \\ Quelle \\ Include \\ \\. \\ VSL VSLUnitTest.h.  
  
 simulierten Implementierungen von häufig verwendeten COM\- und Visual Studio\-Schnittstellen sind in den Headerdateien, VSLMockSystemInterfaces.h und VSLMockVisualStudioInterfaces.h, die in *Pfad SDK\-Installations Visual Studio*\\ VisualStudioIntegration \\ \\. \\ \\ Quelle CPP \(Common VSL \\ Include \\ installiert werden.  
  
## Siehe auch  
 [Entwickeln von VSPackages mithilfe der Visual Studio Library](../misc/developing-vspackages-by-using-the-visual-studio-library.md)