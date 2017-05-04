---
title: "Gewusst wie: Erstellen eines Ereignisempf&#228;ngers f&#252;r eine bestimmte Listeninstanz | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Ereignisempfänger [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Ereignisempfänger"
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Gewusst wie: Erstellen eines Ereignisempf&#228;ngers f&#252;r eine bestimmte Listeninstanz
  Ein Listeninstanzereignisempfänger reagiert auf Ereignisse, die in einer beliebigen Instanz einer Listendefinition auftreten.  Obwohl die Ereignisempfängervorlage die Zielgruppenadressierung einer bestimmten Listeninstanz nicht aktiviert, können Sie einen auf eine Listendefinition beschränkten Ereignisempfänger ändern, um auf Ereignisse in einer bestimmten Listeninstanz zu reagieren.  
  
 Ersetzen Sie in der Datei "Elements.xml" für den Ereignisempfänger `ListTemplateId` durch `ListUrl`, und fügen Sie die URL der Listeninstanz hinzu, um eine bestimmte Listeninstanz als Ziel festzulegen.  
  
## Erstellen eines Listeninstanzereignisempfängers  
 Die folgenden Schritte zeigen, wie ein Listenelementereignisempfänger geändert wird, um nur auf Ereignisse, die in einer benutzerdefinierten Ankündigungslisteninstanz auftreten, zu reagieren.  
  
#### So ändern Sie einen Ereignisempfänger, der auf eine bestimmte Listeninstanz reagieren soll  
  
1.  In einem Browser öffnen Sie die SharePoint\-Website.  
  
2.  im Navigationsbereich Link **Listen**.  
  
3.  Auf der Seite **Gesamter Websiteinhalt** Wählen Sie den Link **Erstellen** aus.  
  
4.  Im Dialogfeld **Erstellen** wählen Sie den Typ **Ankündigungen** aus, nennen Sie die Ankündigung "TestAnnouncements", und wählen Sie dann die Schaltfläche **Erstellen** aus.  
  
5.  Erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Ereignisempfängerprojekt.  
  
6.  In der Liste **Welchen Typ soll der Ereignisempfänger aufweisen?** wählen Sie **Listenelementereignisse** aus.  
  
    > [!NOTE]  
    >  Sie können auch einen beliebigen anderen Ereignisempfänger auswählen, der auf eine Listendefinition beschränkt ist, z. B. **Listen\-E\-Mail\-Ereignisse** oder **Listenworkflowereignisse**.  
  
7.  In der Liste **Welche Element soll als Ereignisquelle dienen?** wählen Sie **Ankündigungen** aus.  
  
8.  In der Liste **Die folgenden Ereignisse behandeln** aktivieren Sie das Kontrollkästchen **Ein Element wird hinzugefügt.** und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
9. In **Projektmappen\-Explorer** unter "EventReceiver1", öffnen Sie Elements.xml.  
  
     Der Ereignisempfänger verweist gerade die Ankündigungenlistendefinition, indem er die folgende Zeile:  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Ändern Sie diese Zeile in den folgenden Text:  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Dies weist den Ereignisempfänger an, nur auf Ereignisse, die in der neuen, von Ihnen gerade erstellten Ankündigungsliste **TestAnnouncements** auftreten, zu reagieren.  Sie können das `ListURL`\-Attribut ändern, um auf eine beliebige Listeninstanz auf dem SharePoint\-Server zu verweisen.  
  
10. Öffnen Sie die Codedatei für den Ereignisempfänger, und setzen Sie einen Haltepunkt in der ItemAdding\-Methode.  
  
11. Drücken Sie die F5\-TASTE, um die Projektmappe zu erstellen und auszuführen.  
  
12. In SharePoint Wählen Sie den Link **TestAnnouncements** im Navigationsbereich aus.  
  
13. Wählen Sie den Link **Neue Ankündigung hinzufügen** aus.  
  
14. Geben Sie einen Titel für die Ankündigung ein, und wählen Sie dann die Schaltfläche **Speichern** aus.  
  
     Beachten Sie, dass der Haltepunkt erreicht wird, wenn der benutzerdefinierten Ankündigungsliste das neue Element hinzugefügt wird.  
  
15. Drücken Sie die F5\-TASTE, um fortzusetzen.  
  
16. im Navigationsbereich Wählen Sie den Link **Listen**, und dann den Link **Ankündigungen** aus.  
  
17. Fügen Sie eine neue Ankündigung hinzu.  
  
     Beachten Sie, dass der Ereignisempfänger nicht bei der neuen Ankündigung ausgelöst wird, da der Empfänger so konfiguriert ist, dass er nur auf Ereignisse in der benutzerdefinierten Ankündigungslisteninstanz **TestAnnouncements** reagiert.  
  
## Siehe auch  
 [Gewusst wie: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  