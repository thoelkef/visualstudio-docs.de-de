---
title: Suchen und Verwenden von Visual Studio-Erweiterungen| Microsoft-Dokumentation
ms.custom: 
ms.date: 06/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6ed49a18c7497eefc21a7fe7bfe9d35003863a5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="find-and-use-visual-studio-extensions"></a>Suchen und Verwenden von Visual Studio-Erweiterungen

Visual Studio-Extensions sind Codepakete, die innerhalb von Visual Studio ausgeführt werden und neue oder verbesserte Visual Studio-Funktionen bereitstellen. Weitere Informationen zu Visual Studio-Extensions finden Sie hier: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Sie können das Dialogfeld **Erweiterungen und Updates** verwenden, um Visual Studio-Erweiterungen und Beispiele von Websites und anderen Speicherorten zu installieren, und sie dann aktivieren, deaktivieren, aktualisieren oder deinstallieren. (**Extras/Extensions und Updates**, oder geben Sie **Extensions** im Fenster **Schnellstart** ein.) Das Dialogfeld zeigt auch Updates für installierte Beispiele und Erweiterungen. Sie können auch Erweiterungen von Websites herunterladen oder von anderen Entwicklern erhalten.

> [!NOTE]
> Ab Visual Studio 2015 werden in Visual Studio Marketplace gehostete Erweiterungen automatisch aktualisiert.  Diese Einstellung können Sie über das Dialogfeld **Erweiterungen und Updates** ändern.  Details finden Sie im untenstehenden Abschnitt **Automatische Erweiterungsaktualisierungen** .

## <a name="finding-visual-studio-extensions"></a>Suchen von Visual Studio-Extensions

Sie können Erweiterungen über [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) installieren. Zu diesen Erweiterungen können Steuerelemente, Beispiele, Vorlagen, Werkzeuge oder andere Komponenten zählen, die Visual Studio Funktionen hinzufügen. In Visual Studio werden Erweiterungen im VSIX-Paketformat unterstützt. Diese umfassen Projektvorlagen, Elementvorlagen, **Werkzeugkasten** -Komponenten des Managed Extension Framework (MEF) und VSPackages. Sie können auch MSI-basierte Erweiterungen herunterladen und installieren, doch können diese nicht über das Dialogfeld **Erweiterungen und Updates** aktiviert oder deaktiviert werden. Visual Studio Marketplace enthält sowohl VSIX- als auch MSI-Erweiterungen.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Installieren oder Deinstallieren von Visual Studio-Extensions

Suchen Sie in **Erweiterungen und Updates**nach der Erweiterung, die Sie installieren möchten. (Wenn Sie den Namen der Erweiterung oder einen Teil des Namens kennen, können Sie im Fenster **Suche** danach suchen.) Klicken Sie auf **Download** (Herunterladen).  Die Erweiterung wird der Warteschlange für die Installation hinzugefügt. Sie wird installiert, sobald alle Instanzen von Visual Studio geschlossen wurden.

Wenn Sie versuchen, eine Erweiterung zu installieren, die Abhängigkeiten enthält, wird vom Installationsprogramm überprüft, ob diese bereits installiert sind. Sind sie nicht installiert, werden im Dialogfeld **Erweiterungen und Updates** die vor der Installation der Erweiterung zu installierenden Abhängigkeiten aufgeführt.

Wenn Sie die Verwendung einer Erweiterung beenden möchten, können Sie diese deaktivieren oder deinstallieren. Beim Deaktivieren einer Erweiterung bleibt sie installiert, wird jedoch nicht geladen. Sie können nur VSIX-Erweiterungen deaktivieren. Erweiterungen, die mit MSI installiert wurden, können nur deinstalliert werden. Suchen Sie nach der Erweiterung, und klicken Sie auf **Deinstallieren** oder **Deaktivieren**. Sie müssen Visual Studio neu starten, um eine deaktivierte Erweiterung zu entladen.

## <a name="per-user-and-administrative-extensions"></a>Erweiterungen pro Benutzer und Verwaltungserweiterungen

Bei den meisten Erweiterungen handelt es sich um Erweiterungen pro Benutzer, und diese werden im Ordner **%LocalAppData%\Microsoft\VisualStudio\\<Visual Studio-Version>\>\Extensions\\** installiert. Bei einigen Erweiterungen handelt es sich um Verwaltungserweiterungen, und diese werden im Ordner **\<Visual Studio-Installationsordner>\Common7\IDE\Extensions\\** installiert.

