---
title: "Identifizieren und Anpassen von Tastenkombinationen in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.Keyboard"
helpviewer_keywords: 
  - "Befehle [Visual Studio], Tastenkombinationen"
  - "Benutzerdefinierte Tastenkombinationen [Visual Studio]"
  - "Anpassen von Tastenkombinationen [Visual Studio]"
  - "Exportieren von Tastenkombinationen [Visual Studio]"
  - "Importieren von Tastenkombinationen [Visual Studio]"
  - "Tastenkombinationen [Visual Studio], Anpassen"
  - "Tastenkombinationen [Visual Studio]"
ms.assetid: d2774be2-60a4-4d6f-95f1-79d0d9e55b56
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Identifizieren und Anpassen von Tastenkombinationen in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Tastenkombinationen für Visual Studio\-Befehle nachschlagen, diese Tastenkombinationen anpassen und sie dann exportieren, damit andere Benutzer sie verwenden können.  Viele Tastenkombinationen rufen immer dieselben Befehle auf, aber das Verhalten einer Tastenkombination kann auf der Grundlage von Bedingungen unterschiedlich sein, die von folgenden Fragen abhängen:  
  
-   Welche Standardumgebungseinstellungen wurde bei der erstmaligen Ausführung von Visual Studio ausgewählt \(beispielsweise "Allgemeine Entwicklungseinstellungen" oder Visual C\#\)?  
  
-   Wurde das Verhalten der Tastenkombination angepasst?  
  
-   In welchem Kontext wird die Tastenkombination angewendet?  Beispielsweise ruft die Taste F2 den Edit.EditCell\-Befehl auf, wenn Sie den Einstellungs\-Designer verwenden, aber den File.Rename\-Befehl, wenn Sie mit Team Explorer arbeiten.  
  
 Unabhängig von Einstellungen, Anpassungen und Kontext können Sie eine Tastenkombination im Dialogfeld **Optionen** immer nachschlagen und ändern.  Sie finden in [Standardtastenkombinationen für häufig verwendete Befehle](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) die Standardtastenkombinationen für einige Dutzend Befehle, und in [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md) die vollständige Liste aller Standardtastenkombinationen für "Allgemeine Entwicklungseinstellungen".  
  
 **In diesem Thema**  
  
-   [So finden Sie eine Tastenkombination](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)  
  
-   [Anpassen einer Tastenkombination](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)  
  
-   [Benutzerdefinierte Tastenkombinationen freigeben](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)  
  
 Wenn eine Tastenkombinationen einem Befehl im globalen Kontext und in keinem anderen zugewiesen ist, ruft diese Tastenkombination immer diesen Befehl auf.  Aber eine Tastenkombination kann einem Befehl im globalen Kontext und einem anderen Befehl in einem speziellen Kontext zugewiesen werden.  Wenn Sie eine solche Tastenkombination in dem speziellen Kontext verwenden, ruft sie den Befehl für diesen Kontext auf und nicht den Befehl für den globalen Kontext.  
  
> [!NOTE]
>  Je nach Ihren Einstellungen und der Edition von Visual Studio ändern sich möglicherweise auch die Namen und Positionen von Menübefehlen oder die Optionen in Dialogfeldern.  Dieses Thema bezieht sich auf **Allgemeine Entwicklungseinstellungen**.  
  
##  <a name="bkmk_identify"></a> So finden Sie eine Tastenkombination  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  
  
2.  Erweitern Sie **Umgebung**, und wählen Sie dann **Tastatur**.  
  
     ![Tastenkombinationen im Dialogfeld "Optionen" anzeigen](../ide/media/optionskeyboard.png "OptionsKeyboard")  
  
3.  Geben Sie im Feld **Befehle mit folgendem Inhalt anzeigen** den gesamten Befehlsnamen ohne Leerzeichen ein.  
  
     Beispielsweise können Sie Befehle für "solutionexplorer" suchen.  
  
4.  Wählen Sie in der Liste den richtigen Befehl aus.  
  
     Beispielsweise können Sie **View.SolutionExplorer** auswählen.  
  
5.  Wenn dem Befehl eine Tastenkombination zugeordnet ist, wird sie in der Liste **Tastenkombination für ausgewählten Befehl** aufgeführt.  
  
     ![Tastenkombination für einen bestimmten Befehl anzeigen](../ide/media/viewshortcut.png "ViewShortcut")  
  
##  <a name="bkmk_assign"></a> Anpassen einer Tastenkombination  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Optionen**.  
  
2.  Erweitern Sie den Ordner **Umgebung**, und wählen Sie dann **Tastatur**.  
  
     ![Tastenkombinationen im Dialogfeld "Optionen" anzeigen](../ide/media/optionskeyboard.png "OptionsKeyboard")  
  
3.  Geben Sie im Feld **Befehle mit folgendem Inhalt anzeigen** den gesamten Befehlsnamen ohne Leerzeichen ein.  
  
     Beispielsweise können Sie Befehle für "solutionexplorer" suchen.  
  
4.  Wählen Sie in der Liste den Befehl aus, dem Sie eine Tastenkombination zuweisen möchten.  
  
5.  Wählen Sie in der Liste **Neue Tastenkomb. verwenden in** den Funktionsbereich aus, in dem die Tastenkombination verwendet werden soll.  
  
     Wählen Sie beispielsweise **Global** aus, wenn die Tastenkombination in allen Zusammenhängen funktionieren soll.  Sie können jede Tastenkombination verwenden, die in keinem anderen Editor \(als Global\) zugeordnet ist.  Andernfalls wird die Tastenkombination vom Editor überschrieben.  
  
    > [!NOTE]
    >  Folgende Tasten können im Gültigkeitsbereich **Global** nicht in einer Tastenkombination verwendet werden: DRUCK\/S\-ABF, ROLLEN, PAUSE\/UNTBR, TAB, FESTSTELLTASTE, EINFG, POS1, ENDE, BILD\-AUF, BILD\-AB, die WINDOWS\-TASTE, die ANWENDUNGSTASTE, alle PFEILTASTEN sowie die EINGABETASTE, NUM, ENTF bzw. ENTF auf der Zehnertastatur und STRG\+ALT\+ENTF.  
  
6.  Im Feld **Tastenkombination drücken** geben Sie die Tastenkombination ein, die Sie verwenden möchten.  
  
    > [!NOTE]
    >  Sie können eine Tastenkombination erstellen, die einen Buchstaben mit der ALT\-TASTE, der STRG\-TASTE oder mit beiden kombiniert.  Sie können auch eine Tastenkombination erstellen, welche die UMSCHALTTASTE und einen Buchstaben mit der ALT\-TASTE, der STRG\-TASTE oder mit beiden kombiniert.  
  
     Wenn eine Tastenkombination bereits einem anderen Befehl zugeordnet ist, wird sie im Feld **Tastenkombination wird momentan verwendet von** angezeigt.  In diesem Fall löschen Sie die Tastenkombination mit der RÜCKTASTE und versuchen es mit einer anderen Tastenkombination.  
  
     ![Eine andere Tastenkombination für einen Befehl angeben](../ide/media/reassignshortcut.png "ReassignShortcut")  
  
7.  Wählen Sie die Schaltfläche **Zuweisen**.  
  
    > [!NOTE]
    >  Wenn Sie eine andere Tastenkombination für einen Befehl angeben, wählen Sie die Schaltfläche **Zuweisen** und dann **Abbrechen**. Damit wird das Dialogfeld geschlossen, aber die Änderung bleibt bestehen.  
  
##  <a name="bkmk_transfer"></a> Benutzerdefinierte Tastenkombinationen freigeben  
 Sie können Ihre selbstdefinierten Tastenkombinationen freigeben, indem Sie sie in eine Datei exportieren und die Datei dann anderen Benutzern zur Verfügung stellen, sodass diese die Daten importieren können.  
  
#### So exportieren Sie nur Tastenkombinationen  
  
1.  Wählen Sie in der Menüleiste die Optionen **Extras** und **Einstellungen importieren und exportieren** aus.  
  
2.  Wählen Sie **Ausgewählte Umgebungseinstellungen exportieren**, und wählen Sie dann die Schaltfläche **Weiter**.  
  
3.  Deaktivieren Sie unter **Welche Einstellungen sollen exportiert werden?** das Kontrollkästchen **Alle Einstellungen**, erweitern Sie **Optionen** und dann **Umgebung**.  
  
4.  Aktivieren Sie das Kontrollkästchen **Tastatur**, und wählen Sie dann **Weiter**.  
  
     ![Nur angepasste Tastenkombinationen exportieren](../ide/media/exportshortcuts.png "ExportShortcuts")  
  
5.  In den Feldern **Geben Sie den Namen der Einstellungsdatei ein.** und **Einstellungsdatei in folgendem Verzeichnis speichern** übernehmen Sie entweder die Standardwerte oder geben andere Werte ein, und dann wählen Sie die Schaltfläche **Fertig stellen**.  
  
     Standardmäßig werden die Tastenkombinationen in einer Datei im Ordner %USERPROFILE%\\Dokumente\\Visual Studio 2013\\Settings gespeichert.  Der Name der Datei entspricht dem Datum, an dem Sie die Einstellungen exportiert haben, und die Dateinamenerweiterung ist ".vssettings".  
  
#### So importieren Sie nur Tastenkombinationen  
  
1.  Wählen Sie in der Menüleiste die Optionen **Extras** und **Einstellungen importieren und exportieren** aus.  
  
2.  Wählen Sie das Optionsfeld **Ausgewählte Umgebungseinstellungen importieren**, und wählen Sie dann die Schaltfläche **Weiter**.  
  
3.  Wählen Sie das Optionsfeld **Nein, neue Einstellungen importieren und aktuelle Einstellungen überschreiben**, und wählen Sie dann die Schaltfläche **Weiter**.  
  
4.  Wählen Sie unter **Meine Einstellungen** die Datei mit den Tastenkombinationen aus, die Sie importieren möchten, oder wählen Sie die Schaltfläche **Durchsuchen**, um die gewünschte Datei zu suchen.  
  
5.  Wählen Sie die Schaltfläche **Weiter** aus.  
  
6.  Deaktivieren Sie unter **Welche Einstellungen sollen importiert werden?** das Kontrollkästchen **Alle Einstellungen**, erweitern Sie **Optionen** und dann **Umgebung**.  
  
7.  Aktivieren Sie das Kontrollkästchen **Tastatur**, und wählen Sie dann **Fertig stellen**.  
  
     ![Nur angepasste Tastenkombinationen importieren](../ide/media/importshortcuts.png "ImportShortcuts")  
  
## Siehe auch  
 [Barrierefreiheitsfunktionen in Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)