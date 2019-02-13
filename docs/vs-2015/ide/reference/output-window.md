---
title: Ausgabefenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26b826b19a14731ba4fbbb11eccee5fc4337c4ff
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784818"
---
# <a name="output-window"></a>Ausgabefenster
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Das Fenster **Ausgabe** zeigt die Statusmeldungen für verschiedene Funktionen in der integrierten Entwicklungsumgebung (Integrated Development Environment – IDE) an. Um das Fenster **Ausgabe** zu öffnen, wählen Sie in der Menüleiste **Ansicht/Ausgabe** aus (oder drücken Sie STRG+ALT+O).  
  
> [!WARNING]
>  In Visual Studio Express-Editionen wird das Fenster "Ausgabe" nicht im Menü "Ansicht" angezeigt. Um es einzublenden, verwenden Sie den Hotkey STRG+ALT+O.  
  
## <a name="toolbar"></a>Symbolleiste  
 **Ausgabe anzeigen von**  
 Zeigt einen oder mehrere Ausgabebereiche zur Ansicht an. Je nachdem, welche Tools in der IDE Benutzermeldungen im Fenster **Ausgabe** ausgegeben haben, stehen mehrere Informationsbereiche zur Verfügung.  
  
 **Suchen der Meldung im Code**  
 Verschiebt die Einfügemarke im Code-Editor in die Zeile, die den ausgewählten Buildfehler enthält.  
  
 **Gehe zur vorherigen Meldung**  
 Verschiebt den Fokus im Fenster **Ausgabe** zum vorherigen Buildfehler und positioniert die Einfügemarke im Code-Editor in der Zeile mit dem Buildfehler.  
  
 **Gehe zur nächsten Meldung**  
 Verschiebt den Fokus im Fenster **Ausgabe** zum nächsten Buildfehler und positioniert die Einfügemarke im Code-Editor in der Zeile mit dem Buildfehler.  
  
 **Alle löschen**  
 Löscht den gesamten Text aus dem Bereich **Ausgabe**.  
  
 **Umschalten des Zeilenumbruchs**  
 Schaltet die Zeilenumbruchfunktion im Bereich **Ausgabe** ein und aus. Wenn die Zeilenumbruchfunktion aktiviert ist, wird Text in längeren Einträgen, der über den Anzeigebereich hinausgeht, in der nächsten Zeile angezeigt.  
  
## <a name="output-pane"></a>Ausgabebereich  
 In dem in der Liste **Ausgabe anzeigen von** ausgewählten Bereich **Ausgabe** werden Ausgabedaten aus der angegebenen Quelle angezeigt.  
  
## <a name="routing-messages-to-the-output-window"></a>Meldungsrouting an das Ausgabefenster  
 Um das Fenster **Ausgabe** beim Erstellen eines Projekts anzuzeigen, wählen Sie im Dialogfeld **Allgemein, Projekte und Projektmappen, Optionen** die Option **Ausgabefenster bei Buildbeginn anzeigen** aus. Klicken Sie dann, während eine Codedatei zur Bearbeitung geöffnet ist, auf der Symbolleiste des Fensters **Ausgabe** auf die Schaltflächen **Gehe zur nächsten Meldung** oder **Gehe zur vorherigen Meldung**, um Einträge im Bereich **Ausgabe** auszuwählen. Währenddessen wird die Einfügemarke im Code-Editor in die Codezeile verschoben, in der das jeweilige Problem auftritt.  
  
 Bei bestimmten im [Befehlsfenster](../../ide/reference/command-window.md) aufgerufenen Funktionen und Befehlen der IDE erfolgt die Ausgabe im Fenster **Ausgabe**. Ausgaben von externen Tools, z.B. BAT- und COM-Dateien, die normalerweise im Eingabeaufforderungsfenster angezeigt werden, werden an einen **Ausgabe**-Bereich geroutet, wenn Sie die Funktion **Ausgabefenster verwende**n im Fenster [Verwalten von externen Tools](../../ide/managing-external-tools.md) auswählen. Viele weitere Meldungstypen können ebenfalls in **Ausgabe**-Bereichen angezeigt werden. Wenn beispielsweise Transact-SQL-Syntax in einer gespeicherten Prozedur anhand einer Zieldatenbank überprüft wird, werden die Ergebnisse im Fenster **Ausgabe** angezeigt.  
  
 Sie können auch eigene Anwendungen so programmieren, dass sie Diagnosemeldungen zur Laufzeit in einen **Ausgabe**-Bereich ausgeben. Verwenden Sie dazu Member der <xref:System.Diagnostics.Debug>-Klasse oder der <xref:System.Diagnostics.Trace>-Klasse im <xref:System.Diagnostics>-Namespace der .NET Framework-Klassenbibliothek. Wenn Sie Debugkonfigurationen von einer Projektmappe oder einem Projekt erstellen, wird die Ausgabe von Membern der <xref:System.Diagnostics.Debug>-Klasse angezeigt. Beim Erstellen einer Debug- oder Releasekonfiguration wird die Ausgabe von Membern der <xref:System.Diagnostics.Trace>-Klasse angezeigt. Weitere Informationen finden Sie unter [Diagnosemeldungen im Ausgabefenster](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 Sie können unter [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] benutzerdefinierte Buildschritte und Buildereignisse erstellen, deren Warnungen und Fehler im Bereich **Ausgabe** angezeigt und gezählt werden. Durch Drücken von F1 in einer Ausgabezeile wird ein entsprechendes Hilfethema angezeigt. Weitere Informationen finden Sie unter [Formatieren der Ausgabe eines benutzerdefinierten Buildschritts oder eines benutzerdefinierten Buildereignisses](http://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).  
  
## <a name="scrolling-behavior"></a>Bildlauf-Verhalten  
 Wenn Sie den automatischen Bildlauf im Ausgabefenster verwenden und dann navigieren, indem Sie die Maus oder Pfeiltasten verwenden, wird der automatische Bildlauf beendet. Verwenden Sie zum Fortsetzen des automatischen Bildlaufs STRG+ENDE.  
  
## <a name="see-also"></a>Siehe auch  
 [Diagnosemeldungen im Ausgabefenster](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Vorgehensweise: Steuern des Ausgabefensters](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)   
 [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)   
 [Übersicht über die Klassenbibliothek](http://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157)
