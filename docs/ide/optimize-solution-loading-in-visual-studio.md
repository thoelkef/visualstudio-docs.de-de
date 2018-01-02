---
redirect_url: /visualstudio/ide/optimize-visual-studio-startup-time/
ms.openlocfilehash: 6ba351d5b395caaddd12021b09f8792cd19b2905
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2017
---
title: "Optimieren des Ladens von Projektmappen in Visual Studio | Microsoft-Dokumentation" ms.custom: "" ms.date: 08/31/2017 ms.reviewer: "" ms.suite: "" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "startup time [Visual Studio]"
  - "optimizing startup time [Visual Studio]"
  - "speed up start time [Visual Studio]" ms.assetid: 84989983-84bc-4f81-97a8-2131e3a25138 caps.latest.revision: 4 author: "gewarren" ms.author: "gewarren" manager: ghogen f1_keywords: 
  - "vs.performancecenter" ms.technology: 
  - "vs-ide-general"
---
# <a name="optimize-solution-loading-in-visual-studio"></a>Optimieren des Ladens von Projektmappen in Visual Studio
Viele Projektmappen enthalten eine große Anzahl von Projekten. Dies hat Auswirkungen auf die Zeit, die für das Laden dieser Projektmappen benötigt wird. In Teamumgebungen arbeiten Entwickler jedoch in der Regel an einer anderen Teilmenge dieser Projekte und müssen nicht alle einzelnen Projekte laden.

Visual Studio 2017 unterstützt den **Lightweight-Ladevorgang für Projektmappen**. Wenn der Lightweight-Lademodus für Projektmappen aktiviert ist, lädt Visual Studio 2017 eine kleine Teilmenge von Projekten, statt alle Projekte in eine große Projektmappe zu laden. Die meisten der häufig verwendeten IDE-Features werden im Lightweight-Lademodus für Projektmappen ausgeführt. Dies bietet Ihnen die Möglichkeit zum Erstellen, Suchen und Debuggen in der gesamten Projektmappe. (Das nicht unterstützte Hauptfeature im Lightweight-Lademodus für Projektmappen ist „Bearbeiten und Fortfahren“.)  

> [!NOTE]
> Dieser Inhalt gilt für Visual Studio 2017 Update 3

Bei großen Projektmappen mit mehr als 30 Projekten werden Projektmappen beim Lightweight-Ladevorgang für Projektmappen in der Regel doppelt so schnell geladen (durchschnittlich). Während die meisten IDE-Features im Lightweight-Lademodus für Projektmappen ausgeführt werden, müssen bei einigen IDE-Features möglicherweise alle Projekte geladen werden. In diesen Fällen lädt Visual Studio automatisch die gesamte Projektmappe, damit Sie das Feature verwenden können. Im schlimmsten Fall müssen Sie alle Projekte im Lightweight-Lademodus laden. 

Wenn Sie ein IDE-Feature in einem Projekt verwenden, das derzeit nicht geladen ist, lädt Visual Studio das bzw. die entsprechende(n) Projekt(e) für Sie. Wenn Sie beispielsweise versuchen, ein Klassendiagramm für ein ungeöffnetes Projekt zu erstellen oder zu öffnen, lädt Visual Studio automatisch die entsprechenden Projekte. In den folgenden Abschnitten wird auf die ausführliche Featureliste verwiesen.

In den folgenden Abschnitten wird gezeigt, wie ein Lightweight-Ladevorgang für Projektmappen aktiviert wird. Zudem wird Ihnen bei der Entscheidung geholfen, ob das Feature aktiviert werden soll oder nicht.

## <a name="enable-or-disable-lightweight-solution-load"></a>Aktivieren oder Deaktivieren der Funktion „Lightweight-Ladevorgang für Projektmappen“

Sie können mit der rechten Maustaste im Projektmappen-Explorer auf den Namen der Projektmappe klicken und **Laden der Lightweight-Lösung aktivieren** wählen. Nach Auswahl der Option müssen Sie die Projektmappe schließen und wieder öffnen, um „Lightweight-Ladevorgang für Projektmappen“ zu aktivieren.

