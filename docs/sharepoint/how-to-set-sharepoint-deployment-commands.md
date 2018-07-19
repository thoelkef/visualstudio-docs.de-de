---
title: 'Vorgehensweise: Festlegen von SharePoint-Bereitstellungsbefehlen | Microsoft-Dokumentation'
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
ms.openlocfilehash: 060acd0164ff7819d2abfb8d92f2394b4bcc0672
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119248"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Gewusst wie: Set SharePoint-Bereitstellungsbefehlen
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
  
