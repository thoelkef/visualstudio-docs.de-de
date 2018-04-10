---
title: Verwalten von Python-Umgebungen und -Interpretern | Microsoft-Dokumentation
description: Erfahren Sie, wie über das Fenster „Python-Umgebungen“ in Visual Studio globale und virtuelle Umgebungen verwaltet, benutzerdefinierte Umgebungen eingerichtet, Python-Interpreter und Pakete installiert, Suchpfade festgelegt und Umgebungen für Visual Studio-Projekte verwaltet werden.
ms.custom: ''
ms.date: 03/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: a1bf9c9c016a71c816ed8cc40b675c520e9c9397
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="managing-python-environments-in-visual-studio"></a>Verwalten von Python-Umgebungen in Visual Studio

Eine Python-*Umgebung* ist ein Kontext, in dem Sie Python-Code ausführen und der globale, virtuelle und Conda-Umgebungen umfasst. Eine Umgebung besteht aus einem Interpreter, einer Bibliothek (in der Regel die Python-Standardbibliothek) und mehreren installierten Paketen. Diese Komponenten bestimmen gemeinsam, welche Sprachkonstrukte und Syntax gültig sind, auf welche Betriebssystemfunktionen Sie zugreifen können und welche Pakete Sie verwenden können.

In Visual Studio unter Windows verwalten Sie, wie in diesem Artikel beschrieben, über das Fenster [Python-Umgebungen](#managing-python-environments-in-visual-studio) diese Umgebungen und wählen eine als Standard für neue Projekte. Für ein bestimmtes Projekt können Sie auch eine spezifische Umgebung wählen, anstatt die Standardumgebung zu verwenden.

**Hinweis**: Wenn Sie noch nicht mit Python in Visual Studio vertraut sind, finden Sie das erforderliche Hintergrundwissen in den folgenden Artikeln:

- [Arbeiten mit Python in Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Installieren von Python-Unterstützung für Visual Studio](installing-python-support-in-visual-studio.md)

Beachten Sie zudem, dass Sie keine Umgebungen für Python-Code verwalten können, der nur als Ordner über den Befehl **Datei > Öffnen > Ordner** geöffnet wurde. Stattdessen [erstellen Sie ein Python-Projekt aus vorhandenem Code](quickstart-01-python-in-visual-studio-project-from-existing-code.md), um die Umgebungsfeatures von Visual Studio nutzen zu können.

Wenn Sie Pakete in einer Umgebung installieren möchten, verwenden Sie die [Registerkarte „Pakete“](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Typen von Umgebungen

### <a name="global-environments"></a>Globale Umgebungen

Jede Python-Installation (z.B. Python 2.7, Python 3.6, Anaconda 4.4.0, usw., siehe [Auswählen und Installieren von Python-Interpretern](installing-python-interpreters.md)) verwaltet ihre eigene globale Umgebung. Jede Umgebung besteht aus dem spezifischen Python-Interpreter, einer Standardbibliothek und einer Reihe von vorinstallierten Paketen. Das Installieren eines Pakets in einer globalen Umgebung macht das Paket für alle Projekte verfügbar, die dieselbe Umgebung verwenden. Wenn sich die Umgebung in einem geschützten Bereich des Dateisystems befindet (z.B. in `c:\program files`), sind für die Installation von Paketen Administratorrechte erforderlich.

Globale Umgebungen sind für alle Projekte auf dem Computer verfügbar. Wählen Sie in Visual Studio eine globale Umgebung als Standardumgebung aus, die für alle Projekte genutzt wird, wenn Sie keine spezifische Umgebung für ein Projekt aussuchen. Weitere Informationen finden Sie unter [Auswählen einer Umgebung für ein Projekt](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Virtuelle Umgebungen

Da in einer globalen Umgebung installierte Pakete für alle Projekte verfügbar sind, die diese Umgebung verwenden, können Konflikte auftreten, wenn zwei Projekte inkompatible Pakete oder verschiedene Versionen des gleichen Pakets erfordern. Virtuelle Umgebungen umgehen diese Konflikte, indem sie den Interpreter und die Standardbibliothek einer globalen Umgebung verwenden, dabei aber ihre eigenen Pakete in isolierten Ordnern speichern und verwalten.

Sie können in Visual Studio eine virtuelle Umgebung für ein spezifisches Projekt erstellen, die in einem Unterordner des Projekts gespeichert wird. Visual Studio enthält einen Befehl, um eine `requirements.txt`-Datei aus der virtuellen Umgebung zu generieren. Dies vereinfacht das erneute Erstellen der Umgebung auf anderen Computern. Weitere Informationen finden Sie unter [Verwenden von virtuellen Umgebungen](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Conda-Umgebungen

Eine Conda-Umgebung wird mithilfe des `conda`-Tools erstellt. Conda-Umgebungen werden typischerweise im Ordner `envs` innerhalb einer Anaconda-Installation gespeichert und verhalten sich daher ähnlich wie globale Umgebungen. Wenn Sie z.B. ein neues Paket in einer Conda-Umgebung installieren, steht dieses Paket allen Projekten zur Verfügung, die diese Umgebung verwenden.

Visual Studio erkennt Conda-Umgebungen derzeit nicht automatisch, aber Sie können Visual Studio manuell darauf verweisen. Siehe [Manuelles Identifizieren einer vorhandenen Umgebung](#manually-identifying-an-existing-environment).

## <a name="the-python-environments-window"></a>Das Fenster „Python-Umgebungen“

Die Umgebungen, die Visual Studio bekannt sind, werden im Fenster **Python-Umgebungen** angezeigt. Zum Öffnen dieses Fensters können Sie eine der folgenden Methoden verwenden:

- Wählen Sie den Menübefehl **Ansicht > Weitere Fenster > Python-Umgebungen** aus.
- Klicken Sie für ein Projekt im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Python-Umgebungen**, und wählen Sie **Alle Python-Umgebungen anzeigen** aus:

    ![Befehl „Alle Umgebungen anzeigen“ im Projektmappen-Explorer](media/environments-view-all.png)

In jedem Fall wird das Fenster **Python-Umgebungen** als gleichgeordnete Registerkarte des Projektmappen-Explorers angezeigt:

![Fenster „Python-Umgebungen“](media/environments-default-view.png)

Die Abbildung oben zeigt, dass Visual Studio zwei Installationen von Python 3.6 (32 Bit) zusammen mit Anaconda 5.0.0 erkannt hat.

Die Standardumgebung in Fettdruck ist Python 3.6 (in diesem Fall Teil einer Anaconda-Installation), die Visual Studio für alle neuen Projekte verwendet. Die Befehle im unteren Teil des Fensters gelten für den ausgewählten Python 3.6-Interpreter, welcher die spezifische Installation in `C:\Python36-32` ist. Wenn eine Umgebung wider Erwarten nicht angezeigt wird, finden Sie weitere Informationen unter [Manuelles Identifizieren einer vorhandenen Umgebung](#manually-identifying-an-existing-environment).

Rechts neben jeder aufgelisteten Umgebung befindet sich ein Steuerelement, das ein interaktives Fenster für die jeweilige Umgebung öffnet. Ein anderes Steuerelement wird möglicherweise angezeigt, das die IntelliSense-Datenbank für diese Umgebung aktualisiert (unter
[Referenz zu Umgebungsfenstern](python-environments-window-tab-reference.md#intellisense-tab) erfahren Sie Näheres über die Datenbank).

Unter der Liste der Umgebungen befindet sich eine Dropdownauswahl für die Optionen **Übersicht**, **Pakete** und **IntelliSense**, die in der [Referenz zu den Registerkarten im Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md) beschrieben werden. Wenn Sie darüber hinaus das Fenster **Python-Umgebungen** weit genug erweitern, werden diese Optionen als Registerkarten angezeigt, was Ihre Arbeit damit erleichtern kann:

![Erweiterte Ansicht des Fensters „Python-Umgebungen“](media/environments-expanded-view.png)

> [!Note]
> Obwohl Visual Studio die Option „system-site-packages“ beachtet, gibt es keine Möglichkeit, sie in Visual Studio zu ändern.

|   |   |
|---|---|
| ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen") | [Sehen Sie sich ein Video (Microsoft Virtual Academy](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) zu Python-Umgebungen in Visual Studio an (2 Minuten, 35 Sekunden).|

### <a name="what-if-no-environments-appear"></a>Was geschieht, wenn keine Umgebungen angezeigt werden?

Wenn keine Umgebungen angezeigt werden, bedeutet dies, dass Visual Studio keine Python-Installationen an den standardmäßigen Speicherorten gefunden hat. Angenommen, Sie haben Visual Studio 2017 installiert, aber alle Interpreteroptionen in den Installeroptionen für den Python-Workload gelöscht. Ähnlich verhält es sich, wenn Sie während der Installation von Visual Studio 2015 oder früher keinen Interpreter manuell installiert haben (siehe [Installieren von Python-Interpretern](installing-python-interpreters.md)).

Wenn Sie wissen, dass ein Python-Interpreter auf Ihrem Computer vorhanden ist, Visual Studio (beliebige Version) diesen jedoch nicht erkennt, verwenden Sie den Befehl **+ Benutzerdefiniert...** , um dessen Speicherort manuell anzugeben. Lesen Sie hierzu den nächsten Abschnitt [Manuelles Identifizieren einer vorhandenen Umgebung](#manually-identifying-an-existing-environment).

> [!Tip]
> Visual Studio erkennt Updates auf einen vorhandenen Interpreter, z.B. ein Upgrade von Python 2.7.11 auf 2.7.14 mit den Installationsprogrammen von python.org. Während des Installationsvorgangs wird die ältere Umgebung aus der Liste der **Python-Umgebungen** entfernt und dann durch das Update ersetzt.
>
> Wenn Sie jedoch einen Interpreter und dessen Umgebung manuell über das Dateisystem verschieben, ist Visual Studio der neue Speicherort nicht bekannt. Weitere Informationen finden Sie unter [Verschieben eines Interpreters](installing-python-interpreters.md#moving-an-interpreter).

## <a name="manually-identifying-an-existing-environment"></a>Manuelles Identifizieren einer vorhandenen Umgebung

Führen Sie die folgenden Schritte aus, um eine Umgebung, wie z.B. eine Conda-Umgebung, zu identifizieren, die an einem nicht standardmäßigen Ort installiert ist:

1. Wählen Sie im Fenster **Python-Umgebungen** die Option **+ Benutzerdefiniert...** , um die Registerkarte **Konfigurieren** zu öffnen:

    ![Standardansicht für eine neue benutzerdefinierte Umgebung](media/environments-custom-1.png)

1. Geben Sie einen Namen für die Umgebung in das Feld **Beschreibung** ein.

1. Geben Sie den Pfad des Interpreters in das Feld **Präfixpfad** ein, oder navigieren Sie dahin (mithilfe von **...***).

1. Wenn Visual Studio einen Python-Interpreter an diesem Speicherort erkennt (z.B. unter dem unten gezeigten Pfad für eine Conda-Umgebung), wird der Befehl **Automatische Erkennung** aktiviert. Durch Auswahl von **Automatische Erkennung* werden die verbleibenden Felder ausgefüllt. Sie können diese Felder auch manuell ausfüllen.

    ![Aktivieren des Befehls zur automatischen Erkennung](media/environments-custom-2.png)

    ![Ausfüllen der Felder für die Umgebung nach der automatischen Erkennung](media/environments-custom-3.png)

1. Sobald die Felder alle gewünschten Werte enthalten, wählen Sie **Übernehmen**, um die Konfiguration zu speichern. Sie können die Umgebung nun wie jede andere in Visual Studio verwenden.

1. Wenn Sie eine manuell identifizierte Umgebung entfernen möchten, wählen Sie auf der Registerkarte **Konfigurieren** den Befehl **Entfernen** aus. Umgebungen mit automatischer Erkennung bieten diese Option nicht. Weitere Informationen finden Sie unter [Registerkarte „Konfigurieren“](python-environments-window-tab-reference.md#configure-tab).

## <a name="see-also"></a>Siehe auch

- [Installieren von Python-Interpretern](installing-python-interpreters.md)
- [Auswählen eines Interpreters für ein Projekt](selecting-a-python-environment-for-a-project.md)
- [Verwenden von "requirements.txt" für Abhängigkeiten](managing-required-packages-with-requirements-txt.md)
- [Suchpfade](search-paths.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)