> [!NOTE]
> Ähnliche Schritte gelten für das Deaktivieren des Lightweight-Ladevorgangs für Projektmappen. Wählen Sie zum Deaktivieren des Lightweight-Ladevorgangs für Projektmappen die Option **Laden der Lightweight-Lösung deaktivieren** aus. Schließen Sie anschließend die Projektmappe, und öffnen Sie sie wieder. 

![Projektmappen-Explorer](../ide/media/VSIDE_LSL_Solution_Setting.png)

## <a name="global_solution_load_settings"></a>Konfigurieren globaler Einstellungen für den Lightweight-Ladevorgang für Projektmappen

Sie können den Lightweight-Ladevorgang für Projektmappen für alle Projektmappen deaktivieren oder konfigurieren, indem Sie **Extras > Optionen > Projekte und Projektmappen** auswählen.

![Dialogfeld „Extras“ | „Optionen“](../ide/media/VSIDE_LightweightSolutionLoad.png)

## <a name="how-does-lightweight-solution-load-work-behind-the-scenes"></a>Wie funktioniert der Lightweight-Ladevorgang für Projektmappen im Hintergrund?

Wenn Sie Ihre Projektmappe laden, merkt sich Visual Studio, welche Projekt Sie vorher geöffnet hatten, und lädt nur diese Projekte. Alle anderen Projekte sind im Projektmappen-Explorer sichtbar, werden aber nicht geladen. Sobald Sie ein Projekt erweitern oder mit der rechten Maustaste auf ein Projekt klicken, lädt Visual Studio dieses Projekt automatisch. Für das automatische Laden von Projekten wird in der Regel weniger als eine Sekunde benötigt, es kann jedoch bei einigen Projekten länger dauern. Visual Studio aktiviert jedoch IDE-Features wie das Suchen, Debuggen, Erstellen und die Quellcodeverwaltung, die projektmappenübergreifend ausgeführt werden. Sie können beispielsweise eine gesamte Projektmappe durchsuchen, auch wenn nur einige Projekte im Lightweight-Lademodus für Projektmappen geladen werden. 

Wenn Sie weitere Projekte erweitern, merkt sich Visual Studio die Liste der erweiterten Projekte. Wenn eine Projektmappe erneut geöffnet wird, lädt Visual Studio automatisch Projekte, die Sie zuvor erweitert haben.

## <a name="visual-studio-prompts-developers-likely-to-see-significant-performance-gains"></a>Visual Studio fordert Entwickler, bei denen deutliche Leistungssteigerungen erzielt werden können, dazu auf, den LSL-Modus auszutesten.

Bei der Visual Studio-Telemetrie profitieren große Projektmappen mit über 30 Projekten erheblich von dem LSL-Modus. Folglich werden Entwickler mit großen Projektmappen dazu aufgefordert, den LSL-Modus auszutesten. Die meisten Entwickler, die die Funktion „Lightweight-Ladevorgang für Projektmappen“ zum ersten Mal austesten, verwenden diese am Ende regelmäßig. 

## <a name="visual-studio-makes-recommendations-to-turn-on-lightweight-solution-load-based-on-heuristics"></a>Visual Studio empfiehlt, die Funktion „Lightweight-Ladevorgang für Projektmappen“ basierend auf Heuristiken zu aktivieren.

Visual Studio aktiviert den Lightweight-Ladevorgang für Projektmappen für Benutzer, die sehr wahrscheinlich davon profitieren. Wenn Sie über mehrere Projektmappen verfügen, bietet Visual Studio den Lightweight-Lademodus für Projektmappen an, bei denen die Wahrscheinlichkeit sehr hoch ist, dass sie es zu deutlichen Leistungssteigerungen kommt. Bei Auswahl der Option **Let Visual Studio decide** (Visual Studio entscheiden lassen; Standardoption) für den Lightweight-Lademodus öffnet Visual Studio die Projektmappe im Lightweight-Lademodus möglicherweise basierend auf Heuristiken. Eine Statusleiste gibt an, ob sich die Projektmappe im Lightweight-Lademodus befindet. Wenn die Statusleiste angezeigt wird, können Sie weitere Informationen erhalten oder Einstellungen aktualisieren.

![Popupfenster](../ide/media/VSIDE_LSL_Popup.png)

