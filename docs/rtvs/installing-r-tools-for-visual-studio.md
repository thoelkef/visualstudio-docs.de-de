---
title: "Installieren von R Tools für Visual Studio | Microsoft-Dokumentation"
description: "Installieren der R Tools für Visual Studio in Visual Studio 2017 und Visual Studio 2015, einschließlich Offlineinstallationen."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
dev_langs:
- R
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 76dc2623edebed6cca48c40c0ad0bc96f783e39d
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Installieren von R Tools für Visual Studio

In diesem Artikel:

- [Unterstützte Versionen von Visual Studio](#supported-versions-of-visual-studio)
- [Installieren von RTVS in Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Installieren von RTVS in Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Offlineinstallation](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Nach der Installation von R Tools möchten Sie möglicherweise Visual Studio für ein optimiertes Layout für Datenspezialisten konfigurieren, wie im Artikel [Optionen](options-for-r-tools-in-visual-studio.md) beschrieben.

## <a name="supported-versions-of-visual-studio"></a>Unterstützte Versionen von Visual Studio

R Tools für Visual Studio (RTVS) werden unter Windows in den Editionen Community (kostenlos), Professional und Enterprise von [Visual Studio 2017](https://www.visualstudio.com/downloads/) sowie [Visual Studio 2015 Update 3 (oder höher)](http://go.microsoft.com/fwlink/?LinkId=691129) (direkter Download) unterstützt.

RTVS wird in Visual Studio für Mac derzeit nicht unterstützt.

RTVS wird nicht installiert, wenn Sie nur über Visual Studio Shell verfügen, was in Produkten wie z.B. Visual Studio Test Professional und SQL Server Management Studio enthalten ist. Visual Studio Shell verfügt nicht über die nötigen Komponenten für RTVS.

## <a name="installing-rtvs-in-visual-studio-2017"></a>Installieren von RTVS in Visual Studio 2017

1. Führen Sie den Visual Studio-Installer aus. (Siehe [Downloads](https://www.visualstudio.com/downloads/) , wenn Sie Visual Studio noch nicht installiert haben.) Achten Sie unter Windows 7 darauf, dass Ihr Installer aktualisiert ist und Visual Studio 2017, Version *15.2, Build 26430.12* oder höher anzeigt.

1. Wählen Sie die Workload **Data Science und analytische Anwendungen** aus.

    ![Workload von Data Science und analytischen Anwendungen in VS2017](media/installation-data-science-workload.png)

1. Legen Sie zusätzliche Optionen auf der rechten Seite unter dem gleichen Workloadnamen fest. Diese Workload enthält standardmäßig F#- und Python-Unterstützung. Die Mindestanforderungen für R sind die **R language support** (Unterstützung der Sprache R), **Runtime support for R development** (Laufzeitunterstützung für die R-Entwicklung) , und der **Microsoft R client** (Microsoft R-Client).

RTVS ist installiert in: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`, wobei `<version>` normalerweise `2017` ist, und `<edition>` ist `Community`, `Professional` oder `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Installieren von RTVS in Visual Studio 2015

Mit Visual Studio 2015 müssen Sie einen R-Interpreter und die R Tools separat installieren.

### <a name="install-an-r-interpreter"></a>Installieren eines R-Interpreters

RTVS erfordert eine 64-Bit-Installation der R-Version 3.2.1 oder höher aus mindestens einer der folgenden Quellen:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open und CRAN R lassen beide mehrere parallele Versionen zu. Microsoft R Client unterstützt jedoch nur eine Version und verwendet immer die neueste Version, die Sie installiert haben.

### <a name="install-the-r-tools"></a>Installieren der R Tools

Laden Sie die aktuelle RTVS-Erweiterung für Visual Studio 2015 von [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current) herunter. RTVS prüft auf eine geeignete Visual Studio-Version und hilft Ihnen auch dabei, einen R-Interpreter zu installieren, falls Sie dies noch nicht getan haben.

> [!Note]
> Das eigenständige RTVS-Installationsprogramm funktioniert nur mit Visual Studio 2015. Für Visual Studio 2017 ist, wie zuvor beschrieben, die Installation des R-Supports über die [Workload von Data Science und analytischen Anwendungen](#installing-rtvs-in-visual-studio-2017) nötig.

RTVS für Visual Studio 2015 wird hier installiert:`%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Offlineinstallation von Visual Studio und RTVS

Die Offlineinstallation eignet sich für Computer, die keine Internetverbindung besitzen:

1. Befolgen Sie die Anweisungen, um einen Offlineinstaller für Ihre Visual Studio-Version zu erstellen:

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Laden Sie für Visual Studio 2015 die RTVS-Offlineinstaller unter [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) und [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip) herunter.

1. Installieren von Visual Studio und RTVS über die Offlineinstaller.

## <a name="see-also"></a>Siehe auch

- [Erste Schritte mit R](getting-started-with-r.md)
- [R Tools sample projects (R Tools und Beispielprojekte)](getting-started-samples.md)
- [Anzeigen der Hilfe](getting-started-help.md)
- [Einstellungen der Optionen](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (vorher R Server)](/machine-learning-server/)