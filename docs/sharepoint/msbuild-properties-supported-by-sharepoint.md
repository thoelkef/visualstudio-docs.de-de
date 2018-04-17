---
title: MSBuild-Eigenschaften, die von SharePoint unterstützte | Microsoft Docs
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
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1e60843119ee72f1164288f50b27116cdda31e9b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Von SharePoint unterstützte MSBuild-Eigenschaften
  Alle [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] der Microsoft.VisualStudio.SharePoint.targets Datei, die Projektdatei oder die Benutzer-Projektdatei definierte Eigenschaft kann verwendet werden, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekte. Zusätzlich zu den allgemeinen [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften, die von der SharePoint-Projekt bereitgestellten definiert zusätzliche Eigenschaften, die spezifisch für SharePoint-Projekte sind.  
  
 Eine Liste der allgemeinen [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften finden Sie in [gemeinsame MSBuild-Projekteigenschaften](http://go.microsoft.com/fwlink/?LinkID=168687). Eine vollständige Liste der Eigenschaften, die von der Programmiersprache unterstützt, finden Sie in den TARGETS-Datei, die Projektdatei (.csproj oder .vbproj) oder die Projektdatei des Benutzers (csproj.user oder. vbproj.user).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>MSBuild-spezifische Eigenschaften in SharePoint  
 Die folgende Tabelle enthält [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften, die speziell für die SharePoint-Projekte in gelten [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Andere Eigenschaften vorhanden, aber sie sind für die interne Verwendung.  
  
|Eigenschaftenname|Beschreibung|  
|-------------------|-----------------|  
|' SharePointSiteUrl '|Eine Zeichenfolge, die stellt die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] zur SharePoint-Website.|  
|SandboxedSolution|Ein boolescher Wert, der angibt, ob die Lösung eine Sandbox geeignet ist.|  
|ActiveDeploymentConfiguration|Die aktive Bereitstellungskonfiguration.|  
|IncludeAssemblyInPackage|Ein boolescher Wert, der angibt, ob die Assembly im Paket enthalten ist.|  
|PreDeploymentCommand|Ein Zeichenfolgenwert, der im Befehl vor der Bereitstellung-Schritt-Anweisung auszuführende Befehl darstellt.|  
|PostDeploymentCommand|Ein Zeichenfolgenwert, der im Befehl nach der Bereitstellung-Schritt-Anweisung auszuführende Befehl darstellt.|  
|CustomBeforeSharePointTargets|Eine Zeichenfolge, die den Pfad des repräsentiert eine [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Targets-Datei. Wenn die Zieldatei vorhanden ist und definiert ist, wird sie vor allen anderen SharePoint-Ziele-Daten importiert. Diese Eigenschaft können Sie der Paketprozess durch vordefinieren Packaging-bezogene Eigenschaften anpassen, ohne die gelieferte SharePoint Targets-Datei ändern, aber Targets-Datei gilt weiterhin für alle SharePoint-Projekte.|  
|CustomAfterSharePointTargets|Eine Zeichenfolge, die den Pfad des repräsentiert eine [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Targets-Datei. Wenn die Zieldatei vorhanden ist und definiert ist, ist es nach allen SharePoint-Ziele-Daten importiert. Mit dieser Eigenschaft können Sie anpassen, wie der Paketprozess durch Überschreiben der Verpackung-bezogene Eigenschaften und Ziele ohne gelieferte SharePoint Targets-Datei ändern zu müssen, aber die Targets-Datei gilt weiterhin für alle SharePoint-Projekte.|  
|LayoutPath|Eine Zeichenfolge darstellt, das Stammverzeichnis, in dem alle Dateien verpackt werden vorübergehend platziert werden, bevor sie die WSP-Datei hinzugefügt werden. Dieser Pfad kann hilfreich zu wissen, wenn Sie überschreiben die BeforeLayout und AfterLayout Ziele hinzufügen, entfernen oder Ändern von Dateien verpackt werden, da Sie so ändern Sie den Inhalt der WSP-Datei verwendet werden können.|  
|BasePackagePath|Eine Zeichenfolge, die den Ordner darstellt, in dem das Paket befindet. Dieser Wert verwendet das Ausgabeverzeichnis des Projekts, z. B. "bin\Debug".|  
|PackageExtension|Eine Zeichenfolge, die die Dateinamenerweiterung zum Anfügen an das Paket darstellt. Der Standardwert ist Wsp.|  
|AssemblyDeploymentTarget|Eine Zeichenfolge, die den Speicherort darstellt, in dem die Projektassembly auf dem SharePoint-Server bereitgestellt wird. Der Wert ist GlobalAssemblyCache (Standard) oder WebApplication. Diese Eigenschaft kann auch im Eigenschaftenfenster festgelegt werden.|  
|PackageWithValidation|Ein boolescher Wert, der angibt, ob die Überprüfung vor dem Packen. Diese Eigenschaft können Sie die Überprüfungsfehler ignorieren beim Erstellen von Paketen.|  
|ValidatePackageDependsOn|Eine Zeichenfolge, die zusätzliche Ziele ausgeführt wird, bevor das ValidatePackage Ziel definiert.|  
|TokenReplacementFileExensions|Eine Zeichenfolge, die Dateien definiert, die ihren Token, die während des Verpackens ersetzt haben.|  
  
## <a name="using-msbuild-properties-in-the-properties-page"></a>Verwenden von MSBuild-Eigenschaften in der Seite "Eigenschaften"  
 Für Flexibilität, anstelle von hartcodierten Zeichenfolgen in die **vor der Bereitstellung über die Befehlszeile** und **nach der Bereitstellung über die Befehlszeile** Felder auf der Seite "SharePoint-Eigenschaften" können Sie die SharePoint die Eigenschaften als Argumente. Z. B. angeben, statt einen bestimmten [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] Zeichenfolge für die SharePoint-Website können Sie stattdessen `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Verwenden Sie entweder die [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Variable Syntax `$(` *PropertyName* `)` oder die Umgebungsvariablensyntax `%` *PropertyName* `%` Um eine Eigenschaft anzugeben.  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild-Referenz](/visualstudio/msbuild/msbuild-reference)  
  
  