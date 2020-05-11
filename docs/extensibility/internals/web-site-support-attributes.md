---
title: Website-Supportattribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703498"
---
# <a name="web-site-support-attributes"></a>Attribute der Websiteunterstützung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Websiteprojekt kann erweitert werden, um Unterstützung für Webprogrammiersprachen bereitzustellen. Die Sprache muss [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sich selbst registrieren, damit Projektvorlagen im Dialogfeld **Neue Website** angezeigt werden können, wenn die Sprache ausgewählt ist.

Das IronPython Studio-Beispiel enthält Websiteunterstützung. Das Beispiel enthält die folgenden Attributklassen, um IronPython als CodeBehind-Sprache für neue Webprojekte zu registrieren.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Dieses Attribut wird im Sprachprojekt platziert. Es fügt die Sprache zur Liste der Webprogrammiersprachen in der **Sprachliste** im Dialogfeld **Neue Website** hinzu. Der folgende Code fügt der Liste beispielsweise IronPython hinzu:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Dieses Attribut legt auch fest, dass der Vorlagenpfad auf den Vorlagenordner verweist. Weitere Informationen zum Speicherort des Vorlagenordners finden Sie unter [Websitesupportvorlagen](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Dieses Attribut wird im Sprachprojekt platziert. Es ermöglicht dem Websiteprojekt, einen Dateityp (bezogen) unter einem anderen Dateityp (primär) im **Projektmappen-Explorer**zu verschachteln.

 Der folgende Code gibt beispielsweise an, dass eine IronPython-Codebehind-Datei mit einer ASPX-Datei verknüpft ist. Wenn eine neue ASPX-Webseite in einer IronPython-Websitelösung erstellt wird, wird eine neue .py-Quelldatei generiert und als untergeordneter Knoten der ASPX-Seite angezeigt.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Dieses Attribut wird im Sprachprojektpaket platziert. Es wählt den IntelliSense-Anbieter für die Sprache aus.

 Der folgende Code gibt beispielsweise an, dass eine Instanz von PythonIntellisenseProvider, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>implementiert, bei Bedarf erstellt werden soll, um Sprachdienste bereitzustellen.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Die IVsIntellisenseProject-Implementierung verarbeitet Verweise und ruft den Sprachcompiler auf, wenn eine Webseite mit Code angefordert, aber nicht zwischengespeichert wird.

## <a name="see-also"></a>Weitere Informationen
- [Websiteunterstützung](../../extensibility/internals/web-site-support.md)
