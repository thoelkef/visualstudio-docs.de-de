---
title: Python-Projekte in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 07/13/2017
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
ms.openlocfilehash: 44065522229a1661efc41e79905d9650f7949ac3
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2017
---
# <a name="python-projects"></a>Python-Projekte

Python-Anwendungen werden in der Regel nur mit Ordnern und Dateien definiert, aber diese Struktur kann bei größeren Anwendungen, die vielleicht automatisch generierte Dateien, JavaScript für Webanwendungen usw. einbeziehen, komplex werden. Um diese Komplexität in den Griff zu bekommen, können Sie Visual Studio-Projekte für Python-Anwendungen erstellen. Ein Python-Projekt (eine `.pyproj`-Datei) identifiziert alle Quell- und Inhaltsdateien des Projekts, enthält Buildinformationen für jede Datei, verwaltet die Informationen zur Integration in Quellcodeverwaltungssysteme und hilft Ihnen, Ihre Anwendung in logischen Komponenten zu organisieren.

Darüber hinaus werden Projekte immer in einer Visual Studio-*Projektmappe* verwaltet, die eine beliebige Anzahl von Projekten enthalten kann, die möglicherweise aufeinander verweisen. Ein Python-Projekt kann z.B. auf ein C++-Projekt für ein Erweiterungsmodul verweisen, sodass Visual Studio (falls erforderlich) automatisch das C++-Projekt erstellt, wenn Sie mit dem Debuggen des Python-Projekts beginnen. (Eine allgemeine Erörterung finden Sie unter [Projektmappen und Projekte in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).)

![Python-Projekt im Projektmappen-Explorer](media/projects-solution-explorer.png)

