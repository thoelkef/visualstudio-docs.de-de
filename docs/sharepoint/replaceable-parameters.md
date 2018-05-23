---
title: Ersetzbare Parameter | Microsoft Docs
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
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86d6b08d209703f73901d7a839c731e1a9a63fdd
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
---
# <a name="replaceable-parameters"></a>Ersetzbare Parameter
  Ersetzbare Parameter oder *Token*, können in Projektdateien verwendet werden, um Werte für SharePoint-Projektmappenelemente bereitzustellen, deren tatsächliche Werte zur Entwurfszeit nicht bekannt sind. Sie sind Funktion ähnelt dem Standard [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vorlagentoken. Weitere Informationen finden Sie unter [Vorlagenparameter](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Tokenformat  
 Token beginnen und enden mit einem Dollarzeichen ($). Bereitstellung werden alle Token verwendet durch tatsächliche Werte ersetzt, wenn ein Projekt, in einer SharePoint-Lösungspaket (WSP-Datei verpackt wird). Z. B. das Token **$SharePoint.Package.Name$** möglicherweise behoben, um die Zeichenfolge "Test der SharePoint-Paket".  
  
## <a name="token-rules"></a>Token Regeln  
 Die folgenden Regeln gelten für Token:  
  
-   Token können eine beliebige Stelle in einer Zeile angegeben werden.  
  
-   Token können nicht mehrere Zeilen umfassen.  
  
-   Das gleiche Token möglicherweise mehrere Male in derselben Zeile und in derselben Datei angegeben werden.  
  
-   Unterschiedliche Token können in derselben Zeile angegeben werden.  
  
 Token, die nicht diese Regeln folgen werden ignoriert, ohne eine Warnung oder einen Fehler.  
  
 Das Ersetzen von Token durch Zeichenfolgenwerte erfolgt sofort nach der manifest-Transformation. Diese Ersetzung kann der Benutzer das Manifesten Vorlagen mit Token zu bearbeiten.  
  
### <a name="token-name-resolution"></a>Tokenname Auflösung  
 In den meisten Fällen löst ein Token auf einen bestimmten Wert, unabhängig davon, in dem sie enthalten ist. Wenn das Token auf ein Paket oder eine Funktion verknüpft ist, hängt jedoch das Token-Wert, in dem sie enthalten ist. Beispielsweise ist eine Funktion ein, und klicken Sie dann das Token Packen `$SharePoint.Package.Name$` aufgelöst wird, auf den Wert "Paket a" Wenn die gleiche Funktion klicken Sie dann im Paket-B ist `$SharePoint.Package.Name$` zu "Paket b" aufgelöst.  
  
## <a name="tokens-list"></a>Tokenliste  
 Die folgende Tabelle enthält die verfügbaren Token.  
  
|name|Beschreibung|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Der Name der enthaltenden Projektdatei, z. B. "NewProj.csproj".|  
|$SharePoint.Project.FileNameWithoutExtension$|Der Name der enthaltenden Projektdatei ohne die Dateinamenerweiterung. Zum Beispiel: "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Der Anzeigename (starker Name) des enthaltenden Projekts Ausgabeassembly.|  
|$SharePoint.Project.AssemblyFileName$|Der Name des enthaltenden Projekts Ausgabeassembly.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Der Name des enthaltenden Projekts Ausgabe Assembly ohne die Dateinamenerweiterung.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Das Token des öffentliche Schlüssels des enthaltenden Projekts Ausgabe Assembly, in eine Zeichenfolge konvertiert. (16-Zeichen in "X2" Hexadezimalformat.)|  
|$SharePoint.Package.Name$|Der Name des Pakets enthält.|  
|$SharePoint.Package.FileName$|Der Name der dem entsprechenden Paket-Definitionsdatei.|  
|$SharePoint.Package.FileNameWithoutExtension$|Der Name (ohne Erweiterung), der dem entsprechenden Paket-Definitionsdatei.|  
|$SharePoint.Package.Id$|Die SharePoint-ID für das Paket enthält. Wenn eine Funktion in mehreren Paketen verwendet wird, wird dieser Wert geändert.|  
|$SharePoint.Feature.FileName$|Der Name der Definitionsdatei der enthaltenden Funktion, z. B. "Feature1.Feature".|  
|$SharePoint.Feature.FileNameWithoutExtension$|Der Name von der Funktionsdefinitionsdatei, ohne die Dateinamenerweiterung.|  
|$SharePoint.Feature.DeploymentPath$|Der Name des Ordners, der die Funktion im Paket enthält. Dieses Token entspricht der Eigenschaft "Bereitstellungspfad" im Funktions-Designer. Ein Beispielwert ist "Project1_Feature1".|  
|$SharePoint.Feature.Id$|Die SharePoint-ID der enthaltenden Funktion. Dieses Token hinzugefügt, da nur von Dateien in ein Paket über eine Funktion, die mit allen Funktionsebene Token verwendet werden kann nicht direkt zu einem Paket außerhalb einer Funktion.|  
|$SharePoint.ProjectItem.Name$|Der Name des Projektelements (nicht der Dateiname), als vom erhaltenen **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|Die Assembly qualifizierten Namen der übereinstimmenden Typ der [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] des Tokens. Das Format der [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] Kleinbuchstaben und entspricht dem Format Kleinschreibung verwendet (also Xxxxxxxx-Xxxx-Xxxx-Xxxx-Xxxxxxxxxxxx).|  
|$SharePoint.Type. \<GUID >. FullName$|Der vollständige Name des Typs der GUID im Token. Das Format der GUID Kleinbuchstaben und entspricht dem Format Kleinschreibung verwendet (also Xxxxxxxx-Xxxx-Xxxx-Xxxx-Xxxxxxxxxxxx).|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>Hinzufügen von Erweiterungen für die Tokenersetzung Datei Erweiterungsliste  
 Obwohl Token theoretisch von einer beliebigen Datei verwendet werden können, die zu einem SharePoint-Projekt, das standardmäßig im Paket enthaltenen gehört [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sucht Token nur Paketdateien, die Manifestdateien und Dateien mit den folgenden Erweiterungen:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX-DATEI  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 Diese Erweiterungen werden definiert, indem die `<TokenReplacementFileExtensions>` Element in der Datei Microsoft.VisualStudio.SharePoint.targets befindet sich in der... \\<-Programmdateien\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools Ordner.  
  
 Sie können jedoch zusätzliche Erweiterungen zur Liste hinzufügen. Hinzufügen einer `<TokenReplacementFileExtensions>` Element jeder PropertyGroup in der SharePoint-Projektdatei, bevor Sie definiert ist, die \<Import > von der SharePoint-Targets-Datei.  
  
> [!NOTE]  
>  Da tokenersetzung tritt auf, nachdem ein Projekt kompiliert ist, sollten Sie nicht für Dateitypen, die kompiliert werden, z. B. cs,. vb oder RESX-Erweiterungen hinzufügen. Token werden nur in Dateien ersetzt, die nicht kompiliert werden.  
  
 Um die Datei namens Extensions ".myextension" und ".yourextension" die Liste der Dateinamenerweiterungen tokenersetzung hinzuzufügen, fügen Sie beispielsweise Folgendes verwenden, um eine `.csproj` Datei:  
  
```xml  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Sie können die Erweiterung direkt an die TARGETS-Datei hinzufügen. Allerdings auf diese Weise die Liste der Erweiterungen für alle SharePoint-Projekte, die nicht nur auf dem lokalen System verpackt ändert eigene. Dies kann praktisch sein, wenn Sie der einzige Entwickler im System sind oder Großteil Ihrer Projekte erforderlich. Jedoch hinzugefügt werden, da es systemspezifische ist, diese Vorgehensweise nicht sehr leicht portieren ist und aus diesem Grund empfohlen, die wird Sie alle Erweiterungen an der Projektdatei stattdessen.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  