---
title: "Vorgehensweise: hinzufügen eine Projektausgabereferenz | Microsoft Docs"
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
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0114971baa164858add68f2f1d6f571407ba5320
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-project-output-reference"></a>Gewusst wie: Hinzufügen einer Projektausgabereferenz
  Fügen Sie sie zum Bereitstellen von Assemblys für nicht-SharePoint-Projekt (oder XAP-Dateien in Silverlight-Projekte) in SharePoint als einer Projektausgabereferenz hinzu.  
  
 Dieser Vorgang erstellt eine Projektmappe Buildabhängigkeit zwischen den zwei Projekten. Projekte Projektausgabeverweise zugeordnet werden erstellt, bevor das SharePoint-Projekt erstellt und bereitgestellt wird.  
  
### <a name="to-add-a-project-output-reference"></a>Hinzufügen einer Projektausgabereferenz  
  
1.  Laden Sie eine Lösung, die mindestens ein SharePoint-Projekt und eine nicht-SharePoint-Projekt enthält.  
  
2.  In **Projektmappen-Explorer**, wählen Sie ein Element in der SharePoint-Projektknoten.  
  
3.  In der **Eigenschaften** Fenster, wählen Sie die **Projektausgabeverweise** -Eigenschaft, und klicken Sie dann auf die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP. NET-Mobile-Designer Ellipse")) Schaltfläche daneben.  
  
4.  In der **Projektausgabeverweise** Dialogfeld Wählen Sie die **hinzufügen** Schaltfläche.  
  
5.  Klicken Sie im Bereich "Eigenschaften" Wählen Sie den Pfeil neben der **Bereitstellungstyp** -Eigenschaft, und wählen Sie dann einen geeigneten Wert für das nicht-SharePoint-Element, das Sie verweisen auf, wie z. B. **ElementFile**.  
  
6.  Wählen Sie den Pfeil neben **Projektname**, wählen Sie den Namen des nicht-SharePoint-Projektelements aus, und wählen Sie dann die **OK** Schaltfläche.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Vorgehensweise: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  