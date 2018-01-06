---
title: 'Vorgehensweise: Festlegen von SharePoint-Bereitstellungsbefehlen | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d5692195f340ce347df0bc6f8ad2d60225f24e6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Gewusst wie: Festlegen von SharePoint-Bereitstellungsbefehlen
  Sie können den Bereitstellungsprozess anpassen, indem Sie Befehle vor der Bereitstellung und nach der Bereitstellung festlegen. Diese Befehle führen Sie vor und nach anderen Bereitstellungsaktionen beim Debuggen von SharePoint-Lösungen in Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>So fügen Sie einen Befehl vor der Bereitstellung hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**, *Projektname***Eigenschaften**.  
  
2.  Wählen Sie die **SharePoint** Registerkarte.  
  
3.  In der **vor der Bereitstellung über die Befehlszeile** Text Geben Sie MS-DOS- oder MSBuild Befehle aus, um diesen Schritt anzupassen.  
  
     Geben Sie beispielsweise zum Auflisten der Verzeichnisinhalt vor dem Abschluss der Bereitstellung **Dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>So fügen Sie einen Befehl nach der Bereitstellung hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**, *Projektname***Eigenschaften**.  
  
2.  Wählen Sie die **SharePoint** Registerkarte.  
  
3.  In der **nach der Bereitstellung über die Befehlszeile** Text Geben Sie MS-DOS- oder MSBuild Befehle aus, um diesen Schritt anzupassen.  
  
     Geben Sie beispielsweise zum Auflisten der Verzeichnisinhalt nach Abschluss der Bereitstellung **Dir**. Um einer MSBuild-Variablen verwenden, um die Assembly aus dem Verzeichnis "Build" zu kopieren, geben Sie **kopieren $(TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  