## <a name="ide-features-fully-supported-in-lightweight-mode"></a>Vollständig unterstützte IDE-Features im Lightweight-Lademodus

|Funktion|Wird das Feature im Lightweight-Lademodus unterstützt?|
|-|-|-|
|IntelliSense|Ja|
|Suchen|Ja|
|Debuggen|Ja|
|Build|Ja|
|Codenavigation (Wechseln Sie zu „Definition“ und „Alle Verweise suchen“)|Ja|
|Code Lens|Ja|
|Statische Codeanalyse|Ja|
|Bereitstellen und Veröffentlichen|Ja|
|Hinzufügen und Entfernen von Verweisen|Ja|
|Festlegung von Zielversionen|Ja|
|IntelliTrace|Ja|
|Live Unit Testing|Ja|
|IntelliTest|Ja|
|Microsoft Fakes|Ja|
|Bearbeiten und Fortfahren|Nicht unterstützt|
|Unittests|Macht das Laden von Testprojekten gefolgt von einem Projektmappenbuild erforderlich|

## <a name="scenarios-in-which-lightweight-solution-loads-the-appropriate-projects-to-complete-the-operation"></a>Szenarios, in denen in der Lightweight-Projektmappe die entsprechenden Projekte geladen werden, um den Vorgang abzuschließen

Wenn Sie nicht an einem Projekt in der Projektmappe arbeiten, wird das Projekt nicht im Lightweight-Lademodus geladen. Bei einigen Features werden zur Unterstützung des Featureszenarios automatisch zusätzliche Projekte geladen. (Diese Liste mit Szenarios soll minimiert werden.) Bei diesen Szenarios lädt Visual Studio die Projekte selbst oder fordert Sie dazu auf, die Projekte nach Bedarf zu laden.

|Kategorie|Problem|
|-|-|-|
|Komponententest|Derzeit nicht geladene Projekte werden nicht in der Liste der Testprojekte für die Assistenten „IntelliTest erstellen“ und „Komponententest erstellen“ angezeigt. </br>Sie müssen die Projekte laden, für die Sie Tests erstellen möchten (Sie können den Projektknoten erweitern, um die Projekte zu laden).|
|Klassendiagramme|Wenn Sie das Klassendiagramm eines Projekts erstellen oder öffnen, lädt Visual Studio automatisch die Projekte, die direkte Abhängigkeiten von diesem Projekt darstellen. </br>Wenn die gesamte Projektmappe nicht geladen wird, wird die Überprüfung veralteter Artefakte deaktiviert, auf die von einem Abhängigkeitsüberprüfungsdiagramm verwiesen wird.|

## <a name="scenarios-in-which-lightweight-solution-loads-the-entire-solution"></a>Szenarios, in denen in der Lightweight-Projektmappe die gesamte Projektmappe geladen wird 

Bei einigen Features lädt Visual Studio automatisch die gesamte Projektmappe, um das Szenario zu unterstützen. Dadurch wird sichergestellt, dass jederzeit eine vollständige Funktionalität gewährleistet ist. Beispielsweise ist für einige TFS-Vorgänge erforderlich, dass die gesamte Projektmappe geladen wird. Visual Studio lädt die gesamte Projektmappe, um eine vollständige Funktionalität bieten zu können.

|Kategorie|Szenario|
|-|-|-|
|TFS-SCC-Befehl für den Projektmappenknoten|Wenn im Projektmappenknoten (innerhalb des Projektmappen-Explorers) ein SSC-Befehl ausgelöst wird, lädt Visual Studio vor der Ausführung des Befehls automatisch die gesamte Projektmappe.|
|Laden von Projekten|Wenn Ihre Projektmappe .NET Core-Projekte und freigegebene Projekte enthält, lädt Visual Studio diese Projekte immer automatisch während des ersten Ladens der Projektmappe. Diese Projekte unterstützen derzeit keinen Lightweight-Lademodus.|
|Configuration Manager für Projektmappen|Bei Verwendung des Konfigurations-Managers für Projektmappen oder dem Erstellen von Batches lädt Visual Studio automatisch die gesamte Projektmappe, um eine umfassende Benutzererfahrung bieten zu können.|
|NuGet-Paket-Manager|Wenn Sie die Benutzeroberfläche oder die Konsole des NuGet-Paket-Managers öffnen, lädt Visual Studio automatisch die gesamte Projektmappe, um eine umfassende Benutzererfahrung bieten zu können.|

