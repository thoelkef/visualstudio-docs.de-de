---
title: 'Gewusst wie: Upgrade von Visual C++-Projekten auf Visual Studio 2015 | Microsoft-Dokumentation'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: c998433ca96c46f6a24b75aec5d3a2a95912b786
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823289"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Gewusst wie: Upgrade von Visual C++-Projekten auf Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter [Visual C++-Handbuch: Portieren und Aktualisieren](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Beim ersten Öffnen eines Visual C++-Projekts, das in einer früheren Version von Visual Studio erstellt wurde, werden Sie evtl. aufgefordert, das Projekt zu aktualisieren. Sie werden mit einer Meldung gefragt, ob Sie auf die neueste Version des Visual C++-Compilers und der Bibliotheken aktualisieren möchten. Welche Optionen zum Aktualisieren verfügbar sind, hängt davon ab, welche Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zum Erstellen des Projekts verwendet wurde.

 Sie können [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] verwenden, um [!INCLUDE[win8](../includes/win8-md.md)] -Projekte, die in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]erstellt wurden, zu öffnen, zu bearbeiten und zu erstellen. Um ein neues [!INCLUDE[win8](../includes/win8-md.md)] -Projekt zu erstellen, müssen Sie jedoch [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]verwenden. (Um ein [!INCLUDE[win81](../includes/win81-md.md)] -Projekt zu erstellen, müssen Sie [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]verwenden.)

 Um ein Windows 10-Projekt zu erstellen, müssen Sie [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]verwenden.

 Wenn Sie nicht zum Aktualisieren des Projekts aufgefordert werden, müssen Sie möglicherweise gar nichts unternehmen, um das Projekt zu aktualisieren.

- Wurde das Projekt (.vcproj) in einer Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erstellt, die älter als [!INCLUDE[vs2010](../includes/vs2010-md.md)]ist, müssen Sie das Projekt aktualisieren.

- Wurde das Projekt (.vcxproj) in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)],  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]oder [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] erstellt, haben Sie zwei Möglichkeiten:

  - Sie können das Update überspringen. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] lädt das Projekt, ohne Änderungen vorzunehmen, wenn mit SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] oder [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] auf die Visual C++-Tools in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] zugegriffen werden kann. Sie können diesen Zugriff aktivieren, indem Sie die Version von Visual Studio, mit der das Projekt erstellt wurde, auf demselben Computer installieren, auf dem [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]bereitsteht. Weitere Informationen finden Sie unter [Installing Visual Studio Versions Side-by-Side](../install/install-visual-studio-versions-side-by-side.md).

  - Sie können das Projekt aktualisieren, indem Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] die Berechtigung erteilen, die weiter hinten in diesem Thema beschriebenen Änderungen vorzunehmen. Wenn Ihre Projektmappe mehrere Visual C++-Projekte enthält, müssen Sie alle aktualisieren.

    > [!NOTE]
    > Wenn Sie die Aktualisierung bei der ersten Aufforderung ablehnen, können Sie das Projekt später aktualisieren. Wählen Sie dazu die Option **VC++Projekt aktualisieren** im Menü **Projekt** aus. Wenn der Befehl nicht angezeigt wird, ist kein Update erforderlich.

## <a name="upgrading-a-visual-c-project"></a>Aktualisieren eines Visual C++-Projekts
 Wenn Sie zulassen, dass [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] das Projekt automatisch aktualisiert, werden möglicherweise die folgenden Änderungen vorgenommen:

- Das Projekt wird dahingehend geändert, dass es den [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] -Compiler und die Bibliotheken (PlatformToolset = VisualStudio v140) verwendet.

- Für [!INCLUDE[cppcli](../includes/cppcli-md.md)] -Projekte wird "TargetFrameworkVersion" in ".NET Framework 4.5.2" geändert.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Verwenden eines benutzerdefinierten PlatformToolset
 Wenn Sie weiterhin ein benutzerdefiniertes PlatformToolset in [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]verwenden möchten, muss das Toolset unter %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ auf einem x86-Computer oder unter %ProgramFiles (x86)%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ auf einem x64-Computer gespeichert sein. Informationen zum Erstellen eines benutzerdefinierten PlatformToolset finden Sie im Visual C++-Teamblog im Beitrag zur [systemeigenen Festlegung von Zielversionen in C++](http://go.microsoft.com/fwlink/?LinkId=248587) .

## <a name="see-also"></a>Siehe auch
 [Visual C++-Handbuch: Portieren und Aktualisieren](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [Portieren, Migrieren und Upgraden von Visual Studio-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
