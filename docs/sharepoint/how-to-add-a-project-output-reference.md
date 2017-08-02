---
title: "Gewusst wie: Hinzuf&#252;gen einer Projektausgabereferenz"
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
  - "Projektausgabeverweise [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Erweiterte Tools zum Packen"
  - "SharePoint-Entwicklung in Visual Studio, Projektausgabeverweise"
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Hinzuf&#252;gen einer Projektausgabereferenz
  Wenn Sie SharePoint\-fremde Projektassemblys \(oder XAP\-Dateien in Silverlight\-Projekten\) in SharePoint bereitstellen möchten, fügen Sie sie als Projektausgabeverweis hinzu.  
  
 Bei diesem Prozess wird eine Lösungsbuildabhängigkeit zwischen den beiden Projekten erstellt.  Projektausgabeverweisen zugeordnete Projekte werden erstellt, bevor das SharePoint\-Projekt erstellt und bereitgestellt wird.  
  
### So fügen Sie eine Projektausgabereferenz hinzu  
  
1.  Laden Sie eine Lösung, die mindestens ein SharePoint\-Projekt und ein SharePoint\-fremdes Projekt enthält.  
  
2.  Wählen Sie im **Projektmappen\-Explorer** ein Element im SharePoint\-Projektknoten aus.  
  
3.  Im Fenster **Eigenschaften** wählen Sie die Eigenschaft **Projektausgabeverweis**, und wählen Sie dann die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](~/sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")\) neben sie aus.  
  
4.  Im Dialogfeld **Projektausgabeverweis** wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
5.  Im Eigenschaftenbereich wählen Sie den Pfeil neben der Eigenschaft **Bereitstellungstyp**, und wählen Sie einen geeigneten Wert für das SharePoint\-fremde Element, das Sie verweisen, wie **ElementFile** aus.  
  
6.  Wählen Sie den Pfeil neben **Projektname**, wählen Sie den Namen des SharePoint\-fremden Namen, und wählen Sie dann die Schaltfläche **OK** aus.  
  
## Siehe auch  
 [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Gewusst wie: Markieren von Steuerelementen als sichere Steuerelemente](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  