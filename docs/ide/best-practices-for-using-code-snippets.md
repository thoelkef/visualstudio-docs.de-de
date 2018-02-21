---
title: "Empfohlene Vorgehensweisen für die Verwendung von Codeausschnitten | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 31951001512578446c4a3ab05efe3ade99223068
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="best-practices-for-using-code-snippets"></a>Bewährte Methoden für die Verwendung von Codeausschnitten

Der Code in einem Codeausschnitt zeigt nur die grundlegende Methode, etwas zu tun. Für die meisten Anwendungen muss der Code geändert werden, um der Anwendung zu entsprechen.

## <a name="handling-exceptions"></a>Behandeln von Ausnahmen

Normalerweise fangen Try…Catch-Blöcke des Codeausschnitts alle Ausnahmen ab und lösen sie erneut aus. Möglicherweise ist dies nicht die richtige Wahl für Ihr Projekt. Bei jeder Ausnahme gibt es mehrere Reaktionsmöglichkeiten. Beispiele finden Sie unter [Vorgehensweise: Behandeln einer Ausnahme mit try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) und [Try...Catch...Finally Statement (Visual Basic) (Try...Catch...Finally-Anweisung (Visual Basic))](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Dateispeicherorte

Wenn Sie die Speicherorte an die Anwendung anpassen, sollten Sie Folgendes beachten:

- Suchen eines verfügbaren Speicherorts. Benutzer haben möglicherweise keinen Zugriff auf den Ordner „Programme“ des Computers. Daher kann das Speichern von Dateien mit den Anwendungsdateien eventuell nicht funktionieren.

- Suchen eines sicheren Speicherorts. Das Speichern von Dateien im Stammordner (*C:\\*) ist nicht sicher. Zum Speichern von Anwendungsdaten wird der Ordner *Anwendungsdaten* empfohlen. Für die Daten einzelner Benutzer kann die Anwendung im Ordner *Dokumente* eine Datei für jeden Benutzer erstellen.

- Verwenden eines gültigen Dateinamens. Sie können die Steuerelemente <xref:System.Windows.Forms.OpenFileDialog> und <xref:System.Windows.Forms.SaveFileDialog> verwenden, um die Wahrscheinlichkeit ungültiger Dateinamen zu reduzieren. Denken Sie daran, dass die Datei zwischen dem Zeitpunkt, zu dem der Benutzer die Datei auswählt, und dem Zeitpunkt, zu dem sie vom Code bearbeitet wird, möglicherweise gelöscht wird. Zudem ist der Benutzer eventuell nicht berechtigt, in die Datei zu schreiben.

## <a name="security"></a>Sicherheit

Wie sicher ein Ausschnitt ist, hängt davon ab, wo er im Quellcode verwendet wird und wie er geändert wird, nachdem er in den Code eingefügt wurde. Die folgende Liste enthält einige der zu berücksichtigenden Bereiche.

- Zugriff auf Dateien und Datenbanken

- Codezugriffssicherheit

- Schützen von Ressourcen (z.B. Ereignisprotokolle, Registrierung)

- Speichern von geheimen Daten

- Überprüfen von Eingaben

- Übergeben von Daten an Skriptingtechnologien

Weitere Informationen finden Sie unter [Sichern von Anwendungen](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>Heruntergeladene Codeausschnitte

IntelliSense-Codeausschnitte, die von Visual Studio installiert werden, sind in sich selbst kein Sicherheitsrisiko. Allerdings können sie Sicherheitsrisiken in Ihrer Anwendung erstellen. Aus dem Internet heruntergeladene Ausschnitte sollten wie jeglicher anderer heruntergeladener Inhalt mit äußerster Sorgfalt behandelt werden.

- Laden Sie Ausschnitte nur von vertrauenswürdigen Sites herunter, und verwenden Sie Antivirensoftware, die auf dem neuesten Stand ist.

- Öffnen Sie alle heruntergeladenen Ausschnittdateien im Editor oder XML-Editor von Visual Studio, und überprüfen Sie sie vor der Installation sorgfältig. Achten Sie dabei auf Folgendes:

    - Der Code eines Ausschnitts kann bei der Ausführung das System beschädigen. Lesen Sie den Quellcode sorgfältig, bevor Sie ihn ausführen.

    - Der Hilfe-URL-Block der Ausschnittdatei kann URLs enthalten, die eine bösartige Skriptdatei ausführen oder eine anstößige Website anzeigen.

    - Der Codeausschnitt kann Verweise enthalten, die automatisch dem Projekt hinzugefügt werden und von überall auf Ihr System geladen werden können. Diese Verweise wurden möglicherweise von der Stelle auf den Computer heruntergeladen, von der Sie den Ausschnitt heruntergeladen haben. Der Ausschnitt kann dann eine Methode im Verweis aufrufen, die bösartigen Code ausführt. Um sich gegen einen solchen Angriff zu schützen, sollten Sie die Import- und Verweisblöcke der Ausschnittdatei überprüfen.

## <a name="see-also"></a>Siehe auch

[Visual Basic IntelliSense-Codeausschnitte](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)  
[Sichern von Anwendungen](../ide/securing-applications.md)  
[Codeausschnitte](../ide/code-snippets.md)