---
title: 'Vorgehensweise: Anpassen von Menüs und Symbolleisten in Visual Studio | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.renametoolbar
- vs.customize.toolbars
- vs.buttoneditor
- vs.customize.commands
- vs.newtoolbar
helpviewer_keywords:
- captions, customizing toolbar
- custom toolbars [Visual Studio]
- command buttons, customizing toolbar
- labels, customizing toolbar
- images [Visual Studio], toolbar buttons
- buttons [Visual Studio], custom toolbars
- toolbars [Visual Studio], creating in the IDE
- icons [Visual Studio], customizing toolbar
- commands [Visual Studio], customizing environment
- customizing toolbars
- toolbars [Visual Studio], customizing
- toolbars [Visual Studio], customizing in the IDE
ms.assetid: b570ae2f-5302-45dc-9cc9-8d4d1ad50603
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f7301a05ff17c20532a394fd1f26ab9fd98c3b65
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237886"
---
# <a name="how-to-customize-menus-and-toolbars-in-visual-studio"></a>Gewusst wie: Anpassen von Menüs und Symbolleisten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Visual Studio nicht nur anpassen, indem Sie Symbolleisten und Menüs in der Menüleiste hinzufügen und entfernen, sondern auch durch Hinzufügen und Entfernen von Befehlen in jeder angegebenen Symbolleiste oder jedem Menü.  
  
> [!WARNING]
>  Stellen Sie nach dem Anpassen einer Symbolleiste oder eines Menüs sicher, dass das entsprechende Kontrollkästchen im Dialogfeld **Anpassen** aktiviert bleibt. Andernfalls werden die Änderungen nicht beibehalten, wenn Sie Visual Studio schließen und erneut öffnen.  
  
 **In diesem Thema:**  
  
-   [Hinzufügen, entfernen oder Verschieben eines Menüs in der Menüleiste](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addmenu)  
  
-   [Hinzufügen, entfernen oder Verschieben einer Symbolleiste](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_addtoolbar)  
  
-   [Anpassen eines Menüs oder einer Symbolleiste](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_customize)  
  
