---
title: Optionen, Text-Editor, JavaScript, IntelliSense | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b0d9dec8ec9b3eb8860bb8b3a4ed8f7347aa54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662236"
---
# <a name="options-text-editor-javascript-intellisense"></a>Optionen, Text-Editor, JavaScript, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie die Seite **IntelliSense** des Dialogfelds **Optionen** , um Einstellungen zu ändern, die das Verhalten von IntelliSense für JavaScript beeinflussen. Sie erreichen die **IntelliSense** -Seite, indem Sie **Tools**, **Optionen** in der Menüleiste wählen und anschließend **Text-Editor**, **JavaScript**, **IntelliSense**erweitern.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Die Seite **IntelliSense** enthält folgende Abschnitte:

## <a name="validation"></a>Validation
 Sie können diese Optionen verwenden, um Einstellungen dafür festzulegen, wie der JavaScript-Editor Syntax im Dokument überprüft.

## <a name="uielement-list"></a>UIElement-Liste
 **Syntax Fehler anzeigen** Wenn dieses Kontrollkästchen nicht aktiviert ist, zeigt der JavaScript-Code-Editor keine Syntax Fehler an. Dies ist nützlich, wenn Sie mit Code arbeiten, der nicht Ihr eigener ist und in dem Sie nicht beabsichtigen, Syntaxfehler zu beheben.

 Wenn dieses Kontrollkästchen aktiviert ist, haben Sie die Möglichkeit, das Kontrollkästchen **Fehler als Warnung anzeigen** zu aktivieren.

 **Fehler als Warnungen anzeigen** Wenn dieses Kontrollkästchen aktiviert ist, werden JavaScript-Fehler als Warnungen und nicht als Fehler in der Fehlerliste angezeigt.

 **Herunterladen von Remote verweisen (z. b. http://) für Dateien im Projekt "sonstige Dateien** " Wenn dieses Kontrollkästchen aktiviert ist und Sie eine JavaScript-Datei haben, die außerhalb des Kontexts eines Projekts geöffnet ist, lädt Visual Studio die JavaScript-Remote Dateien herunter, auf die in der Datei verwiesen wird, um IntelliSense-Informationen bereitzustellen. Wenn diese Option aktiviert ist, werden Dateien heruntergeladen, wenn Sie diese als Verweis in der JavaScript-Datei eingeschlossen haben.

> [!NOTE]
> Für Webprojekte werden die Remotedateien, auf die im Projekt verwiesen wird, standardmäßig heruntergeladen.

## <a name="statement-completion"></a>Anweisungsabschluss
 Sie können diese Optionen verwenden, um das Verhalten der IntelliSense-Anweisungsvervollständigung zu ändern.

## <a name="uielement-list"></a>UIElement-Liste
 **Nur Tab oder EINGABETASTE zum Commit verwenden** Wenn dieses Kontrollkästchen aktiviert ist, fügt der JavaScript-Code-Editor Anweisungen nur dann an die Elemente, die in der Vervollständigungsliste ausgewählt sind, nachdem Sie die Tab-oder EINGABETASTE gewählt haben. Wenn dieses Kontrollkästchen deaktiviert ist, können auch andere Zeichen, wie Punkt, Komma, Doppelpunkt, öffnende runde Klammer und öffnende geschweiften Klammer ({) Anweisungen mit den ausgewählten Elementen erweitern.

## <a name="references"></a>References
 Sie können diese Optionen verwenden, um die Typen von IntelliSense-JS-Dateien anzugeben, die für verschiedene JavaScript-Projekttypen verfügbar sind. Die IntelliSense-Verweise werden normalerweise verwendet, um die IntelliSense-Unterstützung für globale Objekte bereitzustellen. Sie können diese Seite auch verwenden, um die Ladereihenfolge für Skripts festlegen, die zur Laufzeit geladen werden müssen, und um IntelliSense-Erweiterungsdateien hinzuzufügen.

## <a name="uielement-list"></a>UIElement-Liste
 **Verweis Gruppen** Diese Option gibt den Verweis Gruppentyp an. Drei Verweisgruppen werden unterstützt:

 Sie können vordefinierte Verweisgruppen verwenden, um anzugeben, dass bestimmte IntelliSense-JS-Dateien für verschiedene JavaScript-Projekte verfügbar sind. Vier Verweisgruppen sind verfügbar:

- Implizit (Windows- *Version*) für [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] -Apps, die JavaScript verwenden. Die in dieser Gruppe enthalten Dateien sind für jede im Code-Editor geöffnete JS-Datei für [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]-Apps mit JavaScript verfügbar.

- Implizit (Internet), für HTML5-Projekte. Die Dateien, die in dieser Gruppe enthalten sind, sind im Bereich für jede JS-Datei, die im Code-Editor für die Projekttypen geöffnet ist.

- Dedizierte Workerverweisgruppen, für HTML5-Web-Worker. Die Dateien, die in dieser Gruppe angegeben werden, sind für JS-Dateien verfügbar, die einen expliziten Verweis auf eine dedizierte Workerverweisgruppe haben.

- Generisch, für andere JavaScript-Projekttypen.

  **Enthaltene Dateien** Diese Option gibt die Reihenfolge an, in der Dateien in den Kontext des sprach Dienstanbieter geladen werden. Sie können die Reihenfolge konfigurieren, indem Sie die Schaltflächen **Entfernen**, **Nach oben**und **Nach unten** verwenden. Damit IntelliSense ordnungsgemäß funktioniert, muss eine Datei, die von einer anderen abhängig ist, im Anschluss an diese geladen werden.

> [!CAUTION]
> Wenn ein Objekt ohne Einschränkung in zwei oder mehr impliziten Verweisen definiert ist, wird der letzte Verweis in dieser Liste verwendet, um das Objekt zu definieren.

 **Fügen Sie einen Verweis auf die Gruppe hinzu** . Mit dieser Option können Sie weitere IntelliSense. js-Dateien hinzufügen, indem Sie zu den entsprechenden Dateien navigieren.

## <a name="see-also"></a>Weitere Informationen
 [JavaScript IntelliSense](../../ide/javascript-intellisense.md)
