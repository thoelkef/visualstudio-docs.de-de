---
title: "Gewusst wie: Hinzuf&#252;gen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt | Microsoft Docs"
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
  - "VS.SharePointTools.BDC.ImportDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint-Entwicklung in Visual Studio], Importieren eines Modells"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Entfernen eines Modells"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Importieren eines Modells"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Wiederverwenden eines Modells"
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Gewusst wie: Hinzuf&#252;gen einer vorhandenen BDC-Modelldatei zu einem SharePoint-Projekt
  Sie können ein Business Data Connectivity \(BDC\)\- \- Modell anpassen, packen und erneut bereitstellen, indem Sie Visual Studio verwenden, um der Modelldatei \(.bdcm\) jedem SharePoint\-Farmprojekt hinzuzufügen.  Weitere Informationen finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### Um einer BDC\-Modelldatei fügen Sie einem SharePoint\-Projekt  
  
1.  Wählen Sie im **Projektmappen\-Explorer** den Ordner für ein SharePoint\-Projekt aus.  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **Vorhandenes Element hinzufügen** aus.  
  
3.  Im Dialogfeld **Vorhandenes Element hinzufügen** navigieren Sie zum Speicherort der Modelldefinitionsdatei, die Sie dem Projekt hinzufügen möchten, wählen Sie die Datei und wählen Sie dann die Schaltfläche **Hinzufügen**.  
  
     Wenn das Modell kein *Branchen \(lob\)\- System vom Typ .net Assembly* definiert, wird das Dialogfeld **.NET\-Assembly\-LobSystem hinzufügen**.  
  
4.  Wenn das Dialogfeld angezeigt wird, führen Sie einen der folgenden Schritte aus:  
  
    -   Wenn Sie benutzerdefinierten Code schreiben und einen Designer verwenden möchten, um die Metadaten für das importierte Modell zu definieren, wählen Sie die Schaltfläche **Ja** aus, nennen Sie das System, und wählen Sie dann die Schaltfläche **OK** aus.  
  
    -   Andernfalls wählen Sie die Schaltfläche **Nein**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Das Element **Business Data Connectivity\-Modell** wird dem Projekt hinzugefügt.  
  
## Siehe auch  
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Gewusst wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Gewusst wie: Einfügen einer benutzerdefinierten Assembly in eine BDC-Funktion](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  