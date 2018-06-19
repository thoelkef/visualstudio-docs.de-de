---
title: Installieren von außerhalb der Ordner "Extensions" mit VSIX v3 | Microsoft Docs
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8476b300974d66efc60f647c897ec6892191e7fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136775"
---
# <a name="installing-outside-the-extensions-folder"></a>Installieren von außerhalb der Ordner "Extensions"

Beginnend mit Visual Studio 2017 und VSIX v3 (Version 3) besteht nun Unterstützung für die Installation der Erweiterung Objekte außerhalb der Ordner "Extensions". Derzeit werden die folgenden Speicherorte als gültige Installationspfade aktiviert (wobei [INSTALLDIR] zum Installationsverzeichnis für Visual Studio-Instanz zugeordnet ist):

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets

>**Hinweis:** das VSIX-Format können Sie außerhalb der Ordnerstruktur des VS-Installation installieren.

Um unterstützen die Installation auf diese Verzeichnisse, muss die VSIX installiert sein "pro Computer instanzweise". Dies kann aktiviert werden, indem Sie das Kontrollkästchen "alle Benutzer" im Designer "Extension.vsixmanifest" überprüfen:

![Überprüfen Sie alle Benutzer](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Gewusst wie: Festlegen der installroot an

Um die Installationsverzeichnisse festzulegen, können Sie die **Eigenschaften** Fenster in Visual Studio. Sie können z. B. Festlegen der `InstallRoot` Eigenschaft einen Projektverweis auf einem der oben genannten Speicherorte:

![Installieren Sie die Root-Eigenschaften](media/install-root-properties.png)

Dadurch wird einige Metadaten hinzugefügt, um das entsprechende `ProjectReference` Eigenschaft innerhalb des VSIX-Projekts CSPROJ-Datei:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Hinweis:** Sie können die CSPROJ-Datei direkt bearbeiten, falls gewünscht.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Wie Sie ein Unterpfad unter der InstallRoot festlegen

Wenn Sie ein Unterpfad unterhalb installieren möchten die `InstallRoot`, können Sie dies tun, indem Sie festlegen der `VsixSubPath` Eigenschaft ebenso wie die `InstallRoot` Eigenschaft. Angenommen, wir möchten unsere Projektverweis Ausgabe für die Installation "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Wir können dies problemlos mit dem Designer Eigenschaft durchführen:

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

Die Eigenschaft-Designers Änderungen gelten für mehr als nur Projektverweise; Sie können festlegen, die `InstallRoot` Metadaten für Elemente in Ihrem Projekt auch (mithilfe derselben Methoden, die oben beschriebene).