Visual Studio bietet eine Vielzahl von Python-Projektvorlagen, mit der Sie schnell eine Reihe von Anwendungsstrukturen einrichten können, einschließlich einer Vorlage zum Erstellen eines Projekts aus einer vorhandenen Ordnerstruktur und einer Vorlage zum Erstellen eines leeren Projekts. Einen Index finden Sie unten unter [-Projektvorlagen](#project-templates).

In diesem Thema:

- [Hinzufügen von Dateien, Zuweisen einer Startdatei und Festlegen von Umgebungen](#adding-files-assigning-a-startup-file-and-setting-environments)
- [Projektvorlagen](#project-templates)
- [Verknüpfte Dateien](#linked-files)
- [Verweise](#references)

<a name="lightweight-usage-project-free"</a>
> [!Tip]
> Auch ohne Projekt funktioniert Visual Studio gut mit Python-Code, da Sie eine Python-Datei unabhängig öffnen und automatische Vervollständigung, IntellSense und Debuggen (indem Sie mit der rechten Maustaste im Editor klicken und **[Mit|Ohne] Debuggen starten** auswählen) genießen können. Da diese Art von Code immer die globale Standardumgebung verwendet, stellen Sie jedoch möglicherweise falsche Vervollständigungen oder Fehler fest, wenn der Code für eine andere Umgebung vorgesehen ist. Darüber hinaus analysiert Visual Studio alle Dateien und Pakete in dem Ordner, in dem die einzelne Datei geöffnet wird, was sehr viel CPU-Zeit in Anspruch nimmt.
>
> Es ist einfach, ein Visual Studio-Projekt aus vorhandenem Code zu erstellen, wie unten in [Erstellen eines Projekts aus vorhandenen Dateien](#creating-a-project-from-existing-files) beschrieben.

Eine Einführung in Projekte mit Python in Visual Studio finden Sie im Video [Getting Python Code (Abrufen von Python-Code)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=iLAv23LWE_3905918567) (Microsoft Virtual Academy, 2 Min. 17 Sek.).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Getting-Python-Code-iLAv23LWE_3905918567]

Sehen Sie sich auch das ältere Video [Deep Dive: Using source control with Python projects (Tieferer Einblick: Verwenden der Quellcodeverwaltung mit Python-Projekten)](https://youtu.be/Aq8eqApnugM) (youtube.com, 8 Min. 55 Sek.) an.

## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>Hinzufügen von Dateien, Zuweisen einer Startdatei und Festlegen von Umgebungen

Bei der Entwicklung Ihrer Anwendung müssen Sie dem Projekt in der Regel neue Dateien verschiedenen Typs hinzufügen. Um solche Dateien hinzuzufügen, müssen Sie einfach mit der rechten Maustaste auf das Projekt klicken und **Hinzufügen > Vorhandenes Element...** auswählen, um nach einer hinzuzufügenden Datei zu suchen, oder **Hinzufügen > Neues Element...**, worauf ein Dialogfeld mit einer Vielzahl von Elementvorlagen einschließlich leerer Python-Dateien, einer Python-Klasse, eines Unittests und verschiedener Dateien im Zusammenhang mit Webanwendungen angezeigt wird. Wir empfehlen Ihnen, diese Optionen mit einem Testprojekt zu erforschen, um zu erfahren, was in Ihrer Visual Studio-Version verfügbar ist.

Jedem Python-Projekt ist eine im Projektmappen-Explorer fett angezeigte Startdatei zugewiesen. Die Startdatei ist die Datei, die ausgeführt wird, wenn Sie das Debuggen starten (F5 oder **Debuggen > Debuggen starten**) oder das Projekt im interaktiven Fenster ausführen (UMSCHALT+ALT+ F5 oder **Debuggen > Projekt in interaktivem Python ausführen**). Um dies zu ändern, klicken Sie mit der rechten Maustaste auf die neue Datei, und wählen Sie **Als Startdatei festlegen**.

> [!Tip]
> Wenn Sie die ausgewählte Datei aus einem Projekt entfernen und keine neue auswählen, wird beim Versuch, Ihr Projekt auszuführen, ein Python-Ausgabefenster angezeigt, dass aber daraufhin sofort wieder verschwindet. Wenn dieses Verhalten auftritt, überprüfen Sie, ob Sie eine zugewiesene Startdatei haben. Damit das Ausgabefenster in Fällen wie diesem geöffnet bleibt, klicken Sie mit der rechten Maustaste auf Ihr Projekt, wählen Sie **Eigenschaften** und dann die Registerkarte **Debuggen** aus, fügen Sie anschließend `-i` zum Feld **Interpreterargumente** hinzu. Durch dieses Argument wird der Interpreter nach Abschluss des Programms in den interaktiven Modus versetzt, und das Fenster bleibt dabei offen, bis Sie STRG + Z, EINGABETASTE zum Beenden drücken.

Ein neues Projekt ist immer der standardmäßigen globalen Python-Umgebung zugeordnet. Um das Projekt einer anderen Umgebung zuzuordnen (einschließlich virtueller Umgebungen), klicken Sie mit der rechten Maustaste auf den **Python-Umgebungen**-Knoten im Projekt, wählen Sie **Python-Umgebungen hinzufügen/entfernen**, und wählen Sie die gewünschten Umgebungen. Um die aktive Umgebung zu ändern, klicken Sie mit der rechten Maustaste auf die gewünschte Umgebung, und wählen Sie **Umgebung aktivieren**, wie unten dargestellt. Nähere Informationen finden Sie unter [Python-Umgebungen](python-environments.md#project-specific-environments).

![Aktivieren einer Umgebung für ein Python-Projekt](media/projects-activate-environment.png)

<a name="project-types"</a>
## <a name="project-templates"></a>Projektvorlagen

Visual Studio bietet Ihnen eine Reihe von Methoden zum Einrichten eines Python-Projekts, entweder von Grund auf oder aus vorhandenem Code. Um eine Vorlage zu verwenden, wählen Sie den Menübefehl **Datei > Neu > Projekt...**, oder klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf die Projektmappe, und wählen Sie **Hinzufügen > Neues Projekt...**. In beiden Fällen rufen Sie so das folgende Dialogfeld **Neues Projekt** auf. Um Python-spezifische Vorlagen anzuzeigen, suchen Sie entweder nach „Python“, oder wählen Sie den Knoten **Vorlagen > Andere Sprachen > Python**:

![Dialogfeld „Neues Projekt“ mit Python-Vorlagen](media/projects-new-project-dialog.png)

Die folgende Tabelle fasst die in Visual Studio 2017 verfügbaren Vorlagen zusammen (nicht alle Vorlagen stehen in allen früheren Versionen zur Verfügung):

| Vorlage | Beschreibung | 
| --- | --- |
| [Aus vorhandenem Python-Code](#creating-a-project-from-existing-files) | Erstellt ein Visual Studio-Projekt aus vorhandenem Python-Code in einer Ordnerstruktur.  |
| Python-Anwendung | Eine grundlegende Projektstruktur für eine neue Python-Anwendung mit einer einzelnen, leeren Quelldatei. Standardmäßig wird das Projekt im Konsoleninterpreter der globalen Standardumgebung ausgeführt, die Sie durch [Zuweisen einer anderen Umgebung](python-environments.md#project-specific-environments) ändern können. |
| [Azure-Clouddienst](template-azure-cloud-service.md) | Ein in Python geschriebenes Projekt für einen Azure-Clouddienst. |
| [Webprojekte](template-web.md) | Auf verschiedenen Frameworks einschließlich Bottle, Django, Flask und Flask/Jade basierende Projekte für Webserver. |
| IronPython-Anwendung | Ähnlich wie die Python-Anwendungsvorlage, verwendet aber IronPython durch standardmäßige Aktivierung .von NET-Interop und Debuggen im gemischten Modus mit .NET-Sprachen. |
| IronPython-WPF-Anwendung | Eine Projektstruktur mit IronPython mit Windows Presentation Foundation-XAML-Dateien für die Benutzeroberfläche der Anwendung. Visual Studio bietet einen XAML-Benutzeroberflächen-Designer, CodeBehind kann in Python geschrieben werden, und die Anwendung wird ohne Anzeige einer Konsole ausgeführt. |
| IronPython-Silverlight-Webseite | Ein IronPython-Projekt, das in einem Browser mit Silverlight ausgeführt wird. Der Python-Code für die Anwendung ist auf der Webseite als Skript enthalten. Ein Codebaustein-Skript-Tag übernimmt JavaScript-Code, der die Ausführung von IronPython in Silverlight initialisiert, von wo aus der Python-Code mit dem DOM kommunizieren kann. |
| IronPython-Windows Forms-Anwendung | Eine Projektstruktur mit IronPython, wo die Benutzeroberfläche mithilfe von Windows Forms-Code erstellt wird. Die Anwendung wird ohne Anzeige einer Konsole ausgeführt. |
| Hintergrundanwendung (IoT) | Unterstützt die Bereitstellung von Python-Projekten zur Ausführung als Hintergrunddienste auf Geräten. Unter [Windows 10 IoT Core](https://dev.windows.com/en-us/iot) erhalten Sie weitere Informationen. |
| Python-Erweiterungsmodul | Diese Vorlage wird unter Visual C++ angezeigt, wenn Sie die **nativen Python-Entwicklungstools** mit der Python-Arbeitsauslastung in Visual Studio 2017 installiert haben (weitere Informationen finden Sie unter [Installation](installation.md)). Sie stellt die grundlegende Struktur für eine C++-Erweiterungs-DLL bereit, ganz ähnlich der, die unter [Erstellen einer C++-Erweiterung für Python](cpp-and-python.md) beschrieben ist. |

<a name="create-project-from-existing-files"</a>

### <a name="creating-a-project-from-existing-files"></a>Erstellen eines Projekts aus vorhandenen Dateien

> [!Important]
> Der hier beschriebene Prozess verschiebt oder kopiert die ursprünglichen Quelldateien nicht. Wenn Sie mit einer Kopie arbeiten möchten, erstellen Sie zunächst eine Kopie des Ordners.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>Verknüpfte Dateien

Verknüpfte Dateien sind Dateien, die in ein Projekt eingebunden sind, sich aber in der Regel außerhalb der Projektordner der Anwendung befinden. Sie werden im Projektmappen-Explorer wie normale Dateien überlagert mit einem Verknüpfungssymbol angezeigt: ![Dateiverknüpfungssymbol](media/projects-linked-file-icon.png)

Verknüpfte Dateien werden in der `.pyproj`-Datei mit dem normalen `<Compile Include="...">`-Element angegeben. Sie können implizite verknüpfte Dateien sein, wenn sie einen relativen Pfad außerhalb der Verzeichnisstruktur verwenden, oder explizite verknüpfte Dateien, deren Pfad im Projektmappen-Explorer angeben ist:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

Verknüpfte Dateien werden unter folgenden Bedingungen ignoriert:

- Die verknüpfte Datei enthält Linkmetadaten, und der im Include-Attribut angegebene Pfad befindet sich im Projektverzeichnis.
- Die verknüpfte Datei dupliziert eine Datei, die in der Projekthierarchie vorhanden ist
- Die verknüpfte Datei enthält Linkmetadaten, und der Linkpfad ist ein relativer Pfad außerhalb der Projekthierarchie.
- Der Linkpfad ist ein Stammpfad.

### <a name="working-with-linked-files"></a>Arbeiten mit verknüpften Dateien

Klicken Sie zum Hinzufügen eines vorhandenen Elements als Link mit der rechten Maustaste auf den Ordner im Projekt, dem Sie die Datei hinzufügen möchten, und wählen Sie **Hinzufügen > Vorhandenes Element...**. Wählen Sie im daraufhin angezeigten Dialogfeld eine Datei aus, und wählen Sie **Als Link hinzufügen** aus der Dropdownliste der Schaltfläche **Hinzufügen**. Sofern keine in Konflikt stehenden Dateien vorhanden sind, wird mit diesem Befehl ein Link im ausgewählten Ordner erstellt. Allerdings wird der Link nicht hinzugefügt, wenn bereits eine Datei mit dem gleichen Namen vorhanden ist, oder ein Link zu dieser Datei bereits im Projekt vorhanden ist.

Wenn Sie versuchen, eine Verknüpfung zu einer Datei zu erstellen, die bereits im Projektordner vorhanden ist, wird sie als normale Datei und nicht als Link hinzugefügt. Um eine Datei in einen Link zu konvertieren, wählen Sie **Datei > Speichern unter**, um die Datei an einem Speicherort außerhalb der Projekthierarchie zu speichern; Visual Studio konvertiert sie automatisch in einen Link. Auf ähnliche Weise kann ein Link mit **Datei > Speichern unter** zurückkonvertiert werden, um die Datei an beliebiger Stelle in der Projekthierarchie zu speichern. 

Wenn Sie eine verknüpfte Datei im Projektmappen-Explorer verschieben, wird der Link verschoben, aber die eigentliche Datei ist nicht betroffen. Ebenso wird beim Löschen eines Links nur der Link entfernt, ohne Auswirkung auf die Datei.

Verknüpfte Dateien können nicht umbenannt werden.

## <a name="references"></a>Verweise

Visual Studio-Projekte unterstützen das Hinzufügen von Verweisen auf Projekte und Erweiterungen, die im Projektmappen-Explorer unter dem **Verweise**-Knoten angezeigt werden:

![Erweiterungsverweise in Python-Projekten](media/projects-extension-references.png)

Erweiterungsverweise geben in der Regel Abhängigkeiten zwischen Projekten an und dienen zum Bereitstellen von IntelliSense beim Entwurf oder der Verknüpfung bei der Kompilierung. Python-Projekte verwenden Verweise ähnlich, aber aufgrund der Dynamik von Python werden sie in erster Linie zur Entwurfszeit verwendet, um verbessertes IntelliSense bereitzustellen. Sie können auch für die Bereitstellung in Microsoft Azure verwendet werden, um zusätzliche Abhängigkeiten zu installieren.

### <a name="extension-modules"></a>Erweiterungsmodule

Ein Verweis auf eine `.pyd`-Datei aktiviert IntelliSense für das generierte Modul. Visual Studio lädt die `.pyd`-Datei in den Python-Interpreter und prüft Typen und Funktionen. Es wird auch versucht, die Dokumentzeichenfolgen für Funktionen zu analysieren, um Signaturhilfe zu bieten.

Wenn zu einem beliebigen Zeitpunkt das Erweiterungsmodul auf dem Datenträger aktualisiert wird, analysiert Visual Studio das Modul im Hintergrund neu. Diese Aktion hat keine Auswirkung auf das Laufzeitverhalten, aber einige Vervollständigungen stehen nicht zur Verfügung, bis die Analyse abgeschlossen ist.

Sie müssen dem Ordner, der das Modul enthält, möglicherweise auch einen [Suchpfad](python-environments.md#search-paths) hinzufügen.

### <a name="net-projects"></a>.NET-Projekte

Bei der Arbeit mit IronPython können Sie .NET-Assemblys Verweise hinzufügen, um IntelliSense zu aktivieren. Klicken Sie für .NET-Projekte in der Projektmappe mit der rechten Maustaste auf den **Verweise**-Knoten in Ihrem Python-Projekt, wählen Sie **Verweis hinzufügen**, wählen Sie die **Projekte**-Registerkarte, und suchen Sie das gewünschte Projekt. Wählen Sie für DLLs, die Sie separat heruntergeladen haben, stattdessen die Registerkarte **Durchsuchen**, und navigieren Sie zu der gewünschten DLL.

Da Verweise in IronPython nicht verfügbar sind, bis ein Aufruf von `clr.AddReference('AssemblyName')` erfolgt, müssen Sie der Assembly auch einen `clr.AddReference`-Aufruf hinzufügen.

### <a name="webpi-projects"></a>WebPI-Projekte

Sie können WebPI-Produkteinträgen Verweise für die Bereitstellung im Microsoft Azure Cloud-Dienst hinzufügen, wo Sie zusätzliche Komponenten über den WebPI-Feed installieren können. Standardmäßig ist der angezeigte Feed Python-spezifisch und enthält Django, CPython und andere Kernkomponenten. Sie können auch Ihre eigenen Feeds auswählen, wie unten dargestellt. Beim Veröffentlichen in Microsoft Azure installiert eine Setupaufgabe alle Produkte, auf die verwiesen wird.

![WebPI-Verweise](media/projects-webPI-components.png)