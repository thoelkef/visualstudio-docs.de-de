---
title: "Installieren von R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.devlang: r
ms.topic: article
ms.assetid: 3ff60292-1b88-4ee9-b2b2-edd957f1a519
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 8e35c82a5f8583a609e9fccbacb0b27d9c3eac8f
ms.contentlocale: de-de
ms.lasthandoff: 07/12/2017

---

# <a name="how-to-install-r-tools-for-visual-studio"></a>Installieren von R Tools für Visual Studio

In diesem Thema:

- [Unterstützte Versionen von Visual Studio](#supported-versions-of-visual-studio)
- [Installieren von RTVS in Visual Studio 2017](#installing-rtvs-in-visual-studio-2017)
- [Installieren von RTVS in Visual Studio 2015](#installing-rtvs-in-visual-studio-2015)
- [Offlineinstallation](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Nach der Installation von R Tools möchten Sie möglicherweise Visual Studio für ein optimiertes Layout für Datenspezialisten konfigurieren, so wie im Thema [Optionen](options.md#data-scientist-layout).

## <a name="supported-versions-of-visual-studio"></a>Unterstützte Versionen von Visual Studio

R Tools für Visual Studio (RTVS) werden in den Editionen Community (kostenlos), Professional und Enterprise von [Visual Studio 2017](https://www.visualstudio.com/downloads/) sowie [Visual Studio 2015 Update 3 (oder höher)](http://go.microsoft.com/fwlink/?LinkId=691129) (direkter Download) unterstützt. 

RTVS wird nicht installiert, wenn Sie nur über Visual Studio Shell verfügen, was in Produkten wie z.B. Visual Studio Test Professional und SQL Server Management Studio enthalten ist. Visual Studio Shell verfügt nicht über die nötigen Komponenten für RTVS.


## <a name="installing-rtvs-in-visual-studio-2017"></a>Installieren von RTVS in Visual Studio 2017

1. Führen Sie den Visual Studio-Installer aus. (Siehe [Downloads](https://www.visualstudio.com/downloads/) , wenn Sie Visual Studio noch nicht installiert haben.) Achten Sie unter Windows 7 darauf, dass Ihr Installer aktualisiert ist und Visual Studio Version *15.2 Build 26430.12* oder neuer anzeigt.

2. Wählen Sie die Workload **Data Science und analytische Anwendungen** aus.

    ![Workload von Data Science und analytischen Anwendungen in VS2017](media/installation-data-science-workload.png)

3. Legen Sie zusätzliche Optionen auf der rechten Seite unter dem gleichen Workloadnamen fest. Diese Workload enthält standardmäßig F#- und Python-Unterstützung. Die Mindestanforderungen für R sind die **R language support** (Unterstützung der Sprache R), **Runtime support for R development** (Laufzeitunterstützung für die R-Entwicklung) , und der **Microsoft R client** (Microsoft R-Client).

RTVS ist installiert in: `%ProgramFiles(x86)%\Microsoft Visual Studio\<version>\<edition>Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`, wobei `<version>` normalerweise `2017` ist, und `<edition>` ist `Community`, `Professional` oder `Enterprise`.

## <a name="installing-rtvs-in-visual-studio-2015"></a>Installieren von RTVS in Visual Studio 2015

Mit Visual Studio 2015 müssen Sie einen R-Interpreter und die R Tools separat installieren.

### <a name="install-an-r-interpreter"></a>Installieren eines R-Interpreters

RTVS erfordert eine 64-Bit-Installation der R-Version 3.2.1 oder höher aus mindestens einer der folgenden Quellen:

* [Microsoft R Open](https://mran.microsoft.com/download/)
* [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)
* [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open und CRAN R lassen beide mehrere parallele Versionen zu. Microsoft R Client unterstützt jedoch nur eine Version und verwendet immer die neueste Version, die Sie installiert haben.

### <a name="install-the-r-tools"></a>Installieren der R Tools

Laden Sie die aktuelle RTVS-Version von [https://aka.ms/rtvs-current](https://aka.ms/rtvs-current) herunter. RTVS prüft auf eine geeignete Visual Studio-Version und hilft Ihnen auch dabei, einen R-Interpreter zu installieren, falls Sie dies noch nicht getan haben.

RTVS ist installiert in: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Offlineinstallation von Visual Studio und RTVS

Die Offlineinstallation eignet sich für Computer, die keine Internetverbindung besitzen:

1. Befolgen Sie die Anweisungen, um einen Offlineinstaller für Ihre Visual Studio-Version zu erstellen: 

    - [Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md)
    - [Visual Studio 2015](https://msdn.microsoft.com/library/mt706497.aspx)

1. Laden Sie die RTVS-Offlineinstaller unter [https://aka.ms/rtvs-current-zip](https://aka.ms/rtvs-current-zip) und [https://aka.ms/rtvs-remote-zip](https://aka.ms/rtvs-remote-zip) herunter. 

1. Installieren von Visual Studio und RTVS über die Offlineinstaller.

## <a name="see-also"></a>Siehe auch

- [Erste Schritte mit R](getting-started-with-r.md)
- [R Tools sample projects (R Tools und Beispielprojekte)](getting-started-samples.md)
- [Anzeigen der Hilfe](getting-started-help.md)
- [Einstellungen der Optionen](options.md)

