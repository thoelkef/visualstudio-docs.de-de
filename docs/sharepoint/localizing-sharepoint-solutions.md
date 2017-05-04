---
title: "Lokalisieren von SharePoint-L&#246;sungen | Microsoft Docs"
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
  - "VS.SharePointTools.Project.GlobalAndFeatureResource"
  - "VS.SharePoint.Project.AddResourceDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Globalisieren [SharePoint-Entwicklung in Visual Studio]"
  - "Lokalisieren [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Lokalisierung"
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Lokalisieren von SharePoint-L&#246;sungen
  Die Vorbereitung von Anwendungen für eine weltweite Verwendung wird als Lokalisierung bezeichnet.  Bei der Lokalisierung werden die Ressourcen für einen bestimmten Kulturkreis übersetzt.  Weitere Informationen finden Sie unter [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md).  Dieses Thema bietet eine Übersicht über die Lokalisierung einer SharePoint\-Lösung.  
  
 Für die Lokalisierung einer Lösung werden die hartcodierten Zeichenfolgen aus dem Code entfernt und in Ressourcendateien zusammengefasst.  Bei einer Ressourcendatei handelt es sich um eine [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-basierte Datei mit der Erweiterung ".resx".  Die Ressourcendatei enthält die übersetzten Versionen der in der Lösung verwendeten Zeichenfolgen.  Weitere Informationen finden Sie unter [Ressourcen in Desktop\-Apps](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
> [!NOTE]  
>  Fügen Sie Ressourcendateien von SharePoint\-Lösungen ausschließlich Zeichenfolgenressourcen hinzu.  Zwar ermöglicht der Ressourcen\-Editor auch das Hinzufügen von Ressourcen, bei denen es sich nicht um Zeichenfolgen handelt, diese Ressourcen werden jedoch nicht für SharePoint bereitgestellt.  
  
## Ressourcendateien  
 Drei Arten von Ressourcendateien stehen zur Verfügung: Standarddateien, sprachunabhängige Dateien und sprachspezifische Dateien.  
  
|Ressourcendateityp|**Beschreibung**|  
|------------------------|----------------------|  
|Default|Standardressourcendateien werden auch als Fallbackressource bezeichnet und enthalten lokalisierte Zeichenfolgen für die Standardkultur \(beispielsweise Englisch\).  Sie werden verwendet, wenn keine lokalisierten Ressourcendateien für die angegebene Sprache gefunden werden.  Standardressourcen besitzen keine separaten Dateien und sind in der Hauptanwendungsassembly gespeichert.|  
|Sprachunabhängig|Eine Ressourcendatei mit lokalisierten Zeichenfolgen für eine Sprache, aber nicht für eine bestimmte Kultur.  Beispiel: "fr" für Französisch.|  
|Sprachspezifisch|Eine Ressourcendatei mit lokalisierten Zeichenfolgen für eine Sprache und eine Kultur.  Beispiel: "fr\-CA" für Französisch \(Kanada\).|  
  
 Weitere Informationen finden Sie unter [Hierarchische Organisation der Ressourcen für die Lokalisierung](http://go.microsoft.com/fwlink/?LinkId=178360).  
  
 Wählen Sie beim Hinzufügen einer Ressourcendatei in der Kulturliste des Dialogfelds **Ressource hinzufügen** die Option **Invariante Sprache \(Invariantes Land\)** aus, um in SharePoint\-Projekten, die Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] entwickeln, Standardressourcendateien anzugeben.  
  
## Lokalisieren von Visual Studio SharePoint\-Lösungen  
 Beim Lokalisieren einer Lösung müssen alle den Benutzern angezeigten Textinformationen berücksichtigt werden.  Informationsmeldungen, Fehlermeldungen und [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]\-Zeichenfolgen müssen übersetzt und die Übersetzungen in die Ressourcendateien eingefügt werden.  
  
 Jede Zeichenfolge in einer Ressourcendatei besitzt einen eindeutigen Bezeichner.  Verwenden Sie in jeder Ressourcendatei den gleichen Bezeichner für die übersetzte Zeichenfolge.  Wenn also "String1" der Bezeichner für die erste Zeichenfolge in der Standardressourcendatei ist, verwenden Sie diesen Bezeichner auch in den sprachspezifischen Ressourcendateien für die erste Zeichenfolge.  
  
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint\-Anwendungen werden in der Regel drei Bereiche lokalisiert: Funktionen, ASPX\-Seitenmarkup und Code.  Zur Veranschaulichung wird in den folgenden Abschnitten von einer SharePoint\-Lösung ausgegangen, die ins Deutsche und ins Japanische lokalisiert werden soll.  Die Standardsprache ist Englisch.  
  
### Lokalisieren von Funktionen  
 Zum Lokalisieren einer Funktion müssen der hartcodierte Titel und die Beschreibung der Funktion durch einen Ausdruck ersetzt werden, durch den auf den übersetzten Titel und die Zeichenfolge in der lokalisierten Ressourcendatei verwiesen wird.  Diese Änderung wird in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] im Funktions\-Designer vorgenommen.  Weitere Informationen finden Sie unter [Gewusst wie: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md).  
  
 Zum Lokalisieren der englischen Funktion für Deutsch und Japanisch werden dem Projekt drei Ressourcendatei\-Projektelemente hinzugefügt – jeweils eins für Englisch, Deutsch und Japanisch.  Funktionsressourcendateien können nicht zum Lokalisieren von ASPX\-Markup oder \-Code verwendet werden. Hierfür werden separate Ressourcendateien benötigt.  
  
 Nach dem Erstellen der Funktionsressourcendateien werden ihnen die übersetzten Zeichenfolgen hinzugefügt.  Der Zugriff auf die lokalisierten Zeichenfolgen erfolgt mittels eines Ausdrucks im folgenden Format:  
  
```  
$Resources:String ID  
```  
  
 Funktionsressourcen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden immer mit "Resources" benannt.  Wenn Sie eine andere Sprache als die invariante Sprache auswählen, wird dem Ressourcendateinamen die Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] hinzugefügt.  Wenn Sie beispielsweise eine Standard\-Funktionsressourcendatei mit invarianter Sprache hinzufügen, wird diese "Resources.resx" genannt.  Wenn Sie eine sprachspezifische Funktionsressource hinzufügen, indem Sie als Kultur die Option "Japanisch \(Japan\)" auswählen, wird die Datei mit "Resources.ja\-JP.resx" benannt.  Der Name einer Funktionsressourcendatei wird automatisch zugewiesen und kann nicht geändert werden.  
  
 Der Bereich von Funktionsressourcen ist für die Funktion, der sie hinzugefügt werden, lokal.  Wenn Sie Ressourcen erstellen möchten, die von jeder Funktions\- oder Elementdatei in der Lösung verwendet werden können, fügen Sie dem Projekt anstelle einer Funktionsressourcendatei eine globale Ressourcendatei hinzu.  Das Projektelement **Globale Ressourcendatei** befindet sich im Dialogfeld **Neues Element hinzufügen** unter **SharePoint** im Ordner **2010**.  Das Bereitstellungsziel globaler Ressourcendateien ist der Ordner "\\Resources" des SharePoint\-Stammordners.  
  
