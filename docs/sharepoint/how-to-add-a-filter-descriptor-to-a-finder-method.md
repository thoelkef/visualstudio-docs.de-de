---
title: "Gewusst wie: Hinzuf&#252;gen eines Filterdeskriptors zu einer Finder-Methode | Microsoft Docs"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Hinzufügen eines Filters"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Filterdeskriptoren"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Hinzufügen eines Filters"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Filterdeskriptoren"
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Hinzuf&#252;gen eines Filterdeskriptors zu einer Finder-Methode
  Filterdeskriptoren ermöglichen es Consumern des Modells, Werte an Methoden zu übergeben, bevor sie ausgeführt werden.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Häufig möchten Benutzer in SharePoint Instanzen eines externen Inhaltstyps abrufen, auf die bestimmte Kriterien zutreffen.  Dies können Sie unterstützen, indem Sie einer Finder\-Methode einen Filterdeskriptor hinzufügen.  
  
### So fügen Sie einer Finder\-Methode einen Filterdeskriptor hinzu  
  
1.  Erweitern Sie im Fenster **BDC\-Methodendetails** den Knoten einer Finder\-Methode, erweitern Sie den Knoten **Parameter**, und fügen Sie einen Eingabeparameter hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  Im Fenster **Methodendetails** wählen Sie den Typdeskriptor des Parameters aus.  
  
3.  Wählen Sie auf der Menüleiste die Optionen **Ansicht** und **Eigenschaftenfenster** aus.  
  
4.  Legen Sie im Eigenschaftenfenster die Eigenschaft **Typname** auf einen für den Filter geeigneten Datentyp fest.  
  
     So kann in einem Filter beispielsweise anhand des Bestelldatums die Anzahl der von der Methode zurückgegebenen Aufträge eingeschränkt werden.  Damit dieser Filter unterstützt wird, muss die Eigenschaft **Typname** des Typdeskriptors auf **System.DateTime** festgelegt werden.  
  
5.  Erweitern Sie im Fenster **Methodendetails** den Knoten **Filterdeskriptoren**.  
  
6.  In der Liste **Filterdeskriptor hinzufügen** wählen Sie **Filterdeskriptor erstellen** aus.  
  
     Unter dem Knoten **Filterdeskriptoren** wird ein neuer Filterdeskriptor angezeigt.  
  
7.  Wählen Sie auf der Menüleiste die Optionen **Ansicht** und **Eigenschaftenfenster** aus.  
  
8.  Im Fenster **Eigenschaften** wählen Sie die Eigenschaft **Typ** aus.  
  
9. In der Liste, die für die Eigenschaft **Typ** wird, wählen Sie das gewünschte Filtermuster aus, dass Sie möchten.  
  
     Um beispielsweise eines Filters, der Bestelldatums eingeschränkt wird, die Option einzuschränken, der in einer Finder\-Methode, **Vergleich** aus.  Ein Vergleichsfilter wird garantiert, dass von einer Finder\-Methode nur Instanzen zurückgibt, die eine bestimmte Bedingung erfüllen.  Weitere Informationen über jedes gewünschte Filtermuster, Sie finden. [Typen von den Filtern die von der BDC](http://go.microsoft.com/fwlink/?LinkId=169287)  
  
10. Im Fenster **Eigenschaften** wählen Sie die Eigenschaft **Zugeordnete Typdeskriptoren** aus.  
  
11. In der Liste, die für die Eigenschaft **Zugeordnete Typdeskriptoren** wird, wählen Sie den Typdeskriptor aus, dass Sie zuvor in dieser Prozedur erstellt haben.  Dadurch wird der Filter mit dem Eingabeparameter der Finder\-Methode verknüpft.  
  
12. Fügen Sie der Finder\-Methode Code hinzu, durch den Daten zurückgegeben werden.  Der Eingabeparameter kann als Bedingung in einer Auswahlabfrage verwendet werden.  
  
     Im folgenden Beispiel werden Aufträge mit dem angegebenen Bestelldatum zurückgegeben.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert des Felds `ServerName` durch den Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#11](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#11)]  
  
## Siehe auch  
 [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: Hinzufügen einer bestimmten Finder-Methode](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  