---
title: "Gewusst wie: Hinzuf&#252;gen eines Parameters zu einer Methode | Microsoft Docs"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Hinzufügen einer Methode zu einem Parameter"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Methodenparameter"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Parameter"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Hinzufügen einer Methode zu einem Parameter"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Methodenparameter"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Parameter"
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Gewusst wie: Hinzuf&#252;gen eines Parameters zu einer Methode
  Verwenden Sie einen Parameter, um Informationen an die Methode zu übergeben oder um Informationen von einer Methode zurückzugeben.  Alle Methoden müssen wenigstens einen Parameter aufweisen.  Weitere Informationen zum Entwerfen eines Parameters, um den Methodentyp zu unterstützen, den Sie erstellen möchten, finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Wenn Sie einer Methode einen Parameter hinzufügen, fügt Visual Studio dem XML der Modelldatei im Projekt ein `<Parameter>`\-Element hinzu.  Weitere Informationen zu den Attributen eines Elements `<Parameter>`, Sie finden. [Parameter](http://go.microsoft.com/fwlink/?LinkId=169284)  
  
### So fügen Sie einer Methode einen Parameter hinzu  
  
1.  Hinzufügen einer Methode zu einer Entität  
  
2.  Klicken Sie auf der Menüleiste **Weitere Fenster**, **BDC\-Methodendetails**, **Ansicht** aus.  
  
     Das Fenster **BDC\-Methodendetails** wird geöffnet.  Weitere Informationen finden Sie unter [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Erweitern Sie im Fenster **BDC\-Methodendetails** den Knoten der Methode, und erweitern Sie dann den Knoten **Parameter**.  
  
4.  In der Liste **Parameter hinzufügen** wählen Sie **Parameter erstellen** aus.  
  
     Ein neuer Parameter wird unter dem Knoten **Parameters** angezeigt.  
  
5.  Wählen Sie auf der Menüleiste die Optionen **Ansicht** und **Eigenschaftenfenster** aus.  
  
6.  Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Name** auf einen beliebigen, sinnvollen Namen fest.  Wenn die Methode beispielsweise Kunden zurückgibt, können Sie die Methode GetCustomers nennen.  
  
7.  Im Fenster **BDC\-Methodendetails** öffnen Sie die Liste, die für die Richtung des Parameters angezeigt wird, und wählen Sie anschließend, **InOut**, **Aus** oder **RückgabeIn** aus.  
  
     Weitere Informationen über die Richtung, die Sie für die Typmethode, die Sie erstellen, auswählen sollten, finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Ändern Sie den Typdeskriptor des Parameters.  Weitere Informationen finden Sie unter [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## Siehe auch  
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  