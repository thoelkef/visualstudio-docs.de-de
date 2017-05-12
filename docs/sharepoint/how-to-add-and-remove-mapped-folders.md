---
title: "Gewusst wie: Hinzuf&#252;gen und Entfernen zugeordneter Ordner"
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
  - "VS.SharePointTools.Project.MappedFolder"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Zugeordnete Ordner [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Zugeordnete Ordner"
ms.assetid: 115c8b00-7d4c-4fbe-b42c-e82dca944504
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Gewusst wie: Hinzuf&#252;gen und Entfernen zugeordneter Ordner
  Einige häufig verwendete Ordner in SharePoint, wie Bilder und Layouts, sind tief in die Dateihierarchie eingebettet.  Sie können diese Ordner in einem SharePoint\-Projekt zuordnen, um den Zugriff darauf zu erleichtern.  Zugeordnete Ordner sind Ordner im SharePoint\-Projekt, die dem physikalischen Speicherort der Dateien in der Installation des SharePoint Servers entsprechen.  
  
 Wenn Sie eine SharePoint\-Anwendung bereitstellen, wird der Inhalt des zugeordneten Ordners und aller Unterordner vom Lösungspaket \(.wsp\) auf den Server kopiert, der SharePoint an der angegebenen Position in der SharePoint\-Ordnerstruktur ausführt.  Dieser Speicherort wird von der **Deployment Location**\-Eigenschaft bestimmt, die für den zugeordneten Ordner festgelegt wird.  Alle Unterordner im zugeordneten Ordner sind relativ zum **Deployment Location** des zugeordneten Ordners.  Beachten Sie, dass die Eigenschaft **Deployment Location**, nicht der Name vom zugeordneten Ordner, bestimmt, wo Elemente bereitgestellt werden.  
  
 Sie können einem Projekt zugeordnete Ordner hinzufügen, indem Sie Befehle auf der Menüleiste oder im Kontextmenü für das Projekt verwenden.  Sie können die Befehle **Zugeordneten SharePoint\-Ordner "Bilder" hinzufügen** und **SharePoint\-Ordner "Layouts" hinzufügen** verwenden, diese zugeordneten Ordner hinzuzufügen, die am häufigsten verwendet werden.  Außerdem können Sie einen der anderen verfügbaren SharePoint\-Ordner dem Project zuordnen, indem Sie den Befehl **Zugeordneten SharePoint\-Ordner hinzufügen** im Kontextmenü verwenden und dann den Ordner im Dialogfeld **Zugeordneten SharePoint\-Ordner hinzufügen** angeben.  
  
## Hinzufügen von zugeordneten Ordnern zu einem Projekt  
 Die folgende Prozedur beschreibt, wie zwei zugeordnete Ordner ein visuelles Webpartprojekt hinzufügt.  Um zu starten, erstellen Sie ein visuelles Webpartprojekt.  
  
#### So fügen Sie einem Projekt zugeordnete Ordner hinzu  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  Im Dialogfeld **Neues Projekt** Erweitern Sie entweder **Visual Basic** oder **Visual C\#** Knoten, erweitern Sie den Knoten **Office\/SharePoint**, und wählen Sie den Knoten **SharePoint\-Lösungen** aus.  
  
3.  In der Liste der Projektvorlagen, wählen Sie die Vorlage **Visuelles SharePoint 2013\-Webpart** aus.  
  
4.  Im Feld **Name** geben Sie "TestProject1" ein und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  Im **Assistent zum Anpassen von SharePoint** wählen Sie die Schaltfläche **Fertig stellen**, um die Standardeinstellungen zu erhalten.  
  
6.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten, und klicken Sie auf der Menüleiste, **Projekt** auswählen, **Zugeordneten SharePoint\-Ordner "Bilder" hinzufügen** aus.  
  
     Ein Ordner, der dem Namen **Bilder**, wird im Projekt angezeigt und enthält einen Unterordner, der TestProject1 ".  Dieser zugeordnete Ordner enthält Bilder für das visuelle Webpartprojekt.  
  
7.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten, und klicken Sie auf der Menüleiste, **Projekt** auswählen, **Zugeordneten SharePoint\-Ordner hinzufügen**, um das Dialogfeld anzuzeigen **Zugeordneten SharePoint\-Ordner hinzufügen** aus.  
  
8.  In der Strukturansicht von Ordnern, die zum Zuordnen verfügbar sind, wählen Sie den Ordner **Ressourcen**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Ein Ordner, der dem Namen **Ressourcen**, wird im Projekt.  Dieser Ordner kann Elemente wie Zeichenfolgenressourcendateien speichern.  Unterordner können für das Organisieren des Inhalts eines zugeordneten Ordners nützlich sein, aber sie werden nicht automatisch erstellt, wenn Sie einen zugeordneten Ordner hinzufügen, indem Sie den Befehl **Zugeordneten SharePoint\-Ordner hinzufügen** verwenden.  Um einen Unterordner hinzuzufügen, wählen Sie den Ordner **Ressourcen** und dann, auf der Menüleiste, **Projekt** auswählen, **Neuer Ordner**.  
  
## Ändern des Bereitstellungsspeicherorts eines zugeordneten Ordners  
 Standardmäßig werden zugeordnete Ordner in bestimmten Speicherorten relativ zum SharePoint\-Stamminstallationspfad hinzugefügt, den Token {SharePointRoot} bezeichnet.  Sie können diesen Speicherort jedoch ändern, indem Sie die **Deployment location**\-Eigenschaft des zugeordneten Ordners ändern.  Jeder zugeordnete Ordner verfügt über eine eigene **Deployment location**\-Eigenschaft.  
  
#### So ändern Sie den Bereitstellungsspeicherort eines zugeordneten Ordners  
  
1.  im Projekt, das Sie zuvor erstellt haben, wählen Sie einen zugeordneten Ordner aus.  
  
2.  Im Fenster **Eigenschaften** wählen Sie die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\) in der **Deployment location**\-Eigenschaft aus.  
  
3.  Im Dialogfeld **Zugeordneten SharePoint\-Ordner hinzufügen** zu dem Ordner, dem Sie den zugeordneten Ordner zum Punkt möchten.  
  
4.  Wählen Sie den Knoten, und wählen Sie dann die Schaltfläche **OK** aus.  
  
## Umbenennen oder Entfernen von zugeordneten Ordnern  
  
#### So benennen Sie einen zugeordneten Ordner um oder entfernen diesen  
  
1.  im Projekt, das Sie zuvor erstellt haben, wählen Sie einen zugeordneten Ordner aus.  
  
2.  Um den zugeordneten Ordner umzubenennen, öffnen Sie das Kontextmenü, wählen Sie **Umbenennen** aus, geben Sie den neuen Namen ein, und wählen Sie dann die EINGABETASTE aus.  
  
     Alternativ können Sie den zugeordneten Ordner auswählen, den Sie umbenennen möchten, öffnen das Fenster **Eigenschaften** und legen Sie dann den Wert der **Folder name**\-Eigenschaft auf den neuen Namen.  
  
3.  Um einen zugeordneten Ordner aus dem Projekt zu entfernen, öffnen Sie das Kontextmenü, wählen Sie **Löschen** aus und dann die Schaltfläche **OK** im Dialogfeld um den Löschvorgang zu bestätigen.  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  