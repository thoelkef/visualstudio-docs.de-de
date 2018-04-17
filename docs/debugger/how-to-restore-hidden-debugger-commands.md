---
title: 'Vorgehensweise: Wiederherstellen von ausgeblendeten Debuggerbefehlen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e48e52f7d838b701745a449b979486b11a708faa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Gewusst wie: Wiederherstellen von ausgeblendeten Debuggerbefehlen
Beim Einrichten von Visual Studio werden Sie aufgefordert, die IDE-Standardeinstellungen für Ihre bevorzugte Programmiersprache festzulegen. Möglicherweise blenden die IDE-Standardeinstellungen für einige Sprachen bestimmte Debuggerbefehle aus.  
  
 Falls Sie eine Debuggerfunktion verwenden möchten, das durch Ihre IDE-Standardeinstellungen ausgeblendet ist, können Sie dem Menü den Befehl durch folgende Prozedur wieder hinzufügen.  
  
### <a name="to-restore-hidden-debugger-commands"></a>So stellen Sie ausgeblendete Debuggerbefehle wieder her  
  
1.  Ein Projekt geöffnet ist, auf die **Tools** Menü klicken Sie auf **anpassen**.  
  
2.  In der **anpassen** (Dialogfeld), klicken Sie auf die **Befehle** Registerkarte.  
  
3.  In der **Menüleiste:** Dropdownliste, wählen die **Debuggen** Menü, das den wiederhergestellten Befehl enthalten soll.  
  
4.  Klicken Sie auf die **Befehl hinzufügen...**  Schaltfläche.  
  
5.  In der **Befehl hinzufügen** Feld, wählen Sie den Befehl, die Sie hinzufügen möchten, und klicken Sie auf **OK**.  
  
6.  Wiederholen Sie den vorigen Schritt, um einen weiteren Befehl hinzuzufügen.  
  
7.  Klicken Sie auf **schließen** nach Abschluss des Hinzufügen von Befehlen zum Menü.  
  
    > [!WARNING]
    >  Einige Menüelemente sind nur in bestimmten Debuggermodi sichtbar, etwa im Ausführmodus oder im Unterbrechungsmodus. Deshalb ist ein Element, das Sie hinzugefügt haben, nicht notwendigerweise sofort nach Ausführung dieser Schritte sichtbar.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Wiederherstellen von Befehlen, die im Dialogfeld Anpassen nicht verfügbar sind  
 Einige Befehle, besonders solche in hierarchischen Menüs, können nicht wiederhergestellt werden, aus der **anpassen** (Dialogfeld). Um diese Befehle wiederherzustellen, müssen Sie eine neue Auflistung von IDE-Einstellungen importieren.  
  
#### <a name="to-import-new-ide-settings"></a>So importieren Sie neue IDE-Einstellungen  
  
1.  Auf der **Tools** Menü klicken Sie auf **Einstellungen importieren und exportieren**.  
  
2.  Auf der **Willkommen bei den Import / Export-Assistent** auf **ausgewählte umgebungseinstellungen importieren**, und klicken Sie dann auf **Weiter**.  
  
3.  Auf der **aktuelle Einstellungen speichern** Seite erstellen, entscheiden, ob die bestehenden Einstellungen speichern, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **wählen Sie eine Auflistung von Einstellungen für den import** Seite der **Standardeinstellungen** Ordner, wählen Sie eine Auflistung von entwicklungseinstellungen, die Befehle sind Sie verwenden möchten. Wenn Sie die Sammlung, wählen nicht wissen, versuchen Sie es **allgemeine Entwicklungseinstellungen** oder **Visual C++-Entwicklungseinstellungen**, die die meisten Debuggerbefehle bereitstellen.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **wählen Sie die Einstellungen für den import** Seite **Optionen**, stellen Sie sicher, dass **Debuggen** ausgewählt ist. Deaktivieren Sie die anderen Kontrollkästchen, sofern Sie nicht noch weitere Einstellungen importieren möchten.  
  
7.  Klicken Sie auf **Fertig stellen**.  
  
8.  Auf der **Importvorgang abgeschlossen** überprüfen Sie alle Fehler im Zusammenhang mit beim Zurücksetzen der Einstellungen unter **Details**.  
  
9. Klicken Sie auf **Schließen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)