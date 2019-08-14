---
title: Entwerfen von XAML-Code in Visual Studio und Blend
titleSuffix: ''
ms.date: 08/05/2019
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd0ff12b141a50872d586764d2b33bd68f3224fb
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821865"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Entwerfen mithilfe von XAML in Visual Studio und Blend für Visual Studio

Visual Studio und Blend für Visual Studio sind visuelle Tools zum Erstellen ansprechender Benutzeroberflächen und Rich-Media-Umgebungen mit XAML für eine Vielzahl von App-Typen. Beide integrierten Entwicklungsumgebungen (IDE) teilen sich eine Reihe von Funktionen, wie z.B. einen visuellen XAML-Editor (Designer). Blend für Visual Studio, das die WPF-und UWP-Plattformen unterstützt, stellt zusätzliche Tools zum Entwerfen von visuellen Zuständen und zum Erstellen von Animationen bereit.

Sie können zwischen Visual Studio und Blend für Visual Studio wechseln. Sie können sogar in beiden IDEs dasselbe Projekt geöffnet haben. Änderungen an XAML-Dateien in einer IDE lassen sich beim Wechsel zur anderen IDE automatisch neu laden. Das Verhalten beim Neuladen können Sie in beiden IDEs über **Tools** > **Optionen** > **Umgebung** > **Dokumente** steuern.

## <a name="installation"></a>Installation

- Um WPF-Apps zu erstellen, installieren Sie die Workload **.NET-Desktopentwicklung** in Visual Studio. Blend für Visual Studio wird ebenfalls installiert.
- Um UWP-Apps zu erstellen, installieren Sie die Workload **Universelle Windows-Plattformentwicklung** in Visual Studio. Blend für Visual Studio wird ebenfalls installiert.
- Um Xamarin.Forms-Apps zu erstellen, installieren Sie die Workload **Mobile-Entwicklung mit .NET** in Visual Studio. Blend für Visual Studio wird *nicht* installiert. Xamarin.Forms-Apps werden in Blend nicht unterstützt.

## <a name="shared-capabilities"></a>Gemeinsam genutzte Funktionen

Für die meisten grundlegenden Entwicklungsaufgaben teilen sich Visual Studio und Blend für Visual Studie denselben Fenster- und Funktionssatz, mit einigen geringfügigen Unterschieden. Hier einige Highlights:

- **IntelliSense:** Beide IDES unterstützen IntelliSense-Funktionen wie Anweisungsvervollständigung.

- **Debuggen:** Sie können in [Visual Studio](../debugger/inspect-xaml-properties-while-debugging.md) und [Blend for Visual Studio](../debugger/debug-xaml-in-blend.md) debuggen, einschließlich dem Festlegen von Haltepunkten im Code zum Debuggen einer laufenden Anwendung und dem Verwenden von [Neuladen im laufenden Betrieb](../debugger/xaml-hot-reload.md) zum Ändern Ihres XAML-Codes während der Ausführung der Anwendung. Für ein einheitliches Debugerlebnis in Visual Studio beinhaltet Blend für Visual Studio die meisten der Debugfenster und -symbolleisten von Visual Studio.

- **Datei neu laden:** Sie können Ihre XAML-Dateien entweder in Visual Studio oder Blend für Visual Studio bearbeiten. Bearbeitete Dateien, die gespeichert wurden, werden automatisch neu geladen, wenn Sie zwischen den IDES wechseln. Das Verhalten beim Neuladen können Sie in beiden IDEs über **Tools** > **Optionen** > **Umgebung** > **Dokumente** steuern.

