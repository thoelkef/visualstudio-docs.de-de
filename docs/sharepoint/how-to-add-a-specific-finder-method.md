---
title: "Gewusst wie: Hinzuf&#252;gen einer bestimmten Finder-Methode"
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
  - "BDC [SharePoint-Entwicklung in Visual Studio], Abrufen einer Entität"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Zurückgeben einer Entität"
  - "BDC [SharePoint-Entwicklung in Visual Studio], Spezifischer Finder"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Abrufen einer Entität"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Zurückgeben einer Entität"
  - "Business Data Connectivity-Dienst [SharePoint-Entwicklung in Visual Studio], Spezifischer Finder"
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Gewusst wie: Hinzuf&#252;gen einer bestimmten Finder-Methode
  Sie können eine einzelne Entitätsinstanz zurückgeben, indem Sie eine *spezifische Finder*\-Methode erstellen.  Der Business Data Connectivity \(BDC\)\- \- Dienst führt die spezifische Finder\-Methode aus, wenn ein Benutzer eine Entität in einem Geschäftsdatenwebpart oder einer externen Liste auswählt.  Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### So erstellen Sie eine spezifische Finder\-Methode  
  
1.  Wählen Sie im BDC\-Designer eine Entität aus.  
  
     Informationen dazu, wie einer Entität zum BDC\-Designer in Visual Studio, finden Sie unter [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Klicken Sie auf der Menüleiste **Weitere Fenster**, **BDC\-Methodendetails**, **Ansicht** aus.  
  
     Das Fenster **BDC\-Methodendetails** wird geöffnet.  Weitere Informationen über dieses Fenster, finden Sie unter [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  In der Liste **Methode hinzufügen** wählen Sie **Spezifische Finder\-Methode erstellen** aus.  
  
     Mit Visual Studio werden dem Modell die folgenden Elemente hinzugefügt.  Diese Elemente werden im Fenster **BDC\-Methodendetails** angezeigt.  
  
    -   Eine Methode.  
  
    -   Ein Eingabeparameter für die Methode.  
  
    -   Ein Rückgabeparameter für die Methode.  
  
    -   Ein Typdeskriptor für jeden Parameter.  
  
    -   Eine Methodeninstanz für die Methode.  
  
     Weitere Informationen finden Sie unter [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Öffnen Sie das Fenster **Eigenschaften** von Visual Studio.  
  
5.  Konfigurieren Sie den Typdeskriptor des Rückgabeparameters als Entitätstypdeskriptor.  Informationen darüber, wie Sie eines Entitätstypdeskriptors, finden Sie unter [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Sie müssen diesen Schritt nicht ausführen, wenn Sie der Entität eine Finder\-Methode hinzugefügt haben.  Visual Studio verwendet den Typdeskriptor, den Sie in der Finder\-Methode definiert haben.  
  
    > [!NOTE]  
    >  Wenn das Bezeichnerfeld des Entitätstyps ein Feld in einer Datenbanktabelle darstellt, die automatisch generiert wird, legen Sie die Eigenschaft **Schreibgeschützt** des Bezeichnerfelds auf **True** fest.  
  
6.  Im Fenster **Methodendetails** wählen Sie die Methodeninstanz der Methode aus.  
  
7.  Legen Sie im **Eigenschaftenfenster** die Eigenschaft **Rückgabeparametername** auf den Namen des Rückgabeparameters der Methode fest.  Weitere Informationen zu Methodeninstanzeigenschaften, Sie finden [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü der Dienstcodedatei, die für die Entität generiert wurde, und dann **Code anzeigen** aus.  
  
     Die Codedatei für den Entitätsdienst wird im Code\-Editor geöffnet.  Weitere Informationen zur Codedatei für den Entitätsdienst finden Sie unter [Erstellen eines Business Data Connectivity-Modells](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Fügen Sie der spezifischen Finder\-Methode Code hinzu.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Ruft einen Datensatz aus einer Datenquelle.  
  
    -   Gibt einer Entität an den BDC\-Dienst.  
  
     Im folgenden Beispiel wird ein Kontakt aus der AdventureWorks\-Beispieldatenbank für SQL Server zurückgegeben.  
  
    > [!NOTE]  
    >  Ersetzen Sie den Wert des Felds `ServerName` durch den Namen Ihres Servers.  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Siehe auch  
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Gewusst wie: Hinzufügen einer Finder-Methode](../sharepoint/how-to-add-a-finder-method.md)   
 [Gewusst wie: Hinzufügen einer Creator-Methode](../sharepoint/how-to-add-a-creator-method.md)   
 [Gewusst wie: Hinzufügen einer Deleter-Methode](../sharepoint/how-to-add-a-deleter-method.md)   
 [Gewusst wie: Hinzufügen einer Updater-Methode](../sharepoint/how-to-add-an-updater-method.md)   
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)  
  
  