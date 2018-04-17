---
title: Attribute für Website-Support | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b312322c1d707f13c5121f1fd159f3fd7736886c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="web-site-support-attributes"></a>Attribute für Website-Unterstützung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Website-Projekt kann zum Bereitstellen von Unterstützung für das Web erweitert Programmiersprachen zu vergleichen. Die Sprache muss selbst registrieren, mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , damit Projektvorlagen angezeigt werden können, in der **neue Website** (Dialogfeld), wenn die Sprache ausgewählt ist.

Das IronPython Studio-Beispiel enthält der Support-Website. Das Beispiel enthält die folgenden Attributklassen um IronPython als Codebehind Sprache für die neue Webprojekte zu registrieren.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Dieses Attribut wird für das Language-Projekt eingefügt. Die Liste der Web-Programmiersprachen in der Sprache hinzugefügt der **Sprache** in Liste der **neue Website** (Dialogfeld). Im folgende Code wird z. B. IronPython zur Liste hinzugefügt:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Dieses Attribut legt außerdem fest, die Vorlagen Pfad auf den Vorlagenordner verweist. Weitere Informationen zum Speicherort des-Vorlagenordners finden Sie unter [Websitevorlagen Unterstützung](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Dieses Attribut wird für das Language-Projekt eingefügt. Er ermöglicht das Websiteprojekt einer Dateityp (verknüpft) geschachtelt unter einem anderen Dateiformat (primär) in der **Projektmappen-Explorer**.

 Der folgende Code gibt beispielsweise, dass eine IronPython Codebehind-Datei in eine ASPX-Datei verknüpft ist. Wenn eine neue ASPX-Webseite in einer IronPython Web Site-Lösung erstellt wird, wird eine neue py-Quelldatei wird generiert und als untergeordneter Knoten der ASPX-Seite wird angezeigt.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Dieses Attribut wird auf das Sprachpaket für das Projekt eingefügt. Er wählt die IntelliSense-Anbieter für die Sprache aus.

 Der folgende Code gibt beispielsweise an, dass eine Instanz von PythonIntellisenseProvider, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, bei Bedarf, um die Sprache Dienstleistungen erstellt werden soll.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Die Implementierung IVsIntellisenseProject Verweise verarbeitet und des Sprachcompilers aufruft, wenn eine Webseite durch Code angefordert, aber wird nicht zwischengespeichert.

## <a name="see-also"></a>Siehe auch
 [Websiteunterstützung](../../extensibility/internals/web-site-support.md)