### Lokalisieren von ASPX\-Seitenmarkup  
 Um [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Seiten zu lokalisieren, fügen Sie dem Projekt drei Ressourcendatei\-Projektelemente hinzu: eins für Englisch, eins für Deutsch und eins für Japanisch.  Wenn Sie neben dem Markup nicht auch noch Code lokalisieren müssen, können Sie stattdessen globale Ressourcendateien hinzufügen.  
  
 Geben Sie einen Namen für die Ressourcendatei der Standardsprache an.  Benennen Sie die lokalisierten Ressourcendateien mit dem gleichen Namen, und fügen Sie diesem jeweils die sprachspezifische [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]\-ID an.  Beispiel: "MyAppResources.de\-DE.resx" für Deutsch und "MyAppResources.ja\-JP.resx" für Japanisch.  
  
 Legen Sie die Eigenschaft **Bereitstellungstyp** der einzelnen Ressourcendateien auf **AppGlobalResource** fest.  Dadurch werden die Ressourcendateien im Ordner "App\_GlobalResources" bereitgestellt und stehen somit allen ASPX\-Seiten und \-Steuerelementen in der Lösung zur Verfügung.  Der Ordner "App\_GlobalResources" befindet sich unter "C:\\inetpub\\wwwroot\\wss\\VirtualDirectories\\\<Portnummer\>\\App\_GlobalResources".  
  
> [!NOTE]  
>  Verschieben Sie bei Verwendung nicht globaler Ressourcendateien die nicht globalen Ressourcendateien in den Projektelementordner, um die Eigenschaft "Bereitstellungstyp" und andere SharePoint\-spezifische Eigenschaften zu aktivieren.  
  
 Ressourcendateien für ASPX\-Markup können auch zum Lokalisieren von Code verwendet werden.  Wenn Sie mithilfe der Ressourcen neben ASPX\-Markup auch Code lokalisieren, belassen Sie die Einstellung der Eigenschaft "Buildvorgang" der einzelnen Dateien auf "Eingebettete Ressource", damit die Ressource in eine Satellitenassembly kompiliert wird.  Wenn dagegen mit den Ressourcendateien ausschließlich Markup lokalisiert wird, können Sie optional die Einstellung für "Buildvorgang" zu "Inhalt" ändern, um zu verhindern, dass die Datei in die Hauptanwendungsassembly kompiliert wird.  
  
 Ersetzen Sie im Markup der ASPX\-Seiten und \-Steuerelemente alle hartcodierten Eigenschaftenzeichenfolgen durch einen Ausdruck im folgenden Format:  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Beispiel:  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Verwenden Sie für ASPX als Text einen Ausdruck im folgenden Format:  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Beispiel:  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md).  
  
