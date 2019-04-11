---
title: Allgemein, Umgebung, Dialogfeld "Optionen"
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fdbd8c64514854aa77c358145badbf6583996f1
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647270"
---
# <a name="options-dialog-box-environment--general"></a>Dialogfeld „Optionen“: Umgebung \> Allgemein

Verwenden Sie diese Seite, um Farbschemas, Statusleisteneinstellungen, Dateierweiterungszuordnungen sowie weitere Optionen für die integrierte Entwicklungsumgebung (IDE) zu ändern. Sie können das Dialogfeld **Optionen** öffnen, indem Sie im Menü **Extras** auf **Optionen** klicken und dann im Ordner **Umgebung** die Seite **Allgemein** auswählen. Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.

## <a name="visual-experience"></a>Visuelle Darstellung

**Farbdesign**

Wählen Sie **Blau**, **Hell**, **Dunkel** oder **Blau (zusätzlicher Kontrast)** als Farbdesign für die IDE aus.

Sie können auch weitere vordefinierte Farbdesigns installieren und benutzerdefinierte Designs erstellen. Dazu müssen Sie den **Visual Studio Color Theme Editor** aus dem [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) herunterladen und installieren. Nachdem Sie dieses Tool installiert haben, werden zusätzliche Farbdesigns im **Farbdesignlistenfeld** angezeigt.

**Traditionellen Menüleistenstil mit großen Anfangsbuchstaben verwenden**

Menüs verwenden diesen Stil mit großen Anfangsbuchstaben standardmäßig. Deaktivieren Sie diese Option, wenn Sie stattdessen den Stil „Alles Großbuchstaben“ verwenden möchten.

::: moniker range=">=vs-2019"

**Rendering für Bildschirme mit anderen Pixeldichten optimieren (Neustart erforderlich)**

Diese Option aktiviert oder deaktiviert den DPI-Grad (Dots Per Inch) pro Monitor (oder *PMA* (Per-Monitor Aware)). Wenn PMA aktiviert ist, wird die Visual Studio-Benutzeroberfläche in jedem Skalierungsfaktor der Monitoranzeige und jeder DPI-Konfiguration als hochauflösend angezeigt, auch wenn mehrere Monitore verwendet werden. Wenn Sie PMA aktivieren möchten, benötigen Sie das Windows-Update vom 10. April 2018 oder höhere Updates und mindestens .NET Framework 4.8. (Diese Option wird ausgeblendet, wenn diese beiden Voraussetzungen nicht erfüllt sind.)

::: moniker-end

**Visuelle Darstellung automatisch basierend auf der Clientleistung anpassen**

Gibt an, ob Visual Studio die Anpassung der visuellen Darstellung automatisch festlegt oder Sie die Anpassung explizit festlegen. Mit dieser Anpassung können Sie die Darstellung von Farben von Farbverläufen in gleichmäßige Farben ändern oder die Verwendung von Animationen in Menüs oder Popupfenstern einschränken.

**Enable rich client experience** (Umfassende visuelle Clientdarstellung aktivieren)

Aktiviert die vollständige visuelle Darstellung von Visual Studio, u. a. mit Farbverläufen und Animationen. Deaktiviert diese Option bei Verwendung von Remotedesktopverbindungen oder älteren Grafikkarten, da diese Funktionen in solchen Fällen zu einer schlechteren Leistung führen können. Diese Option ist nur verfügbar, wenn Sie die Option **Visuelle Darstellung automatisch basierend auf der Clientleistung anpassen** deaktivieren.

**Hardwaregrafikbeschleunigung verwenden, falls verfügbar**

Verwendet Hardwaregrafikbeschleunigung, sofern verfügbar, anstelle von Softwarebeschleunigung.

## <a name="other"></a>Andere

**Anzuzeigende Elemente im Windows-Menü**

Passt die Anzahl der Fenster an, die in der Fensterliste des Menüs **Fenster** angezeigt werden. Geben Sie eine Zahl zwischen 1 und 24 ein. Der Standardwert ist 10.

**In den Listen der zuletzt verwendeten Elemente angezeigte Elemente**

Passt die Anzahl der zuletzt geöffneten Projekte und Dateien an, die im Menü **Datei** angezeigt werden. Geben Sie eine Zahl zwischen 1 und 24 ein. Der Standardwert ist 10. Dies ist eine einfache Möglichkeit, zuletzt verwendete Projekte und Dateien abzurufen.

**Statusleiste anzeigen**

Zeigt die Statusleiste an. Die Statusleiste befindet sich am unteren Rand des IDE-Fensters und zeigt Informationen über den Fortschritt derzeit ausgeführter Vorgänge an.

**Schaltfläche „Schließen“ bezieht sich nur auf aktives Toolfenster**

Gibt an, dass beim Klicken auf die Schaltfläche **Schließen** nur das Toolfenster geschlossen wird, das den Fokus besitzt, und nicht alle Toolfenster im angedockten Satz. Diese Option ist standardmäßig ausgewählt.

**Schaltfläche „Automatisch ausblenden“ bezieht sich nur auf aktives Toolfenster**

Gibt an, dass beim Klicken auf die Schaltfläche **Automatisch ausblenden** nur das Toolfenster automatisch ausgeblendet wird, das den Fokus besitzt, und nicht alle Toolfenster im angedockten Satz. Diese Option ist standardmäßig nicht ausgewählt.

## <a name="see-also"></a>Siehe auch

- [Dialogfeld „Umgebungsoptionen“](../../ide/reference/environment-options-dialog-box.md)
- [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)