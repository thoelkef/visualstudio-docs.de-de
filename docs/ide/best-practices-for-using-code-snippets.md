---
title: "Empfohlene Vorgehensweisen f&#252;r die Verwendung von Codeausschnitten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeausschnitte, Bewährte Methoden"
  - "Codeausschnitte, Sicherheit"
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Empfohlene Vorgehensweisen f&#252;r die Verwendung von Codeausschnitten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Code in einem Codeausschnitt zeigt nur die grundlegendste Methode etwas zu ermöglichen.  Für die meisten Anwendungen muss der Code geändert werden, um die Anwendung zu entsprechen.  
  
## Behandeln von Ausnahmen  
 Normalerweise fangen Codeausschnitt Try… Catch\-Blöcke lösen alle Ausnahmen ab und erneut aus.  Möglicherweise ist dies nicht die richtige Wahl für das Projekt.  Bei jeder Ausnahme gibt es mehrere Reaktionsmöglichkeiten.  Beispiele zu diesem Thema finden Sie unter [Gewusst wie: Behandeln einer Ausnahme mit try\/catch](../Topic/How%20to:%20Handle%20an%20Exception%20Using%20try-catch%20\(C%23%20Programming%20Guide\).md) und [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).  
  
## Dateispeicherorte  
 Wenn Sie die Speicherorte der Anwendung anpassen, sollten Sie sich Folgendes an:  
  
-   Suchen eines verfügbaren Speicherorts.  Benutzer haben keinen Zugriff auf den Ordner Programme des Computers. Daher funktioniert möglicherweise das Speichern von Dateien mit den Anwendungsdateien nicht.  
  
-   Suchen eines sicheren Speicherorts.  Dateien im Stammordner \(C:\\\) gespeichert ist nicht sicher.  Zum Speichern von Anwendungsdaten empfehlen wir den Ordner Anwendungsdaten.  Für die Daten einzelner Benutzer kann die Anwendung im Ordner Eigene Dateien eine Datei für jeden Benutzer erstellen.  
  
-   Verwenden eines gültigen Dateinamens.  Sie können die <xref:System.Windows.Forms.OpenFileDialog> und <xref:System.Windows.Forms.SaveFileDialog>\-Steuerelemente verwenden, um die Wahrscheinlichkeit ungültiger Dateinamen zu reduzieren.  Denken Sie daran, dass die Datei zwischen dem Zeitpunkt, zu dem der Benutzer die Datei auswählt, und dem Zeitpunkt, zu dem sie vom Code bearbeitet wird, unter Umständen gelöscht wird.  Zudem ist der Benutzer eventuell nicht berechtigt, in die Datei zu schreiben.  
  
## Sicherheit  
 Wie sicher ein Ausschnitt ist, hängt davon ab, wo er im Quellcode verwendet wird und wie er geändert wird, nachdem er in den Code eingefügt wurde.  Die folgende Liste enthält einige der zu berücksichtigenden Bereiche.  
  
-   Datei\- und Datenbankzugriff  
  
-   Codezugriffssicherheit  
  
-   Schützen von Ressourcen \(z. B. Ereignisprotokolle, Registrierung\)  
  
-   Speichern von geheimen Daten  
  
-   Überprüfen von Eingaben  
  
-   Übergeben von Daten an Skripttechnologien  
  
 Weitere Informationen finden Sie unter [Sichern von Anwendungen](../ide/securing-applications.md).  
  
## Heruntergeladene Codeausschnitte  
 Die IntelliSense\-Codeausschnitte, die von Visual Studio installiert sind, sind nicht in eine gefahr Sicherheit.  Allerdings können sie Sicherheitsrisiken in Ihrer Anwendung erstellen.  Die Ausschnitte, die aus dem Internet heruntergeladen werden, sollten wie ein beliebiges anderes heruntergeladener Inhalt behandelt werden mit extremer Vorsicht.  
  
-   Download ausschnitte nur von vertrauenswürdigen Sites Sie vertrauen und verwenden die aktuelle Virus\-Software.  
  
-   Öffnen Sie alle heruntergeladenen Dateien des Ausschnitts im Editor oder XML\-Editor von Visual Studio und führen Sie sie sorgfältig, bevor Sie sie installieren.  Suchen Sie nach den folgenden Probleme:  
  
    -   Der Code des Ausschnitts könnte Ihr System schädigen, wenn Sie sie ausführen.  Lesen Sie den Quellcode sorgfältig, bevor Sie ihn ausführen.  
  
    -   Der Block der Hilfe\-URL der Ausschnittdatei URL enthalten kann, die eine Datei bösartigen Skriptcode ausführen oder eine offensive Website anzeigen.  
  
    -   Der Ausschnitt kann Verweise enthält, die dem Projekt automatisch hinzugefügt werden und wird von einer beliebigen Stelle auf dem System geladen werden.  Diese Verweise wurden möglicherweise von der Stelle auf den Computer heruntergeladen, von der Sie den Ausschnitt heruntergeladen hatten.  Der Ausschnitt kann dann eine Methode im Verweis aufrufen, die bösartigen Code ausführt.  Um sich gegen einen solchen Angriff zu schützen, sollten Sie die Import\- und " Verweise " Blockierung der Ausschnittdatei.  
  
## Siehe auch  
 [Visual Basic IntelliSense Code Snippets](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [Sichern von Anwendungen](../ide/securing-applications.md)   
 [Codeausschnitte](../ide/code-snippets.md)