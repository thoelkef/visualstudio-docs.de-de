---
title: Optionen, Text-Editor, C/C++, Erweitert | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 236135cd4b4f813471ece7a0eeb1b221c7242df9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662362"
---
# <a name="options-text-editor-cc-advanced"></a>Optionen, Text-Editor, C/C++, Erweitert
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie diese Optionen ändern, können Sie beim Programmieren in C oder C++ das Verhalten ändern, das mit IntelliSense und der Suchdatenbank zusammenhängt.

 Klicken Sie zum Öffnen dieser Seite im linken Fenster auf das Dialogfeld **Optionen**, erweitern Sie **Text-Editor** und **C/C++** , und klicken Sie dann auf **Erweitert**.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Informationen hierzu finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio)](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Durchsuchen/Navigation
 Diese Optionen sollten nur in dem seltenen Fall ausgewählt werden, wenn eine Projektmappe so groß ist, dass die Datenbankaktivität einen unzulässigen Anteil der Systemressourcen beansprucht.

 **Datenbank deaktivieren** Die gesamte Verwendung der Code Suchdatenbank (SDF), alle anderen Browser-/Navigationsoptionen und alle IntelliSense-Features, außer #include Auto vervollständigen, sind deaktiviert.

 **Daten Bank Updates deaktivieren** Die Datenbank wird schreibgeschützt geöffnet, und es werden keine Updates ausgeführt, wenn Dateien bearbeitet werden. Die meisten Funktionen können weiterhin verwendet werden. Bei Vornahme von Änderungen veralten die Daten jedoch, und Sie erhalten falsche Ergebnisse.

 **Automatische Daten Bank Updates deaktivieren** Die Code Suchdatenbank wird nicht automatisch aktualisiert, wenn Quelldateien geändert werden. Wenn Sie jedoch den **Projektmappen-Explorer** und das Kontextmenü für das Projekt öffnen und dann **Projektmappe neu prüfen** auswählen, werden alle veralteten Dateien überprüft, und die Datenbank wird aktualisiert.

 **Implizite Dateien deaktivieren** Die Code Suchdatenbank erfasst keine Daten für Dateien, die nicht in einem Projekt angegeben sind. Ein Projekt enthält Quelldateien und Headerdateien, die explizit angegeben werden. Implizite Dateien sind in expliziten Dateien enthalten (beispielsweise afxwin.h, windows.h und atlbase.h). Normalerweise findet das System diese Dateien und indiziert sie auch für unterschiedliche Suchfunktionen (einschließlich "Navigieren zu"). Wenn Sie diese Option auswählen, werden diese Dateien nicht indiziert, und einige Funktionen stehen ihnen nicht zur Verfügung. Wenn Sie diese Option auswählen, werden "Implizites Bereinigen deaktivieren" und "Externe Abhängigkeiten deaktivieren" ebenfalls implizit ausgewählt.

 **Implizites bereinigen deaktivieren** Die Code Suchdatenbank bereinigt keine impliziten Dateien, auf die nicht mehr verwiesen wird. Diese Option verhindert, dass implizite Dateien aus der Datenbank entfernt werden, wenn sie nicht mehr verwendet werden. Wenn Sie beispielsweise eine `#include`-Direktive hinzufügen, die festlegt, dass mapi.h auf eine der Quelldateien verweist, wird mapi.h gefunden und indiziert. Wenn Sie #include anschließend entfernen und von keinem anderen Ort auf die Datei verwiesen wird, werden die Informationen über die Datei schließlich entfernt, es sei denn, Sie wählen diese Option aus. (Weitere Informationen finden Sie unter Option zum erneuten Einlesen des **Lösungs Intervalls** Diese Option wird ignoriert, wenn Sie die Projekt Mappe explizit neu einlesen.

 **Ordner für externe Abhängigkeiten deaktivieren** Der Ordner "externe Abhängigkeiten" für jedes Projekt wird nicht erstellt oder aktualisiert. Im **Projektmappen-Explorer** enthält jedes Projekt einen Ordner für externe Abhängigkeiten mit allen impliziten Dateien für dieses Projekt. Wenn Sie diese Option auswählen, wird dieser Ordner nicht angezeigt.

 **Datenbank neu erstellen** Erstellen Sie die Code Suchdatenbank beim nächsten Laden der Projekt Mappe neu. Wenn Sie diese Option auswählen, wird die SDF-Datenbankdatei beim nächsten Laden der Projektmappe gelöscht, was zur Folge hat, dass die Datenbank neu erstellt wird und alle Dateien indiziert werden.

 **Lösungs Intervall neu** einlesen Der Auftrag "Projekt Mappe jetzt neu einlesen" ist für das von Ihnen angegebene Intervall geplant. Sie müssen einen Wert zwischen 0 und 5000 Minuten angeben. Der Standardwert ist 60 Minuten. Beim erneuten Durchsuchen der Projektmappe werden die Zeitstempel der Dateien überprüft, um zu bestimmen, ob eine Datei außerhalb der IDE geändert wurde. (Änderungen, die in der IDE vorgenommen werden, werden automatisch nachverfolgt, und die Dateien werden aktualisiert.) Implizit enthaltene Dateien werden geprüft, um zu bestimmen, ob auf Sie noch verwiesen wird.

## <a name="diagnostic-logging"></a>Diagnoseprotokollierung
 Diese Optionen stehen zur Verfügung, falls Sie von Microsoft gebeten werden, weitere Informationen zur Diagnose eines Problems zu sammeln. Da die Protokollierungsinformationen für Benutzer nicht hilfreich sind, empfehlen wir, sie deaktiviert zu belassen.

 **Aktivieren der Protokollierung** Aktiviert die Diagnoseprotokollierung im Ausgabefenster.

 **Protokolliergrad** Legen Sie die Ausführlichkeit des Protokolls von 0 auf 5 fest.

 **Protokollierungs Filter** Filtert angezeigte Ereignis Typen mit einer Bitmaske.

 Wird durch eine Summe aus den folgenden Optionen festgelegt:

- 0 – Keine

- 1 – Allgemein

- 2 – Leerlauf

- 4 – WorkItem

- 8 – IntelliSense

- 16 – ACPerf

- 32 – ClassView

## <a name="fallback-location"></a>Ausweichpfad
 Der Ausweichpfad gibt an, wo die SDF- und IntelliSense-Unterstützungsdateien (beispielsweise iPCH) abgelegt werden, wenn der primäre Speicherort (dasselbe Verzeichnis wie die Projektmappe) nicht verwendet wird. Diese Situation kann auftreten, wenn der Benutzer keine Schreibberechtigungen für das Projektmappenverzeichnis hat, oder wenn sich das Projektmappenverzeichnis auf einem langsamen Gerät befindet. Der Standardausweichpfad befindet sich im temporären Verzeichnis des Benutzers.

 **Immer Fall Back Pfad verwenden** Gibt an, dass die Code Suchdatenbank und IntelliSense-Dateien immer in einem Ordner gespeichert werden sollen, den Sie als "Ausweich Pfad" angeben, nicht neben der SLN-Datei. Die IDE legt die SDF- oder iPCH-Dateien nie neben dem Projektmappenverzeichnis ab und verwendet immer den Ausweichpfad.

 **Nicht warnen, wenn Ausweich Pfad verwendet wird** Sie werden nicht informiert oder aufgefordert, wenn ein "Ausweich Pfad" verwendet wird. Normalerweise werden Sie von der IDE informiert, wenn der Ausweichpfad verwendet wurde. Mit dieser Option wird diese Warnung deaktiviert.

 **Fallbackort** Dieser Wert wird als sekundärer Speicherort zum Speichern der Code Suchdatenbank oder IntelliSense-Dateien verwendet. Das temporäre Verzeichnis ist standardmäßig der Ausweichpfad. Die IDE erstellt ein Unterverzeichnis unter dem angegebenen Pfad (oder im temporären Verzeichnis), das den Namen der Projektmappe zusammen mit einem Hash des vollständigen Pfads zur Projektmappe enthält. Dadurch werden Probleme mit identischen Projektmappennamen vermieden.

## <a name="intellisense"></a>IntelliSense
 **Automatische QuickInfo** Aktiviert Quick Infos, wenn Sie den Zeiger über Text bewegen.

 **IntelliSense deaktivieren** Deaktiviert alle IntelliSense-Funktionen. Die IDE erstellt keine VCPkgSrv.exe-Prozesse für IntelliSense-Anforderungen, und die IntelliSense-Funktionen werden nicht ausgeführt (QuickInfo, Memberliste, AutoVervollständigen, Parameterhilfe). Semantische Einfärbung und Verweishervorhebung sind ebenfalls deaktiviert. Diese Option deaktiviert keine Browserfunktionen, die ausschließlich von der Datenbank abhängen (einschließlich Navigationsleiste, ClassView und Eigenschaftenfenster).

 **Automatisches Aktualisieren deaktivieren** Die Aktualisierung von IntelliSense wird verzögert, bis eine tatsächliche Anforderung für IntelliSense erfolgt. Diese Verzögerung kann zu einer längeren Ausführungszeit des ersten IntelliSense-Vorgangs für eine Datei führen. Es kann jedoch hilfreich sein, diese Option auf sehr langsamen oder ressourcenbeschränkten Geräten festzulegen. Wenn Sie diese Option auswählen, wählen Sie auch implizit die Optionen "Fehlerberichterstellung deaktivieren" und "Wellenlinien deaktivieren".

 **Fehlerberichterstattung deaktivieren** Deaktiviert die Berichterstellung von IntelliSense-Fehlern über Wellenlinien und das Fenster "Fehlerliste". Außerdem wird das Analysieren im Hintergrund deaktiviert, das mit der Fehlerberichterstellung zusammenhängt. Wenn Sie diese Option auswählen, wählen Sie auch implizit die Option "Wellenlinien dekativieren" aus.

 Wellenlinien **Deaktivieren** Deaktiviert IntelliSense-Fehler Wellenlinien. Die roten Wellenlinien werden nicht im Editorfenster, der Fehler jedoch weiterhin im Fenster "Fehlerliste" angezeigt.

 **Deaktivieren #include Auto Vervollständigen** Deaktiviert die automatische Vervollständigung von `#include` Anweisungen.

 **Schrägstrich in #include Auto Vervollständigen verwenden** Löst die automatische Vervollständigung von `#include`-Anweisungen aus, wenn "/" verwendet wird. Das Standardtrennzeichen ist der umgekehrte Schrägstrich (\). Der Compiler akzeptiert beide. Geben Sie daher mit dieser Option an, welches Zeichen in Ihrer Codebasis verwendet wird.

 **Maximale Anzahl zwischen gespeicherter Übersetzungseinheiten** Die maximale Anzahl von Übersetzungseinheiten, die zu einem beliebigen Zeitpunkt für IntelliSense-Anforderungen aktiv gehalten werden. Sie müssen einen Wert zwischen 2 und 15 angeben. Diese Zahl bezieht sich direkt auf die maximale Anzahl von ausgeführten VCPkgSrv.exe-Prozessen (für eine angegebene Instanz von Visual Studio). Der Standardwert ist 2. Wenn Sie jedoch verfügbaren Arbeitsspeicher haben, können Sie diesen Wert erhöhen und erzielen möglicherweise eine bessere IntelliSense-Leistung.

 Weitere Informationen zu Übersetzungseinheiten finden Sie unter [Phasen der Übersetzung](https://msdn.microsoft.com/library/a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db).

 **Aggressive Mitgliederliste deaktivieren** Die Elementliste wird nicht angezeigt, wenn Sie den Namen eines Typs oder einer Variablen eingeben. Die Liste wird nur nach Eingabe eines der Commitzeichen angezeigt, die in der Option **Commitzeichen der Memberliste** definiert wurden.

 **Schlüsselwörter für Member auflisten deaktivieren** Sprach Schlüsselwörter, wie z. b. `void`, `class` `switch`, werden nicht in Vorschlägen der Mitgliederliste angezeigt

 **Code Ausschnitte für Mitgliederliste deaktivieren** Code Ausschnitte werden in Vorschlägen der Mitgliederliste nicht angezeigt.

 **Semantische Farbgebung deaktivieren** Deaktiviert die farbliche Kennzeichnung von Code mit Ausnahme von sprach Schlüsselwörtern, Zeichen folgen und Kommentaren.

 **Commit für Smart Member List** Fügt eine Zeile hinzu, wenn Sie die EINGABETASTE am Ende eines vollständig typisierten Worts auswählen.

 **Filter Modus** der Elementliste Legt den Typ des übereinstimmenden Algorithmus fest. **Fuzzy** sucht die meisten möglichen Übereinstimmungen, da ein Algorithmus zur Suche von ähnlichen, jedoch nicht identischen Übereinstimmungen verwendet wird, der einer Rechtschreibprüfung ähnelt. **Intelligentes Filtern** sucht Übereinstimmungen in Teilzeichenfolgen, auch wenn sie nicht am Anfang eines Worts stehen. **Präfix** sucht nur Übereinstimmungen in identischen Teilzeichenfolgen am Wortanfang.

 **Commit-Zeichen für Mitgliederliste** Gibt die Zeichen an, die bewirken, dass für den aktuell markierten Member List-Vorschlag ein Commit ausgeführt wird. Sie können Zeichen zu dieser Liste hinzufügen oder aus der Liste entfernen.

## <a name="references"></a>Verweise
 **Auflösen deaktivieren** Aus Leistungsgründen zeigt "alle Verweise suchen" standardmäßig unformatierte Text Suchergebnisse an, anstatt IntelliSense zur Überprüfung der einzelnen Kandidaten zu verwenden. Sie können dieses Kontrollkästchen deaktivieren, um genauere Ergebnisse aus sämtlichen Suchoperationen zu erhalten. Öffnen Sie zum Filtern pro Suche das Kontextmenü für die Ergebnisliste, und wählen Sie dann "Ergebnisse auflösen" aus.

 **Nicht bestätigte ausblenden** Blenden Sie nicht bestätigte Elemente in den Ergebnissen von "alle Verweise suchen" aus. Wenn Sie die Option "Auflösen deaktiveren" nicht festlegen, können Sie mit dieser Option unbestätigte Elemente in den Ergebnissen ausblenden.

 **Markieren von Verweisen deaktivieren**

## <a name="see-also"></a>Siehe auch
 [Festlegen von sprachspezifischen Editoroptionen](../../ide/reference/setting-language-specific-editor-options.md)
