---
title: Allgemein, Umgebung, Dialogfeld „Optionen“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83fc6adeba0529be03a9a982713d0584a2a7bc45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661276"
---
# <a name="general-environment-options-dialog-box"></a>Allgemein, Umgebung, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie diese Seite, um Farbschemas, Statusleisteneinstellungen, Dateierweiterungszuordnungen sowie weitere Optionen für die integrierte Entwicklungsumgebung (IDE) zu ändern. Sie können das Dialogfeld **Optionen** öffnen, indem Sie im Menü **Extras** auf **Optionen** klicken und dann im Ordner **Umgebung** die Seite **Allgemein** auswählen. Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="visual-experience"></a>Visuelle Darstellung
 **Farb** Schema Wählen Sie das Farbschema **blau**, **hell** oder **dunkel** für die IDE aus.

 Sie können auch weitere vordefinierte Farbschemas installieren und benutzerdefinierte Schemas erstellen. Dazu müssen Sie den **Visual Studio 2015 Color Theme Editor** aus [Visual Studio Marketplace](https://marketplace.visualstudio.com) herunterladen und installieren. Nachdem Sie dieses Tool installiert haben, werden zusätzliche Farbschemas im Farbschemalistenfeld angezeigt.

 Das Anwenden der Titel Schreibweise in Menüleisten Menüs ist in Visual Studio 2015 standardmäßig in **Titel** Schreibweise. Deaktivieren Sie diese Option, um die Menüs auf **Großbuchstaben** festzulegen.

 **Visuelle Darstellung automatisch basierend auf der Client Leistung anpassen** Gibt an, ob Visual Studio die Anpassung der visuellen Darstellung automatisch festlegt oder Sie die Anpassung explizit festlegen. Mit dieser Anpassung können Sie die Darstellung von Farben von Farbverläufen in gleichmäßige Farben ändern oder die Verwendung von Animationen in Menüs oder Popupfenstern einschränken.

 Umfassende **Client Darstellung aktivieren** Ermöglicht die vollständige visuelle Darstellung von Visual Studio, einschließlich Farbverläufen und Animationen. Deaktiviert diese Option bei Verwendung von Remotedesktopverbindungen oder älteren Grafikkarten, da diese Funktionen in solchen Fällen zu einer schlechteren Leistung führen können. Diese Option ist nur verfügbar, wenn Sie die Option **Visuelle Darstellung automatisch basierend auf der Clientleistung anpassen** deaktivieren.

 **Hardware Grafik Beschleunigung verwenden, falls verfügbar** Verwendet Hardware Grafik Beschleunigung, sofern verfügbar, anstelle von Software Beschleunigung.

## <a name="other"></a>Sonstiges
 **Im Menü „Fenster“ angezeigte Elemente** Passt die Anzahl der Fenster an, die in der Fensterliste des Menüs **Fenster** angezeigt werden. Geben Sie eine Zahl zwischen 1 und 24 ein. Die Standardanzahl ist 10.

 **In den Listen der zuletzt geöffneten Elemente angezeigte Elemente** Passt die Anzahl der zuletzt geöffneten Projekte und Dateien an, die im Menü **Datei** angezeigt werden. Geben Sie eine Zahl zwischen 1 und 24 ein. Die Standardanzahl ist 10. Dies ist eine einfache Möglichkeit, zuletzt verwendete Projekte und Dateien abzurufen.

 **Statusleiste anzeigen** Zeigt die Statusleiste an. Die Statusleiste befindet sich am unteren Rand des IDE-Fensters und zeigt Informationen über den Fortschritt derzeit ausgeführter Vorgänge an.

 **Schaltfläche „Schließen“ bezieht sich nur auf aktives Toolfenster** Gibt an, dass beim Klicken auf die Schaltfläche **Schließen** nur das Toolfenster geschlossen wird, das den Fokus besitzt, und nicht alle Toolfenster im angedockten Satz. Diese Option ist standardmäßig ausgewählt.

 **Schaltfläche „Automatisch ausblenden“ bezieht sich nur auf aktives Toolfenster** Gibt an, dass beim Klicken auf die Schaltfläche **Automatisch ausblenden** nur das Toolfenster automatisch ausgeblendet wird, das den Fokus besitzt, und nicht alle Toolfenster im angedockten Satz. Diese Option ist standardmäßig nicht ausgewählt.

 **Dateizuordnungen verwalten** Zeigt das Dialogfeld " **Programm Zuordnungen von Windows festlegen** " an, in dem Sie Dateierweiterungen für Elemente anzeigen können, die in der Regel mit Visual Studio und dem aktuellen Standardprogramm zum Öffnen der einzelnen Dateitypen verknüpft sind. Um Visual Studio als Standardanwendung für Dateitypen festzulegen, die noch nicht entsprechend zugeordnet sind, wählen Sie die Dateierweiterung aus, und klicken Sie dann auf **Speichern**.

 Diese Option kann hilfreich sein, wenn zwei Versionen von Visual Studio auf demselben Computer installiert sind und im Nachhinein eine dieser Versionen deinstalliert wird. Nach der Deinstallation werden die Symbole für Visual Studio-Dateien im Datei-Explorer nicht mehr angezeigt. Außerdem wird Visual Studio von Windows nicht mehr als Standardanwendung zur Bearbeitung dieser Dateien erkannt. Mit dieser Option werden die entsprechenden Verknüpfungen wiederhergestellt.

## <a name="see-also"></a>Weitere Informationen
 [Dialogfeld „Umgebungsoptionen“](../../ide/reference/environment-options-dialog-box.md) [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)