Um das System vor Erweiterungen zu schützen, in denen möglicherweise Fehler oder bösartiger Code enthalten ist, können Sie das Laden von Erweiterungen pro Benutzer dahingehend einschränken, dass sie nur geladen werden, wenn Visual Studio mit normalen Benutzerberechtigungen ausgeführt wird. Das bedeutet, dass Erweiterungen pro Benutzer deaktiviert sind, wenn Visual Studio mit Administratorberechtigungen ausgeführt wird. Wechseln Sie hierzu zur Optionsseite **Extensions und Updates** (**Extras/Optionen**, **Umgebung**, **Extensions und Updates**, oder geben Sie einfach **Extension** in das Fenster **Schnellstart** ein). Deaktivieren Sie das Kontrollkästchen **Pro-Benutzer-Erweiterungen bei Ausführung als Administrator laden** , und starten Sie Visual Studio dann neu.

## <a name="automatic-extension-updates"></a>Automatische Erweiterungsaktualisierungen

Pro-Benutzer-Erweiterungen werden automatisch aktualisiert, wenn eine neue Version für Visual Studio Marketplace zur Verfügung steht.  Die neue Version der Erweiterung wird erkannt und im Hintergrund installiert. Beim nächsten Neustart von Visual Studio wird entsprechend die neue Version der Erweiterung ausgeführt.

Nur Pro-Benutzer-Erweiterungen können automatisch aktualisiert werden.  Administrative Erweiterungen, die für alle Benutzer installiert werden, werden nicht aktualisiert, und Sie müssen neue Versionen weiterhin über das Dialogfeld **Erweiterungen und Updates** und den Knoten **Updates** manuell installieren. Sie können im Detailbereich des Dialogfelds **Erweiterungen und Updates** der Erweiterung anzeigen, welche Erweiterungen automatisch aktualisiert werden.

Wenn Sie automatische Updates deaktivieren möchten, können Sie das Feature für alle Erweiterungen oder nur für bestimmte Erweiterungen deaktivieren.

- Wählen Sie zum Deaktivieren von automatischen Updates für alle Erweiterungen den Link **Einstellungen für die Erweiterungen und Updates ändern** im Dialogfeld **Erweiterungen und Updates** aus, und deaktivieren Sie **Erweiterungen automatisch aktualisieren**.

- Deaktivieren Sie zum automatischen Deaktivieren einer bestimmten Erweiterung die Option **Diese Extension automatisch aktualisieren** im Detailbereich der Erweiterung auf der rechten Seite des Dialogfelds **Erweiterungen und Updates**.

> [!NOTE]
> Von Visual Studio 2015 Update 2 an können Sie (in **Extras / Optionen / Umgebung / Erweiterungen und Updates**) angeben, ob automatische Updates für Erweiterungen pro Benutzer, alle Benutzererweiterungen oder beides (Standardeinstellung) vorgenommen werden sollen.

## <a name="extension-crash-notifications"></a>Absturzberichte zu Erweiterungen

In Visual Studio 2017 (Version 15.3 -Preview) werden Sie von Visual Studio benachrichtigt, wenn die Wahrscheinlichkeit besteht, dass eine Erweiterung während einer vorherigen Sitzung in einen Absturz verwickelt war. Wenn Visual Studio abstürzt, speichert das Programm den Ausnahmestapel. Beim nächsten Start von Visual Studio untersucht es den Stapel. Es beginnt dabei auf der Blattebene und arbeitet sich zur Basis herunter. Wenn Visual Studio feststellt, dass ein Modul ein Teil einer installierten und aktivierten Erweiterung ist, werden Sie über eine Meldung benachrichtigt, z.B.

„A previous session terminated unexpectedly. Disabling extension 'extension_name' might help prevent similar issues.“ („Eine vorherige Sitzung wurde unerwartet beendet. Das Deaktivieren der Erweiterung „extension_name“ kann ähnlichen Problemen vorbeugen.“)

Sie können die Benachrichtigung deaktivieren oder eine der folgenden Maßnahmen ergreifen:

