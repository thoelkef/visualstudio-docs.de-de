---
title: 'Vorgehensweise: Lokalisieren von ASPX-Markup | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: df6e4be288e957708ba7339383d8e80e82f27e40
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870268"
---
# <a name="how-to-localize-aspx-markup"></a>Vorgehensweise: Lokalisieren von ASPX-markup
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (ASPX) verwenden Sie in der Regel hartcodierte Zeichenfolgenwerte. Um diese Zeichenfolgen zu lokalisieren, ersetzen Sie sie mit Ausdrücken, die lokalisierte Ressourcen zu verweisen.  
  
## <a name="localize-aspx-markup"></a>Lokalisieren von ASPX-markup  
  
#### <a name="to-localize-aspx-markup"></a>Zum Lokalisieren von ASPX-markup  
  
1.  Separate Ressourcendateien hinzuzufügen: eine für die Standardsprache und eine für jede lokalisierte Sprache.  
  
     Wenn Sie nur-Markup und nicht Code lokalisieren, fügen Sie ein Projektelement globale Ressourcendatei hinzu. Wenn Sie Code und Markup lokalisieren, fügen Sie ein Projektelement Ressourcendatei hinzu.  
  
    1.  Hinzufügen einer globalen Ressourcendatei in **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für eine SharePoint-Projektelement, und wählen Sie dann **hinzufügen** > **neues Element**. Unter SharePoint **2010** Knoten, wählen Sie die **globale Ressourcendatei** Vorlage.  
  
    2.  Hinzufügen einer Ressourcendatei in **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für eine SharePoint-Projektelement, und wählen Sie dann **hinzufügen** > **neues Element**. Entweder unter der **Visual Basic** oder **Visual C#-** Knoten, wählen Sie die **Ressourcendatei** Vorlage.  
  
    > [!NOTE]  
    >  Achten Sie darauf, dass die Dateien zu einem SharePoint-Projektelement, aktivieren Sie die Eigenschaft "Bereitstellungstyp" hinzufügen. Diese Eigenschaft ist später in dieser Prozedur erforderlich. Wenn Ihre Lösung keine SharePoint-Projektelements, können Sie ein leeres SharePoint-Projekt hinzufügen und entfernen Sie den Standardwert *"Elements.xml"* Datei.  
  
2.  Benennen Sie die Ressourcendatei der Standardsprache der mit einem *resx* Erweiterung, z. B. MyAppResources.resx. Verwenden Sie für jede lokalisierte Ressourcendatei den gleichen Basisnamen, aber fügen Sie die Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Z. B. Namen, eine für Deutsch lokalisierte Ressource *MyAppResources.de-DE.resx*.  
  
3.  Ändern Sie den Wert, der die **Bereitstellungstyp** Eigenschaft der einzelnen Ressourcendateien auf **AppGlobalResource** , dazu führen, dass sie zum Ordner "App_GlobalResources" des Servers bereitstellen.  
  
4.  Wenn Sie die Ressourcen zum Lokalisieren von Code neben ASPX-Markup verwenden, sollten Sie den Wert von der **Buildvorgang** Eigenschaft der einzelnen Dateien **eingebettete Ressource**. Wenn Sie nur für das Markup lokalisiert die Ressourcendateien verwenden, können Sie optional ändern, auf den Wert der Eigenschaft, der die Dateien in **Content**. Weitere Informationen finden Sie unter [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Öffnen Sie die einzelnen Ressourcendateien und fügen Sie die lokalisierte Zeichenfolgen, die über die gleichen Zeichenfolgen-IDs in jeder Datei.  
  
6.  In der [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Markup für die ASPX-Seite oder das Steuerelement, ersetzen Sie die hartcodierten Zeichenfolgen mit Werten, die das folgende Format verwenden:  
  
    ```aspx-csharp  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     Z. B. um den Text für ein Label-Steuerelement auf einer Anwendungsseite zu lokalisieren, ändern Sie:  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     auf  
  
    ```aspx-csharp  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Wählen Sie die **F5** Schlüssel zu erstellen und Ausführen der Anwendung.  
  
8.  Legen Sie die Anzeigesprache in SharePoint auf eine Sprache fest, die nicht der Standardsprache entspricht.  
  
     In der Anwendung werden die lokalisierten Zeichenfolgen angezeigt. Zum Anzeigen lokalisierter Ressourcen muss auf dem SharePoint-Server ein Sprachpaket installiert sein, das der Kultur der Ressourcendatei entspricht.  
  
## <a name="see-also"></a>Siehe auch
 [Lokalisieren von SharePoint-Lösungen](../sharepoint/localizing-sharepoint-solutions.md)   
 [Vorgehensweise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)   
 [Vorgehensweise: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)   
 [Vorgehensweise: Lokalisieren von code](../sharepoint/how-to-localize-code.md)  
