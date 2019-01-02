---
title: Lokalisieren von SharePoint-Lösungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3897efa937991b598f6aae1cf24781ab2ce26c37
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684742"
---
# <a name="localize-sharepoint-solutions"></a>Lokalisieren von SharePoint-Lösungen

  Die Vorbereitung von Anwendungen für eine weltweite Verwendung wird als Lokalisierung bezeichnet. Bei der Lokalisierung werden die Ressourcen für einen bestimmten Kulturkreis übersetzt. Weitere Informationen finden Sie unter [Globalizing and Localizing Applications](../ide/globalizing-and-localizing-applications.md). Dieses Thema bietet eine Übersicht über die Lokalisierung einer SharePoint-Lösung.  
  
 Für die Lokalisierung einer Lösung werden die hartcodierten Zeichenfolgen aus dem Code entfernt und in Ressourcendateien zusammengefasst. Eine Ressourcendatei ist ein [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]--basierte Datei mit einer *resx* Erweiterung. Die Ressourcendatei enthält die übersetzten Versionen der in der Lösung verwendeten Zeichenfolgen. Weitere Informationen finden Sie unter [Ressourcen in Anwendungen](http://go.microsoft.com/fwlink/?LinkID=155844).  
  
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
  
 An Standardressourcendateien in SharePoint-Projekten, die Sie in entwickeln [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie **invarianten Sprache (Invariantes Land)** in der Kulturliste des der **Ressource hinzufügen** Dialogfeld, wenn Sie Fügen Sie eine Ressourcendatei hinzu.  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>Lokalisieren von Visual Studio SharePoint-Lösungen
 Beim Lokalisieren einer Lösung müssen alle den Benutzern angezeigten Textinformationen berücksichtigt werden. Informationsmeldungen, Fehlermeldungen und [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]-Zeichenfolgen müssen übersetzt und die Übersetzungen in die Ressourcendateien eingefügt werden.  
  
 Jede Zeichenfolge in einer Ressourcendatei besitzt einen eindeutigen Bezeichner. Verwenden Sie in jeder Ressourcendatei den gleichen Bezeichner für die übersetzte Zeichenfolge. Wenn also "String1" der Bezeichner für die erste Zeichenfolge in der Standardressourcendatei ist, verwenden Sie diesen Bezeichner auch in den sprachspezifischen Ressourcendateien für die erste Zeichenfolge.  
  
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Anwendungen werden in der Regel drei Bereiche lokalisiert: Funktionen, ASPX-Seitenmarkup und Code. Zur Veranschaulichung wird in den folgenden Abschnitten von einer SharePoint-Lösung ausgegangen, die ins Deutsche und ins Japanische lokalisiert werden soll. Die Standardsprache ist Englisch.  
  
### <a name="localize-features"></a>Lokalisieren von Funktionen
 Zum Lokalisieren einer Funktion müssen der hartcodierte Titel und die Beschreibung der Funktion durch einen Ausdruck ersetzt werden, durch den auf den übersetzten Titel und die Zeichenfolge in der lokalisierten Ressourcendatei verwiesen wird. Sie stellen diese Änderung in der **Funktions-Designer** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md).  
  
 Zum Lokalisieren der englischen Funktion für Deutsch und Japanisch werden dem Projekt drei Ressourcendatei-Projektelemente hinzugefügt – jeweils eins für Englisch, Deutsch und Japanisch. Funktionsressourcendateien können nicht zum Lokalisieren von ASPX-Markup oder -Code verwendet werden. Hierfür werden separate Ressourcendateien benötigt.  
  
 Nach dem Erstellen der Funktionsressourcendateien werden ihnen die übersetzten Zeichenfolgen hinzugefügt. Der Zugriff auf die lokalisierten Zeichenfolgen erfolgt mittels eines Ausdrucks im folgenden Format:  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 Funktionsressourcen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden immer mit "Resources" benannt. Wenn Sie eine andere Sprache als die invariante Sprache auswählen, wird dem Ressourcendateinamen die Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] hinzugefügt. Z. B. Wenn Sie eine Ressourcendatei für Invariante Sprache (Standard)-Funktion hinzufügen, es heißt *"Resources.resx"*. Wenn Sie eine sprachspezifische Funktionsressource hinzufügen, durch Auswahl einer Kultur Japanisch (Japan), kann die Datei heißt *Resources.ja-JP.resx*. Der Name einer Funktionsressourcendatei wird automatisch zugewiesen und kann nicht geändert werden.  
  
 Der Bereich von Funktionsressourcen ist für die Funktion lokal, der sie hinzugefügt werden. Um Ressourcen zu erstellen, die von jeder Funktions- oder Elementdatei-Datei in der Projektmappe verwendet werden kann, fügen einen **globale Ressourcendatei** Projektelement anstelle einer Funktionsressourcendatei Datei. Die **globale Ressourcendatei** Projektelement befindet sich in der **2010** Ordner unter **SharePoint** in die **neues Element hinzufügen** Dialogfeld. Das Bereitstellungsziel globaler Ressourcendateien ist der Ordner "\Resources" des SharePoint-Stammordners.  
  
