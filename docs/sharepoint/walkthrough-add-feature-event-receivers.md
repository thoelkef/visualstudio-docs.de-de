---
title: "Exemplarische Vorgehensweise: Hinzuf&#252;gen von Funktionsereignisempf&#228;ngern"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Erweiterte Tools zum Packen"
  - "SharePoint-Entwicklung in Visual Studio, Ereignisempfänger"
  - "SharePoint-Entwicklung in Visual Studio, Funktionsereignisempfänger"
ms.assetid: fbd44c33-2c27-4d57-abca-21cddc16fbc3
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Exemplarische Vorgehensweise: Hinzuf&#252;gen von Funktionsereignisempf&#228;ngern
  Funktionsereignisempfänger sind Methoden, die ausgeführt werden, wenn eines der folgenden funktionsbezogenen Ereignisse in SharePoint eintritt:  
  
-   Eine Funktion wird installiert.  
  
-   Eine Funktion wird aktiviert.  
  
-   Eine Funktion wird deaktiviert.  
  
-   Eine Funktion wird entfernt.  
  
 In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einer Funktion in einem SharePoint\-Projekt ein Ereignisempfänger hinzugefügt wird.  Die folgenden Aufgaben werden veranschaulicht:  
  
-   Erstellen eines leeren Projekts mit einem Funktionsereignisempfänger.  
  
-   Behandeln der **FeatureDeactivating**\-Methode.  
  
-   Hinzufügen einer Ankündigung zur Liste Ankündigungen mithilfe des SharePoint\-Projektobjektmodells.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Erstellen eines Projekts vom Typ Funktionsereignisempfänger  
 Erstellen Sie zunächst ein Projekt, das den Funktionsereignisempfänger enthalten soll.  
  
#### So erstellen Sie ein Projekt mit einem Funktionsereignisempfänger  
  
1.  Klicken Sie auf der Menüleiste **Neu**, **Projekt**, **Datei**, um das Dialogfeld **Neues Projekt** anzuzeigen.  
  
2.  Erweitern Sie den Knoten **SharePoint** entweder unter **Visual C\#** oder **Visual Basic**, und wählen Sie den Knoten **2010** aus.  
  
3.  Im Bereich **Vorlagen** wählen Sie die Vorlage **SharePoint 2010\-Projekt** aus.  
  
     Sie verwenden diesen Projekttyp für Funktionsereignisempfänger vorgesehen, da diese keine Projektvorlage aufweisen.  
  
4.  Im Feld **Name** geben Sie FeatureEvtTest ein und dann die Schaltfläche **OK**, um den **Assistent zum Anpassen von SharePoint** anzuzeigen.  
  
5.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** geben Sie die URL für die SharePoint\-Webserversite, der Sie das neue benutzerdefinierte Feldelement hinzufügen möchten, oder verwenden Sie den Standardspeicherort \(http:\/\/\<*system name*\>\/\).  
  
6.  Wählen Sie im Abschnitt **Wie lautet die Vertrauensebene für diese SharePoint\-Lösung?** das Optionsfeld **Als Farmlösung bereitstellen** aus.  
  
     Weitere Informationen über Sandkastenlösungen im Vergleich zu Farmlösungen finden Sie in [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wählen Sie die Schaltfläche **Fertig stellen** aus, und beachten Sie, dass eine Funktion, die dem Namen Feature1 wird, unter dem Knoten **Funktionen** wird.  
  
## Hinzufügen eines Ereignisempfängers zur Funktion  
 Fügen Sie der Funktion danach einen Ereignisempfänger hinzu, und fügen Sie Code hinzu, der ausgeführt wird, wenn die Funktion deaktiviert wird.  
  
#### So fügen Sie der Funktion einen Ereignisempfänger hinzu  
  
1.  Öffnen Sie das Kontextmenü für den Knoten Funktionen, und wählen Sie dann **Funktion hinzufügen**, um eine Funktion zu erstellen.  
  
2.  unter dem Knoten **Funktionen** öffnen Sie das Kontextmenü für **Feature1**, und wählen Sie dann **Ereignisempfänger hinzufügen**, um der Funktion einen Ereignisempfänger hinzuzufügen.  
  
     Hiermit wird unter Feature1 eine Codedatei hinzugefügt.  In diesem Fall lautet der Name entweder Feature1.EventReceiver.cs oder Feature1.EventReceiver.vb, abhängig von der Entwicklungssprache des Projekts.  
  
3.  Wenn das Projekt in [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] geschrieben ist, fügen Sie folgenden Code am Anfang des Ereignisempfängers hinzu, wenn er nicht bereits vorhanden ist:  
  
     [!code-csharp[SP_FeatureEvt#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  Die Ereignisempfängerklasse enthält einige auskommentierte Methoden, die als Ereignisse fungieren.  Ersetzen Sie die **FeatureDeactivating**\-Methode durch Folgendes:  
  
     [!code-csharp[SP_FeatureEvt#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_featureevt/cs/features/feature1/feature1.eventreceiver.cs#2)]
     [!code-vb[SP_FeatureEvt#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_featureevt/vb/features/feature1/feature1.eventreceiver.vb#2)]  
  
## Testen des Funktionsereignisempfängers  
 Deaktivieren Sie dann die Funktion, um zu testen, ob die **FeatureDeactivating**\-Methode eine Ankündigung in der SharePoint\-Liste "Ankündigungen" ausgibt.  
  
#### So testen Sie den Funktionsereignisempfänger  
  
1.  Legen Sie den Wert der Eigenschaft **Aktive Bereitstellungskonfiguration** des Projekts auf **Keine Aktivierung** fest.  
  
     Das Festlegen dieser Eigenschaft verhindert, dass die Funktion in SharePoint aktiviert wird, und ermöglicht Ihnen das Debuggen von Funktionsereignisempfängern.  Weitere Informationen finden Sie unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Wählen Sie den Schlüssel **F5**, um das Projekt auszuführen und in SharePoint bereitzustellen.  
  
3.  Am oberen Rand der SharePoint\-Webseite öffnen Sie das Menü **Websiteaktionen**, und wählen Sie dann **Websiteeinstellungen** aus.  
  
4.  unter dem Abschnitt **Websiteaktionen** der Seite **Websiteeinstellungen**, wählen Sie den Link **Websitefeatures verwalten** aus.  
  
5.  Auf der Seite **Funktionen** wählen Sie die Schaltfläche **Aktivieren** neben der Funktion **FeatureEvtTest Feature1** aus.  
  
6.  Auf der Seite **Funktionen** wählen Sie die Schaltfläche **Deaktivieren** neben der Funktion **FeatureEvtTest Feature1** aus, und wählen Sie dann den **Dieses Feature deaktivieren** Bestätigungslink, um die Funktion zu deaktivieren.  
  
7.  Wählen Sie die Schaltfläche **Startseite** aus.  
  
     Beachten Sie, dass in der Liste **Ankündigungen** eine Ankündigung angezeigt wird, nachdem die Funktion deaktiviert wurde.  
  
## Siehe auch  
 [Gewusst wie: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  