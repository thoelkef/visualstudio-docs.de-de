---
title: "Installation für Python in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 066612a132bf6a092771afd5fc4a876d4b3be425
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2017
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>Installieren von Python-Unterstützung für Visual Studio auf Windows

Um die Python-Unterstützung für Visual Studio zu installieren, befolgen Sie die Anweisungen in dem Abschnitt, der Ihrer Version von Visual Studio entspricht:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 und früher](#visual-studio-2013-and-earlier)

Für Visual Studio 2015 und früher müssen Sie ebenfalls separat einen Python-Interpreter Ihrer Wahl installieren (Python 3.5 und früher, 3.6 wird nicht unterstützt). Weitere Informationen finden Sie unter [Python-Umgebungen](python-environments.md). Auf dieser Seite sind ebenfalls Anweisungen für das Hinzufügen eines vorhandenen Python-Interpreters zu Visual Studio 2017 enthalten.

Um die Python-Unterstützung nach den Installationsschritten schnell zu testen, öffnen Sie das interaktive Python-Fenster durch Drücken von ALT-I und Eingabe von `2+2`. Wenn Sie die Ausgabe von `4` nicht sehen, überprüfen Sie Ihre Schritte.

> [!Tip]
> Die Python-Arbeitsauslastung enthält die hilfreiche Cookiecutter-Erweiterung, die eine grafische Benutzeroberfläche bietet, auf der Sie Vorlagen ermitteln, Vorlageoptionen eingeben und Projekte und Dateien erstellen können. Weitere Informationen finden Sie unter [Verwenden der Cookiecutter-Erweiterung](cookiecutter.md).

> [!Note]
> Python wird zurzeit nicht von Visual Studio für Mac unterstützt, steht jedoch auf Mac und Linux über Visual Studio-Code zur Verfügung. Siehe [Fragen und Antworten](python-in-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Laden Sie den aktuellen Visual Studio 2017-Installer herunter, und führen Sie diesen aus:

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Installieren von Visual Studio 2017 Community</a>

    >[!Tip]
    > Die Community Edition eignet sich für einzelne Entwickler, Schulungsumgebungen, akademische Forschung und Open Source-Entwicklung. Installieren Sie für andere Verwendungen <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> oder <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>.

1. Der Installer bietet Ihnen eine Liste von Workloads, bei denen es sich um Gruppen von verwandten Optionen für bestimmte Entwicklungsbereiche handelt. Wählen Sie für Python die Workload **Python-Entwicklung** aus.

    ![Arbeitsauslastung zur Python-Entwicklung im Visual Studio-Installationsprogramm](media/installation-python-workload.png)

    Optional: Wenn Sie mit Data Science arbeiten, verwenden Sie ggf. die Workload **Data Science und analytische Anwendungen**. Diese Workload enthält Unterstützung für Python und R- und F#-Sprachen. Weitere Informationen finden Sie unter [Data science and analytical applications workload (Workload für Data Science und analytische Anwendungen)](../rtvs/data-science-workload.md).

    > [!Note]
    > Die Python- und Data Science-Workloads sind nur für Visual Studio 2017 Release 15.2 und höher verfügbar.

1. Wählen Sie bei Bedarf zusätzliche Optionen auf der rechten Seite des Installers aus. Überspringen Sie diesen Schritt, um die Standardoptionen zu akzeptieren.

    ![Optionen zur Python-Entwicklung im Visual Studio-Installationsprogramm](media/installation-python-options.png)

    | Option | Beschreibung | 
    | --- | --- |
    | Python-Verteilungen | Wählen Sie eine beliebige Kombination aus den 32-Bit- und 64-Bit-Varianten der Python 2-, Python 3-, Anaconda2- und Anaconda3-Verteilungen aus, mit denen Sie arbeiten möchten. Jede enthält den Interpreter, die Runtime und die Bibliotheken der Verteilung. Bei Anaconda handelt es sich um eine offene Data Science-Plattform, die eine große Auswahl an Paketen enthält. (Sie können jederzeit zum Visual Studio-Installer zurückkehren, um Verteilungen hinzuzufügen oder zu entfernen.) |
    | Unterstützung von Cookiecutter-Vorlagen | Installiert die grafische Benutzeroberfläche von Cookiecutter, um Vorlagen zu ermitteln, Vorlageoptionen einzugeben und Projekte und Dateien zu erstellen. Weitere Informationen finden Sie unter [Verwenden der Cookiecutter-Erweiterung](cookiecutter.md). |
    | Webunterstützung für Python | Installiert Tools für die Webentwicklung einschließlich der Bearbeitungsunterstützung für HTML, CSS und JavaScript sowie Vorlagen für Projekte, die Bottle-, Flask- und Django-Frameworks verwenden. Weitere Informationen finden Sie unter [Python-Webprojektvorlagen](template-web.md). |
    | Python IoT-Unterstützung | Unterstützt die Windows IoT Core-Entwicklung mithilfe von Python. |
    | Native Python-Entwicklungstools | Installiert den C++-Compiler und andere erforderliche Komponenten, um native Erweiterungen für Python zu entwickeln. Weitere Informationen finden Sie unter [Erstellen einer C++-Erweiterung für Python](cpp-and-python.md). |
    | Azure Cloud Services-Kerntools | Bietet zusätzliche Unterstützung für Azure Cloud Services-Entwickler in Python. Weitere Informationen finden Sie unter [Azure Cloud Services-Projekte für Python](template-azure-cloud-service.md). |

1. Nach der Installation bietet der Installer Optionen für das Ändern, Starten, Reparieren oder Deinstallieren von Visual Studio. Die Schaltfläche **Ändern** ändert sich zu **Update**, wenn Updates für die installierten Komponenten von Visual Studio verfügbar sind. (Die Option „Ändern“ ist dann im Dropdownmenü verfügbar.) Sie können Visual Studio und den Installer ebenfalls über das Windows-Startmenü starten, indem Sie nach „Visual Studio“ suchen.

    ![Starten, Ändern oder Deinstallieren von Visual Studio über den Installer](media/installation-vs-launch.png)


> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Führen Sie das Visual Studio-Installationsprogramm über **Systemsteuerung > Programme und Funktionen** aus, wählen Sie **Microsoft Visual Studio 2015** aus, und dann **Ändern**.

1. Wählen Sie im Installationsprogramm **Ändern**.

1. Wählen Sie **Programmiersprachen > Python-Tools für Visual Studio** und dann **Weiter**:

    ![PTVS-Option im Visual Studio 2015-Installationsprogramm](media/installation-vs2015.png)    

1. Nach Abschluss der Installation von Visual Studio [installieren Sie einen Python-Interpreter Ihrer Wahl](python-environments.md#selecting-and-installing-python-interpreters). Wenn Sie bereits einen Interpreter installiert haben, gehen Sie zu [Erstellen einer Umgebung für einen vorhandenen Interpreter](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 und früher

1. Installieren Sie die entsprechende Version der Python-Tools für Visual Studio für Ihre Version von Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 für Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). Im Dialogfeld **Datei > Neues Projekt** in Visual Studio 2013 finden Sie eine Verknüpfung für diesen Prozess.
    - Visual Studio 2012: [PTVS 2.1 für Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 für Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Installieren Sie einen Python-Interpreter Ihrer Wahl](python-environments.md#selecting-and-installing-python-interpreters). Wenn Sie bereits einen Interpreter installiert haben, gehen Sie zu [Erstellen einer Umgebung für einen vorhandenen Interpreter](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="install-locations"></a>Installationsspeicherorte

Standardmäßig wird die Python-Unterstützung für alle Benutzer auf einem Computer installiert.

Für Visual Studio 2017 wird die Python-Arbeitsauslastung in `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python` installiert, wobei &lt;VS_edition&gt; „Community“, „Professional“ oder „Enterprise“ ist.

Für Visual Studio 2015 und früher gelten folgende Installationspfade:

- 32-Bit:
  - Pfad: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Registrierungsspeicherort des Pfads: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64-Bit:
  - Pfad: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Registrierungsspeicherort des Pfads: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

Dabei gilt:

- &lt;VS_ver&gt; ist:    
    - 14.0 für Visual Studio 2015
    - 12.0 für Visual Studio 2013
    - 11.0 für Visual Studio 2012
    - 10.0 für Visual Studio 2010
- &lt;PTVS_ver&gt; ist eine Versionsnummer, z.B. 2.2, 2.1, 2.0, 1.5, 1.1 oder 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Benutzerspezifische Installationen (1.5 und früher)

Bei Python-Tools für Visual Studio 1.5 und früher war die Installation nur für den aktuellen Benutzer zulässig. In diesem Fall ist der Installationspfad `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`, wobei für &lt;VS_ver&gt; und &lt;PTVS_ver&gt; die obige Beschreibung gilt.

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
