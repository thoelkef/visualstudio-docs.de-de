---
title: "How to: Define the Type Descriptor of a Parameter"
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
  - "Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor"
  - "BDC [SharePoint development in Visual Studio], parameter types"
  - "BDC [SharePoint development in Visual Studio], type descriptor"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], parameter types"
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# How to: Define the Type Descriptor of a Parameter
  Ein Typdeskriptor enthält Eigenschaften, mit denen der Datentyp eines Parameters beschrieben wird.  Von einem Typdeskriptor kann ein Feld, eine Entität oder eine Auflistung von Entitäten definiert werden.  Weitere Informationen finden Sie unter [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### So definieren Sie den Typdeskriptor für einen Parameter  
  
1.  Wählen Sie im Fenster **BDC\-Methodendetails** den Typdeskriptor des Parameters aus.  
  
2.  Wählen Sie auf der Menüleiste die Optionen **Ansicht** und **Eigenschaftenfenster** aus.  
  
3.  Legen Sie im Eigenschaftenfenster die Eigenschaften des Typdeskriptors fest.  
  
     In den folgenden Prozeduren wird beschrieben, wie ein Typdeskriptor als Feld, Entität oder Entitätsauflistung definiert wird.  
  
### So definieren Sie ein Feld  
  
1.  Legen Sie im Eigenschaftenfenster die Eigenschaft **Name** des Typdeskriptors auf den Namen eines Felds im Typ fest, der die Entität darstellt \(beispielsweise "FirstName"\).  
  
2.  In der Liste neben der **TypeName**\-Eigenschaft wählen Sie den entsprechenden Datentyp aus \(beispielsweise **Int32**\).  
  
     Informationen zu anderen optionalen Parametern finden Sie unter [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### So definieren Sie eine Entität  
  
1.  Legen Sie im Eigenschaftenfenster die Eigenschaft **Name** auf einen aussagekräftigen Namen für die Entität fest \(beispielsweise "Kontakt"\).  
  
2.  Legen Sie die Eigenschaft **TypeName** auf den vollqualifizierten Namen des Typs fest, der die Entität darstellt.  Bei diesem Typ kann es sich um eine Klasse im Projekt, um einen im BDC\-Objektmodell definierten Typ oder um einen Typ handeln, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.  
  
    -   Klicken Sie bei Verwendung einer Klasse im Projekt neben der **TypeName**\-Eigenschaft auf den Nach\-unten\-Pfeil, wählen Sie im geöffneten Dialogfeld die Registerkarte **Aktuelles Projekt** aus, und wählen Sie dann eine Klasse im Projekt aus.  
  
         Der vollqualifizierte Name enthält den Namespace und den Namen der Klasse, gefolgt vom Namen des LOB\-Systems.  Im folgenden Beispiel wird der Wert der Eigenschaft **TypeName** auf eine Klasse im Projekt festgelegt.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Bei Verwendung eines Typs, der sich in einer Assembly der Lösung befindet, enthält der vollqualifizierte Name den Namen des Typs, den Namen der Assembly, die Versionsnummer, die Kultur sowie das öffentliche Schlüsseltoken.  
  
         Im folgenden Beispiel wird der Wert der Eigenschaft **TypeName** auf einen Typ festgelegt, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Bei Verwendung eines im BDC\-Objektmodell definierten Typs enthält der vollqualifizierte Name den Namespace und den Namen des Typs.  
  
         Im folgenden Beispiel wird der Wert der Eigenschaft **TypeName** auf einen Typ im BDC\-Objektmodell festgelegt.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  Öffnen Sie im Fenster **BDC\-Methodendetails** die Liste, die für den Typdeskriptor angezeigt wird, und wählen Sie anschließend **Bearbeiten** aus.  
  
     Das Fenster **BDC\-Explorer** wird geöffnet.  
  
4.  Öffnen Sie in **BDC\-Explorer** das Kontextmenü des Typdeskriptors, und wählen Sie dann **Typdeskriptor hinzufügen** aus.  
  
     Dem Entitätstypdeskriptor wird ein neuer Typdeskriptor als untergeordnetes Element hinzugefügt.  Konfigurieren Sie diesen Typdeskriptor als Feld.  
  
5.  Wiederholen Sie Schritt 4, um für jedes Feld der Entität einen untergeordneten Typdeskriptor hinzuzufügen.  
  
### So definieren Sie eine Auflistung von Entitäten  
  
1.  Wählen Sie im Fenster **BDC\-Methodendetails** den Typdeskriptor des gewünschten Parameters aus.  
  
2.  Wählen Sie auf der Menüleiste die Optionen **Ansicht** und **Eigenschaftenfenster** aus.  
  
3.  Legen Sie im Eigenschaftenfenster die Eigenschaft **Name** auf einen aussagekräftigen Namen für die Entität fest \(beispielsweise "Kontakte"\).  
  
4.  Legen Sie die Eigenschaft **IsCollection** auf **True** fest.  Dadurch wird angegeben, dass es sich bei diesem Typdeskriptor um eine Auflistung von Entitäten handelt.  
  
5.  Legen Sie die Eigenschaft **TypeName** auf eine Zeichenfolge fest, die einen Verweis auf die <xref:System.Collections.Generic.IEnumerable%601>\-Schnittstelle und den vollqualifizierten Namen des Typs enthält, der die Entität darstellt.  Bei diesem Typ kann es sich um eine Klasse im Projekt, um einen im BDC\-Objektmodell definierten Typ oder um einen Typ handeln, der in einer Assembly definiert ist, auf die in der Lösung verwiesen wird.  
  
    -   Klicken Sie bei Verwendung einer Klasse im Projekt neben der **TypeName**\-Eigenschaft auf den Nach\-unten\-Pfeil, wählen Sie im geöffneten Dialogfeld die Registerkarte **Aktuelles Projekt** aus, und wählen Sie dann eine Klasse im Projekt aus.  
  
         Der vollqualifizierte Name enthält den Namespace und den Namen der Klasse, gefolgt vom Namen des LOB\-Systems.  
  
         Im folgenden Beispiel wird der Wert der Eigenschaft **TypeName** auf eine Auflistung von Klassen im Projekt festgelegt.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` `BdcModel1.Contact, BdcModel1]`  
  
    -   Bei Verwendung eines Typs, der sich in einer Assembly der Lösung befindet, enthält der vollqualifizierte Name den Namen des Typs, den Namen der Assembly, die Versionsnummer, die Kultur sowie das öffentliche Schlüsseltoken.  
  
         Im folgenden Beispiel wird der Wert der Eigenschaft **TypeName** auf eine Auflistung von Typen in einer Assembly festgelegt, auf die in der Lösung verwiesen wird.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`  
  
    -   Bei Verwendung eines im BDC\-Objektmodell definierten Typs enthält der vollqualifizierte Name lediglich den Namespace und den Namen des Typs.  
  
         Im folgenden Beispiel wird der Wert der Eigenschaft **TypeName** auf eine Auflistung von im BDC\-Objektmodell definierten Typen festgelegt.  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`  
  
6.  Öffnen Sie im Fenster **BDC\-Methodendetails** die Liste, die für den Typdeskriptor angezeigt wird, und wählen Sie anschließend **Bearbeiten** aus.  
  
     Das Fenster **BDC\-Explorer** wird geöffnet.  
  
7.  Öffnen Sie in **BDC\-Explorer** das Kontextmenü des Typdeskriptors, und wählen Sie dann **Typdeskriptor hinzufügen** aus.  
  
     Dem Auflistungstypdeskriptor wird ein neuer Typdeskriptor als untergeordnetes Element hinzugefügt.  Konfigurieren Sie diesen Typdeskriptor als Entität.  
  
## Siehe auch  
 [Übersicht über Entwurfstools für BDC-Modelle](../sharepoint/bdc-model-design-tools-overview.md)   
 [Gewusst wie: Hinzufügen einer Entität zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Gewusst wie: Hinzufügen eines Parameters zu einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Gewusst wie: Definieren einer Methodeninstanz](../sharepoint/how-to-define-a-method-instance.md)   
 [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  