---
title: "Gewusst wie: Hinzuf&#252;gen einer Ressourcendatei"
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
  - "Ressourcendateien [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Ressourcendateien"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Gewusst wie: Hinzuf&#252;gen einer Ressourcendatei
  Die Befehle zum Hinzufügen von Ressourcendateien sind im Kontextmenü des Projektmappenknotens und der Funktionsknoten im Projektmappen\-Explorer enthalten.  Weitere Informationen finden Sie unter [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md).  
  
### So fügen Sie einer SharePoint\-Lösung eine globale Ressourcendatei hinzu  
  
1.  Öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine SharePoint\-Lösung.  
  
2.  Wählen Sie im **Projektmappen\-Explorer** einen SharePoint\-Projektknoten und dann, auf der Menüleiste, **Projekt** auswählen, **Neues Element hinzufügen** aus.  
  
3.  Im Dialogfeld **Neues Element hinzufügen** wählen Sie die Vorlage **Globale Ressourcendatei** aus, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
    > [!NOTE]  
    >  Die Projektelementvorlage "Globale Ressourcendatei" wird nur angezeigt, wenn ein SharePoint\-Projektelement ausgewählt wird.  
  
4.  Im Dialogfeld **Ressource hinzufügen** wählen Sie als Kultur für die Ressourcendatei aus, z Englisch \(USA\).  
  
     Dieser Schritt fügt der Projektmappe eine globale Ressourcendatei im Format Resource*x***.***culture***.**resx, z. B. Resource1.en\-US.resx, hinzu.  
  
5.  Wenn **Ressourcen\-Editor** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] geöffnet wird, fügen Sie der Ressourcendatei Ressourcen hinzu.  
  
### So fügen Sie einer SharePoint\-Funktion eine Funktionsressourcendatei hinzu  
  
1.  Wenn die SharePoint\-Lösung in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nicht bereits geöffnet ist, öffnen Sie die Projektmappe.  
  
2.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Namen einer Funktion im Knoten **Funktionen**, und wählen Sie dann **Funktionsressource hinzufügen** aus.  
  
     In diesem Schritt wird der Funktion eine Ressourcendatei im Format *ResourceFileName***.***culture***.**resx, z. B. Feature1.en\-US.resx, hinzugefügt.  
  
3.  Wenn **Ressourcen\-Editor** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] geöffnet wird, fügen Sie der Ressourcendatei Ressourcen hinzu.  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  