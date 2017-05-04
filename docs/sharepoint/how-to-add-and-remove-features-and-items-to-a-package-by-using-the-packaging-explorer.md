---
title: "Gewusst wie: Hinzuf&#252;gen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Explorer | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.PackagingExplorer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Pakete"
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Gewusst wie: Hinzuf&#252;gen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Explorer
  Um ein Paket so zu konfigurieren, dass SharePoint\-Elemente und \-Funktionen bereitgestellt werden, können Sie den Paket\-Explorer verwenden.  Sie können die SharePoint\-Projektelemente und \-Funktionen innerhalb der WSP\-Datei anpassen.  
  
 Alternativ können Sie den Paket\-Designer zum Anzeigen und Neuanordnen der Funktionen verwenden, um die Aktivierungsreihenfolge zu ändern.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## Öffnen des Paket\-Explorers  
 Sie können den Paket\-Explorer mithilfe des folgenden Verfahrens öffnen, wenn die Visual Studio\-Projektmappe mindestens ein SharePoint\-Projekt enthält.  Alternativ wird der Paket\-Explorer automatisch geöffnet, wenn Sie eine Funktion oder den Paket\-Designer anzeigen.  Nachdem Sie alle Funktion und Paket\-Designer geschlossen haben, wird der Paket\-Explorer ebenfalls geschlossen.  
  
#### So öffnen Sie den Paket\-Explorer  
  
1.  Klicken Sie auf der Menüleiste **Weitere Fenster**, **Paket\-Explorer**, **Ansicht** aus.  
  
     Im **Paket\-Explorer** wird **Werkzeugkasten** angezeigt.  
  
## Hinzufügen einer Funktion zu einem Paket  
 Sie können einem Paket mit dem Paket\-Explorer neue und vorhandene Funktionen hinzufügen.  
  
#### So fügen Sie eine SharePoint\-Funktion hinzu  
  
1.  Öffnen Sie **Paket\-Explorer**, öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Funktion hinzufügen** aus.  
  
#### So verschieben Sie eine vorhandene SharePoint\-Funktion  
  
1.  Öffnen Sie **Paket\-Explorer**, und führen Sie dann einen der folgenden Schritte aus:  
  
    -   Ziehen Sie eine **Funktion** aus einem Projekt in ein anderes Projekt.  
  
    -   Öffnen Sie das Kontextmenü für eine Funktion, wählen Sie **Ausschneiden** aus, öffnen Sie das Kontextmenü für das Projekt, dessen Funktion verschieben möchten, und wählen Sie dann **Einfügen** aus.  
  
    > [!NOTE]  
    >  Verwenden Sie diese Prozedur, wenn Sie mehr als ein SharePoint\-Projekt in der Projektmappe vorhanden sind.  
  
## Überprüfen einer Funktion oder eines Pakets  
 Sie können potenzielle Probleme der SharePoint\-Funktionen und \-Pakete identifizieren, indem Sie die Dateien überprüfen.  Warnungen und Fehler werden im Ausgabefenster und im Fenster Fehlerliste angezeigt.  
  
#### So überprüfen Sie eine SharePoint\-Funktion oder ein SharePoint\-Paket  
  
1.  Öffnen Sie den **Paket\-Explorer**.  
  
2.  Öffnen Sie das Kontextmenü für eine Funktion oder ein Paket, und wählen Sie dann **Überprüfen** aus.  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  