### <a name="localize-aspx-page-markup"></a>Lokalisieren von ASPX-Seitenmarkup
 Zum Lokalisieren von [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten Sie dem Projekt drei Ressourcendatei-Projektelemente hinzufügen: eins für Englisch, Deutsch und Japanisch. Wenn Sie nicht zum Lokalisieren von Code, neben dem Markup verfügen, können Sie stattdessen globale Ressourcendateien hinzufügen.  
  
 Geben Sie einen Namen für die Ressourcendatei der Standardsprache an. Benennen Sie die lokalisierten Ressourcendateien mit dem gleichen Namen, und fügen Sie diesem jeweils die sprachspezifische [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]-ID an. Z. B. *MyAppResources.de-DE.resx* für Deutsch und *MyAppResources.ja-JP.resx* für Japanisch.  
  
 Legen Sie die **Bereitstellungstyp** Eigenschaft der einzelnen Ressourcendateien auf **AppGlobalResource**. Dadurch werden die Ressourcendateien im Ordner "App_GlobalResources" bereitgestellt und stehen somit allen ASPX-Seiten und -Steuerelementen in der Lösung zur Verfügung. Der Ordner "App_GlobalResources" befindet sich im C:\inetpub\wwwroot\wss\VirtualDirectories\\< Portnummer\>\App_GlobalResources.  
  
> [!NOTE]  
>  Verschieben Sie bei Verwendung nicht globaler Ressourcendateien die nicht globalen Ressourcendateien in den Projektelementordner, um die Eigenschaft "Bereitstellungstyp" und andere SharePoint-spezifische Eigenschaften zu aktivieren.  
  
 Ressourcendateien für ASPX-Markup können auch zum Lokalisieren von Code verwendet werden. Wenn Sie mithilfe der Ressourcen neben ASPX-Markup auch Code lokalisieren, belassen Sie die Einstellung der Eigenschaft "Buildvorgang" der einzelnen Dateien auf "Eingebettete Ressource", damit die Ressource in eine Satellitenassembly kompiliert wird. Wenn dagegen mit den Ressourcendateien ausschließlich Markup lokalisiert wird, können Sie optional die Einstellung für "Buildvorgang" zu "Inhalt" ändern, um zu verhindern, dass die Datei in die Hauptanwendungsassembly kompiliert wird.  
  
 Ersetzen Sie im Markup der ASPX-Seiten und -Steuerelemente alle hartcodierten Eigenschaftenzeichenfolgen durch einen Ausdruck im folgenden Format:  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Zum Beispiel:  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 Verwenden Sie für ASPX als Text einen Ausdruck im folgenden Format:  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 Zum Beispiel:  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md).  
  
