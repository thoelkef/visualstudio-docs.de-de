---
title: "Lokalisieren von SharePoint-Lösungen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b8186110b04e3ff56b3c6b0cad03890f3233c03d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-sharepoint-solutions"></a>Lokalisieren von SharePoint-Lösungen
  Die Vorbereitung von Anwendungen für eine weltweite Verwendung wird als Lokalisierung bezeichnet. Bei der Lokalisierung werden die Ressourcen für einen bestimmten Kulturkreis übersetzt. Weitere Informationen finden Sie unter [Globalizing und Lokalisieren von Anwendungen](/visualstudio/ide/globalizing-and-localizing-applications). Dieses Thema bietet eine Übersicht über die Lokalisierung einer SharePoint-Lösung.  
  
 Für die Lokalisierung einer Lösung werden die hartcodierten Zeichenfolgen aus dem Code entfernt und in Ressourcendateien zusammengefasst. Bei einer Ressourcendatei handelt es sich um eine [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-basierte Datei mit der Erweiterung ".resx". Die Ressourcendatei enthält die übersetzten Versionen der in der Lösung verwendeten Zeichenfolgen. Weitere Informationen finden Sie unter [Ressourcen in Anwendungen](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Fügen Sie Ressourcendateien von SharePoint-Lösungen ausschließlich Zeichenfolgenressourcen hinzu. Zwar ermöglicht der Ressourcen-Editor auch das Hinzufügen von Ressourcen, bei denen es sich nicht um Zeichenfolgen handelt, diese Ressourcen werden jedoch nicht für SharePoint bereitgestellt.  
  
## <a name="resource-files"></a>Ressourcendateien  
 Drei Arten von Ressourcendateien stehen zur Verfügung: Standarddateien, sprachunabhängige Dateien und sprachspezifische Dateien.  
  
|Ressourcendateityp|Beschreibung|  
|------------------------|-----------------|  
|Standard|Standardressourcendateien werden auch als Fallbackressource bezeichnet und enthalten lokalisierte Zeichenfolgen für die Standardkultur (beispielsweise Englisch). Sie werden verwendet, wenn keine lokalisierten Ressourcendateien für die angegebene Sprache gefunden werden. Standardressourcen besitzen keine separaten Dateien und sind in der Hauptanwendungsassembly gespeichert.|  
|Sprachunabhängig|Eine Ressourcendatei mit lokalisierten Zeichenfolgen für eine Sprache, aber nicht für eine bestimmte Kultur. Beispiel: "fr" für Französisch.|  
|Sprachspezifisch|Eine Ressourcendatei mit lokalisierten Zeichenfolgen für eine Sprache und eine Kultur. Beispiel: "fr-CA" für Französisch (Kanada).|  
  
 Weitere Informationen finden Sie unter [hierarchische Organisation der Ressourcen für die Lokalisierung](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Standardressourcendateien in SharePoint-Projekte angeben, die Sie, in entwickeln [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie **Invariante Sprache (invariante Land)** in der Kulturliste, der die **Ressource hinzufügen** Dialogfeld, wenn Sie Fügen Sie eine Ressourcendatei hinzu.  
  
## <a name="localizing-visual-studio-sharepoint-solutions"></a>Lokalisieren von Visual Studio SharePoint-Lösungen  
 Beim Lokalisieren einer Lösung müssen alle den Benutzern angezeigten Textinformationen berücksichtigt werden. Informationsmeldungen, Fehlermeldungen und [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]-Zeichenfolgen müssen übersetzt und die Übersetzungen in die Ressourcendateien eingefügt werden.  
  
 Jede Zeichenfolge in einer Ressourcendatei besitzt einen eindeutigen Bezeichner. Verwenden Sie in jeder Ressourcendatei den gleichen Bezeichner für die übersetzte Zeichenfolge. Wenn also "String1" der Bezeichner für die erste Zeichenfolge in der Standardressourcendatei ist, verwenden Sie diesen Bezeichner auch in den sprachspezifischen Ressourcendateien für die erste Zeichenfolge.  
  
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Anwendungen werden in der Regel drei Bereiche lokalisiert: Funktionen, ASPX-Seitenmarkup und Code. Zur Veranschaulichung wird in den folgenden Abschnitten von einer SharePoint-Lösung ausgegangen, die ins Deutsche und ins Japanische lokalisiert werden soll. Die Standardsprache ist Englisch.  
  
### <a name="localizing-features"></a>Lokalisieren von Funktionen  
 Zum Lokalisieren einer Funktion müssen der hartcodierte Titel und die Beschreibung der Funktion durch einen Ausdruck ersetzt werden, durch den auf den übersetzten Titel und die Zeichenfolge in der lokalisierten Ressourcendatei verwiesen wird. Sie stellen diese Änderung in der **Funktions-Designer** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md).  
  
 Zum Lokalisieren der englischen Funktion für Deutsch und Japanisch werden dem Projekt drei Ressourcendatei-Projektelemente hinzugefügt – jeweils eins für Englisch, Deutsch und Japanisch. Funktionsressourcendateien können nicht zum Lokalisieren von ASPX-Markup oder -Code verwendet werden. Hierfür werden separate Ressourcendateien benötigt.  
  
 Nach dem Erstellen der Funktionsressourcendateien werden ihnen die übersetzten Zeichenfolgen hinzugefügt. Der Zugriff auf die lokalisierten Zeichenfolgen erfolgt mittels eines Ausdrucks im folgenden Format:  
  
```  
$Resources:String ID  
```  
  
 Funktionsressourcen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden immer mit "Resources" benannt. Wenn Sie eine andere Sprache als die invariante Sprache auswählen, wird dem Ressourcendateinamen die Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] hinzugefügt. Wenn Sie beispielsweise eine Standard-Funktionsressourcendatei mit invarianter Sprache hinzufügen, wird diese "Resources.resx" genannt. Wenn Sie eine sprachspezifische Funktionsressource hinzufügen, indem Sie als Kultur die Option "Japanisch (Japan)" auswählen, wird die Datei mit "Resources.ja-JP.resx" benannt. Der Name einer Funktionsressourcendatei wird automatisch zugewiesen und kann nicht geändert werden.  
  
 Der Bereich von Funktionsressourcen ist für die Funktion lokal, der sie hinzugefügt werden. Wenn Sie Ressourcen erstellen, die von jeder Funktions- oder Elementdatei in der Lösung verwendet werden kann, fügen einen **globale Ressourcendatei** Projektelement anstelle einer Funktionsressourcendatei. Die **globale Ressourcendatei** Projektelement befindet sich der **2010** Unterordner **SharePoint** in der **neues Element hinzufügen** (Dialogfeld). Das Bereitstellungsziel globaler Ressourcendateien ist der Ordner "\Resources" des SharePoint-Stammordners.  
  
### <a name="localizing-aspx-page-markup"></a>Lokalisieren von ASPX-Seitenmarkup  
 Zum Lokalisieren von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten, die Sie dem Projekt drei Ressourcendatei-Projektelemente hinzugefügt: jeweils eins für Englisch, Deutsch und Japanisch. Wenn Sie nicht zum Lokalisieren von Code neben dem Markup verfügen, können Sie stattdessen globale Ressourcendateien hinzufügen.  
  
 Geben Sie einen Namen für die Ressourcendatei der Standardsprache an. Benennen Sie die lokalisierten Ressourcendateien mit dem gleichen Namen, und fügen Sie diesem jeweils die sprachspezifische [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]-ID an. Z. B. "MyAppResources.de-de.resx" für Deutsch "und" MyAppResources.ja-JP.resx für Japanisch.  
  
 Legen Sie die **Bereitstellungstyp** Eigenschaft der einzelnen Ressourcendateien auf **AppGlobalResource**. Dadurch werden die Ressourcendateien im Ordner "App_GlobalResources" bereitgestellt und stehen somit allen ASPX-Seiten und -Steuerelementen in der Lösung zur Verfügung. Der Ordner "App_GlobalResources" befindet sich im C:\inetpub\wwwroot\wss\VirtualDirectories\\< Portnummer\>\App_GlobalResources.  
  
> [!NOTE]  
>  Verschieben Sie bei Verwendung nicht globaler Ressourcendateien die nicht globalen Ressourcendateien in den Projektelementordner, um die Eigenschaft "Bereitstellungstyp" und andere SharePoint-spezifische Eigenschaften zu aktivieren.  
  
 Ressourcendateien für ASPX-Markup können auch zum Lokalisieren von Code verwendet werden. Wenn Sie mithilfe der Ressourcen neben ASPX-Markup auch Code lokalisieren, belassen Sie die Einstellung der Eigenschaft "Buildvorgang" der einzelnen Dateien auf "Eingebettete Ressource", damit die Ressource in eine Satellitenassembly kompiliert wird. Wenn dagegen mit den Ressourcendateien ausschließlich Markup lokalisiert wird, können Sie optional die Einstellung für "Buildvorgang" zu "Inhalt" ändern, um zu verhindern, dass die Datei in die Hauptanwendungsassembly kompiliert wird.  
  
 Ersetzen Sie im Markup der ASPX-Seiten und -Steuerelemente alle hartcodierten Eigenschaftenzeichenfolgen durch einen Ausdruck im folgenden Format:  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Zum Beispiel:  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Verwenden Sie für ASPX als Text einen Ausdruck im folgenden Format:  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Zum Beispiel:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localizing-code"></a>Lokalisieren von Code  
 Neben Funktionszeichenfolgen und [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Markup müssen auch die im Code der Lösung enthaltenen Meldungs- und Fehlerzeichenfolgen lokalisiert werden. Lokalisierte Informations- und Fehlermeldungen sind in Satellitenassemblys enthalten. Satellitenassemblys enthalten Zeichenfolgen, die Benutzern angezeigt werden, beispielsweise [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]-Text und Ausgabemeldungen wie Ausnahmen.  
  
 Von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird das standardmäßige Hub- und Spoke-Modell von .NET Framework verwendet. Der Hub (Hauptprogrammassembly) enthält die Ressourcen für die Standardsprache. Die Spokes Satellitenassemblys, enthalten die sprachspezifischen Ressourcen. Weitere Informationen finden Sie unter [Verpacken und Bereitstellen von Ressourcen](http://go.microsoft.com/fwlink/?LinkId=179280). Satellitenassemblys werden aus Ressourcendateien (RESX-Dateien) kompiliert. Wenn Sie das Projekt und das Lösungspaket sprachspezifischen Ressourcendateien hinzufügen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kompiliert die Ressourcendateien in Satellitenassemblys, die mit dem Namen *Projektnamen*. resources.dll.  
  
 Beim Lokalisieren von SharePoint-Anwendungscode müssen dem Projekt genau wie bei ASPX-Markup separate Ressourcendatei-Projektelemente hinzugefügt werden. Dabei wird jeweils ein Element für die Standardsprache und ein Element für jede lokalisierte Sprache hinzugefügt. Wie jedoch zuvor bereits erwähnt: Wenn Sie bereits über Ressourcendateien zum Lokalisieren von ASPX-Markup verfügen, können Sie diese für die Lokalisierung des Codes wiederverwenden. Wenn Sie Ressourcendateien erstellen müssen, benennen Sie die Ressourcendatei für die Standardsprache mit einem beliebigen Namen, gefolgt von der Erweiterung ".resx". Benennen Sie die lokalisierten Ressourcendateien mit dem gleichen Namen, und fügen Sie diesem jeweils die sprachspezifische [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]-ID an. Legen Sie die Eigenschaft "Buildvorgang" der einzelnen Ressourcendateien auf "Eingebettete Ressource" fest, um die Erstellung von Satellitenressourcenassemblys zu aktivieren.  
  
 Um die Satellitenassemblys zu erstellen, erstellen Sie das Projekt, und fügen Sie die Dateien als zusätzliche Assemblys über die **erweitert** auf der Registerkarte die **Paket-Designer**. Beim Hinzufügen der Assemblys voranstellen eine Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] Ordner dem Pfad zum Speicherort, z. B. de-DE\\*Name des Projektelements*. resources.dll. Dadurch kann das Paket Dateien mit dem gleichen Namen enthalten.  
  
 Ersetzen Sie hartcodierte Zeichenfolgen im Code durch Aufrufe der <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>-Methode, und verwenden Sie dabei die folgende Syntax:  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Lokalisieren von Code](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Lokalisieren von Webpartcode  
 Webparts enthalten eine benutzerdefinierte Funktion des Eigenschaften-Editors mit Codeattributen, von denen hartcodierte Zeichenfolgen wie "WebDisplayName", "Category" oder "WebDescription" verwendet werden. Erstellen Sie eine separate, von der Klasse des Attributs abgeleitete Klasse, um die Zeichenfolgenwerte für diese Attribute zu ersetzen. Legen Sie in diesen Klassen die Eigenschaft des Attributs fest. Die Attributeigenschaft hängt von der Basisklasse ab. So lautet beispielsweise die WebDisplayName-Attributeigenschaft "DisplayNameValue", und die WebDescription-Attributeigenschaft lautet "DescriptionValue".  
  
 Verweisen Sie in der abgeleiteten Klasse auf die Zeichenfolgen-ID aus der Ressourcendatei sowie auf das ResourceManager-Objekt, um den lokalisierten Wert für die Zeichenfolgen-ID abzurufen. Geben Sie diesen Wert an das Eigenschaften-Editor-Attribut zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)   
 [Vorgehensweise: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)   
 [Vorgehensweise: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)   
 [Vorgehensweise: hinzufügen eine Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)   
 [Vorgehensweise: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  