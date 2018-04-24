---
title: Tipps und Tricks zur Barrierefreiheit für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06f378c3ac0cfc808094170c37792399812538bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Tipps und Tricks zur Barrierefreiheit für Visual Studio
> [!TIP]
> Weitere Informationen zu aktuellen Barrierefreiheitupdates finden Sie im Blogbeitrag [Accessibility improvements in Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Verbesserungen der Barrierefreiheit in Visual Studio 2017 [Version 15.3]).

Visual Studio verfügt über integrierte Barrierefreiheitsfunktionen, die mit Sprachausgaben und anderen Hilfstechnologien kompatibel sind. In diesem Thema werden allgemeine Tastenkombinationen aufgeführt, die Sie verwenden können, um Aufgaben nur über die Tastatur auszuführen. Außerdem werden Informationen darüber bereitgestellt, wie Sie die Designs mit hohem Kontrast zum Verbessern der Sichtbarkeit verwenden. Außerdem erfahren Sie, wie Anmerkungen verwendet werden, um nützliche Informationen über Ihren Code anzuzeigen. Sie erhalten ebenfalls Informationen darüber, wie Sie Sounds für Build- und Breakpointereignisse festlegen.

## <a name="save-your-ide-settings"></a>Speichern Ihrer IDE-Einstellungen  
 Sie können Ihre IDE-Umgebung anpassen, indem Sie Fensterlayout, Tastaturzuordnungsschema und andere Einstellungen speichern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).  

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Ändern Ihrer IDE für die Ansicht mit hohem Kontrast
Einige Personen haben Schwierigkeiten damit, manche Farben zu erkennen. Wenn Sie beim Schreiben von Code einen höheren Kontrast wünschen, aber nicht die üblichen Themen für hohen Kontrast verwenden möchten, bieten wir nun das Design „Blau (zusätzlicher Kontrast)“ an.

  ![Vergleich der Designs „Blau“ und „Blau (zusätzlicher Kontrast)“](media/blue-extra-contrast-theme.png "Beachten Sie den Unterschied zwischen den Designs „Blau“ und „Blau (zusätzlicher Kontrast)“")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Verwenden von Anmerkungen, um nützliche Informationen über Ihren Code anzuzeigen

Der Visual Studio-Editor enthält viele Randsteuerelemente für den Text, die Sie über Charakteristiken und Funktionen an bestimmten Punkten einer Codezeile informieren, z.B. Glühbirnen, Wellenlinien für Fehler und Warnungen, Lesezeichen usw. Sie können den Befehlssatz „Zeilenanmerkungen anzeigen“ verwenden, um diese Randsteuerelemente zu ermitteln und zwischen diesen zu navigieren.

  ![Verwenden des Befehlssatzes „Zeilenanmerkungen anzeigen“](media/show-line-annotations-command-set.png "Zeigt, wie der Befehlssatz „Zeilenanmerkungen anzeigen“ festgelegt wird")

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Zugreifen auf Symbolleisten mithilfe von Tastenkombinationen
Die Visual Studio-IDE verfügt genau wie viele andere Toolfenster über Symbolleisten. Die folgenden Tastenkombinationen helfen Ihnen, auf diese zuzugreifen.

|Feature|description|Tastenkombination|  
|-------------|-----------------|---------------------|  
|IDE-Symbolleisten|Wählen Sie die erste Schaltfläche in der Standardsymbolleiste.|**ALT**, **STRG** + **TAB**|  
|Symbolleisten des Toolfensters|Verschieben Sie den Fokus zu den Symbolleisten in einem Toolfenster. <br> <br> **HINWEIS:** Dies funktioniert für die meisten Toolfenster, jedoch nur, wenn sich der Fokus in einem Toolfenster befindet. Sie müssen außerdem die UMSCHALTTASTE vor der ALT-TASTE drücken. In einigen Toolfenstern wie Team Explorer müssen Sie die UMSCHALTTASTE einen Moment gedrückt halten, bevor Sie die ALT-TASTE drücken.|**UMSCHALT** + **ALT**|
|Symbolleisten|Wechseln Sie zum ersten Element in der nächsten Symbolleiste (wenn eine Symbolleiste über Fokus verfügt).|**STRG** + **TAB**|

