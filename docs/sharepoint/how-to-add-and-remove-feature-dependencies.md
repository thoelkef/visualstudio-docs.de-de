---
title: "Gewusst wie: Hinzuf&#252;gen und Entfernen von Funktionsabh&#228;ngigkeiten"
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
  - "MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW"
  - "VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Funktionen"
ms.assetid: 2b34c8d9-c975-4fe9-b8e0-52db4a6014ea
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Gewusst wie: Hinzuf&#252;gen und Entfernen von Funktionsabh&#228;ngigkeiten
  Die SharePoint\-Funktion hängt hinsichtlich Funktionalität oder Daten möglicherweise von anderen Funktionen ab.  In diesen Fällen können Sie diese anderen Funktionen als Abhängigkeiten für die Funktion kennzeichnen.  Auf diese Weise stellt der SharePoint\-Server sicher, dass abhängige Funktionen aktiviert werden, bevor die betreffende Funktion aktiviert wird.  
  
## Hinzufügen von Abhängigkeiten  
 Sie können in der Projektmappe weitere Funktionen als Abhängigkeiten hinzufügen.  Auf diese Weise können Sie sicherstellen, dass erforderliche Funktionen installiert und aktiviert werden, bevor die betreffende Funktion installiert wird.  
  
#### So fügen Sie in der Projektmappe eine Abhängigkeit für eine Funktion hinzu  
  
1.  Öffnen Sie den Funktions\-Designer, erweitern Sie den Knoten **Funktionsaktivierungsabhängigkeiten**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
2.  Im Dialogfeld **Funktionsaktivierungsabhängigkeiten hinzufügen** wählen Sie das Optionsfeld **Abhängigkeit von Funktionen in der Projektmappe hinzufügen**, den Titel der Funktion, die Sie als Abhängigkeit hinzufügen möchten, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Sie können mehrere Funktionen hinzufügen, indem Sie auswählen mehrere Titel zum Auswählen der STRG\-TASTE.  
  
## Hinzufügen von benutzerdefinierten Abhängigkeiten  
 Sie können Funktionen hinzufügen, die bereits auf einem SharePoint\-Server als Abhängigkeit bereitgestellt wurden.  Auf diese Weise wird im SharePoint\-Aktivierungsvorgang durch eine entsprechende Überprüfung sichergestellt, dass alle abhängigen Funktionen aktiviert sind, bevor die Funktion installiert wird.  
  
#### So fügen Sie eine Abhängigkeit anhand der Funktions\-ID hinzu  
  
1.  Öffnen Sie den Funktions\-Designer, erweitern Sie den Knoten **Funktionsaktivierungsabhängigkeiten**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
2.  Im Dialogfeld **Funktionsaktivierungsabhängigkeiten hinzufügen** wählen Sie das Optionsfeld **Benutzerdefinierte Abhängigkeit hinzufügen** aus.  
  
3.  Im Textfeld **Funktions\-ID** die GUID für die Funktion, die Sie als Aktivierungsabhängigkeit markieren möchten, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
## Bearbeiten von benutzerdefinierten Abhängigkeiten  
 Sie können zuvor hinzugefügte benutzerdefinierte Abhängigkeiten bearbeiten.  Abhängige Funktionen in der Projektmappe können jedoch nur entfernt und nicht bearbeitet werden.  
  
#### So ändern Sie in der Projektmappe eine Abhängigkeit für eine Funktion  
  
1.  Öffnen Sie den Funktions\-Designer, und dann den Knoten **Funktionsaktivierungsabhängigkeiten**.  
  
2.  Wählen Sie den Namen der Funktion, die Sie bearbeiten möchten, und dann die Schaltfläche **Bearbeiten** aus.  
  
3.  Im Dialogfeld **Benutzerdefinierte Funktionsaktivierungsabhängigkeit bearbeiten** Ändern Sie den Titel, kennzeichnen Sie ID oder Beschreibung, und wählen Sie dann die Schaltfläche **Senden** aus.  
  
## Entfernen von Abhängigkeiten  
  
#### So entfernen Sie in der Projektmappe eine Abhängigkeit für eine Funktion  
  
1.  im Funktions\-Designer erweitern Sie den Knoten **Funktionsaktivierungsabhängigkeiten**, den Namen der Funktion, die Sie entfernen möchten, und wählen Sie dann die Schaltfläche **Entfernen**.  
  
## Siehe auch  
 [Erstellen von SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md)   
 [Gewusst wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Gewusst wie: Hinzufügen und Entfernen von Elementen in SharePoint-Funktionen](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  