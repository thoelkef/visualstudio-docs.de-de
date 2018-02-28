---
title: Visual Studio-Codierung und Zeilenumbruchzeichen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8a472a09a4d4d67f59d7879d03b466932d1445e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="encodings-and-line-breaks"></a>Codierungen und Zeilenumbrüche
In Visual Studio werden die folgenden Zeichen als Zeilenumbrüche interpretiert:  
  
-   CR LF: Wagenrücklauf und Zeilenvorschub, Unicode-Zeichen 000D und 000A  
  
-   LF: Zeilenvorschub, Unicode-Zeichen 000A  
  
-   NEL: Nächste Zeile, Unicode-Zeichen 0085  
  
-   LS: Zeilentrennzeichen, Unicode-Zeichen 2028  
  
-   PS: Absatztrennzeichen, Unicode-Zeichen 2029  
  
In Text, der aus anderen Anwendungen kopiert wurde, bleiben die Codierungen und Zeilenumbruchzeichen unverändert. Wenn Sie beispielsweise Text aus Windows-Editor kopieren und in eine Textdatei in Visual Studio einfügen, weist der Text dieselben Einstellungen auf wie in Windows-Editor.  
  
Wenn Sie eine Datei öffnen, die andere Zeilenumbruchzeichen aufweist, wird evtl. ein Dialogfeld angezeigt, in dem Sie gefragt werden, ob die inkonsistenten Zeilenumbruchzeichen normalisiert werden sollen und welche Art von Zeilenumbrüchen verwendet werden soll.

Klicken Sie auf **Datei** und dann auf **Erweiterte Speicheroptionen**. Über das sich öffnende Dialogfeld können Sie den Typ des Zeilenumbruchs bestimmen. Sie können auch die Codierung einer Datei mit denselben Einstellungen ändern.

![Dialogfeld „Erweiterte Speicheroptionen“](media/line_endings.png)
  
> [!NOTE]
>  Wenn **Erweiterte Speicheroptionen** im **Dateimenü** nicht angezeigt wird, können Sie dies hinzufügen. Klicken Sie auf **Extras** > **Customize...** (Anpassen ...) und anschließend auf die Registerkarte **Befehle**. Klicken Sie in der Dropdownliste der **Menüleiste** auf **Datei** und dann auf **Befehl hinzufügen**. Klicken Sie unter **Kategorien** im Dialogfeld **Befehl hinzufügen** auf **Datei**, und klicken Sie dann in der Liste **Befehle** auf **Erweiterte Speicheroptionen**. Klicken Sie auf **OK** und auf **Nach unten verschieben**, um den Befehl an eine beliebige Stelle im Menü zu verschieben. Klicken Sie auf **Schließen**, um das Dialogfeld **Anpassen** zu schließen. Weitere Informationen finden Sie unter [Anpassen von Menüs und Symbolleisten](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).

Alternativ können Sie über **Datei** > **\<Datei\> speichern unter ...** das Dialogfeld **Erweiterte Speicheroptionen** öffnen. Klicken Sie im Dialogfeld **Datei speichern unter** auf den Dropdownlistenpfeil neben der Schaltfläche **Speichern**, und klicken Sie auf **Mit Codierung speichern**.

## <a name="see-also"></a>Siehe auch
[Writing code in the editor (Schreiben von Code im Code-Editor)](../ide/writing-code-in-the-code-and-text-editor.md)