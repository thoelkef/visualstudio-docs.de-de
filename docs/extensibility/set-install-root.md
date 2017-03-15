---
title: "Installieren außerhalb des Ordners Erweiterungen mit VSIX v3 | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4e8ceb1c988f639d0ea18b94e206ddec2d3e764c
ms.openlocfilehash: 5c103b5f038260a17f64af56f78f0b3f37e3bb32
ms.lasthandoff: 02/22/2017

---
# <a name="installing-outside-the-extensions-folder"></a>Installieren von außerhalb der Ordner "Extensions"

>**Hinweis:** diese Dokumentation ist vorläufig und basierend auf der Visual Studio 2017 RC-Version.

Beginnend mit Visual Studio 2017 und VSIX v3 (Version 3) wird jetzt unterstützt für die Installation der Erweiterung Ressourcen außerhalb der Ordner "Extensions". Derzeit werden die folgenden Speicherorte als gültige Installationsorte aktiviert (wobei [Installdir] zum Installationsverzeichnis von Visual Studio-Instanz zugeordnet ist):

* [Installdir] \Common7\IDE\PublicAssemblies
* [Installdir] \Common7\IDE\ReferenceAssemblies
* [Installdir] \MSBuild
* [Installdir] \Schemas
* [Installdir] \Licenses
* [Installdir] \RemoteDebugger
* [Installdir] \VSTargets

>**Hinweis:** das VSIX-Format können Sie außerhalb der Ordnerstruktur des VS-Installation installieren.

Um unterstützen, in diese Verzeichnisse zu installieren, muss der VSIX-Datei installiert werden "pro Computer Instanzebene". Dies kann durch Aktivieren des Kontrollkästchens "All Users" im Designer extension.vsixmanifest aktiviert werden:

![Überprüfen Sie alle Benutzer](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Gewusst wie: Festlegen der InstallRoot

Um die Installationsverzeichnisse festzulegen, können Sie die **Eigenschaften** in Visual Studio im Fenster. Sie können z. B. Festlegen der `InstallRoot` Eigenschaft einen Projektverweis auf einer der Speicherorte:

![Installieren Sie die Root-Eigenschaften](media/install-root-properties.png)

Dadurch wird einige Metadaten hinzugefügt, um das entsprechende `ProjectReference` Eigenschaft innerhalb des VSIX-Projekts CSPROJ-Datei:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**Hinweis:** Sie können auf Wunsch die CSPROJ-Datei direkt bearbeiten.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Ein Unterpfad unter der InstallRoot festlegen

Wenn Sie, um ein Unterpfad unter installieren möchten der `InstallRoot`, dazu können Sie festlegen der `VsixSubPath` Eigenschaft wie die `InstallRoot` Eigenschaft. Angenommen, wir möchten unsere Projektverweis Ausgabe für die Installation "[installdir]\MSBuild\MyCompany\MySDK\1.0'. Dies problemlos mit dem Designer für die Eigenschaft ist möglich:

![Set-Unterpfad](media/set-subpath.png)

Die entsprechenden .csproj Änderungen sieht folgendermaßen aus:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Zusätzliche Informationen

Die Eigenschaft geändert, gelten für mehr als nur Verweise des Projekts. Sie können festlegen, die `InstallRoot` Metadaten für Elemente in Ihrem Projekt auch (mit den gleichen oben beschriebenen Verfahren).

