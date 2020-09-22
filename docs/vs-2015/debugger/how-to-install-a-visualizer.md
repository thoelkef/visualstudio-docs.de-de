---
title: 'Vorgehensweise: Installieren einer Schnellansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726cea8b2e81c53b5f3fff963357946f26b199f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840970"
---
# <a name="how-to-install-a-visualizer"></a>Vorgehensweise: Installieren einer Schnellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem Sie eine Schnellansicht erstellt haben, müssen Sie die Schnellansicht installieren, sodass sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zur Verfügung steht. Das Installieren einer Schnellansicht ist einfach.  
  
> [!NOTE]
> In **Store** -apps werden nur die standardmäßigen Text-, HTML-, XML-und JSON-Visualisierungen unterstützt. Benutzerdefinierte (von Benutzern erstellte) Schnellansichten werden nicht unterstützt.  
  
### <a name="to-install-a-visualizer"></a>So installieren Sie eine Schnellansicht  
  
1. Suchen Sie die DLL, die die erstellte Schnellansicht enthält.  
  
2. Kopieren Sie die DLL an einen der folgenden Speicherorte:  
  
    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3. Wenn Sie eine verwaltete Schnellansicht zum Remotedebuggen verwenden möchten, kopieren Sie die DLL-Datei in denselben Pfad auf dem Remotecomputer.  
  
4. Starten Sie die Debugsitzung neu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von benutzerdefinierten Visualisierungen](../debugger/create-custom-visualizers-of-data.md)   
 [How to: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)
