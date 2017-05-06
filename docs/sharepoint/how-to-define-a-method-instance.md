---
title: "Gewusst wie: Definieren einer Methodeninstanz"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Methode"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Methodeninstanzen"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Methode"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Methodeninstanzen"
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Definieren einer Methodeninstanz
  Sie müssen für jede Methode im Modell mindestens eine Methodeninstanz definieren.  
  
 Fügen Sie eine Methodeninstanz über das Fenster **BDC\-Methodendetails** hinzu.  Wenn Sie die Methodeninstanz hinzufügen, fügt Visual Studio dem XML der Modelldatei im Projekt ein `<MethodInstance>`\-Element hinzu.  Weitere Informationen zu den Attributen eines Elements `<MethodInstance>`, Sie finden. [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282)  
  
### So definieren Sie eine Methodeninstanz  
  
1.  Erweitern Sie im Fenster **BDC\-Methodendetails** den Knoten einer Methode, und erweitern Sie dann den Knoten **Instanzen**.  
  
2.  In der Liste **Methodeninstanz hinzufügen** wählen Sie **Finder\-Instanz erstellen** aus.  
  
     Eine neue Methodeninstanz wird unter dem Knoten **Instanzen** angezeigt.  
  
3.  Wählen Sie in der Menüleiste **Ansicht** aus, wählen Sie **Eigenschaftenfenster** aus.  
  
4.  Legen Sie im Fenster **Eigenschaften** die Eigenschaften der Methodeninstanz fest.  Weitere Informationen zu den einzelnen Eigenschaften, Sie finden [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## Siehe auch  
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  