### <a name="localize-code"></a>Lokalisieren von code
 Neben Funktionszeichenfolgen und [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Markup müssen auch die im Code der Lösung enthaltenen Meldungs- und Fehlerzeichenfolgen lokalisiert werden. Lokalisierte Informations- und Fehlermeldungen sind in Satellitenassemblys enthalten. Satellitenassemblys enthalten Zeichenfolgen, die Benutzern angezeigt werden, beispielsweise [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]-Text und Ausgabemeldungen wie Ausnahmen.  
  
 Von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird das standardmäßige Hub- und Spoke-Modell von .NET Framework verwendet. Der Hub (Hauptprogrammassembly) enthält die Ressourcen für die Standardsprache. Die Spokes oder Satellitenassemblys, enthalten die sprachspezifischen Ressourcen. Weitere Informationen finden Sie unter [Verpacken und Bereitstellen von Ressourcen](http://go.microsoft.com/fwlink/?LinkId=179280). Satellitenassemblys werden aus Ressource kompiliert (*resx*) Dateien. Wenn Sie Ihr Projekt und dem Lösungspaket sprachspezifische Ressourcendateien hinzufügen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kompiliert die Dateien in Satellitenassemblys, die mit dem Namen *{Projektname}.resources.dll*.  
  
 Beim Lokalisieren von SharePoint-Anwendungscode müssen dem Projekt genau wie bei ASPX-Markup separate Ressourcendatei-Projektelemente hinzugefügt werden. Dabei wird jeweils ein Element für die Standardsprache und ein Element für jede lokalisierte Sprache hinzugefügt. Wie jedoch zuvor bereits erwähnt: Wenn Sie bereits über Ressourcendateien zum Lokalisieren von ASPX-Markup verfügen, können Sie diese für die Lokalisierung des Codes wiederverwenden. Wenn Sie Ressourcendateien erstellen möchten, benennen Sie die Ressourcendatei der Standardsprache der mit einem *resx* Erweiterung. Benennen Sie die lokalisierten Ressourcendateien mit dem gleichen Namen, und fügen Sie diesem jeweils die sprachspezifische [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]-ID an. Legen Sie die Eigenschaft "Buildvorgang" der einzelnen Ressourcendateien auf "Eingebettete Ressource" fest, um die Erstellung von Satellitenressourcenassemblys zu aktivieren.  
  
 Um die Satellitenassemblys zu erstellen, erstellen Sie das Projekt, und klicken Sie dann die Dateien als zusätzliche Assemblys durch Hinzufügen der **erweitert** Registerkarte die **-Paket-Designer**. Wenn Sie die Assemblys hinzufügen, stellen Sie eine Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] Ordner den Pfad zum Speicherort, z. B. *de-DE\\{Projektelementname}.resources.dll*. Dadurch kann das Paket Dateien mit dem gleichen Namen enthalten.  
  
 Ersetzen Sie hartcodierte Zeichenfolgen im Code durch Aufrufe der <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>-Methode, und verwenden Sie dabei die folgende Syntax:  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Lokalisieren von Code](../sharepoint/how-to-localize-code.md).  
  
#### <a name="web-part-code-localization"></a>Webpartcode
 Webparts enthalten eine benutzerdefinierte Funktion des Eigenschaften-Editors mit Codeattributen, von denen hartcodierte Zeichenfolgen wie „WebDisplayName“, „Category“ oder „WebDescription“ verwendet werden. Erstellen Sie eine separate, von der Klasse des Attributs abgeleitete Klasse, um die Zeichenfolgenwerte für diese Attribute zu ersetzen. Legen Sie in diesen Klassen die Eigenschaft des Attributs fest. Die Attributeigenschaft hängt von der Basisklasse ab. So lautet beispielsweise die WebDisplayName-Attributeigenschaft "DisplayNameValue", und die WebDescription-Attributeigenschaft lautet "DescriptionValue".  
  
 Verweisen Sie in der abgeleiteten Klasse auf die Zeichenfolgen-ID aus der Ressourcendatei sowie auf das ResourceManager-Objekt, um den lokalisierten Wert für die Zeichenfolgen-ID abzurufen. Geben Sie diesen Wert an das Eigenschaften-Editor-Attribut zurück.  
  
## <a name="see-also"></a>Siehe auch
 [Vorgehensweise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)   
 [Vorgehensweise: Lokalisieren von ASPX-markup](../sharepoint/how-to-localize-aspx-markup.md)   
 [Vorgehensweise: Lokalisieren von code](../sharepoint/how-to-localize-code.md)   
 [Vorgehensweise: Hinzufügen einer Ressourcendatei](../sharepoint/how-to-add-a-resource-file.md)   
 [Vorgehensweise: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
