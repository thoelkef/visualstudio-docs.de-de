---
title: 'Vorgehensweise: erstellen eine Anwendungsseite | Microsoft Docs'
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 75c896f101f1eb0a11884b492ba559045a1dd180
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-application-page"></a>Gewusst wie: Erstellen einer Anwendungsseite
  Sie können eine ASP.NET-Webseite für eine oder mehrere SharePoint-Websites erstellen. In SharePoint werden diese Seiten Anwendungsseiten bezeichnet. Im Gegensatz zu einer Websiteseite enthält eine Anwendungsseite Code, der hinter der Seite ausgeführt wird. Weitere Informationen finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>So erstellen Sie eine Anwendungsseite  
  
1.  Öffnen oder erstellen Sie in Visual Studio ein SharePoint-Projekt.  
  
     Weitere Informationen finden Sie unter [SharePoint-Projekte und Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.  
  
3.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
4.  In der **neues Element hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Element.  
  
5.  Wählen Sie in der Liste der SharePoint-Vorlagen **Seite "Anwendung"**.  
  
6.  In der **Namen** Feld Geben Sie einen Namen für die Seite "Anwendung", und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Visual Studio fügt dem Projekt mehrere Ordner und Dateien hinzu. Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     In der **Quelle** Ansicht des Visual Web Developer-Designers, die Auslagerungsdatei von ASP.NET wird angezeigt. Sie können die Seite entwerfen, durch das Hinzufügen von Steuerelementen aus dem **Toolbox** und sie für Inhaltsplatzhalter platziert werden. Weitere Informationen finden Sie unter [Quellansicht, Webseiten-Designers](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Wenn Sie die Steuerelementereignisse behandeln möchten, fügen Sie Code hinzu, um die Codedatei für die Seite "Anwendung".  
  
     Die Codedatei wird angezeigt, wenn Sie den Knoten für die Auslagerungsdatei ASP.NET zu erweitern und hat die Erweiterung .cs oder .vb abhängig von der Sprache des Projekts. Ein End-to-End-Beispiel zum Erstellen einer Anwendungsseite finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Anwendungsseite](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  