---
title: 'Vorgehensweise: Festlegen von SharePoint-Bereitstellungsbefehlen | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e76a1e4e19f8f3280b6da71dffa19d3a7e2c16a5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871778"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Vorgehensweise: Festlegen von SharePoint-Bereitstellungsbefehlen
  Sie können während des Bereitstellungsvorgangs anpassen, indem Sie Befehle für vor und nach der Bereitstellung festlegen. Diese Befehle führen vor und nach anderen Bereitstellungsaktionen, beim Debuggen von SharePoint-Lösungen in Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Befehl vor der Bereitstellung hinzufügen  
  
1.  Wählen Sie auf der Menüleiste **Projekt** > **\<*ProjectName*> Eigenschaften**.  
  
2.  Wählen Sie die **SharePoint** Registerkarte.  
  
3.  In der **vor der Bereitstellung über die Befehlszeile** Text Geben Sie MS-DOS oder MSBuild Befehle aus, um diesen Schritt anzupassen.  
  
     Geben Sie beispielsweise zum Auflisten der Verzeichnisinhalte aus, bevor die Bereitstellung abgeschlossen ist, **Dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Hinzufügen eines Befehls nach der Bereitstellung  
  
1.  Wählen Sie auf der Menüleiste **Projekt** > **\<*ProjectName*> Eigenschaften**.  
  
2.  Wählen Sie die **SharePoint** Registerkarte.  
  
3.  In der **Befehlszeile nach der Bereitstellung** Text Geben Sie MS-DOS oder MSBuild Befehle aus, um diesen Schritt anzupassen.  
  
     Geben Sie beispielsweise zum Auflisten der Verzeichnisinhalte aus, nachdem die Bereitstellung abgeschlossen ist, **Dir**. Um eine MSBuild-Variable verwenden, um die Assembly aus dem Buildverzeichnis zu kopieren, geben Sie **kopieren $(TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Siehe auch
 [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
