---
title: 'Vorgehensweise: Navigieren in der IDE | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ea104d08216a4ef7bdb07fc42b5a22eb5352d757
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049618"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Vorgehensweise: Navigieren in der Visual Studio-IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die integrierte Entwicklungsumgebung (IDE) wurde zum Navigieren zwischen Fenstern und Dateien entworfen. Je nach persönlichen Vorlieben und den jeweiligen Projektanforderungen stehen Ihnen hierfür verschiedene Möglichkeiten zur Verfügung. Sie können im Editor durch geöffnete Dateien oder in der IDE durch alle aktiven Toolfenster navigieren. Außerdem können Sie im Editor direkt zu allen geöffneten Dateien wechseln, und zwar unabhängig von der Reihenfolge, in der Sie zuletzt verwendet wurden. Diese Funktionen ermöglichen es Ihnen, in der IDE produktiver zu arbeiten.

> [!NOTE]
>  Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Diese Hilfeseite wurde unter Berücksichtigung der Option **Allgemeine Entwicklungseinstellungen** geschrieben. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Tastenkombinationen
 Fast jeder Menübefehl in Visual Studio verfügt über eine Tastenkombination. Sie können außerdem eigene benutzerdefinierte Tastenkombinationen erstellen. Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Navigieren zwischen Dateien im Editor
 Sie können verschiedene Methoden verwenden, um durch die Dateien zu navigieren, die im Editor geöffnet sind. Sie können zwischen den Dateien auf Grundlage der Reihenfolge wechseln, in der Sie auf sie zugreifen, den IDE-Navigator zur schnellen Suche einer geöffneten Datei verwenden, oder zu bevorzugte Dateien an die Registerkarte anheften, damit sie immer sichtbar sind.

 Die Optionen „Rückwärts navigieren“ und „Vorwärts navigieren“ ermöglichen es Ihnen, im Editor zwischen den geöffneten Dateien zu navigieren. Ähnlich wie die Verlaufsschaltflächen „Zurück“ und „Vorwärts“ in Microsoft Internet Explorer basieren diese Optionen auf der Reihenfolge der letzten Verwendung.

#### <a name="to-move-through-open-files-in-order-of-use"></a>So navigieren Sie in der Verwendungsreihenfolge durch geöffnete Dateien

- Um geöffnete Dokumente in der Reihenfolge zu aktivieren, in der sie zuletzt verwendet wurden, drücken Sie STRG+MINUS.

- Um geöffnete Dokumente in umgekehrter Reihenfolge zu aktivieren, drücken Sie STRG+UMSCHALT+MINUS.

  > [!NOTE]
  >  Die Optionen **Rückwärts navigieren** und **Vorwärts navigieren** befinden sich auch im Menü **Ansicht**.

  Um im Editor zu einer bestimmten geöffneten Datei zu navigieren, egal wann diese zuletzt verwendet wurde, können Sie auch den **IDE-Navigator**, die Liste **Aktive Dateien** im Editor oder das Dialogfeld **Fenster** verwenden.

  Die Funktionsweise des **IDE-Navigators** ist weitestgehend mit der des Windows-Anwendungsschalters vergleichbar. Er ist nicht über die Menüs verfügbar, sondern kann lediglich mithilfe von Tastenkombinationen aufgerufen werden. Je nachdem, in welcher Reihenfolge Sie durch die Dateien navigieren möchten, können Sie den **IDE-Navigator** über einen von zwei (unten gezeigten) Befehlen aufrufen.

  ![Visual Studio IDE-Navigator](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  Der Befehl `Window.PreviousDocumentWindowNav` ermöglicht es Ihnen, zu der zuletzt verwendeten Datei zu navigieren, und der Befehl `Window.NextDocumentWindowNav` ermöglicht Ihnen die Navigation in umgekehrter Reihenfolge. In den allgemeinen Entwicklungseinstellungen ist dem Befehl `Window.PreviousDocumentWindowNav` die Tastenkombination STRG+UMSCHALT+TAB zugewiesen und dem Befehl `Window.NextDocumentWindowNav` die Tastenkombination STRG+TAB.

> [!NOTE]
>  Wenn dem Befehl in der von Ihnen verwendeten Einstellungskombination noch keine Tastenkombination zugewiesen ist, können Sie auf der Seite **Tastatur** des Dialogfelds **Optionen** selbst einen Befehl zuweisen. Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>So wechseln Sie zu bestimmten Dateien im Editor

-   Drücken Sie STRG+TAB, um den **IDE-Navigator** anzuzeigen. Drücken Sie bei gedrückter STRG-TASTE so oft die TAB-TASTE, bis die gewünschte Datei ausgewählt ist.

    > [!TIP]
    >  Um die Reihenfolge umzukehren, in der Sie durch die Liste **Aktive Dateien** navigieren, halten Sie STRG+UMSCHALT gedrückt, und drücken Sie die TAB-TASTE.

     \- oder –

-   Klicken Sie in der oberen rechten Ecke des Editors auf die Schaltfläche **Aktive Dateien**, und wählen Sie eine Datei aus der Liste aus, zu der Sie wechseln möchten.

     \- oder –

-   Wählen Sie auf der Menüleiste **Fenster** **Fenster** aus.

-   Wählen Sie in der Liste die Datei aus, die Sie anzeigen möchten, und wählen Sie dann **Aktivieren**.

## <a name="navigating-among-tool-windows-in-the-ide"></a>Navigieren zwischen Toolfenstern in der IDE
 Mit dem **IDE-Navigator** können Sie auch zwischen den Toolfenstern navigieren, die in der IDE geöffnet sind. Je nachdem, in welcher Reihenfolge Sie durch die Toolfenster navigieren möchten, können Sie den **IDE-Navigator** über einen von zwei Befehlen aufrufen. Der Befehl `Window.PreviousToolWindowNav` ermöglicht es Ihnen, zu der zuletzt verwendeten Datei zu navigieren, und der Befehl `Window.NextToolWindowNav` ermöglicht Ihnen die Navigation in umgekehrter Reihenfolge. In den allgemeinen Entwicklungseinstellungen ist dem Befehl `Window.PreviousDocumentWindowNav` die Tastenkombination UMSCHALT+ALT+F7 zugewiesen und dem Befehl `Window.NextDocumentWindowNav` die Tastenkombination ALT+F7.

> [!NOTE]
>  Wenn dem Befehl in der von Ihnen verwendeten Einstellungskombination noch keine Tastenkombination zugewiesen ist, können Sie auf der Seite **Tastatur** des Dialogfelds **Optionen** selbst einen Befehl zuweisen. Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>So wechseln Sie zu einem bestimmten Toolfenster in der IDE

-   Drücken Sie ALT+F7, um den **IDE-Navigator** anzuzeigen. Drücken Sie bei gedrückter ALT-TASTE so oft die Taste F7, bis das gewünschte Fenster ausgewählt ist.

    > [!TIP]
    >  Um die Reihenfolge umzukehren, in der Sie durch die Liste **Aktive Toolfenster** navigieren, halten Sie UMSCHALT+ ALT gedrückt, und drücken Sie die Taste F7.

## <a name="see-also"></a>Siehe auch
 [Anpassen von Fensterlayouts](../ide/customizing-window-layouts-in-visual-studio.md) [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md)