### Lokalisieren von Code  
 Neben Funktionszeichenfolgen und [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Markup müssen auch die im Code der Lösung enthaltenen Meldungs\- und Fehlerzeichenfolgen lokalisiert werden.  Lokalisierte Informations\- und Fehlermeldungen sind in Satellitenassemblys enthalten.  Satellitenassemblys enthalten Zeichenfolgen, die Benutzern angezeigt werden, beispielsweise [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]\-Text und Ausgabemeldungen wie Ausnahmen.  
  
 Von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird das standardmäßige Hub\- und Spoke\-Modell von .NET Framework verwendet.  Der Hub \(Hauptprogrammassembly\) enthält die Ressourcen für die Standardsprache.  Die Spokes \(Satellitenassemblys\) enthalten die sprachspezifischen Ressourcen.  Weitere Informationen finden Sie unter [Verpacken und Bereitstellen von Ressourcen](http://go.microsoft.com/fwlink/?LinkId=179280).  Satellitenassemblys werden aus Ressourcendateien \(RESX\-Dateien\) kompiliert.  Wenn Sie dem Projekt und dem Lösungspaket sprachspezifische Ressourcendateien hinzufügen, werden die Ressourcendateien von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zu Satellitenassemblys mit dem Namen "*Project Name*.resources.dll" kompiliert.  
  
 Beim Lokalisieren von SharePoint\-Anwendungscode müssen dem Projekt genau wie bei ASPX\-Markup separate Ressourcendatei\-Projektelemente hinzugefügt werden. Dabei wird jeweils ein Element für die Standardsprache und ein Element für jede lokalisierte Sprache hinzugefügt.  Wie jedoch zuvor bereits erwähnt: Wenn Sie bereits über Ressourcendateien zum Lokalisieren von ASPX\-Markup verfügen, können Sie diese für die Lokalisierung des Codes wiederverwenden.  Wenn Sie Ressourcendateien erstellen müssen, benennen Sie die Ressourcendatei für die Standardsprache mit einem beliebigen Namen, gefolgt von der Erweiterung ".resx".  Benennen Sie die lokalisierten Ressourcendateien mit dem gleichen Namen, und fügen Sie diesem jeweils die sprachspezifische [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]\-ID an.  Legen Sie die Eigenschaft "Buildvorgang" der einzelnen Ressourcendateien auf "Eingebettete Ressource" fest, um die Erstellung von Satellitenressourcenassemblys zu aktivieren.  
  
 Erstellen Sie zum Erstellen der Satellitenassemblys das Projekt, und fügen Sie die Dateien mithilfe der Registerkarte **Erweitert** des Paket\-Designers als zusätzliche Assemblys hinzu.  Stellen Sie dem Pfad zum Speicherort beim Hinzufügen der Assemblys einen Kultur\-[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]\-Ordner voran \(beispielsweise "de\-DE\\*Project Item Name*.resources.dll"\).  Dadurch kann das Paket Dateien mit dem gleichen Namen enthalten.  
  
 Ersetzen Sie hartcodierte Zeichenfolgen im Code durch Aufrufe der <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>\-Methode, und verwenden Sie dabei die folgende Syntax:  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Lokalisieren von Code](../sharepoint/how-to-localize-code.md).  
  
#### Lokalisieren von Webpartcode  
 Webparts enthalten eine benutzerdefinierte Funktion des Eigenschaften\-Editors mit Codeattributen, von denen hartcodierte Zeichenfolgen wie "WebDisplayName", "Category" oder "WebDescription" verwendet werden.  Erstellen Sie eine separate, von der Klasse des Attributs abgeleitete Klasse, um die Zeichenfolgenwerte für diese Attribute zu ersetzen.  Legen Sie in diesen Klassen die Eigenschaft des Attributs fest.  Die Attributeigenschaft hängt von der Basisklasse ab.  So lautet beispielsweise die WebDisplayName\-Attributeigenschaft "DisplayNameValue", und die WebDescription\-Attributeigenschaft lautet "DescriptionValue".  
  
 Verweisen Sie in der abgeleiteten Klasse auf die Zeichenfolgen\-ID aus der Ressourcendatei sowie auf das ResourceManager\-Objekt, um den lokalisierten Wert für die Zeichenfolgen\-ID abzurufen.  Geben Sie diesen Wert an das Eigenschaften\-Editor\-Attribut zurück.  
  
## Siehe auch  
 [Gewusst wie: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)   
 [Gewusst wie: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)   
 [Gewusst wie: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)   
 [Gewusst wie: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)   
 [Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  