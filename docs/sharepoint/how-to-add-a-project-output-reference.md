---
title: 'Vorgehensweise: Hinzufügen eine Projektausgabereferenz | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a26f6b2abdf0e24d4179986acc56335fb36d002
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868783"
---
# <a name="how-to-add-a-project-output-reference"></a>Vorgehensweise: Hinzufügen einer Projektausgabereferenz
  Fügen Sie sie zum Bereitstellen von Assemblys für nicht-SharePoint-Projekt (oder XAP-Dateien in Silverlight-Projekten) in SharePoint als Ausgabe Projektverweis hinzu.  
  
 Dieser Vorgang erstellt eine Projektmappe Buildabhängigkeit zwischen den beiden Projekten. Projekte Projektausgabeverweise zugeordnet werden erstellt, bevor das SharePoint-Projekt erstellt und bereitgestellt wird.  
  
### <a name="to-add-a-project-output-reference"></a>Hinzufügen eine Projektausgabereferenz
  
1.  Laden Sie eine Lösung, die mindestens eine SharePoint-Projekt und eine nicht-SharePoint-Projekt enthält.  
  
2.  In **Projektmappen-Explorer**, wählen Sie ein Element in der SharePoint-Projektknoten.  
  
3.  In der **Eigenschaften** Fenster, wählen Sie die **Projektausgabeverweise** -Eigenschaft, und klicken Sie dann auf die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP. NET-Mobile-Designer Ellipse")) Schaltfläche daneben.  
  
4.  In der **Projektausgabeverweise** Dialogfeld auf die **hinzufügen** Schaltfläche.  
  
5.  Wählen Sie im Eigenschaftenbereich den Pfeil neben der **Bereitstellungstyp** -Eigenschaft, und wählen Sie dann einen geeigneten Wert für das nicht-SharePoint-Element, das Sie verweisen auf, wie z. B. **ElementFile**.  
  
6.  Wählen Sie den Pfeil neben **Projektname**, wählen Sie den Namen des nicht-SharePoint-Projektelements, und wählen Sie dann die **OK** Schaltfläche.  
  
## <a name="see-also"></a>Siehe auch
 [Angaben Sie zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Vorgehensweise: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
