---
title: Lokalisieren von SharePoint-Lösungen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7bcd11d7860e1d191479d4a2ea5f9fac78dcdfe2
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189222"
---
# <a name="localize-sharepoint-solutions"></a>Lokalisieren von SharePoint-Lösungen

  Die Vorbereitung von Anwendungen für eine weltweite Verwendung wird als Lokalisierung bezeichnet. Bei der Lokalisierung werden die Ressourcen für einen bestimmten Kulturkreis übersetzt. Weitere Informationen finden Sie unter [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md). Dieses Thema bietet eine Übersicht über die Lokalisierung einer SharePoint-Lösung.

 Für die Lokalisierung einer Lösung werden die hartcodierten Zeichenfolgen aus dem Code entfernt und in Ressourcendateien zusammengefasst. Eine Ressourcen Datei ist eine [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]basierte Datei mit der Erweiterung " *. resx* ". Die Ressourcendatei enthält die übersetzten Versionen der in der Lösung verwendeten Zeichenfolgen. Weitere Informationen finden Sie unter [Ressourcen in Anwendungen](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100)).

> [!NOTE]
> Fügen Sie Ressourcendateien von SharePoint-Lösungen ausschließlich Zeichenfolgenressourcen hinzu. Zwar ermöglicht der Ressourcen-Editor auch das Hinzufügen von Ressourcen, bei denen es sich nicht um Zeichenfolgen handelt, diese Ressourcen werden jedoch nicht für SharePoint bereitgestellt.

## <a name="resource-files"></a>Ressourcendateien
 Drei Arten von Ressourcendateien stehen zur Verfügung: Standarddateien, sprachunabhängige Dateien und sprachspezifische Dateien.

|Ressourcendateityp|Beschreibung|
|------------------------|-----------------|
|Default|Standardressourcendateien werden auch als Fallbackressource bezeichnet und enthalten lokalisierte Zeichenfolgen für die Standardkultur (beispielsweise Englisch). Sie werden verwendet, wenn keine lokalisierten Ressourcendateien für die angegebene Sprache gefunden werden. Standardressourcen besitzen keine separaten Dateien und sind in der Hauptanwendungsassembly gespeichert.|
|Sprachunabhängig|Eine Ressourcendatei mit lokalisierten Zeichenfolgen für eine Sprache, aber nicht für eine bestimmte Kultur. Beispiel: "fr" für Französisch.|
|Sprachspezifisch|Eine Ressourcendatei mit lokalisierten Zeichenfolgen für eine Sprache und eine Kultur. Beispiel: "fr-CA" für Französisch (Kanada).|

 Weitere Informationen finden Sie unter [hierarchische Organisation der Ressourcen für die Lokalisierung](../ide/globalizing-and-localizing-applications.md).

 Um Standard Ressourcen Dateien in SharePoint-Projekten anzugeben, die Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]entwickeln, wählen Sie in der Liste Kultur des Dialog Felds **Ressource hinzufügen** die Option **invariante Sprache (invarianter Land)** aus, wenn Sie eine Ressourcen Datei hinzufügen.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Lokalisieren von Visual Studio SharePoint-Lösungen
 Beim Lokalisieren einer Lösung müssen alle den Benutzern angezeigten Textinformationen berücksichtigt werden. Informationsmeldungen, Fehlermeldungen und [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]-Zeichenfolgen müssen übersetzt und die Übersetzungen in die Ressourcendateien eingefügt werden.

 Jede Zeichenfolge in einer Ressourcendatei besitzt einen eindeutigen Bezeichner. Verwenden Sie in jeder Ressourcendatei den gleichen Bezeichner für die übersetzte Zeichenfolge. Wenn also "String1" der Bezeichner für die erste Zeichenfolge in der Standardressourcendatei ist, verwenden Sie diesen Bezeichner auch in den sprachspezifischen Ressourcendateien für die erste Zeichenfolge.

 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Anwendungen werden in der Regel drei Bereiche lokalisiert: Funktionen, ASPX-Seitenmarkup und Code. Zur Veranschaulichung wird in den folgenden Abschnitten von einer SharePoint-Lösung ausgegangen, die ins Deutsche und ins Japanische lokalisiert werden soll. Die Standardsprache ist Englisch.

