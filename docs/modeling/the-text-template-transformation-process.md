---
title: Textvorlagen-Transformationsprozess
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b9c65762bbc1fe068889c0420f0dec3d28000130
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="the-text-template-transformation-process"></a>Textvorlagen-Transformationsprozess
Das Textvorlagen-Transformationsprozess akzeptiert eine Textvorlagendatei als Eingabe und generiert eine neue Textdatei als Ausgabe. Beispielsweise können Sie Textvorlagen um Visual Basic- oder C#-Code zu generieren, oder können Sie einen HTML-Bericht generieren.

 Nehmen Sie Teil in diesem Prozess drei Komponenten: das Modul, der Host und die Direktivenprozessoren. Das Modul steuert, den Prozess; er interagiert mit dem Host und des Direktivenprozessors komplizierter, um die Ausgabedatei zu erzeugen. Der Host stellt jegliche Interaktion mit der Umgebung, z. B. die Suche von Dateien und Assemblys. Der Direktivenprozessor fügt Funktionen, z. B. das Lesen von Daten aus einer XML-Datei oder eine Datenbank hinzu.

 Das Textvorlagen-Transformationsprozess wird in zwei Schritten ausgeführt. Zunächst erstellt das Modul eine temporäre-Klasse, die als der generierten Transformationsklasse bezeichnet wird. Diese Klasse enthält den Code, der von den Direktiven und Kontrollblöcken generiert wird. Danach wird das Modul kompiliert und führt die generierten Transformationsklasse, um die Ausgabedatei zu erzeugen.

## <a name="components"></a>Komponenten

|Komponente|Beschreibung|Anpassbare (Ja/Nein)|
|---------------|-----------------|------------------------------|
|Datenbankmodul|Die Modulkomponente steuert den Textvorlagen-Transformationsprozess|Nein.|
|Host|Der Host ist die Schnittstelle zwischen dem Datenbankmodul und die Umgebung des Benutzers. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist ein Host die Text-Transformationsprozess ab.|Ja. Sie können einen benutzerdefinierten Host schreiben.|
|Direktivenprozessoren|Direktivenprozessoren sind Klassen, die Direktiven in Textvorlagen zu behandeln. Richtlinien können Sie um Daten auf einer Textvorlage Eingabequelle zu ermöglichen.|Ja. Sie können benutzerdefinierte Direktivenprozessoren schreiben.|

## <a name="the-engine"></a>Das Modul
 Das Modul empfängt die Vorlage als eine Zeichenfolge mit dem Host, der alle Dateien verarbeitet, die im Transformationsprozess verwendet werden. Anschließend müssen Sie das Modul für den Host aus, um eine beliebige benutzerdefinierten Direktivenprozessoren und andere Aspekte der Umgebung zu suchen. Das Modul wird dann kompiliert und ausgeführt wird die generierten Transformationsklasse. Das Modul gibt den generierten Text an den Host, der normalerweise den Text in einer Datei speichert.

## <a name="the-host"></a>Der Host
 Der Host ist verantwortlich für alle Daten, die mit der Umgebung außerhalb der Vorlagentransformationsprozess besteht, einschließlich der folgenden verknüpft:

-   Suchen von Text und Binärdateien, die durch das Modul oder ein Direktivenprozessor angefordert. Der Host kann Verzeichnisse und den globalen Assemblycache nach Assemblys durchsuchen. Der Host kann benutzerdefinierten Direktivenprozessorcode für das Modul finden. Der Host kann auch suchen und Lesen von Textdateien und ihren Inhalt als Zeichenfolgen zurückgegeben.

-   Bereitstellen von Listen mit standard-Assemblys und Namespaces, die vom Modul verwendet werden, um der generierten Transformationsklasse zu erstellen.

-   Bereitstellen der Anwendungsdomäne, die verwendet wird, wenn das Modul kompiliert und führt die generierten Transformationsklasse. Eine separate Anwendungsdomäne wird verwendet, um die hostanwendung nach Fehlern im Vorlagencode zu schützen.

-   Schreiben die generierte Ausgabedatei an.

-   Versetzen die standarderweiterung für die generierte Ausgabedatei an.

-   Behandlung von Fehlern bei der Textvorlagentransformation aus. Beispielsweise kann der Host die Fehler in der Benutzeroberfläche anzeigen oder in eine Datei schreiben. (In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Fehler in das Fenster mit der Fehlermeldung angezeigt.)

-   Einen Erforderlicher Parameterwert bereitstellt, wenn ein Benutzer eine Richtlinie aufgerufen hat, ohne Angabe eines Werts. Die Direktivenprozessor kann Geben Sie den Namen der Direktive und den Parameter und den Host anweisen, einen Standardwert anzugeben, falls vorhanden.

## <a name="directives-and-directive-processors"></a>Direktiven und Direktivenprozessoren
 Eine Anweisung ist ein Befehl in der Textvorlage. Es stellt die Parameter für den Generierungsprozess bereit. Definieren in der Regel Direktiven auf, die Quelle und Typ für das Modell oder andere Eingabe und die Erweiterung der Ausgabedatei.

 Ein Direktivenprozessor kann eine oder mehrere Anweisungen verarbeitet werden. Wenn Sie eine Vorlage transformieren, müssen Sie einen Direktivenprozessor installiert haben, die mit den Richtlinien in der Vorlage aus.

 Hinzufügen von Code in der generierten Transformationsklasse funktionieren Direktiven. Rufen Sie Richtlinien von einer Textvorlage und das Modul verarbeitet die Richtlinie Aufrufe, bei der Erstellung der generierten Transformationsklasse. Nachdem Sie eine Direktive erfolgreich aufgerufen, kann der Rest des Codes, den Sie in der Textvorlage schreiben auf die Funktionalität beruhen, der die Direktive enthält. Sie können z. B. den folgenden Aufruf vornehmen der `import` Richtlinie in der Vorlage:

 `<#@ import namespace="System.Text" #>`

 Die standard Direktivenprozessor konvertiert diese Option, um eine `using` -Anweisung in der generierten Transformationsklasse. Anschließend können Sie die `StringBuilder` Klasse im Rest des Vorlagencodes ohne Qualifizierung als `System.Text.StringBuilder`.