- Wählen Sie **Disable this extension** (Diese Erweiterung deaktivieren) aus. Visual Studio deaktiviert die Erweiterung und informiert Sie, ob Sie Ihr System neu starten müssen, damit die Deaktivierung wirksam wird. Sie können die Erweiterung im Dialogfeld **Erweiterungen und Updates** erneut aktivieren, falls Sie das wünschen.

- Wählen Sie **Don’t show again for this extension** (Für diese Erweiterung nicht mehr anzeigen) aus. Die IDE zeigt keine Benachrichtigungen über Abstürze an, die mit dieser Erweiterung zusammenhängen. Benachrichtigungen über Abstürze, die mit anderen Erweiterungen zusammenhängen, werden trotzdem angezeigt.

- Wählen Sie **Weitere Informationen** aus, um das Hilfethema in Ihrem Standardbrowser anzuzeigen.

- Wählen Sie die Schaltfläche **X** am Ende der Benachrichtigung aus, um die Benachrichtigung zu schließen. Wenn die gleiche Erweiterung in Zusammenhang mit einem Absturz in einer zukünftigen Sitzung steht, wird die Benachrichtigung erneut angezeigt.

> [!NOTE]
> Eine Absturzbenachrichtigung bedeutet nur, dass eines der Module der Erweiterung sich auf dem Stapel für den Absturz befunden hat. Es bedeutet nicht unbedingt, dass die Erweiterung selbst den Absturz verursacht hat. Es ist möglich, dass die Erweiterung Code aufgerufen hat, der ein Teil von Visual Studio ist und dass dieser Code den Absturz verursacht hat. Allerdings ist die Benachrichtigung möglicherweise trotzdem hilfreich, wenn das Szenario, das zum Absturz geführt hat, nicht wichtig für Sie ist. In diesem Fall verhindert das Deaktivieren der Erweiterung den gleichen Absturz ohne Ihre Produktivität zu beeinträchtigen.

## <a name="sample-master-copies-and-working-copies"></a>Beispielmasterkopien und -arbeitskopien

Bei Installation eines Onlinebeispiels wird die Projektmappe an zwei Orten gespeichert:

- Eine Arbeitskopie wird an dem Speicherort gespeichert, den Sie im Dialogfeld **Neues Projekt** angegeben haben.

- Eine separate Masterkopie wird auf dem Computer gespeichert.

Sie können das Dialogfeld **Erweiterungen und Updates** dazu verwenden, die folgenden auf Beispiele bezogenen Aufgaben auszuführen:

- Auflisten der Masterkopien der installierten Beispiele

- Deaktivieren oder deinstallieren der Masterkopie eines Beispiels

- Installieren von Beispielpacks, die Auflistungen von Beispielen zu einer Technologie oder Funktion sind

- Installieren individueller Onlinebeispiele (Sie können dies im Dialogfeld **Neues Projekt** ausführen.)

- Anzeigen von Updatebenachrichtigungen, wenn für installierte Quellcodeänderungen Beispiele veröffentlicht werden

- Aktualisieren Sie die Masterkopie eines installierten Beispiels, wenn Sie über ein Update benachrichtigt werden.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Installieren ohne das Dialogfeld "Erweiterungen und Updates"

Erweiterungen, die in VSIX-Dateien gepackt wurden, sind möglicherweise an anderen Orten als in Visual Studio Marketplace verfügbar. Diese Dateien können mithilfe des Dialogfelds **Extensions und Updates** nicht erkannt werden, Sie können eine VSIX-Datei aber installieren, indem Sie auf die Datei doppelklicken oder sie auswählen und die EINGABETASTE drücken. Befolgen Sie dann die angezeigten Anweisungen. Wenn die Erweiterung installiert ist, können Sie das Dialogfeld **Erweiterungen und Updates** zum Aktivieren, Deaktivieren oder Deinstallieren der Erweiterung verwenden.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Vom Dialogfeld "Erweiterungen und Updates" nicht unterstützte Erweiterungstypen

Visual Studio unterstützt auch weiterhin Erweiterungen, die mit Microsoft Installer (MSI) installiert werden, jedoch nicht über das Dialogfeld **Erweiterungen und Updates** ohne Änderungen.

> [!TIP]
> Wenn eine MSI-basierte Erweiterung eine Datei des Typs "extension.vsixmanifest" enthält, wird die Erweiterung im Dialogfeld **Erweiterungen und Updates** angezeigt.