### <a name="localize-features"></a>Lokalisieren von Features
 Zum Lokalisieren einer Funktion müssen der hartcodierte Titel und die Beschreibung der Funktion durch einen Ausdruck ersetzt werden, durch den auf den übersetzten Titel und die Zeichenfolge in der lokalisierten Ressourcendatei verwiesen wird. Sie nehmen diese Änderung im **Funktions-Designer** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]vor. Weitere Informationen finden Sie unter Vorgehens [Weise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md).

 Zum Lokalisieren der englischen Funktion für Deutsch und Japanisch werden dem Projekt drei Ressourcendatei-Projektelemente hinzugefügt – jeweils eins für Englisch, Deutsch und Japanisch. Funktionsressourcendateien können nicht zum Lokalisieren von ASPX-Markup oder -Code verwendet werden. Hierfür werden separate Ressourcendateien benötigt.

 Nach dem Erstellen der Funktionsressourcendateien werden ihnen die übersetzten Zeichenfolgen hinzugefügt. Der Zugriff auf die lokalisierten Zeichenfolgen erfolgt mittels eines Ausdrucks im folgenden Format:

```aspx-csharp
$Resources:String ID
```

 Funktionsressourcen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden immer mit „Resources“ benannt. Wenn Sie eine andere Sprache als die invariante Sprache auswählen, wird dem Ressourcendateinamen die Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] hinzugefügt. Wenn Sie z. b. eine Funktions Ressourcen Datei mit invarianter Sprache (Standard) hinzufügen, wird Sie als " *Resources. resx*" bezeichnet. Wenn Sie eine sprachspezifische Funktions Ressource hinzufügen, indem Sie eine Kultur von Japanisch (Japan) auswählen, wird die Datei " *Resources. ja-JP. resx*" genannt. Der Name einer Funktionsressourcendatei wird automatisch zugewiesen und kann nicht geändert werden.

 Der Bereich von Funktionsressourcen ist für die Funktion, der sie hinzugefügt werden, lokal. Fügen Sie zum Erstellen von Ressourcen, die von jeder Funktions-oder Element Datei in der Lösung verwendet werden können, anstelle einer featureressourcendatei ein **globales Ressourcen Datei** -Projekt Element hinzu. Das Projekt Element " **Global Resources File** " befindet sich im Ordner " **2010** " unter **SharePoint** im Dialogfeld **Neues Element hinzufügen** . Das Bereitstellungsziel globaler Ressourcendateien ist der Ordner "\Resources" des SharePoint-Stammordners.