-   [Zurücksetzen eines Menüs oder einer Symbolleiste](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#bkmk_reset)  
  
##  <a name="bkmk_addmenu"></a> Hinzufügen, entfernen oder Verschieben eines Menüs in der Menüleiste  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Anpassen** aus.  
  
     Das Dialogfeld **Anpassen** wird geöffnet.  
  
2.  Lassen Sie auf der Registerkarte **Befehle** das Optionsfeld **Menüleiste** ausgewählt, lassen Sie **Menüleiste** in der Liste neben dieser Option ausgewählt, und führen Sie dann einen der folgenden Schritte aus:  
  
    -   Um ein Menü hinzuzufügen, klicken Sie auf die Schaltfläche **Neues Menü hinzufügen** und anschließend auf die Schaltfläche **Auswahl ändern**, und benennen Sie das Menü, das Sie hinzufügen möchten.  
  
         ![Dialogfeld „Anpassen“ zum Hinzufügen eines Menüs](../ide/media/addmenu.png "AddMenu")  
  
    -   Um ein Menü zu entfernen, wählen Sie es in der Liste **Steuerelemente** aus, und klicken Sie dann auf die Schaltfläche **Löschen**.  
  
    -   Um ein Menü in der Menüleiste zu verschieben, wählen Sie das Menü in der Liste **Steuerelemente** aus, und klicken Sie dann auf die Schaltfläche **Nach oben** oder **Nach unten**.  
  
##  <a name="bkmk_addtoolbar"></a> Hinzufügen, entfernen oder Verschieben einer Symbolleiste  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Anpassen** aus.  
  
     Das Dialogfeld **Anpassen** wird geöffnet.  
  
2.  Führen Sie auf der Registerkarte **Symbolleiste** einen der folgenden Schritte aus:  
  
    -   Um eine Symbolleiste hinzufügen, klicken Sie auf die Schaltfläche **Neu**, geben Sie einen Namen für die Symbolleiste ein, die Sie hinzufügen möchten, und klicken Sie dann auf **OK**.  
  
         ![Dialogfeld „Anpassen“ zum Hinzufügen einer Symbolleiste](../ide/media/addtoolbar.png "AddToolbar")  
  
    -   Um eine benutzerdefinierte Symbolleiste zu entfernen, wählen Sie sie in der Liste **Symbolleisten** aus, und klicken Sie dann auf die Schaltfläche **Löschen**.  
  
        > [!IMPORTANT]
        >  Sie können selbst erstellte Symbolleisten löschen, jedoch keine Standardsymbolleisten.  
  
    -   Um eine Symbolleiste an eine andere Andockposition zu verschieben, wählen Sie sie in der Liste **Symbolleisten** aus, klicken Sie auf **Auswahl ändern**, und wählen Sie eine Position in der angezeigten Liste aus.  
  
         Sie können die Symbolleiste auch am linken Rand ziehen, um sie im Hauptandockbereich zu verschieben.  
  
        > [!NOTE]
        >  Weitere Informationen über Möglichkeiten zur Verbesserung der Gebrauchstauglichkeit sowie der Barrierefreiheit von Symbolleisten finden Sie unter [Vorgehensweise: Festlegen von IDE-Barrierefreiheitsoptionen](../ide/reference/how-to-set-ide-accessibility-options.md).  
  
##  <a name="bkmk_customize"></a> Anpassen eines Menüs oder einer Symbolleiste  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Anpassen** aus.  
  
     Das Dialogfeld **Anpassen** wird geöffnet.  
  
2.  Wählen Sie auf der Registerkarte **Befehle** das Optionsfeld für den Elementtyp aus, den Sie anpassen möchten.  
  
3.  Wählen Sie in der Liste für den Elementtyp das Menü oder die Symbolleiste aus, das bzw. die Sie anpassen möchten, und führen Sie dann einen der folgenden Schritte aus:  
  
    -   Um einen Befehl hinzuzufügen, klicken Sie auf **Befehl hinzufügen**.  
  
         Wählen Sie im Dialogfeld **Befehl hinzufügen** ein Element in der Liste **Kategorien** aus, wählen Sie ein Element in der Liste **Befehle** aus, und klicken Sie dann auf **OK**.  
  
         ![Dialogfeld „Befehl hinzufügen“ in Visual Studio](../ide/media/addcommand.png "AddCommand")  
  
    -   Um einen Befehl zu löschen, wählen Sie ihn in der Liste **Steuerelemente** aus, und klicken Sie dann auf die Schaltfläche **Löschen**.  
  
    -   Um Befehle neu anzuordnen, wählen Sie einen Befehl in der Liste **Steuerelemente** aus, und klicken Sie dann auf **Nach oben** oder **Nach unten**.  
  
    -   Um die Befehle in Gruppen zu unterteilen, wählen Sie einen Befehl in der **Steuerelemente** wählen die **Auswahl ändern** Schaltfläche, und wählen Sie dann **Gruppierung beginnen** im Menü, das angezeigt wird.  
  
##  <a name="bkmk_reset"></a> Zurücksetzen eines Menüs oder einer Symbolleiste  
  
1.  Wählen Sie in der Menüleiste **Extras**, **Anpassen** aus.  
  
     Das Dialogfeld **Anpassen** wird geöffnet.  
  
2.  Wählen Sie auf der Registerkarte **Befehle** das Optionsfeld für den Elementtyp aus, den Sie zurücksetzen möchten.  
  
3.  Wählen Sie in der Liste für den Elementtyp das Menü oder die Symbolleiste aus, das bzw. die Sie zurücksetzen möchten.  
  
4.  Klicken Sie auf die Schaltfläche **Auswahl ändern**, und wählen Sie dann im angezeigten Menü **Zurücksetzen** aus.  
  
     Sie können auch alle Menüs und Symbolleisten zurücksetzen, indem Sie die Schaltfläche **Alle zurücksetzen** auswählen.



