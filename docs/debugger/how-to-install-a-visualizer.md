---
title: 'Vorgehensweise: Installieren einer Schnellansicht | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e9864a2a8f3f39e368ae1293b4b27fc0a8d9e056
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-install-a-visualizer"></a>Gewusst wie: Installieren einer Schnellansicht
Nachdem Sie eine Schnellansicht erstellt haben, müssen Sie die Schnellansicht installieren, sodass sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zur Verfügung steht. Das Installieren einer Schnellansicht ist einfach.  
  
> [!NOTE]
>  HTML, XML und JSON-Schnellansichten werden in uwp-apps, die nur die standard-Text unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.  
  
### <a name="to-install-a-visualizer"></a>So installieren Sie eine Schnellansicht  
  
1.  Suchen Sie die DLL, die die erstellte Schnellansicht enthält.  
  
2.  Kopieren Sie die DLL an einen der folgenden Speicherorte:  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  Wenn Sie eine verwaltete Schnellansicht zum Remotedebuggen verwenden möchten, kopieren Sie die DLL-Datei in denselben Pfad auf dem Remotecomputer.  
  
4.  Starten Sie die Debugsitzung neu.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen Sie benutzerdefinierte Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Gewusst wie: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)