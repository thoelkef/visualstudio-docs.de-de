---
title: "Gewusst wie: Erstellen eines BDC-Modells | Microsoft Docs"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Erstellen eines Modells"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Erstellen eines Modells"
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Erstellen eines BDC-Modells
  Sie können ein BDC \(Business Data Connectivity\)\-Modell erstellen, indem Sie die Vorlage für diesen Vorlagentyp verwenden und dann das Modell zu einem SharePoint\-Projekt hinzufügen.  Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  Weitere Informationen zum Entwerfen des Modells finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### So erstellen Sie ein BDC\-Projekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
    > [!NOTE]  
    >  Wenn die IDE auf die Verwendung der Visual Basic\-Entwicklungseinstellungen festgelegt ist, wählen Sie im Menü **Datei** ein **Neues Projekt** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Wählen Sie entweder unter **Visual Basic** oder **Visual C\#** entweder **Office\/SharePoint** oder **SharePoint\-Lösungen** aus.  
  
3.  Im Bereich **Vorlagen** wählen Sie das Element **SharePoint 2013 – Leeres Projekt** und anschließen die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird geöffnet.  
  
4.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** geben Sie die URL der SharePoint\-Website auf dem lokalen Computer an, wählen Sie das Optionsfeld **Als Farmlösung bereitstellen** und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
     Sie werden das Modell auf der von Ihnen angegebenen SharePoint\-Website testen.  
  
    > [!IMPORTANT]  
    >  Sie müssen das Projekt als Farmlösung bereitstellen, da BDC\-Modelle ausschließlich Farmlösungen unterstützen.  
  
     Ein leeres SharePoint\-Projekt wurde erstellt.  
  
5.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
6.  Im Dialogfeld **Neues Element hinzufügen** wählen Sie den Knoten **Office\/SharePoint** aus.  
  
7.  Wählen Sie in der Liste der SharePoint\-Vorlagen **Business Data Connectivity\-Modell \(nur Farmlösung\)** aus.  
  
8.  Geben Sie im Feld **Name** einen Namen für das BDC\-Modell an, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Dem Projekt wird ein **Business Data Connectivity\-Modell** hinzugefügt.  Standardmäßig wird das Modell im BDC\-Designer angezeigt.  Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## Siehe auch  
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Gewusst wie: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Gewusst wie: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  