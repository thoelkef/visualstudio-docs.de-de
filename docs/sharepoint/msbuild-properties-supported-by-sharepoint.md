---
title: Von SharePoint unterstützte MSBuild-Eigenschaften | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b561a4aebe34ac943b0163e66dfbf2edf423eedb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599687"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Von SharePoint unterstützte MsBuild-Eigenschaften
  Alle [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaft, die in der Microsoft.VisualStudio.SharePoint.targets-Datei, die Projektdatei oder das Projektbenutzerdatei definierten kann verwendet werden, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekte. Zusätzlich zu den allgemeinen [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften bereitgestellt, die vom SharePoint-Projekt definiert zusätzliche Eigenschaften, die spezifisch für SharePoint-Projekte sind.

 Eine Liste der allgemeinen [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften finden Sie [gemeinsame MSBuild-Projekteigenschaften](http://go.microsoft.com/fwlink/?LinkID=168687). Eine vollständige Liste der Eigenschaften, Ihre bevorzugte Programmiersprache unterstützt werden, finden Sie in der *targets* -Datei, die Projektdatei (*csproj* oder *vbproj*), oder der Benutzer für Projekt ( *csproj.user* oder *. vbproj.user*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>MsBuild-Eigenschaften, die spezifisch für SharePoint
 Die folgende Tabelle enthält [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Eigenschaften, die speziell für SharePoint-Projekte in gelten [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Andere Eigenschaften vorhanden sind, aber sie sind für die interne Verwendung.

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|SharePointSiteUrl|Eine Zeichenfolge, die stellt die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] zur SharePoint-Website.|
|SandboxedSolution|Ein boolescher Wert, der angibt, ob die Lösung eine Sandbox-Lösung ist.|
|ActiveDeploymentConfiguration|Der aktiven Bereitstellungskonfiguration.|
|IncludeAssemblyInPackage|Ein boolescher Wert, der angibt, ob die Assembly in der Paketdatei enthalten ist.|
|PreDeploymentCommand|Ein Zeichenfolgenwert, der im Schritt Befehl vor der Bereitstellung auszuführenden Befehls darstellt.|
|PostDeploymentCommand|Ein Zeichenfolgenwert, der im Schritt Befehl nach der Bereitstellung auszuführenden Befehls darstellt.|
|CustomBeforeSharePointTargets|Eine Zeichenfolge, die den Pfad des repräsentiert eine [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Targets-Datei. Wenn die Zieldatei ist vorhanden und definiert ist, wird sie vor jeder SharePoint-Ziele-Daten importiert. Mit dieser Eigenschaft können Sie des Verpackungsprozesses vordefinieren Packaging-bezogene Eigenschaften anpassen, ohne zu ausgelieferten SharePoint Targets-Datei ändern, aber die Zieledatei gilt weiterhin für alle SharePoint-Projekte.|
|CustomAfterSharePointTargets|Eine Zeichenfolge, die den Pfad des repräsentiert eine [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Targets-Datei. Wenn die Zieldatei ist vorhanden und definiert ist, ist es importierten schließlich von der SharePoint-Ziele-Daten. Mit dieser Eigenschaft können Sie der Verpackungsprozess anpassen durch Überschreiben von Packaging-bezogene Eigenschaften und Ziele ohne ausgelieferten SharePoint Targets-Datei ändern zu müssen, aber die Zieledatei gilt weiterhin für alle SharePoint-Projekte.|
|LayoutPath|Eine Zeichenfolge, die stellt das Stammverzeichnis, in dem alle Dateien gepackt werden vorübergehend platziert werden, bevor sie hinzugefügt wurden, die *.wsp* Datei. Dieser Pfad kann hilfreich zu wissen, wenn Sie außer Kraft setzen die BeforeLayout und AfterLayout Ziele hinzufügen, entfernen oder ändern Dateien gepackt werden, da Sie ihn verwenden können, um den Inhalt zu ändern, werden die *.wsp* Datei.|
|BasePackagePath|Eine Zeichenfolge, die den Ordner darstellt, in dem das Paket abgelegt wird. Dieser Wert wird verwendet, das Ausgabeverzeichnis des Projekts, z. B. "bin\Debug".|
|PackageExtension|Eine Zeichenfolge, die die Dateinamenerweiterung zum Anfügen an das Paket darstellt. Der Standardwert ist die WSP-Datei.|
|AssemblyDeploymentTarget|Eine Zeichenfolge, die den Speicherort darstellt, in denen die Projektassembly auf dem SharePoint-Server bereitgestellt wird. Der Wert ist entweder GlobalAssemblyCache (Standard) oder WebApplication. Diese Eigenschaft kann auch im Eigenschaftenfenster festgelegt werden.|
|PackageWithValidation|Ein boolescher Wert, der angibt, ob die Überprüfung vor dem Packen. Diese Eigenschaft können Sie die Überprüfungsfehler beim Erstellen von Paketen zu ignorieren.|
|ValidatePackageDependsOn|Eine Zeichenfolge, die zusätzliche Ziele zum Ausführen vor dem ValidatePackage Ziel definiert.|
|TokenReplacementFileExensions|Eine Zeichenfolge, die Dateien definiert, die die Token, die während des Verpackens ersetzt haben.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Verwenden von MsBuild-Eigenschaften auf der Eigenschaftenseite
 Für die Flexibilität, anstelle von hartcodierten Zeichenfolgen in die **vor der Bereitstellung über die Befehlszeile** und **Befehlszeile nach der Bereitstellung** Felder auf der Seite der SharePoint-Eigenschaften können Sie die SharePoint die Eigenschaften als Argumente. Beispielsweise anstelle einen bestimmten [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] Zeichenfolge für die SharePoint-Website können Sie stattdessen `$(SharePointSiteUrl)`.

> [!NOTE]
>  Verwenden Sie entweder die [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Variable Syntax `$(` *PropertyName* `)` oder die Umgebungsvariablensyntax `%` *PropertyName* `%` Um eine Eigenschaft anzugeben.

## <a name="see-also"></a>Siehe auch

- [MSBuild-Referenz](../msbuild/msbuild-reference.md)