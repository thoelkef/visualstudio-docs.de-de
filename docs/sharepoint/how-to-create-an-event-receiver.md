---
title: "Gewusst wie: Erstellen eines Ereignisempf&#228;ngers | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.EventReceiver"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Ereignisempfänger [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Ereignisempfänger"
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Gewusst wie: Erstellen eines Ereignisempf&#228;ngers
  Mithilfe *Ereignisempfänger* erstellen, können Sie reagieren, wenn ein Benutzer auf SharePoint\-Elemente wie Listen oder Listenelemente interagiert.  Code kann beispielsweise in einen Ereignisempfänger ausgelöst werden, wenn ein Benutzer der Kalender geändert oder ein Name aus der Kontaktliste gelöscht wird.  Mit diesem Thema folgen, können Sie erfahren, wie ein Ereignisempfänger einer Listeninstanz.  
  
 Um diese Schritte durchzuführen, müssen Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und die unterstützten Editionen von Windows und SharePoint installiert haben.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  Da dieses Beispiel ein SharePoint\-Projekt erfordert, müssen Sie das Verfahren im Thema auch [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) abgeschlossen haben.  
  
## Hinzufügen eines Ereignisempfängers  
 Das Projekt, das Sie in [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) erstellt haben, schließt benutzerdefinierte Websitespalten, eine benutzerdefinierte Liste und einen Inhaltstyp.  In der folgenden Prozedur Erweitern Sie das Projekt, indem Sie ein einfacher Ereignishandler \(ein Ereignisempfänger\) einer Listeninstanz hinzu, um anzuzeigen, wie Ereignisse behandelt, die in SharePoint\-Elemente wie Listen auftreten.  
  
#### So fügen Sie der Listeninstanz einen Ereignisempfänger hinzu  
  
1.  Öffnen Sie das Projekt, das Sie in [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) erstellt haben.  
  
2.  Wählen Sie im **Projektmappen\-Explorer** den SharePoint\-Projektknoten aus, der dem Namen **Klinik**.  
  
3.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
4.  Entweder unter **Visual C\#** oder den Knoten **Visual BasicSharePoint**, und wählen Sie das Element **2010** aus.  
  
5.  Im Bereich **Vorlagen** wählen Sie **Ereignisempfänger** aus, nennen Sie ihn TestEventReceiver1, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
6.  In der Liste **Welchen Typ soll der Ereignisempfänger aufweisen?** wählen Sie **Listenelementereignisse** aus.  
  
7.  In der Liste **Welche Element soll als Ereignisquelle dienen?** wählen Sie **Patienten \(Klinik\\Patienten\)** aus.  
  
8.  In der Liste **Die folgenden Ereignisse behandeln** wählen Sie das Kontrollkästchen neben **Ein Element wurde hinzugefügt.**, und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
     Die Codedatei des neuen Ereignisempfängers enthält eine einzelne Methode, die `ItemAdded` genannt wird.  Im nächsten Schritt fügen Sie dieser Methode Code hinzu, sodass jeder Kontakt Scott braun standardmäßig ".  
  
9. Ersetzen Sie die vorhandene `ItemAdded`\-Methode durch folgenden Code, und wählen Sie dann die Taste F5 aus:  
  
     [!code-csharp[SP_EventReceiver#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_eventreceiver/CS/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_eventreceiver/VB/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Der Code wird ausgeführt und die SharePoint\-Website im Webbrowser angezeigt.  
  
10. Klicken Sie auf der Schnellstartleiste auf den Link **Patienten**, und dann den Link **Neues Element hinzufügen** aus.  
  
     Das Eingabeformular für neue Elemente wird geöffnet.  
  
11. Geben Sie Daten in den Feldern ein, und wählen Sie dann die Schaltfläche **Speichern** aus.  
  
     Nachdem Sie die Schaltfläche **Speichern** auswählen, die der Spalte **Patientenname** Updates automatisch in den Namen Scott braun.  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  