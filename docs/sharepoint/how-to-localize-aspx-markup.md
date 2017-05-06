---
title: "Gewusst wie: Lokalisieren von ASPX-Markup"
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
  - "Lokalisieren von XML [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Lokalisieren"
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Gewusst wie: Lokalisieren von ASPX-Markup
  Von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Seiten \(ASPX\-Dateien\) werden üblicherweise hartcodierte Zeichenfolgenwerte verwendet.  Zum Lokalisieren dieser Zeichenfolgen werden sie durch Ausdrücke ersetzt, die auf lokalisierte Ressourcen verweisen.  
  
## Lokalisieren von ASPX\-Markup  
  
#### So lokalisieren Sie ASPX\-Markup  
  
1.  Fügen Sie separate Ressourcendateien hinzu: eine für die Standardsprache und jeweils eine für jede lokalisierte Sprache.  
  
     Wenn Sie nur Markup und keinen Code lokalisieren möchten, fügen Sie ein Projektelement vom Typ "Globale Ressourcendatei" hinzu.  Wenn Sie Code und Markup lokalisieren möchten, fügen Sie ein Projektelement vom Typ "Ressourcendatei" hinzu.  
  
    1.  So einer globalen Ressourcen, im **Projektmappen\-Explorer** hinzuzufügen, öffnen das Kontextmenü für ein SharePoint\-Projektelement und wählen dann, **HinzufügenNeues Element** aus.  Wählen Sie unter dem SharePoint\-Knoten **2010** die Vorlage **Globale Ressourcendatei** aus.  
  
    2.  So fügen Sie eine Ressourcendatei, in **Projektmappen\-Explorer** hinzuzufügen, öffnen das Kontextmenü für ein SharePoint\-Projektelement und wählen dann, **HinzufügenNeues Element** aus.  Entweder unter **Visual Basic** oder **Visual C\#** Knoten wählen Sie die Vorlage **Ressourcendatei** aus.  
  
    > [!NOTE]  
    >  Fügen Sie einem SharePoint\-Projektelement die Ressourcendateien hinzuzufügen, um die Eigenschaft "Bereitstellungstyp" zu aktivieren.  Diese Eigenschaft ist später in dieser Prozedur erforderlich.  Wenn die Projektmappe kein SharePoint\-Projektelement enthält, können Sie ein leeres SharePoint\-Projekt hinzufügen und die Standarddatei "Elements.xml" entfernen.  
  
2.  Benennen Sie die Ressourcendatei für die Standardsprache mit einem beliebigen Namen, und versehen Sie diesen mit der Erweiterung ".resx" \(also beispielsweise "MyAppResources.resx"\).  Verwenden Sie für jede lokalisierte Ressourcendatei den gleichen Basisnamen, aber fügen Sie jeweils die Kultur\- [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] hinzu.  Benennen Sie also beispielsweise eine für Deutsch lokalisierte Ressource mit "MyAppResources.de\-DE.resx".  
  
3.  Ändern Sie den Wert der Eigenschaft **Bereitstellungstyp** einzelnen Ressourcendateien zu **AppGlobalResource**, um sie zu veranlassen, um im Ordner "App GlobalResources" des Servers erfolgt.  
  
4.  Wenn Sie Ressourcen verwenden, um neben ASPX\-Markup auch Code lokalisieren, belassen Sie den Wert der Eigenschaft **Buildvorgang** jeder Datei als **Eingebettete Ressource**.  Wenn Sie mithilfe der Ressourcendateien ausschließlich Markup lokalisieren, können Sie den Eigenschaftswert der Dateien optional zu **Inhalt** ändern.  Weitere Informationen finden Sie unter [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Öffnen Sie die einzelnen Ressourcendateien, und fügen Sie lokalisierte Zeichenfolgen hinzu. Verwenden Sie dabei in jeder Datei die gleichen Zeichenfolgen\-IDs.  
  
6.  Ersetzen Sie im [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Markup für die ASPX\-Seite oder für das ASPX\-Steuerelement die hartcodierten Zeichenfolgen durch Werte im folgenden Format:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Wenn Sie also beispielsweise den Text für ein Label\-Steuerelement auf einer Anwendungsseite lokalisieren möchten, ändern Sie Folgendes:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     auf  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Drücken Sie die F5\-TASTE, um die Anwendung zu erstellen und auszuführen.  
  
8.  Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.  
  
     In der Anwendung werden die lokalisierten Zeichenfolgen angezeigt.  Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint\-Server ein Language Pack installiert sein, das der Kultur der Ressourcendatei entspricht.  
  
## Siehe auch  
 [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)   
 [Gewusst wie: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)   
 [Gewusst wie: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)   
 [Gewusst wie: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)  
  
  