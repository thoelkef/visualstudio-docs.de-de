---
title: Ersetzbare Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
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
ms.workload: office
ms.openlocfilehash: f6e311f7c0268cecb94498fffda702438ea921b0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119236"
---
# <a name="replaceable-parameters"></a>Ersetzbare Parameter
  Ersetzbare Parameter oder *Token*, kann in Projektdateien verwendet werden, um Werte für SharePoint-Projektmappenelemente bereitzustellen, deren tatsächliche Werte werden nicht zur Entwurfszeit bekannt. Sie sind ähnlich wie in der Funktion die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vorlagentoken. Weitere Informationen finden Sie unter [Vorlagenparameter](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Tokenformat
 Token beginnen und enden mit einem Dollarzeichen ($). Bei Bereitstellung werden alle verwendeten Token durch tatsächliche Werte ersetzt, wenn ein Projekt in einer SharePoint-Lösungspaket verpackt wird (*.wsp* Datei). Zum Beispiel das Token **$SharePoint.Package.Name$** möglicherweise auf die Zeichenfolge "Test-SharePoint-Paket" behoben.  
  
## <a name="token-rules"></a>Token-Regeln
 Die folgenden Regeln gelten für Token:  
  
-   Token können eine beliebige Stelle in einer Zeile angegeben werden.  
  
-   Token können nicht mehrere Zeilen umfassen.  
  
-   Das gleiche Token kann mehr als einmal in der gleichen Zeile und in der gleichen Datei angegeben werden.  
  
-   Unterschiedliche Token können in der gleichen Zeile angegeben werden.  
  
 Token, die diese Regeln nicht folgen werden ignoriert, und nicht dazu, dass eine Warnung oder einen Fehler.  
  
 Die Ersetzung des Token durch Zeichenfolgenwerte erfolgt sofort nach der manifest-Transformation. Diese Ersetzung ermöglicht die Benutzer, die Manifestdateien Vorlagen mit Token zu bearbeiten.  
  
### <a name="token-name-resolution"></a>Token-Namen auflösen
 In den meisten Fällen löst auf ein Token auf einen bestimmten Wert, unabhängig davon, in dem es enthalten ist. Wenn das Token auf ein Paket oder eine Funktion verknüpft ist, hängt jedoch des Tokens-Wert, in dem es enthalten ist. Beispielsweise ist eine Funktion im Paket ein, und klicken Sie dann das Token `$SharePoint.Package.Name$` ergibt den Wert "Paket A." Wenn dasselbe Feature im Paket B, dann ist `$SharePoint.Package.Name$` zu "Paket b" aufgelöst.  
  
## <a name="tokens-list"></a>Tokenliste
 Die folgende Tabelle enthält die verfügbaren Token.  
  
|name|Beschreibung|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Die Namen der Projektdatei, z. B. *NewProj.csproj*.|  
|$SharePoint.Project.FileNameWithoutExtension$|Der Name der enthaltenden Projektdatei ohne die Dateinamenerweiterung. Zum Beispiel: "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Der Anzeigename (starker Name) des enthaltenden Projekts Ausgabeassembly.|  
|$SharePoint.Project.AssemblyFileName$|Der Name des enthaltenden Projekts Ausgabeassembly.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Der Name des enthaltenden Projekts Ausgabeassembly, ohne die Dateinamenerweiterung.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Das Token des öffentliche Schlüssels des enthaltenden Projekts Ausgabeassembly, in eine Zeichenfolge konvertiert. (16-Zeichen "X2" Hexadezimalformat angegeben.)|  
|$SharePoint.Package.Name$|Der Name des Pakets enthält.|  
|$SharePoint.Package.FileName$|Der Name des dem entsprechenden Paket-Definitionsdatei.|  
|$SharePoint.Package.FileNameWithoutExtension$|Der Name (ohne Erweiterung), der dem entsprechenden Paket-Definitionsdatei.|  
|$SharePoint.Package.Id$|Die SharePoint-ID für das Paket enthält. Wenn eine Funktion in mehrere Pakete verwendet wird, ändert sich dieser Wert.|  
|$SharePoint.Feature.FileName$|Der Name der Definitionsdatei der enthaltenen Features wie z. B. *"Feature1.Feature"*.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Der Name des der Funktionsdefinitionsdatei, ohne die Dateinamenerweiterung.|  
|$SharePoint.Feature.DeploymentPath$|Der Name des Ordners, der die Funktion im Paket enthält. Dieses Token entspricht die Eigenschaft "Bereitstellungspfad" in der Funktions-Designer. Ein Beispielwert ist "Project1_Feature1".|  
|$SharePoint.Feature.Id$|Die SharePoint-ID der enthaltenden Funktion. Dieses Token hinzugefügt, wie mit alle Funktionsebene Token nur von Dateien in ein Paket über eine Funktion, die verwendet werden können nicht direkt auf ein Paket außerhalb einer Funktion.|  
|$SharePoint.ProjectItem.Name$|Der Name des Projektelements (nicht der Name der Objektdatei), als aus abgerufen **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|Die Assembly qualifizierten Namen der übereinstimmenden Typ der [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] des Tokens. Das Format der [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] Kleinbuchstaben und entspricht dem Format Kleinschreibung verwendet (d. h. Xxxxxxxx-Xxxx-Xxxx-Xxxx-Xxxxxxxxxxxx).|  
|$SharePoint.Type. \<GUID >. "FullName" $|Der vollständige Name des Typs der GUID im Token. Das Format der GUID ist in Kleinbuchstaben und entspricht dem Format Kleinschreibung verwendet (d. h. Xxxxxxxx-Xxxx-Xxxx-Xxxx-Xxxxxxxxxxxx).|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Erweiterungen der tokenersetzung Datei Extensions-Liste hinzufügen
 Obwohl das Token theoretisch durch eine beliebige Datei verwendet werden können, die zu einem SharePoint-Projekt, das Element im Paket enthalten sind, in der Standardeinstellung gehört [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sucht Token nur in Paketdateien, manifest-Dateien und Dateien, die die folgenden Erweiterungen aufweisen:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX-DATEI  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 Diese Erweiterungen werden durch definiert die `<TokenReplacementFileExtensions>` Element in der Datei Microsoft.VisualStudio.SharePoint.targets befindet sich in der... \\< Programmdateien\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools-Ordner.  
  
 Sie können jedoch zusätzliche Erweiterungen zur Liste hinzufügen. Hinzufügen einer `<TokenReplacementFileExtensions>` Element alle PropertyGroup in der SharePoint-Projektdatei, bevor Sie definiert ist, die \<Import > von der SharePoint-Targets-Datei.  
  
> [!NOTE]  
>  Da tokenersetzung tritt auf, nachdem ein Projekt kompiliert wurde, sollten Sie keine Dateierweiterungen für Dateitypen, die, wie z. B. kompiliert werden, hinzufügen *cs*, *vb* oder *resx*. Token werden nur in Dateien ersetzt, die nicht kompiliert werden.  
  
 Um beispielsweise die Dateinamenerweiterungen Weitere Erweiterungen hinzufügen (*.myextension* und *.yourextension*) der Liste der Dateinamenerweiterungen tokenersetzung, würden Sie Folgendes zu einem Projekt hinzufügen (*csproj* ) Datei:  
  
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
  
 Sie können die Erweiterung hinzufügen, direkt an die Ziele (*targets*) Datei. Hinzufügen die Erweiterung ändert die Liste der Erweiterungen für alle SharePoint-Projekte, die auf dem lokalen System gepackt, jedoch nicht nur Ihre eigenen. Diese Erweiterung kann praktisch sein, wenn Sie der alleinige Entwickler auf dem System sind, oder, wenn die meisten Ihrer Projekte erforderlich ist. Allerdings hinzugefügt werden, da es spezifische ist dieser Ansatz nicht übertragbar ist und es daher empfohlen wird, Sie alle Erweiterungen in die Projektdatei stattdessen.  
  
## <a name="see-also"></a>Siehe auch
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)  
  
