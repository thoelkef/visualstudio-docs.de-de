---
title: Suchen und Verwenden von Erweiterungen
ms.date: 01/30/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b423f666ed27df1723a30a0413d8388a6c5fa903
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919741"
---
# <a name="find-and-use-visual-studio-extensions"></a>Suchen und Verwenden von Visual Studio-Erweiterungen

Visual Studio-Extensions sind Codepakete, die innerhalb von Visual Studio ausgeführt werden und neue oder verbesserte Visual Studio-Funktionen bereitstellen. Weitere Informationen zu Visual Studio-Erweiterungen finden Sie hier: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Verwenden Sie das Dialogfeld **Erweiterungen und Updates**, um Visual Studio-Erweiterungen zu installieren und zu verwalten. Klicken Sie auf **Extras** > **Erweiterungen und Updates**, oder geben Sie **Erweiterungen** in das Fenster **Schnellstart** ein, um das Dialogfeld **Erweiterungen und Updates** zu öffnen.

![Dialogfeld „Erweiterungen und Updates“ in Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Im linken Bereich werden die Erweiterungen nach installierten Erweiterungen, im Visual Studio Marketplace (**Online**) verfügbaren Erweiterungen und Erweiterungen, für die Updates verfügbar sind, kategorisiert. Der **Roaming-Erweiterungs-Manager** enthält eine Liste aller Visual Studio-Erweiterungen, die Sie auf jeglichen Computern oder Instanzen von Visual Studio installiert haben. Er ist dazu konzipiert, dass Sie Ihre bevorzugten Erweiterungen einfacher finden können.

## <a name="find-visual-studio-extensions"></a>Suchen von Visual Studio-Erweiterungen

Sie können Erweiterungen über den [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) installieren. Zu diesen Erweiterungen können Steuerelemente, Beispiele, Vorlagen, Werkzeuge oder andere Komponenten zählen, die Visual Studio Funktionen hinzufügen. In Visual Studio werden Erweiterungen im VSIX-Paketformat unterstützt. Diese umfassen Projektvorlagen, Elementvorlagen, **Werkzeugkasten** -Komponenten des Managed Extension Framework (MEF) und VSPackages. Sie können auch MSI-basierte Erweiterungen herunterladen und installieren, doch können diese nicht über das Dialogfeld **Erweiterungen und Updates** aktiviert oder deaktiviert werden. Visual Studio Marketplace enthält sowohl VSIX- als auch MSI-Erweiterungen.

## <a name="install-or-uninstall-visual-studio-extensions"></a>Installieren oder Deinstallieren von Visual Studio-Erweiterungen

Suchen Sie in **Erweiterungen und Updates**nach der Erweiterung, die Sie installieren möchten. (Wenn Sie den Namen der Erweiterung oder einen Teil des Namens kennen, können Sie im Fenster **Suche** danach suchen.) Klicken Sie auf **Download** (Herunterladen). Die Erweiterung wird der Warteschlange für die Installation hinzugefügt. Sie wird installiert, sobald alle Instanzen von Visual Studio geschlossen wurden.

Wenn Sie versuchen, eine Erweiterung zu installieren, die Abhängigkeiten enthält, wird vom Installationsprogramm überprüft, ob diese bereits installiert sind. Sind sie nicht installiert, werden im Dialogfeld **Erweiterungen und Updates** die vor der Installation der Erweiterung zu installierenden Abhängigkeiten aufgeführt.

Wenn Sie die Verwendung einer Erweiterung beenden möchten, können Sie diese deaktivieren oder deinstallieren. Beim Deaktivieren einer Erweiterung bleibt sie installiert, wird jedoch nicht geladen. Sie können nur VSIX-Erweiterungen deaktivieren. Erweiterungen, die mit MSI installiert wurden, können nur deinstalliert werden. Suchen Sie nach der Erweiterung, und klicken Sie auf **Deinstallieren** oder **Deaktivieren**. Starten Sie Visual Studio neu, um deaktivierte Erweiterungen zu entladen.

## <a name="per-user-and-administrative-extensions"></a>Erweiterungen pro Benutzer und Verwaltungserweiterungen

Bei den meisten Erweiterungen handelt es sich um Erweiterungen pro Benutzer, und diese werden im Ordner *%LocalAppData%\Microsoft\VisualStudio\\<Visual Studio-Version>\>\Extensions\\* installiert. Bei einigen Erweiterungen handelt es sich um Verwaltungserweiterungen, und diese werden im Ordner *\<Visual Studio-Installationsordner>\Common7\IDE\Extensions\\* installiert.

Um das System vor Erweiterungen zu schützen, in denen möglicherweise Fehler oder bösartiger Code enthalten ist, können Sie das Laden von Erweiterungen pro Benutzer dahingehend einschränken, dass sie nur geladen werden, wenn Visual Studio mit normalen Benutzerberechtigungen ausgeführt wird. Das bedeutet, dass Erweiterungen pro Benutzer deaktiviert sind, wenn Visual Studio mit Administratorberechtigungen ausgeführt wird. Wechseln Sie hierzu zur Optionsseite **Erweiterungen und Updates** (**Extras > Optionen** > **Umgebung** > **Erweiterungen und Updates**). Deaktivieren Sie das Kontrollkästchen **Pro-Benutzer-Erweiterungen bei Ausführung als Administrator laden** , und starten Sie Visual Studio dann neu.

## <a name="automatic-extension-updates"></a>Automatische Erweiterungsupdates

Erweiterungen werden automatisch aktualisiert, wenn eine neue Version im Visual Studio Marketplace zur Verfügung steht. Die neue Version der Erweiterung wird im Hintergrund erkannt und installiert. Beim nächsten Start von Visual Studio wird die neue Version der Erweiterung ausgeführt.

Wenn Sie automatische Updates deaktivieren möchten, können Sie das Feature für alle Erweiterungen oder nur für bestimmte Erweiterungen deaktivieren.

- Wählen Sie zum Deaktivieren von automatischen Updates für alle Erweiterungen den Link **Einstellungen für die Erweiterungen und Updates ändern** im Dialogfeld **Erweiterungen und Updates** aus. Deaktivieren Sie die Option **Erweiterungen automatisch aktualisieren** im Dialogfeld **Optionen**.

- Deaktivieren Sie zum automatischen Deaktivieren einer bestimmten Erweiterung die Option **Diese Extension automatisch aktualisieren** im Detailbereich der Erweiterung auf der rechten Seite des Dialogfelds **Erweiterungen und Updates**.

## <a name="extension-crash-and-unresponsiveness-notifications"></a>Benachrichtigungen zum Absturz von und zu nicht reagierenden Erweiterungen

In **Visual Studio 2017 (Version 15.3)** werden Sie von Visual Studio benachrichtigt, wenn die Vermutung besteht, dass eine Erweiterung während einer vorherigen Sitzung zu einem Absturz beigetragen hat. Wenn Visual Studio abstürzt, speichert das Programm den Ausnahmestapel. Beim nächsten Start von Visual Studio untersucht es den Stapel. Es beginnt dabei auf der Blattebene und arbeitet sich zur Basis herunter. Wenn Visual Studio ermittelt, dass ein Frame zu einem Modul einer installierten und aktivierten Erweiterung gehört, wird eine Benachrichtigung angezeigt.

Neu in **Visual Studio 2017 Version 15.6**: Visual Studio sendet ebenfalls eine Benachrichtigung, wenn eine Erweiterung vermutlich dazu führt, dass die Benutzeroberfläche nicht mehr reagiert.

Sie können diese Benachrichtigung ignorieren oder eine der folgenden Maßnahmen ergreifen:

- Wählen Sie **Disable this extension** (Diese Erweiterung deaktivieren) aus. Visual Studio deaktiviert die Erweiterung und informiert Sie, ob Sie Ihr System neu starten müssen, damit die Deaktivierung wirksam wird. Sie können die Erweiterung im Dialogfeld **Erweiterungen und Updates** erneut aktivieren, falls Sie das wünschen.

- Klicken Sie auf **Diese Meldung nicht mehr anzeigen**.

  - Wenn sich die Benachrichtigung auf einen Absturz in einer vorherigen Sitzung bezieht, zeigt Visual Studio keine weiteren Benachrichtigungen an, wenn ein Absturz in Zusammenhang mit dieser Erweiterung auftritt. Visual Studio zeigt weiterhin Benachrichtigungen an, wenn eine nicht reagierende Benutzeroberfläche dieser Erweiterung zugeordnet werden kann, oder wenn ein Absturz oder eine nicht reagierende Benutzeroberfläche mit anderen Erweiterungen in Zusammenhang steht.
  - Wenn sich die Benachrichtigung auf eine nicht reagierende Benutzeroberfläche bezieht, zeigt die IDE keine Benachrichtigung mehr an, wenn diese Erweiterung mit einer nicht reagierenden Benutzeroberfläche in Zusammenhang steht. Visual Studio zeigt weiterhin absturzbezogene Benachrichtigungen für diese Erweiterung sowie absturzbezogene Benachrichtigungen und Benachrichtigungen zu einer nicht reagierenden Benutzeroberfläche für andere Erweiterungen an.

- Klicken Sie auf **Weitere Informationen**, um zu dieser Seite zu gelangen.

- Wählen Sie die Schaltfläche **X** am Ende der Benachrichtigung aus, um die Benachrichtigung zu schließen. Für künftige Instanzen der Erweiterung in Zusammenhang mit einem Absturz oder einer nicht reagierenden Benutzeroberfläche wird eine neue Benachrichtigung angezeigt.

> [!NOTE]
> Eine nicht reagierende Benutzeroberfläche oder eine Benachrichtigung zu einem Absturz bedeutet nur, dass eines der Erweiterungsmodule sich im Stapel befand, als die Benutzeroberfläche nicht mehr reagierte oder es zum Absturz kam. Es bedeutet nicht unbedingt, dass die Erweiterung selbst die Ursache für den Absturz oder die nicht reagierende Benutzeroberfläche war. Es ist möglich, dass die Erweiterung Code aufgerufen hat, die Teil von Visual Studio ist, und dass dieser Code den Fehler verursacht hat. Allerdings ist die Benachrichtigung möglicherweise trotzdem hilfreich, wenn das Szenario, das zum Absturz oder zu einer nicht reagierenden Benutzeroberfläche geführt hat, nicht wichtig für Sie ist. In diesem Fall verhindert das Deaktivieren der Erweiterung den Absturz oder die fehlende Reaktion der Benutzeroberfläche, ohne Ihre Produktivität zu beeinträchtigen.

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

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Installieren ohne das Dialogfeld „Erweiterungen und Updates“

Erweiterungen, die in *VSIX-Dateien* gepackt wurden, sind möglicherweise an anderen Orten als Visual Studio Marketplace verfügbar. Diese Dateien können mithilfe des Dialogfelds **Erweiterungen und Updates** nicht erkannt werden. Sie können eine *VSIX-Datei* jedoch installieren, indem Sie auf die Datei doppelklicken oder sie auswählen und die **EINGABETASTE** drücken. Befolgen Sie dann die angezeigten Anweisungen. Wenn die Erweiterung installiert ist, können Sie das Dialogfeld **Erweiterungen und Updates** zum Aktivieren, Deaktivieren oder Deinstallieren der Erweiterung verwenden.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Vom Dialogfeld „Erweiterungen und Updates“ nicht unterstützte Erweiterungstypen

Visual Studio unterstützt auch weiterhin Erweiterungen, die mit Microsoft Installer (MSI) installiert werden, jedoch nicht über das Dialogfeld **Erweiterungen und Updates** ohne Änderungen.

> [!TIP]
> Wenn eine MSI-basierte Erweiterung eine *extension.vsixmanifest-Datei* enthält, wird die Erweiterung im Dialogfeld **Erweiterungen und Updates** angezeigt.