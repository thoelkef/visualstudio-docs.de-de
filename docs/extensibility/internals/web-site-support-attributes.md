---
title: Attribute der Websiteunterstützung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea55937318d22a40b90cddb54490b87ab0c44325
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916821"
---
# <a name="web-site-support-attributes"></a>Attribute der Websiteunterstützung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Websiteprojekt kann erweitert werden, um Unterstützung für Web bietet Programmiersprachen zu vergleichen. Die Sprache muss selbst registrieren, mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , damit Projektvorlagen angezeigt werden können, in der **neue Website** im Dialogfeld, wenn die Sprache ausgewählt ist.

Das IronPython Studio-Beispiel enthält der Support-Website. Das Beispiel enthält die folgenden Attributklassen zum Registrieren von IronPython als eine Codebehind-Sprache für die neue Web-Projekte.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Dieses Attribut befindet sich auf das Sprachprojekt. Die Liste der Web-Programmiersprachen, in der Sprache hinzugefügt der **Sprache** Liste der **neue Website** Dialogfeld. Der folgende Code fügt beispielsweise IronPython der Liste an:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Dieses Attribut legt auch fest, den Vorlagenpfad zum Ordner "Templates" verweisen. Weitere Informationen zu den Speicherort der Ordner "Templates", finden Sie unter [Vorlagen für die Websiteunterstützung](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Dieses Attribut befindet sich auf das Sprachprojekt. Es ermöglicht das Websiteprojekt zu schachteln, einen Dateityp (verknüpft) unter einem anderen Dateityp (primär) in der **Projektmappen-Explorer**.

 Der folgende Code gibt beispielsweise, dass eine IronPython-Codebehind-Datei mit einer ASPX-Datei verknüpft ist. Wenn eine neue ASPX-Webseite in einer Projektmappe der IronPython-Web-Standort erstellt wird, wird eine neue .py-Quelldatei wird generiert und als untergeordneter Knoten der ASPX-Seite angezeigt wird.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Dieses Attribut wird auf das Sprachpaket für das Projekt eingefügt. Er wählt den IntelliSense-Anbieter für die Sprache aus.

 Der folgende Code gibt beispielsweise an, dass eine Instanz von PythonIntellisenseProvider, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, bei Bedarf auf Sprachdienste bieten erstellt werden soll.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Die IVsIntellisenseProject-Implementierung Verweise verarbeitet und ruft den Compiler auf, wenn eine Webseite mit Code angefordert, aber nicht zwischengespeichert.

## <a name="see-also"></a>Siehe auch
 [Websiteunterstützung](../../extensibility/internals/web-site-support.md)