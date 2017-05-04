---
title: "Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei | Microsoft Docs"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Lokalisieren von Zeichenfolgen"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Eigenschaften"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Ressourcendatei"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Ressourcenzeichenfolgen"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Lokalisieren von Zeichenfolgen"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Eigenschaften"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Ressourcendatei"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Ressourcenzeichenfolgen"
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei
  Wenn Sie eine Ressourcendatei verwenden, können Sie lokalisierte Namen angeben, Eigenschaften definieren und Berechtigungsfelsenobjekte anwenden, die in einem Business Data Connectivity \(BDC\)\- \- Modell definiert sind.  Um diese Informationen anzugeben, fügen Sie ein Element **Business Data Connectivity\-Ressource** ein Projekt hinzu das ein Element **Business Data Connectivity\-Modell** enthält.  Geben Sie Namen, Eigenschaften und Berechtigungen an, indem Sie das XML für die Ressourcendatei bearbeiten.  
  
### So fügen Sie einem SharePoint\-Projekt eine BDC\-Ressourcendatei hinzu  
  
1.  Erweitern Sie in **Projektmappen\-Explorer** den Ordner für das SharePoint\-Projekt, und wählen Sie dann den Ordner aus, der das BDC\-Modell enthält.  
  
2.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
3.  Erweitern Sie den Knoten **SharePoint**, und wählen Sie den Knoten **2010** aus.  
  
4.  Im Dialogfeld **Neues Element hinzufügen** wählen Sie **Business Data Connectivity\-Ressourcenelement** aus.  
  
5.  Im Feld **Name** den Namen der Ressourcendatei ein, und wählen Sie anschließend die Schaltfläche **Hinzufügen** aus.  
  
     Ressourcendatei, die der Erweiterung hat, wird dem Projekt hinzugefügt und zum Bearbeiten geöffnet.  
  
6.  Fügen Sie XML hinzu, um die lokalisierten Namen, Eigenschaften sowie die Berechtigungen, die Sie auf das BDC\-Modell anwenden möchten.  
  
     Informationen dazu, wie diese Elemente, finden Sie definiert [Modell und Ressourcendateien](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## Siehe auch  
 [Gewusst wie: Hinzufügen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Gewusst wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Gewusst wie: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  