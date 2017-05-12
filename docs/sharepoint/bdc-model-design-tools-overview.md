---
title: "&#220;bersicht &#252;ber Entwurfstools f&#252;r BDC-Modelle"
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
  - "VS.SharePointTools.BDC.Method_Details"
  - "VS.SharePointTools.BDC.Explorer"
  - "VS.SharePointTools.BDC.Diagram"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint-Entwicklung in Visual Studio], BDC-Explorer"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Designer"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Methodendetails"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Visuelle Tools"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], BDC-Explorer"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Designer"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Methodendetails"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Visuelle Tools"
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &#220;bersicht &#252;ber Entwurfstools f&#252;r BDC-Modelle
  Ein Business Data Connectivity \(BDC\)\-Modell können Sie mit dem BDC\-Designer, dem Fenster **BDC\-Methodendetails** und dem **BDC\-Explorer** entwerfen.  
  
 Der **BDC\-Explorer** ermöglicht es Ihnen, zum Modell zu navigieren und es zu durchsuchen sowie Typdeskriptoren zu definieren.  
  
## BDC\-Designer  
 Der BDC\-Designer ermöglicht es Ihnen, die Entitäten im Modell zu definieren und ihre Beziehungen zueinander visuell anzuordnen.  Verwenden Sie den BDC\-Designer, um folgende Aufgaben auszuführen:  
  
-   Hinzufügen von Entitäten zum Modell.  
  
-   Entfernen von Entitäten aus dem Modell.  
  
-   Definieren von Beziehungen zwischen Entitäten.  
  
 Um den BDC\-Designer öffnen, auf die Modelldatei im Projekt doppelklicken, oder das Kontextmenü für die Modelldatei öffnen und dann **Öffnen** auswählen.  Fügen Sie dem Modell eine Entität hinzu, indem Sie eine **Entität** von der **Werkzeugkasten** auf den Designer ziehen oder kopieren.  Um eine Zuordnung zwischen zwei Entitäten zu erstellen, wählen Sie das Steuerelement **Zuordnung** in **Werkzeugkasten**, wählen Sie die erste Entität, und wählen Sie dann die zweite Entität aus.  
  
## Fenster BDC\-Methodendetails  
 Verwenden Sie das Fenster **BDC\-Methodendetails**, um die Parameter, Instanzen und Filterdeskriptoren einer Methode zu definieren.  
  
 Im Fenster **BDC\-Methodendetails** können Sie Finder\-, spezifische Finder\-, Creator\-, Updater\- und Deleter\-Methoden schnell generieren.  Wenn Sie diese Methoden generieren, fügt Visual Studio der Methode Metadaten hinzu, z. B. Parameter, Instanzen und Typdeskriptoren.  Sie können diese Metadaten ändern, um bestimmten Szenarios zu entsprechen.  
  
 Um das Fenster **BDC\-Methodendetails**, in der Menüleiste zu öffnen, wählen Sie **Weitere Fenster**, **BDC\-Methodendetails**, **Ansicht** aus.  
  
 Um Methoden im Fenster **BDC\-Methodendetails** anzuzeigen, wählen Sie die Entität im BDC\-Designer.  Die Methoden der ausgewählten Entität werden im Fenster **BDC\-Methodendetails** angezeigt.  Wenn Sie keine Entität im BDC\-Designer auswählen, zeigt das Fenster **BDC\-Methodendetails** keine Informationen angezeigt.  
  
 Erweitern oder reduzieren Sie die Knoten im Fenster **BDC\-Methodendetails**, um Parameter, Instanzen und Filterdeskriptoren zu definieren.  Verwenden Sie den **BDC\-Explorer**, um Typdeskriptoren zu definieren.  
  
## BDC\-Explorer  
 Im **BDC\-Explorer** werden die Elemente angezeigt, aus denen das Modell besteht.  Um **BDC\-Explorer**, in der Menüleiste zu öffnen, wählen Sie **Weitere Fenster**, **BDC\-Explorer**, **Ansicht** aus.  Um das Modell zu durchsuchen, erweitern Sie die Knoten im **BDC\-Explorer**.  Jeder Knoten stellt ein Element im XML der Modelldatei dar.  
  
 Wenn Sie Knoten im **BDC\-Explorer** auswählen, werden die Eigenschaften eines Knotens, die Sie auswählen, im Fenster **Eigenschaften**.  Viele dieser Eigenschaften entsprechen Attributen in der Modelldatei.  Sie können das Modell mithilfe des Suchfelds am oberen Rand des **BDC\-Explorer** durchsuchen.  
  
> [!NOTE]  
>  Im **BDC\-Explorer** werden keine Bezeichner, benutzerdefinierten Eigenschaften, lokalisierten Zeichenfolgen, Zuordnungsgruppen, Aktionen, Filterdeskriptoren, Aktionssteuerungslisten und Standardparameterwerte angezeigt.  
  
### Definieren von Typdeskriptoren  
 Verwenden Sie den **BDC\-Explorer**, um Typdeskriptoren zu definieren.  Der BDC\-Explorer ermöglicht es Ihnen, einmalig einen Typdeskriptor zu definieren und diesen dann an anderen Stellen im Modell wiederzuverwenden.  Kopieren Sie hierfür einen Typdeskriptor, und fügen Sie ihn in einem beliebigen anderen Parameter oder Typdeskriptor ein.  
  
> [!NOTE]  
>  Änderungen an einem ursprünglichen Typdeskriptor wirken sich nicht auf die Kopien dieses Typdeskriptors aus.  
  
 Weitere Informationen finden Sie unter [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## Siehe auch  
 [Gewusst wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md)   
 [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Erstellen einer Assoziation zwischen Entitäten](../sharepoint/creating-an-association-between-entities.md)   
 [Exemplarische Vorgehensweise: Erstellen einer externen Liste in SharePoint mithilfe von Geschäftsdaten](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  