- **Synchronisierte Layouts und Einstellungen:** Benutzerdefinierte Layouts für Toolfenster und Einstellungen für Visual Studio oder Blend für Visual Studio werden für Ihre verschiedenen Geräte und Versionen synchronisiert, wenn Sie sich mit demselben Personalisierungskonto anmelden. Weitere Informationen finden Sie unter[Synchronisieren von Visual Studio-Einstellungen auf mehreren Computern](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Erweiterte Funktionen in Blend für Visual Studio

Verwenden Sie Blend für Visual Studio für die folgenden Aufgaben, um Ihre Produktivität zu steigern. Dies sind die Bereiche, in denen Blend mehr Funktionalität bietet als Visual Studio-Designer oder Code allein.

| Aufgabe | Visual Studio | Blend for Visual Studio | Weitere Informationen |
| - | - | - | - |
| **Visuelle Zustände für Designs** | Es gibt kein Tool, das Sie beim Entwerfen visueller Zustände unterstützt. Sie müssen sie programmgesteuert erstellen. | Verwenden Sie Designtools, um das Erscheinungsbilds eines Steuerelements basierend auf dessen Status zu ändern. | [Visuelle Zustände](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Erstellen von Animationen** |Es gibt kein Designwerkzeug für Animationen; Sie müssen sie programmgesteuert erstellen. Dies erfordert ein grundlegendes Verständnis des Animations- und Zeitsteuerungssystems in WPF sowie umfangreiche Codierungskenntnisse.|Sie können Animationen in Blend für Visual Studio visuell erstellen und eine Vorschau anzeigen. Dies ist schneller und präziser, als Animationen in Code zu erstellen. Sie können Trigger hinzufügen, um die Benutzerinteraktion zu verarbeiten, und Sie können zum Code wechseln, um Ereignishandler und andere Funktionen zu verarbeiten.|[Animate objects (Animieren von Objekten)](../designers/animate-objects-in-xaml-designer.md)|
|**Umwandeln von Formen und Text in Pfade für eine einfachere Bearbeitung**|Wird nicht unterstützt.|Sie können geringfügige oder erhebliche Änderungen an den Formen (z. B. Rechtecke und Ellipsen) vornehmen, indem Sie sie in Pfade konvertieren, die eine bessere Bearbeitungssteuerung bieten. Sie können Pfade umformen oder kombinieren und zusammengesetzte Pfade aus mehreren Formen erstellen.<br /><br />Sie können auch Textblöcke in Pfade umwandeln, um sie als Vektorgrafiken zu bearbeiten.|[Zeichnen von Formen und Pfaden](../designers/draw-shapes-and-paths.md)|
|**Bearbeiten von Steuerelementen, Vorlagen und Stilen**|Erfordert die Codierung von sowie Kenntnisse über WPF-Stile und -Vorlagen.|Wandeln Sie ein Bild in ein Steuerelement um.<br /><br />Verwenden Sie die Tools zum Bearbeiten von Vorlagen, um Steuerelemente, Stile und Vorlagen mit nur wenigen Mausklicks zu ändern.<br /><br />Beispielsweise können Sie Blend für Visual Studio-Ressourcen verwenden, um WPF-Standardsteuerelemente (z. B. Schaltflächen, Listenfeldern, Bildlaufleisten, Menüs usw.) zu implementieren und um die Farbe, den Stil oder die zugrunde liegende Vorlage direkt in Blend zu ändern. Sie können dann, falls gewünscht, zum Code wechseln, um Ihrer Arbeit den letzten Schliff zu geben.|[Modify the style of objects (Ändern des Stils von Objekten)](../designers/modify-the-style-of-objects-in-blend.md)|
|**Verbinden der Benutzeroberfläche mit Daten**|Sie können eine Datenquelle aus Ressourcen, wie SQL Server-Datenbanken, WCF oder Webdiensten, Objekten oder SharePoint-Listen, erstellen und die Datenquelle mit den Steuerelementen der Benutzeroberfläche verknüpfen.<br /><br />Daten müssen für ein interaktives Designerlebnis zur Entwurfszeit manuell erstellt werden.|Für .NET Framework-Apps erstellen Sie mühelos die Beispieldaten für die Prototyperstellung und für Tests. Wechseln Sie zu den Livedaten, wenn Sie bereit sind.<br /><br />Die Blend-Funktionen zur Datengenerierung von Visual Studio sind hervorragend. Sie können Namen, Zahlen, URLs und Fotos problemlos bei laufendem Betrieb hinzufügen, wodurch Sie viel Zeit sparen können.<br /><br />Bei Live-Daten können Sie die Steuerelemente der Benutzeroberfläche mit einer XML-Datei oder einer beliebigen CLR-Datenquelle verknüpfen.|[Display data (Anzeigen von Daten)](../designers/display-data-in-blend.md)|

Informationen zu erweiterten XAML-Designs finden Sie unter [Erstellen einer Benutzeroberfläche mit Blend für Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).