### <a name="localize-aspx-page-markup"></a>Lokalisieren von ASPX-Seiten Markup
 Um [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Seiten zu lokalisieren, fügen Sie dem Projekt drei Ressourcen Datei-Projekt Elemente hinzu: eine für Englisch, eine für Deutsch und eine für Japanisch. Wenn Sie den Code nicht zusätzlich zum Markup lokalisieren müssen, können Sie stattdessen globale Ressourcen Dateien hinzufügen.

 Geben Sie einen Namen für die Ressourcendatei der Standardsprache an. Benennen Sie die lokalisierten Ressourcendateien mit dem gleichen Namen, und fügen Sie diesem jeweils die sprachspezifische [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]-ID an. Beispiel: *MyAppResources.de-de. resx* für Deutsch und *myappresources. ja-JP. resx* für Japanisch.

 Legen Sie die Eigenschaft **Bereitstellungstyp** jeder Ressourcen Datei auf **appglobalresource**fest. Dadurch werden die Ressourcendateien im Ordner "App_GlobalResources" bereitgestellt und stehen somit allen ASPX-Seiten und -Steuerelementen in der Lösung zur Verfügung. Der Ordner App_GlobalResources befindet sich in c:\Inetpub\wwwroot\wss\VirtualDirectories\\< Portnummer\>\App_GlobalResources.

> [!NOTE]
> Verschieben Sie bei Verwendung nicht globaler Ressourcendateien die nicht globalen Ressourcendateien in den Projektelementordner, um die Eigenschaft "Bereitstellungstyp" und andere SharePoint-spezifische Eigenschaften zu aktivieren.

 Ressourcendateien für ASPX-Markup können auch zum Lokalisieren von Code verwendet werden. Wenn Sie mithilfe der Ressourcen neben ASPX-Markup auch Code lokalisieren, belassen Sie die Einstellung der Eigenschaft "Buildvorgang" der einzelnen Dateien auf "Eingebettete Ressource", damit die Ressource in eine Satellitenassembly kompiliert wird. Wenn dagegen mit den Ressourcendateien ausschließlich Markup lokalisiert wird, können Sie optional die Einstellung für "Buildvorgang" zu "Inhalt" ändern, um zu verhindern, dass die Datei in die Hauptanwendungsassembly kompiliert wird.

 Ersetzen Sie im Markup der ASPX-Seiten und -Steuerelemente alle hartcodierten Eigenschaftenzeichenfolgen durch einen Ausdruck im folgenden Format:

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Beispiel:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 Verwenden Sie für ASPX als Text einen Ausdruck im folgenden Format:

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Beispiel:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Weitere Informationen finden Sie unter Gewusst [wie: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md).

### <a name="localize-code"></a>Lokalisieren von Code
 Neben Funktionszeichenfolgen und [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]-Markup müssen auch die im Code der Lösung enthaltenen Meldungs- und Fehlerzeichenfolgen lokalisiert werden. Lokalisierte Informations- und Fehlermeldungen sind in Satellitenassemblys enthalten. Satellitenassemblys enthalten Zeichenfolgen, die Benutzern angezeigt werden, beispielsweise [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)]-Text und Ausgabemeldungen wie Ausnahmen.

 Von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird das standardmäßige Hub- und Spoke-Modell von .NET Framework verwendet. Der Hub (Hauptprogrammassembly) enthält die Ressourcen für die Standardsprache. Die Spokes oder Satellitenassemblys enthalten die sprachspezifischen Ressourcen. Weitere Informationen finden Sie unter [Verpacken und Bereitstellen von Ressourcen](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100)). Satellitenassemblys werden aus Ressourcen Dateien (*RESX*-Dateien) kompiliert. Wenn Sie dem Projekt und dem Projektmappenpaket sprachspezifische Ressourcen Dateien hinzufügen, werden die Ressourcen Dateien von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] in Satellitenassemblys mit dem Namen " *{Project Name}. resources. dll*" kompiliert.

 Beim Lokalisieren von SharePoint-Anwendungscode müssen dem Projekt genau wie bei ASPX-Markup separate Ressourcendatei-Projektelemente hinzugefügt werden. Dabei wird jeweils ein Element für die Standardsprache und ein Element für jede lokalisierte Sprache hinzugefügt. Wie jedoch zuvor bereits erwähnt: Wenn Sie bereits über Ressourcendateien zum Lokalisieren von ASPX-Markup verfügen, können Sie diese für die Lokalisierung des Codes wiederverwenden. Wenn Sie Ressourcen Dateien erstellen müssen, benennen Sie die Standard Sprachressourcen Datei mit der Erweiterung " *. resx* ". Benennen Sie die lokalisierten Ressourcendateien mit dem gleichen Namen, und fügen Sie diesem jeweils die sprachspezifische [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]-ID an. Legen Sie die Eigenschaft "Buildvorgang" der einzelnen Ressourcendateien auf "Eingebettete Ressource" fest, um die Erstellung von Satellitenressourcenassemblys zu aktivieren.

 Um die Satellitenassemblys zu erstellen, erstellen Sie das Projekt, und fügen Sie dann die Dateien als zusätzliche Assemblys über die Registerkarte **erweitert** des **Paket-Designers** Stellen Sie beim Hinzufügen der Assemblys eine Kultur [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] Ordners dem Speicherort Pfad voran, z. b. " *de-de"\\{Project Item Name}. resources. dll*. Dadurch kann das Paket Dateien mit dem gleichen Namen enthalten.

 Ersetzen Sie hartcodierte Zeichenfolgen im Code durch Aufrufe der <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>-Methode, und verwenden Sie dabei die folgende Syntax:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Weitere Informationen finden Sie unter Gewusst [wie: Lokalisieren von Code](../sharepoint/how-to-localize-code.md).

#### <a name="web-part-code-localization"></a>Lokalisierung des webpartcodes
 Webparts enthalten eine benutzerdefinierte Funktion des Eigenschaften-Editors mit Codeattributen, von denen hartcodierte Zeichenfolgen wie „WebDisplayName“, „Category“ oder „WebDescription“ verwendet werden. Erstellen Sie eine separate, von der Klasse des Attributs abgeleitete Klasse, um die Zeichenfolgenwerte für diese Attribute zu ersetzen. Legen Sie in diesen Klassen die Eigenschaft des Attributs fest. Die Attributeigenschaft hängt von der Basisklasse ab. So lautet beispielsweise die WebDisplayName-Attributeigenschaft "DisplayNameValue", und die WebDescription-Attributeigenschaft lautet "DescriptionValue".

 Verweisen Sie in der abgeleiteten Klasse auf die Zeichenfolgen-ID aus der Ressourcendatei sowie auf das ResourceManager-Objekt, um den lokalisierten Wert für die Zeichenfolgen-ID abzurufen. Geben Sie diesen Wert an das Eigenschaften-Editor-Attribut zurück.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Lokalisieren einer Funktion](../sharepoint/how-to-localize-a-feature.md)
- [Gewusst wie: Lokalisieren von ASPX-Markup](../sharepoint/how-to-localize-aspx-markup.md)
- [Vorgehensweise: Lokalisieren von Code](../sharepoint/how-to-localize-code.md)
- [Vorgehensweise: Hinzufügen einer Ressourcen Datei](../sharepoint/how-to-add-a-resource-file.md)
- [Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcen Datei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
