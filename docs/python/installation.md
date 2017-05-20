---
title: "Installation für Python in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 9cdd87d81f0b0f4748a25c7bb87fb840e246854c
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---

# <a name="installing-python-support-in-visual-studio"></a>Installieren von Python-Unterstützung für Visual Studio

Um die Python-Unterstützung für Visual Studio zu installieren, befolgen Sie die Anweisungen in dem Abschnitt, der Ihrer Version von Visual Studio entspricht:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 und früher](#visual-studio-2013-and-earlier)

Beachten Sie, dass Sie für Visual Studio 2015 und früher separat einen Python-Interpreter Ihrer Wahl installieren müssen. Nähere Informationen finden Sie unter [Python-Umgebungen](python-environments.md).

Um die Python-Unterstützung nach den Installationsschritten schnell zu testen, öffnen Sie das interaktive Python-Fenster durch Drücken von ALT-I und Eingabe von `2+2`. Wenn Sie die Ausgabe von `4` nicht sehen, überprüfen Sie Ihre Schritte.

> [!Tip]
> Die Python-Arbeitsauslastung enthält die hilfreiche Cookiecutter-Erweiterung, die eine grafische Benutzeroberfläche bietet, auf der Sie Vorlagen ermitteln, Vorlageoptionen eingeben und Projekte und Dateien erstellen können. Nähere Informationen finden Sie unter [Using the Cookiecutter Extension](cookiecutter.md) (Verwenden der Cookiecutter-Erweiterung).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Installieren Sie Visual Studio 2017 von [https://www.visualstudio.com/vs/](https://www.visualstudio.com/vs/).

1. Wählen Sie im Visual Studio-Installer die Workload **Web und Cloud > Python-Entwicklung** aus.

    ![Arbeitsauslastung zur Python-Entwicklung im Visual Studio-Installationsprogramm](media/installation-python-workload.png)

    > [!Note]
    > Python ist auch in der Workload **Data Science und analytische Anwendungen** enthalten.

1. Wählen Sie auf der rechten Seite des Installationsprogramms die Python-Interpreter und andere verwandte Tools, die Sie einbeziehen möchten. Wenn Sie z.B. planen, C++-Erweiterungen für Python zu entwickeln, schließen Sie die Option **Native Python-Entwicklungstools** ein.

    ![Optionen zur Python-Entwicklung im Visual Studio-Installationsprogramm](media/installation-python-options.png)

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Führen Sie das Visual Studio-Installationsprogramm über **Systemsteuerung > Programme und Funktionen** aus, wählen Sie **Microsoft Visual Studio 2015** aus, und dann **Ändern**.

1. Wählen Sie im Installationsprogramm **Ändern**.

1. Wählen Sie **Programmiersprachen > Python-Tools für Visual Studio** und dann **Weiter**:

    ![PTVS-Option im Visual Studio 2015-Installationsprogramm](media/installation-vs2015.png)    

1. Nach Abschluss der Installation von Visual Studio [installieren Sie einen Python-Interpreter Ihrer Wahl](python-environments.md#selecting-and-installing-python-interpreters).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 und früher

1. Installieren Sie die entsprechende Version der Python-Tools für Visual Studio für Ihre Version von Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 für Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). Im Dialogfeld **Datei > Neues Projekt** in Visual Studio 2013 finden Sie eine Verknüpfung für diesen Prozess.
    - Visual Studio 2012: [PTVS 2.1 für Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 für Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Installieren Sie einen Python-Interpreter Ihrer Wahl](python-environments.md#selecting-and-installing-python-interpreters).

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

