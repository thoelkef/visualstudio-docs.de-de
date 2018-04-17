---
title: 'Vorgehensweise: Festlegen von SharePoint-Bereitstellungsbefehlen | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8779ba4ee4cf9803982d9849b3af7c83930d8a5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Gewusst wie: Festlegen von SharePoint-Bereitstellungsbefehlen
  Sie können den Bereitstellungsprozess anpassen, indem Sie Befehle vor der Bereitstellung und nach der Bereitstellung festlegen. Diese Befehle führen Sie vor und nach anderen Bereitstellungsaktionen beim Debuggen von SharePoint-Lösungen in Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>So fügen Sie einen Befehl vor der Bereitstellung hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**, * Projektname ***Eigenschaften**.  
  
2.  Wählen Sie die **SharePoint** Registerkarte.  
  
3.  In der **vor der Bereitstellung über die Befehlszeile** Text Geben Sie MS-DOS- oder MSBuild Befehle aus, um diesen Schritt anzupassen.  
  
     Geben Sie beispielsweise zum Auflisten der Verzeichnisinhalt vor dem Abschluss der Bereitstellung **Dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>So fügen Sie einen Befehl nach der Bereitstellung hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**, * Projektname ***Eigenschaften**.  
  
2.  Wählen Sie die **SharePoint** Registerkarte.  
  
3.  In der **nach der Bereitstellung über die Befehlszeile** Text Geben Sie MS-DOS- oder MSBuild Befehle aus, um diesen Schritt anzupassen.  
  
     Geben Sie beispielsweise zum Auflisten der Verzeichnisinhalt nach Abschluss der Bereitstellung **Dir**. Um einer MSBuild-Variablen verwenden, um die Assembly aus dem Verzeichnis "Build" zu kopieren, geben Sie **kopieren $(TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  