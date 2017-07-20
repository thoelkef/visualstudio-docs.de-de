---
title: Ausgabefenster | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 30
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 60636023fc506df5ed6e57d4f4d9c90e680ab607
ms.contentlocale: de-de
ms.lasthandoff: 05/30/2017

---
# Ausgabefenster
<a id="output-window" class="xliff"></a>
Das Fenster **Ausgabe** zeigt die Statusmeldungen für verschiedene Funktionen in der integrierten Entwicklungsumgebung (Integrated Development Environment – IDE) an. Um das Fenster **Ausgabe** zu öffnen, wählen Sie in der Menüleiste **Ansicht/Ausgabe** aus (oder drücken Sie STRG+ALT+O).  
  
> [!WARNING]
>  In Visual Studio Express-Editionen wird das Fenster "Ausgabe" nicht im Menü "Ansicht" angezeigt. Um es einzublenden, verwenden Sie den Hotkey STRG+ALT+O.  
  
## Symbolleiste
<a id="toolbar" class="xliff"></a>  
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
  
## Ausgabebereich
<a id="output-pane" class="xliff"></a>  
 In dem in der Liste **Ausgabe anzeigen von** ausgewählten Bereich **Ausgabe** werden Ausgabedaten aus der angegebenen Quelle angezeigt.  
  
## Meldungsrouting an das Ausgabefenster
<a id="routing-messages-to-the-output-window" class="xliff"></a>  
 Um das Fenster **Ausgabe** beim Erstellen eines Projekts anzuzeigen, wählen Sie im Dialogfeld **Allgemein, Projekte und Projektmappen, Optionen** die Option **Ausgabefenster bei Buildbeginn anzeigen** aus. Klicken Sie dann, während eine Codedatei zur Bearbeitung geöffnet ist, auf der Symbolleiste des Fensters **Ausgabe** auf die Schaltflächen **Gehe zur nächsten Meldung** oder **Gehe zur vorherigen Meldung**, um Einträge im Bereich **Ausgabe** auszuwählen. Währenddessen wird die Einfügemarke im Code-Editor in die Codezeile verschoben, in der das jeweilige Problem auftritt.  
  
 Bei bestimmten im [Befehlsfenster](../../ide/reference/command-window.md) aufgerufenen Funktionen und Befehlen der IDE erfolgt die Ausgabe im Fenster **Ausgabe**. Ausgaben von externen Tools, z.B. BAT- und COM-Dateien, die normalerweise im Eingabeaufforderungsfenster angezeigt werden, werden an einen **Ausgabe**-Bereich geroutet, wenn Sie die Funktion **Ausgabefenster verwende**n im Fenster [Verwalten von externen Tools](../../ide/managing-external-tools.md) auswählen. Viele weitere Meldungstypen können ebenfalls in **Ausgabe**-Bereichen angezeigt werden. Wenn beispielsweise Transact-SQL-Syntax in einer gespeicherten Prozedur anhand einer Zieldatenbank überprüft wird, werden die Ergebnisse im Fenster **Ausgabe** angezeigt.  
  
 Sie können auch eigene Anwendungen so programmieren, dass sie Diagnosemeldungen zur Laufzeit in einen **Ausgabe**-Bereich ausgeben. Verwenden Sie dazu Member der <xref:System.Diagnostics.Debug>-Klasse oder der <xref:System.Diagnostics.Trace>-Klasse im <xref:System.Diagnostics>-Namespace der .NET Framework-Klassenbibliothek. Wenn Sie Debugkonfigurationen von einer Projektmappe oder einem Projekt erstellen, wird die Ausgabe von Membern der <xref:System.Diagnostics.Debug>-Klasse angezeigt. Beim Erstellen einer Debug- oder Releasekonfiguration wird die Ausgabe von Membern der <xref:System.Diagnostics.Trace>-Klasse angezeigt. Weitere Informationen finden Sie unter [Diagnosemeldungen im Ausgabefenster](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 Sie können unter [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] benutzerdefinierte Buildschritte und Buildereignisse erstellen, deren Warnungen und Fehler im Bereich **Ausgabe** angezeigt und gezählt werden. Durch Drücken von F1 in einer Ausgabezeile wird ein entsprechendes Hilfethema angezeigt. Weitere Informationen finden Sie unter [Formatieren der Ausgabe eines benutzerdefinierten Buildschritts oder eines benutzerdefinierten Buildereignisses](/cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).  
  
## Bildlauf-Verhalten
<a id="scrolling-behavior" class="xliff"></a>  
 Wenn Sie den automatischen Bildlauf im Ausgabefenster verwenden und dann navigieren, indem Sie die Maus oder Pfeiltasten verwenden, wird der automatische Bildlauf beendet. Verwenden Sie zum Fortsetzen des automatischen Bildlaufs STRG+ENDE.  
  
## Siehe auch
<a id="see-also" class="xliff"></a>  
 [Diagnosemeldungen im Ausgabefenster](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Vorgehensweise: Steuern des Ausgabefensters](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)   
 [Grundlagen der Buildkonfiguration](../../ide/understanding-build-configurations.md)   
 [Übersicht über die Klassenbibliothek](/dotnet/standard/class-library-overview)