## <a name="known-issues"></a>Bekannte Probleme

Es gibt einige Szenarios, die im Lightweight-Lademodus möglicherweise nicht ausgeführt werden können und bei denen das Laden zusätzlicher Projekte oder der gesamten Projektmappe erforderlich ist. Es wird daran gearbeitet, diese Fälle zu behandeln. 

|Kategorie|Problem|Problemumgehung|
|-|-|-|-|
|IntelliSense|IntelliSense wird nach einer Konfigurationsänderung (z.B. das Ändern eines Releasebuilds zum Debuggen und umgekehrt) möglicherweise nicht aktualisiert. Die Auswirkungen hängen von Codeunterschieden aufgrund von Konfigurationsänderungen ab.|Laden Sie die Projektmappe nach der Konfigurationsänderung erneut.|
|Umgestaltung von Einschränkungen für C#/VB-Projekte|Bei Codefehlerbehebungen, durch die Projektdateien geändert werden, treten beim ersten Mal automatisch Fehler auf.|Laden Sie Projekte, wenn Sie Codefehlerbehebungen an Dateien dieser Projekte vornehmen müssen. Im Lightweight-Lademodus werden bei nicht geladenen Projekten keine Fehler behoben.|
|Komponententestermittlung|Für zurückgestellte Projekte ermittelte Tests werden nicht ausgeführt, wenn ein Projekt manuell geladen wird.|Erstellen Sie das Projekt neu, um wiederholt Tests zu ermitteln und ausgewählte Tests erneut auszuführen.|
|Live Unit Testing (LUT)|Im Lightweight-Lademodus für Projektmappen sehen Sie möglicherweise, dass Live Unit Testing nicht aktiviert ist. Es ist nicht aktiviert, da zunächst eines der Testprojekt geladen werden muss.|Laden Sie ein beliebiges Testprojekt, um Live Unit Testing für die Projektmappe zu aktivieren.|
|Suche in Projektmappen-Explorer|1.    Die Suche im Projektmappen-Explorer im Lightweight-Lademodus für Projektmappen wird nicht in den Dateien durchgeführt. Zudem sind keine Ergebnisse der Fortschrittsermittlung vorhanden (d.h., in der Struktur werden nur Dateien angezeigt, jedoch keine Klassen, Methoden usw.).</br>2.    Alle zu einem Projekt gehörenden Dateien werden in einer flachen Liste und nicht in einer Strukturansicht angezeigt. Wenn Dateien zu einem Projektordner gehören, wird in der Suchansicht der relative Pfad dieser Dateien und nicht nur der Dateiname angezeigt.</br>Es gibt keine Kontextmenüs für die Dateielemente in der Suchansicht.|Laden Sie die gesamte Projektmappe im Nicht-Lightweight-Lademodus für Projektmappen, um die herkömmliche Suche im Projektmappen-Explorer ausführen zu können.</br>Sie können auch die IDE-Suche von Visual Studio verwenden.|
|Objektkatalog für C++-Projekte|Im Objektkatalog werden nur für geladene Projekte Assembly-/WinMD-Verweise angezeigt.|Laden Sie die Projekte, zu denen Sie Informationen im Objektkatalog anzeigen möchten.|

> [!Note]
> Dank unserer Partner funktionieren beliebte Erweiterungen, einschließlich ReSharper, auch gut beim Lightweight-Ladevorgang für Projektmappen.

Wir freuen uns über Innovationen für Entwickler zur Optimierung der Leistung bei der Ladezeit von Projektmappen. Da es sich hierbei um ein neues Feature handelt, werden wir uns aktiv Kundenfeedback ansehen und bekannte Probleme beheben. Wir freuen uns auf Ihr Feedback! Sie können dem Team für die Optimierung des Ladens von Visual Studio-Projektmappen unter lslsupport@microsoft.com eine E-Mail senden.

## <a name="see-also"></a>Siehe auch
[Visual Studio Performance Tips and Tricks (Tipps und Tricks zur Leistungssteigerung für Visual Studio)](../ide/visual-studio-performance-tips-and-tricks.md)  