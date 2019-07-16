---
title: Installieren von außerhalb des Ordners für Erweiterungen mit VSIX v3 | Microsoft-Dokumentation
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d5fc36c1244edd0988b6b76f8106020369cd90b
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "67852202"
---
# <a name="install-outside-the-extensions-folder"></a>Installieren außerhalb des Ordners für Erweiterungen

Ab Visual Studio 2017 und VSIX v3 (Version 3), Erweiterung Assets kann außerhalb der Ordner "Extensions" installiert werden. Derzeit werden die folgenden Speicherorte als gültige Installationsorte aktiviert (wobei die [INSTALLDIR] zum Installationsverzeichnis von Visual Studio-Instanz zugeordnet ist):

* [INSTALLDIR] \MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (nur für Visual Studio 2017; veraltete Elemente für Visual Studio-2019 und höher unterstützt)

> [!NOTE]
> Das VSIX-Format kann nicht außerhalb der Ordnerstruktur des Visual Studio-Installation installieren. 

Um auf diese Verzeichnisse installieren zu unterstützen, muss die VSIX-Datei installiert sein "pro pro-Computer-Instanz". Dies kann durch Aktivieren des Kontrollkästchens "alle Benutzer" im Designer "Extension.vsixmanifest" aktiviert werden:

![Überprüfen Sie alle Benutzer](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Gewusst wie: Festlegen der InstallRoot

Um den Installationsverzeichnissen festzulegen, können Sie die **Eigenschaften** Fenster in Visual Studio. Sie können z. B. Festlegen der `InstallRoot` Eigenschaft einen Projektverweis auf einen der oben genannten Standorte:

![Installieren Sie die Root-Eigenschaften](media/install-root-properties.png)

Dadurch werden einige Metadaten hinzugefügt, mit der entsprechenden `ProjectReference` Eigenschaft innerhalb des VSIX-Projekts CSPROJ-Datei:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Sie können die CSPROJ-Datei direkt bearbeiten, falls gewünscht.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Wie Sie einen Unterpfad unter dem InstallRoot festlegen

Wenn Sie, um einen Unterpfad unter installieren möchten der `InstallRoot`, dazu können Sie festlegen der `VsixSubPath` Eigenschaft wie die `InstallRoot` Eigenschaft. Angenommen, wir möchten unsere Projektverweis-Ausgabe zu installieren "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Dies ganz einfach mit dem Designer für die Eigenschaft ist möglich:

![Set-Unterpfad](media/set-subpath.png)

Die entsprechenden csproj-Änderungen werden wie folgt aussehen:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Zusätzliche Informationen

Der Designer Änderung der Eigenschaft gelten für mehr als nur-Projekt-verweisen. Sie können festlegen, die `InstallRoot` Metadaten für Elemente in Ihrem Projekt auch (mit der gleichen oben beschriebenen Methoden).
