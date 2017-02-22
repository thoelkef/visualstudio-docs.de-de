---
title: "Gewusst wie: Serialisieren von Symbolinformationen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Performance.General"
helpviewer_keywords: 
  - "Profilerstellungstools, Serialisieren von Symbolinformationen"
  - "Leistungstools, Serialisieren von Symbolinformationen"
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Serialisieren von Symbolinformationen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Symbole serialisieren, die zum Analysieren der Anwendung erforderlich sind.  Bei der Serialisierung von Symbolen werden der VSP\-Datei Symbole hinzugefügt.  Durch das Hinzufügen von Symbolinformationen zur VSP\-Datei können andere Personen den Leistungsbericht analysieren, ohne auf die ursprünglichen Symbole zugreifen zu müssen.  Falls die Symbole nicht serialisiert werden, benötigen Sie zum Analysieren der VSP\-Datei instrumentierte EXE\- und PDB\-Dateien.  
  
### So serialisieren Sie automatisch Symbolinformationen  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
     Das Dialogfeld **Optionen** wird angezeigt.  
  
2.  Klicken Sie auf **Leistungstools**.  
  
3.  Wählen Sie unter **Allgemeine Einstellungen** die Option **Symbolinformationen automatisch serialisieren** aus.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Gewusst wie: Verweisen auf Windows\-Symbolinformationen](../profiling/how-to-reference-windows-symbol-information.md)   
 [How to: Save Analyzed Report Files](http://msdn.microsoft.com/de-de/0340ddde-caf4-48ac-8af3-d15dcdade556)