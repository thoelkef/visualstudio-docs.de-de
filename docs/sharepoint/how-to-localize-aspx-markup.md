---
title: 'Vorgehensweise: Lokalisieren von ASPX-Markup | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9dd127fea21a53b9a29082f536ac8c0404299c63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-localize-aspx-markup"></a>Gewusst wie: Lokalisieren von ASPX-Markup
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] in der Regel verwenden Sie Seiten (ASPX) hartcodierte Zeichenfolgenwerte. Um diese Zeichenfolgen zu lokalisieren, ersetzen Sie sie mit Ausdrücken, die lokalisierte Ressourcen zu verweisen.  
  
## <a name="localizing-aspx-markup"></a>Lokalisieren von ASPX-Markup  
  
#### <a name="to-localize-aspx-markup"></a>Zum Lokalisieren von ASPX-markup  
  
1.  Fügen Sie separate Ressourcendateien hinzu: eine für die Standardsprache und jeweils eine für jede lokalisierte Sprache.  
  
     Wenn Sie nur Markup und keinen Code lokalisieren, fügen Sie ein Projektelement globale Ressourcendatei hinzu. Wenn Sie Code und Markup lokalisieren, fügen Sie ein Projektelement Ressourcendatei hinzu.  
  
    1.  So fügen Sie eine globale Ressourcendatei in hinzu **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für ein SharePoint-Projektelement, und wählen Sie dann **hinzufügen**, **neues Element**. Unter SharePoint **2010** Knoten, wählen Sie die **globale Ressourcendatei** Vorlage.  
  
    2.  Hinzufügen einer Ressourcendatei in **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für ein SharePoint-Projektelement, und wählen Sie dann **hinzufügen**, **neues Element**. Unter einem der **Visual Basic** oder **Visual C#-** Knoten, wählen Sie die **Ressourcendatei** Vorlage.  
  
    > [!NOTE]  
    >  Achten Sie darauf, dass die Ressourcendateien in einer SharePoint-Projektelement So aktivieren Sie die Eigenschaft "Bereitstellung" hinzufügen. Diese Eigenschaft ist später in dieser Prozedur erforderlich. Wenn Ihre Lösung kein SharePoint-Projektelement vorhanden ist, können Sie ein leeres SharePoint-Projekt hinzufügen und entfernen die Standarddatei für die Datei "Elements.xml".  
  
2.  Benennen Sie die Ressourcendatei für die Standardsprache mit einem beliebigen Namen, und versehen Sie diesen mit der Erweiterung ".resx" (also beispielsweise "MyAppResources.resx"). Verwenden Sie für jede lokalisierte Ressourcendatei den gleichen Basisnamen, aber fügen Sie die Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Benennen Sie also beispielsweise eine für Deutsch lokalisierte Ressource mit "MyAppResources.de-DE.resx".  
  
3.  Ändern Sie den Wert, der die **Bereitstellungstyp** Eigenschaft der einzelnen Ressourcendateien zu **AppGlobalResource** , dazu führen, dass sie zum Ordner "App_GlobalResources" des Servers bereitstellen.  
  
4.  Wenn Sie der Ressourcen neben ASPX-Markup Code lokalisieren mithilfe, belassen Sie den Wert des der **Buildvorgang** Eigenschaft der einzelnen Dateien **eingebettete Ressource**. Wenn Sie nur für Markup lokalisiert die Ressourcendateien verwenden, können Sie optional ändern, auf den Wert der Eigenschaft der Dateien, die **Content**. Weitere Informationen finden Sie unter [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Öffnen Sie die einzelnen Ressourcendateien und fügen Sie lokalisierte Zeichenfolgen, die die gleiche Zeichenfolgen-IDs in jeder Datei verwenden.  
  
6.  In der [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Markup für die ASPX-Seite oder ein Steuerelement, ersetzen Sie die hartcodierte Zeichenfolgen mit Werten, die das folgende Format verwenden:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Beispielsweise um den Text für ein Label-Steuerelement auf einer Anwendungsseite lokalisieren möchten, ändern Sie:  
  
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
  
7.  Drücken Sie die F5-TASTE, um die Anwendung zu erstellen und auszuführen.  
  
8.  Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.  
  
     In der Anwendung werden die lokalisierten Zeichenfolgen angezeigt. Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint-Server ein Sprachpaket installiert sein, das der Kultur der Ressourcendatei entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)   
 [Vorgehensweise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)   
 [Vorgehensweise: hinzufügen eine Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)   
 [Vorgehensweise: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)  
  
  