### <a name="other-useful-shortcut-key-combinations"></a>Andere häufig verwendete Tastenkombinationen  
Zu diesen Tastenkombinationen gehören:

|Feature|description|Tastenkombination|  
|-------------|-----------------|---------------------|  
|IDE|Hohen Kontrast ein- und ausschalten <br> <br> **HINWEIS:** Windows-Standardtastenkombination|**LINKE ALT-TASTE+LINKE UMSCHALTTASTE+DRUCK**|  
|Dialogfeld|Aktivieren oder deaktivieren Sie die Kontrollkästchenoption in einem Dialogfeld. <br> <br> **HINWEIS:** Windows-Standardtastenkombination|**LEERTASTE**|  
|Kontextmenüs|Öffnen Sie ein Kontextmenü (Rechtsklick). <br> <br> **HINWEIS:** Windows-Standardtastenkombination|**UMSCHALT** + **F10**|
|Menüs|Greifen Sie schnell auf ein Menüelement mithilfe der Zugriffstasten zu. Drücken Sie die **ALT**-TASTE gefolgt von den unterstrichenen Buchstaben in einem Menü, um den Befehl zu aktivieren. Um z.B. das Dialogfeld „Projekt öffnen“ in Visual Studio anzuzeigen, wählen Sie **ALT** + **F** + **O** + **P** aus.  <br><br> **HINWEIS:** Windows-Standardtastenkombination|**ALT** + **[Buchstabe]**|
|Fenster „Toolbox“|Wechseln Sie zwischen Toolboxregisterkarten.|**STRG** + **NACH-OBEN-TASTE**<br /><br /> und<br /><br /> **STRG** + **NACH-UNTEN-TASTE**|  
|Fenster „Toolbox“|Fügen Sie ein Steuerelement aus der Toolbox zu einem Formular oder einem Designer hinzu.|**EINGABETASTE**|  
|Tastatur, Umgebung, Dialogfeld „Optionen“|Löschen Sie die Tastenkombination, die unter **Tastenkombination drücken** eingegeben wurde.|**RÜCKTASTE**|  

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  


## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Verwenden des Sound-Applets, um Hinweise für Builds und Breakpoints festzulegen
Sie können das Sound-Applet in Windows verwenden, um Visual Studio-Programmereignissen einen Sound zuzuweisen. Insbesondere können Sie folgenden Programmereignissen Sounds zuweisen:

 * Haltepunkt erreicht
 * Buildvorgang abgebrochen
 * Fehler beim Buildvorgang
 * Buildvorgang erfolgreich

Gehen Sie folgendermaßen vor:

1. Geben Sie auf einem Computer mit Windows 10 **Systemsounds ändern** in das Feld **Suche** ein.

  ![Suchfeld in Windows 10](media/type-here-to-search.png "Eingeben von „Sounds“ in das Suchfeld auf einem Computer mit Windows 10")

  (Falls Sie Cortana aktiviert haben, können Sie alternativ „Hey Cortana“ und anschließend „Systemsounds ändern“ sagen.)

2. Doppelklicken Sie auf **Systemsounds ändern**.

  ![Suchergebnisse in Windows 10](media/change-system-sounds.png "Doppelklicken auf „Systemsounds ändern“ in den Suchergebnissen")

3. Klicken Sie im Dialogfeld **Sound** auf die Registerkarte **Sounds**. <br><br>
 Scrollen Sie dann in **Programmereignisse** zu **Microsoft Visual Studio**, und wählen Sie die Sounds aus, die Sie auf die gewünschten Ereignisse anwenden möchten.

  ![Registerkarte „Sounds“ des Sound-Applets in Windows 10](media/sound-applet.png "Doppelklicken auf „Systemsounds ändern“ in den Suchergebnissen")

4. Klicken Sie auf **OK**.



## <a name="see-also"></a>Siehe auch  
* [Barrierefreiheitsfeatures in Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
  * [Gewusst wie: Anpassen von Menüs und Symbolleisten in Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md)
* [Microsoft Accessibility (Microsoft-Barrierefreiheit)](https://www.microsoft.com/Accessibility)
