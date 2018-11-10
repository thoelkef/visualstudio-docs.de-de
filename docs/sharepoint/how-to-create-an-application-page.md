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
ms.openlocfilehash: 9f390ddf14925b43f1aa1d9e79db05e2aa64f234
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296202"
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
  
     In der **Quelle** Ansicht des Visual Web Developer-Designers die Auslagerungsdatei von ASP.NET wird angezeigt. Sie können die Seite entwerfen, durch das Hinzufügen von Steuerelementen aus der **Toolbox** und platzieren sie auf den Platzhalter für Inhalte. Weitere Informationen finden Sie unter [Quellansicht, Webseiten-Designer](/previous-versions/aspnet/ms178154\(v\=vs.100\)).  
  
7.  Wenn Sie die Steuerelementereignisse behandeln möchten, fügen Sie Code hinzu, um die Codedatei für die Seite "Anwendung".  
  
     Die Codedatei wird angezeigt, wenn Sie den Knoten für die Auslagerungsdatei ASP.NET erweitern, und verfügt über eine *cs* oder *vb* Erweiterung, abhängig von der Sprache des Projekts. Ein End-to-End-Beispiel zum Erstellen einer Anwendungsseite, finden Sie unter [Exemplarische Vorgehensweise: erstellen eine SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
