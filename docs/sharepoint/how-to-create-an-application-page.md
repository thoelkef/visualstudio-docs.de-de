---
title: 'Vorgehensweise: Erstellen einer Anwendungsseite | Microsoft-Dokumentation'
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eefbb12584cdff2bb32b9d4406c916969ec435c4
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118860"
---
# <a name="how-to-create-an-application-page"></a>Gewusst wie: Erstellen einer Anwendungsseite
  Sie können einer ASP.NET-Webseite für eine oder mehrere SharePoint-Websites erstellen. In SharePoint werden diese Seiten Anwendungsseiten bezeichnet. Im Gegensatz zu einer Webseite enthält eine Anwendungsseite Code, der hinter der Seite ausgeführt wird. Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>So erstellen Sie eine Anwendungsseite  
  
1.  Öffnen oder erstellen Sie in Visual Studio ein SharePoint-Projekt.  
  
     Weitere Informationen finden Sie unter [SharePoint-Projekt und Projekt Elementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.  
  
3.  Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.  
  
4.  In der **neues Element hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Element.  
  
5.  Wählen Sie in der Liste der SharePoint-Vorlagen, **Anwendungsseite**.  
  
6.  In der **Namen** Feld Geben Sie einen Namen für die Seite "Anwendung", und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Visual Studio fügt dem Projekt mehrere Ordner und Dateien hinzu. Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     In der **Quelle** Ansicht des Visual Web Developer-Designers die Auslagerungsdatei von ASP.NET wird angezeigt. Sie können die Seite entwerfen, durch das Hinzufügen von Steuerelementen aus der **Toolbox** und platzieren sie auf den Platzhalter für Inhalte. Weitere Informationen finden Sie unter [Quellansicht, Webseiten-Designer](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Wenn Sie die Steuerelementereignisse behandeln möchten, fügen Sie Code hinzu, um die Codedatei für die Seite "Anwendung".  
  
     Die Codedatei wird angezeigt, wenn Sie den Knoten für die Auslagerungsdatei ASP.NET erweitern, und verfügt über eine *cs* oder *vb* Erweiterung, abhängig von der Sprache des Projekts. Ein End-to-End-Beispiel zum Erstellen einer Anwendungsseite, finden Sie unter [Exemplarische Vorgehensweise: erstellen eine SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
