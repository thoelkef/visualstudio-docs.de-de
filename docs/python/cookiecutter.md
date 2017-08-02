---
title: "CookieCutter-Erweiterung für Python in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 783da5fd-726c-4716-994e-aa04d6b75896
caps.latest.revision: 1
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
ms.openlocfilehash: 44aa74104cbb27de62fe739dbdd8f269fbf42c53
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---

# <a name="using-the-cookiecutter-extension"></a>Verwenden der Cookiecutter-Erweiterung

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) stellt eine grafische Benutzeroberfläche bereit, auf der Sie Vorlagen ermitteln, Vorlageoptionen eingeben und Projekte und Dateien erstellen können. Die Erweiterung ist im Lieferumfang von Visual Studio 2017 enthalten und kann separat in früheren Versionen von Visual Studio installiert werden.

Cookiecutter erfordert Python 3.3 oder höher (32 oder 64 Bit) oder Anaconda 3 4.2 oder höher (32 oder 64 Bit). Wenn kein geeigneter Python-Interpreter verfügbar ist, zeigt Visual Studio eine Warnung an. Wenn Sie einen Python-Interpreter installieren, während Visual Studio ausgeführt wird, klicken Sie auf der Symbolleiste von Cookiecutter auf die Startschaltfläche, um den neu installierten Interpreter zu erkennen.

Wählen Sie nach der Installation **Ansicht > Cookiecutter-Explorer**, um das Fenster von Cookiecutter zu öffnen:

![Cookiecutter – Hauptfenster](~/docs/python/media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter-Workflow

Beim Arbeiten mit Cookiecutter durchsuchen Sie Vorlagen, wählen eine Vorlage aus, klonen sie auf Ihren lokalen Computer, richten Optionen ein und erstellen dann Code aus dieser Vorlage, wie in den folgenden Abschnitten beschrieben.

### <a name="browsing-templates"></a>Durchsuchen von Vorlagen

Die Startseite von Cookiecutter zeigt eine Liste der auswählbaren Vorlagen an, unterteilt in die folgenden Gruppen:

| Gruppieren | Beschreibung | 
| --- | --- |
| Installiert | Vorlagen, die auf Ihrem lokalen Computer installiert wurden. Bei Verwendung einer Onlinevorlage wird das zugehörige Repository automatisch in einen Unterordner von`~/.cookiecutters` geklont. Sie können eine ausgewählte installierte Vorlage löschen, indem Sie die Taste **ENTF** drücken. |
| Empfohlen | Aus dem empfohlenen Feed geladene Vorlagen. Der Standardfeed wird von Microsoft kuratiert. Informationen zum Anpassen des Feeds finden Sie weiter unten im Abschnitt [Cookiecutter-Optionen](#cookiecutter-options). |
| GitHub | GitHub-Suchergebnisse für das Stichwort „cookiecutter“. Die Ergebnisse von GitHub sind in Seiten sortiert. Wenn weitere Ergebnisse verfügbar sind, wird am Ende der Liste **Weitere laden** angezeigt. |
| Benutzerdefiniert | Wenn ein benutzerdefinierter Speicherort in das Suchfeld eingegeben wurde, wird er in dieser Gruppe angezeigt. Sie können entweder den vollständigen Pfad zum GitHub-Repository oder den vollständigen Pfad zu einem Ordner auf Ihrem lokalen Datenträger eingeben. |

### <a name="cloning"></a>Klonen?

Wenn Sie eine Vorlage auswählen und dann auf **Weiter** klicken, erstellt Cookiecutter eine lokale Kopie zum Arbeiten.

Wenn Sie eine Vorlage aus den Gruppen **Empfohlen** oder **GitHub** auswählen oder wenn Sie eine benutzerdefinierte URL in das Suchfeld eingeben und dann diese Vorlage auswählen, wird die Vorlage geklont und auf Ihrem lokalen Computer installiert. Wenn diese Vorlage in einer früheren Visual Studio-Sitzung installiert wurde, wird diese automatisch gelöscht und die neueste Version geklont.

Wenn Sie eine Vorlage aus der Gruppe **Installiert** auswählen oder wenn Sie einen benutzerdefinierten Ordnerpfad in das Suchfeld eingeben und dann diese Vorlage auswählen, lädt Visual Studio die Vorlage, ohne sie zu klonen.

> [!Important]
> Cookiecutter-Vorlagen werden in einem einzigen Ordner geklont: `~/.cookiecutters`. Jeder Unterordner wird nach dem entsprechenden Git-Repositorynamen benannt. Dieser enthält nicht den GitHub-Benutzernamen. Wenn Sie verschiedene Vorlagen mit dem gleichen Namen, aber von unterschiedlichen Erstellern klonen, können Konflikte auftreten. In diesem Fall verhindert Cookiecutter das Überschreiben der vorhandenen Vorlage mit einer anderen Vorlage des gleichen Namens. Um die andere Vorlage zu installieren, müssen Sie zunächst die vorhandene löschen.

### <a name="setting-template-options"></a>Festlegen von Vorlagenoptionen

Nachdem die Vorlage lokal installiert wurde, zeigt Cookiecutter eine Optionsseite an, auf der Sie angeben können, ob Cookiecutter Dateien generieren soll. Sie können auf der Seite noch weitere Optionen festlegen:

![Cookiecutter – Optionsseite](~/docs/python/media/cookiecutter-template-options.png)

Jede Cookiecutter-Vorlage definiert einen eigenen Satz von Optionen und legt einen Standardwert für jede Option fest (angezeigt als vorgeschlagener Text in den jeweiligen Eingabefeldern). Bei einem Standardwert kann es sich um einen Codeausschnitt handeln. Dies ist häufig bei dynamischen Werten der Fall, die weitere Optionen nutzen. 

Es ist möglich, Standardwerte für bestimmte Optionen mithilfe einer Benutzerkonfigurationsdatei anzupassen. Wenn die Cookiecutter-Erweiterung eine Benutzerkonfigurationsdatei erkennt, werden die Standardwerte der Vorlage mit den Standardwerten der Benutzerkonfiguration überschrieben. Dieser Vorgang wird im Abschnitt [Benutzerkonfiguration](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) der Cookiecutter-Dokumentation erläutert.

Wenn in der Vorlage bestimmte Visual Studio-Tasks festgelegt sind, die nach dem Generieren des Codes ausgeführt werden sollen, wird die Option **Bei Abschluss zusätzliche Tasks ausführen** angezeigt, mit der Sie diese Tasks deaktivieren können. Die häufigste Verwendung von Tasks ist das Öffnen eines Webbrowsers, das Öffnen von Dateien im Editor, das Installieren von Abhängigkeiten usw.

### <a name="create"></a>Erstellen

Wenn Sie die erforderlichen Optionen festgelegt haben, wählen Sie **Erstellen** aus, um den Code zu generieren. Beachten Sie, dass eine Warnung angezeigt wird, wenn der Ausgabeordner nicht leer ist. Wenn Sie die Ausgabe der Vorlage kennen und nichts dagegen haben, dass Dateien überschrieben werden, können Sie die Warnung ignorieren. Andernfalls klicken Sie auf **Abbrechen**, geben einen leeren Ordner an und kopieren die erstellten Dateien dann manuell in Ihren nicht leeren Ausgabeordner.

Nach dem erfolgreichen Erstellen der Dateien bietet Cookiecutter eine Option zum Öffnen der Dateien im **Projektmappen-Explorer**:

![Cookiecutter mit Projektmappen-Explorer-Befehl](~/docs/python/media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter-Optionen

Cookiecutter-Optionen stehen über **Tools > Optionen > Cookiecutter** zur Verfügung:

![Cookiecutter-Optionen](~/docs/python/media/cookiecutter-tools-options.png)

| Option | Beschreibung |
| --- | --- |
| URL des empfohlenen Feeds | Der Speicherort des empfohlenen Vorlagenfeeds. Hierbei kann es sich um eine URL oder den Pfad zu einer lokalen Datei handeln. Lassen Sie die URL leer, um den standardmäßigen, von Microsoft kuratierten Feed zu verwenden. Der Feed bietet eine einfache, durch Zeilenumbrüche getrennte Liste mit Vorlagenspeicherorten. Um Änderungen am kuratierten Feed anzufordern, führen Sie eine Pullanforderung in der [Quelle in GitHub](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt) aus. |
| Hilfe anzeigen | Steuert die Sichtbarkeit der Hilfeinformationsleiste am oberen Rand des Cookiecutter-Fensters. |

## <a name="optimizing-cookiecutter-templates-for-visual-studio"></a>Optimieren von Cookiecutter-Vorlagen für Visual Studio

Grundlegende Informationen zum Erstellen einer Cookiecutter-Vorlage finden Sie in der [Cookiecutter-Dokumentation](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Beachten Sie, dass die Cookiecutter-Erweiterung für Visual Studio Vorlagen unterstützt, die für Cookiecutter v1.4 erstellt wurden.

Die standardmäßige Umsetzung von Vorlagenvariablen hängt vom Datentyp ab (Zeichenfolge oder Liste):

- Zeichenfolge: Bezeichnung für den Variablennamen, Textfeld zum Eingeben eines Werts und ein Wasserzeichen mit dem Standardwert. Eine QuickInfo im Textfeld zeigt den Standardwert.
- Liste: Bezeichnung für den Variablennamen, Kombinationsfeld zum Auswählen eines Werts. Eine QuickInfo im Kombinationsfeld zeigt den Standardwert.

Diese Optionen können verbessert werden, indem Sie zusätzliche Metadaten in Ihrer `cookiecutter.json`-Datei angeben, die speziell für Visual Studio eingerichtet wurde (und von der Cookiecutter-Befehlszeilenschnittstelle ignoriert wird). Alle Eigenschaften sind optional:

| Eigenschaft | Beschreibung |
| --- | --- |
| Bezeichnung | Gibt an, was statt des Variablennamens über dem Editor für die Variable angezeigt werden soll. |
| Beschreibung | Gibt an, dass in der QuickInfo im Bearbeitungssteuerelement statt des Standardwerts für die Variable diese Beschreibung angezeigt werden soll. |
| URL | Ändert die Bezeichnung in einen Hyperlink mit einer QuickInfo, in der die URL angezeigt wird. Durch Klicken auf den Hyperlink wird diese URL im Standardbrowser des Benutzers geöffnet. |
| Auswahl | Ermöglicht die Anpassung des Editors für eine Variable. Folgende Auswahlmöglichkeiten werden zurzeit unterstützt:<ul><li>`string`: Standardtextfeld, standardmäßig für Zeichenfolgen.</li><li>`list`: Standardkombinationsfeld, standardmäßig für Listen.</li><li>`yesno`: Kombinationsfeld zur Auswahl zwischen `y` und `n`, für Zeichenfolgen.</li><li>`odbcConnection`: Textfeld mit einer „...“-Schaltfläche, die ein Dialogfeld für eine Datenbankverbindung öffnet.</li></ul> |

Beispiel:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="running-visual-studio-tasks"></a>Ausführen von Visual Studio-Tasks

Cookiecutter verfügt über eine Funktion namens *Post-Generate Hooks*, mit der nach dem Generieren der Dateien beliebiger Python-Code ausgeführt werden kann. Diese Funktion ist zwar flexibel, bietet jedoch keinen einfachen Zugriff auf Visual Studio.

Ein Beispiel: Sie möchten eine Datei im Visual Studio-Editor oder im Webbrowser öffnen oder die Visual Studio-Benutzeroberfläche aufrufen, die den Benutzer dazu auffordert, eine virtuelle Umgebung zu erstellen und erforderliche Paketelemente zu installieren.

Für diese Szenarien sucht Visual Studio in `cookiecutter.json` nach erweiterten Metadaten, mit denen die Befehle beschrieben werden, die ausgeführt werden müssen, nachdem ein Benutzer die generierten Dateien im Projektmappen-Explorer geöffnet hat oder nachdem die Dateien zu einem vorhandenen Projekt hinzugefügt wurden. (Auch hier kann der Benutzer die Ausführung der Tasks mithilfe der Vorlagenoption **Bei Abschluss zusätzliche Tasks ausführen** deaktivieren.)

Beispiel:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Befehle werden anhand ihres Namens angegeben, und Sie sollten auch in lokalisierten Installationen von Visual Studio die nicht lokalisierten (also englischen) Namen verwenden. Sie können Befehlsnamen im Visual Studio-Befehlsfenster testen und ermitteln.

Wenn Sie ein einzelnes Argument übergeben möchten, geben Sie es als Zeichenfolge an, wie im vorherigen Beispiel gezeigt.

Wenn Sie kein Argument übergeben müssen, geben Sie in der JSON eine leere Zeichenfolge an oder lassen die Zeile einfach weg:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Wenn Sie mehrere Argumente übergeben möchten, verwenden Sie ein Array. Wenn Sie Schalter verwenden, teilen Sie den Schalter und den zugehörigen Wert in separate Argumente auf, um eine ordnungsgemäße Angabe sicherzustellen. Beispiel:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Argumente können auf andere Cookiecutter-Variablen verweisen. In den oben stehenden Beispielen wird die interne `_output_folder_path`-Variable verwendet, um einen absoluten Pfad zu den generierten Dateien zu bilden.

Beachten Sie, dass der `Python.InstallProjectRequirements`-Befehl nur beim Hinzufügen von Dateien zu einem vorhandenen Projekt funktioniert. Dies liegt daran, dass der Befehl vom Python-Projekt im Projektmappen-Explorer verarbeitet wird und kein Projekt zum Empfangen der Meldung vorhanden ist, wenn Sie sich in der Ordneransicht des Projektmappen-Explorers befinden. Diese Einschränkung soll in einer zukünftigen Version aufgehoben werden (geplant ist auch eine bessere Unterstützung der Ordneransicht im Allgemeinen).

## <a name="troubleshooting"></a>Problembehandlung

### <a name="error-loading-template"></a>Fehler beim Laden der Vorlage

Einige Vorlagen verwenden in der `cookiecutter.json` möglicherweise ungültige Datentypen – z.B. einen booleschen Typ. Dies sollte dem Autor der Vorlage gemeldet werden. Klicken Sie im Informationsbereich der Vorlage auf den Link **Probleme**.

### <a name="hook-script-failed"></a>Fehler beim Hookskript

Einige Vorlagen verwenden möglicherweise Skripts zum Ausführen nach der Generierung, die nicht mit der Cookiecutter-Benutzeroberfläche kompatibel sind. Beispielsweise treten Fehler auf bei Skripts, die eine Eingabe vom Benutzer anfordern, da keine Terminalkonsole vorhanden ist.

### <a name="hook-script-not-supported-on-windows"></a>Keine Unterstützung für Hookskript unter Windows

Wenn die Postskriptdatei eine `.sh`-Datei ist, ist sie möglicherweise mit keiner Anwendung auf Ihrem Windows-Computer verknüpft. Möglicherweise wird ein Windows-Dialogfeld angezeigt, in dem Sie aufgefordert werden, eine kompatible Anwendung im Windows-Store zu suchen.

### <a name="templates-with-known-issues"></a>Vorlagen mit bekannten Fehlern

Klonfehler:

- **wildfish/cookiecutter-django-crud** (ungültiges `|`-Zeichen im Namen des Unterordners)
- **cookiecutter-pyvanguard** (ungültiges `|`-Zeichen im Namen des Unterordners)

Ladefehler:

- **chrisdev/wagtail-cookiecutter-foundation** (verwendet einen booleschen Typ in cookiecutter.json)
- **quintoandar/cookiecutter-android** (kein Vorlagenordner)

Ausführungsfehler:

- **iknite/cookiecutter-ansible-role** (Posthookskript erfordert Konsoleneingabe)
- **benregn/cookiecutter-django-ansible** (Jinja-Fehler)

Verwendet Bash (nicht schwerwiegend):

- **openstack-dev/cookiecutter**

