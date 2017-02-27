---
title: "Gewusst wie: Installieren einer Schnellansicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Schnellansichten"
  - "Schnellansichten, Installieren"
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Gewusst wie: Installieren einer Schnellansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nachdem Sie eine Schnellansicht erstellt haben, müssen Sie die Schnellansicht installieren, sodass sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zur Verfügung steht.  Das Installieren einer Schnellansicht ist einfach.  
  
> [!NOTE]
>  In **Speicher**\-Anwendungen werden nur die Schnellansichten Standardtext, HTML, XML und JSON unterstützt.  Benutzerdefinierte \(von Benutzern erstellte\) Schnellansichten werden nicht unterstützt.  
  
### So installieren Sie eine Schnellansicht  
  
1.  Suchen Sie die DLL, die die erstellte Schnellansicht enthält.  
  
2.  Kopieren Sie die DLL an einen der folgenden Speicherorte:  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  Wenn Sie eine verwaltete Schnellansicht zum Remotedebuggen verwenden möchten, kopieren Sie die DLL\-Datei in denselben Pfad auf dem Remotecomputer.  
  
4.  Starten Sie die Debugsitzung neu.  
  
## Siehe auch  
 [Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Gewusst wie: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)