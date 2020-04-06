---
title: Installieren außerhalb des Erweiterungsordners mit VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700179"
---
# <a name="install-outside-the-extensions-folder"></a>Installieren außerhalb des Ordners für Erweiterungen

Ab Visual Studio 2017 und VSIX v3 (Version 3) können Erweiterungselemente außerhalb des Erweiterungsordners installiert werden. Derzeit sind die folgenden Speicherorte als gültige Installationsspeicherorte aktiviert (wobei [INSTALLDIR] dem Installationsverzeichnis der Visual Studio-Instanz zugeordnet ist):

* [INSTALLDIR]-MSBuild
* [INSTALLDIR]-Xml-Schemas
* [INSTALLDIR]
* [INSTALLDIR]-Lizenzen
* [INSTALLDIR]
* [INSTALLDIR]-Common7-IDE-RemoteDebugger
* [INSTALLDIR]-Common7-IDE-VC-VCTargets (nur für Visual Studio 2017 unterstützt; für Visual Studio 2019 und höher veraltet)

> [!NOTE]
> Das VSIX-Format ermöglicht es Ihnen nicht, außerhalb der Visual Studio-Installationsordnerstruktur zu installieren. 

Um die Installation in diesen Verzeichnissen zu unterstützen, muss der VSIX "pro Instanz pro Computer" installiert werden. Dies kann aktiviert werden, indem Sie das Kontrollkästchen "All-Users" im Erweiterungsmanifest-Designer aktivieren:

![Überprüfen Sie alle Benutzer](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>So legen Sie den InstallRoot fest

Zum Festlegen der Installationsverzeichnisse können Sie das **Eigenschaftenfenster** in Visual Studio verwenden. Sie können z. `InstallRoot` B. die Eigenschaft eines Projektverweises auf einen der oben genannten Positionen festlegen:

![Installieren von Root-Eigenschaften](media/install-root-properties.png)

Dadurch werden der entsprechenden `ProjectReference` Eigenschaft innerhalb der .csproj-Datei des VSIX-Projekts einige Metadaten hinzugefügt:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Sie können die .csproj-Datei direkt bearbeiten, wenn Sie es vorziehen.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>So legen Sie einen Unterpfad unter InstallRoot fest

Wenn Sie in einem Unterpfad unterhalb `InstallRoot`des installieren möchten, können `VsixSubPath` Sie dies tun, indem Sie die Eigenschaft genau wie die `InstallRoot` Eigenschaft festlegen. Angenommen, die Ausgabe unserer Projektreferenz soll in '[INSTALLDIR]'MSBuild'MyCompany'MySDK'1.0' installiert werden. Wir können dies ganz einfach mit dem Immobiliendesigner tun:

![Set-Unterpfad](media/set-subpath.png)

Die entsprechenden .csproj-Änderungen sehen wie folgt aus:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Zusätzliche Informationen

Die Eigenschaftendesigneränderungen gelten für mehr als nur Projektverweise. Sie können `InstallRoot` die Metadaten auch für Elemente innerhalb Des Projekts festlegen (mit den oben beschriebenen Methoden).
