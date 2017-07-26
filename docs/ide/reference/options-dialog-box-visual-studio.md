---
title: "Dialogfeld „Optionen“ (Visual Studio) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 19
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
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 127a28e735b72d836c1a98044b3e8b95e13f5c54
ms.contentlocale: de-de
ms.lasthandoff: 05/24/2017

---
# <a name="options-dialog-box-visual-studio"></a>Dialogfeld "Optionen" (Visual Studio)
Mit dem Dialogfeld **Optionen** können Sie die integrierte Entwicklungsumgebung (IDE) Ihren Wünschen entsprechend konfigurieren. Sie können beispielsweise einen Standardspeicherort für Ihre Projekte festlegen, das Standardverhalten und-aussehen von Windows anpassen und Tastenkombinationen für häufig verwendete Befehle erstellen. Zudem gibt es Optionen, die für Ihre Entwicklungssprachen und -plattform spezifisch sind. Sie können über das Menü **Extras** auf die **Optionen** zugreifen.  
  
> [!NOTE]
>  Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="layout-of-the-options-dialog-box"></a>Layout des Dialogfelds „Optionen“  
 Das Dialogfeld **Optionen** ist in zwei Teile aufgeteilt: einen Navigationsbereich auf der linken Seite und einen Anzeigebereich rechts. Das Struktursteuerelement im Navigationsbereich enthält Ordnerknoten wie z.B. „Umgebung“, „Text-Editor“, „Projekte und Projektmappen“ und „Quellcodeverwaltung“. Erweitern Sie einen Ordnerknoten, um die Optionen, die er enthält, aufzulisten. Wenn Sie einen Knoten für eine bestimmte Seite ausgewählt haben, werden deren Optionen im Anzeigebereich angezeigt.  
  
 Die Optionen einer IDE-Funktion werden erst dann im Navigationsbereich angezeigt, wenn die Funktion in den Arbeitsspeicher geladen wird. Deshalb kann es sein, dass zu Beginn einer neuen Sitzung nicht die gleichen Optionen angezeigt werden wie am Ende der letzten. Wenn Sie ein Projekt erstellen oder einen Befehl ausführen, der eine bestimmte Anwendung verwendet, werden Knoten für wichtige Optionen dem Dialogfeld „Optionen“ hinzugefügt. Diese hinzugefügten Optionen bleiben dann solange verfügbar, wie die IDE-Funktion im Arbeitsspeicher vorhanden ist.  
  
> [!NOTE]
>  Einige Einstellungsauflistungen geben die Zahl an Seiten an, die im Navigationsbereich des Dialogfelds „Optionen“ angezeigt werden. Sie können festlegen, dass alle möglichen Seiten angezeigt werden, indem Sie **Alle Einstellungen anzeigen** auswählen.  
  
## <a name="how-options-are-applied"></a>So werden Optionen angewendet  
 Wenn Sie im Dialogfeld **Optionen** auf OK klicken, werden alle Einstellungen auf allen Seiten gespeichert. Wenn Sie auf einer beliebigen Seite auf „Abbrechen“ klicken, werden alle Änderungsanforderungen abgebrochen, auch Einstellungen, die gerade erst auf anderen **Optionsseiten** vorgenommen wurden. Einige Änderungen auf Optionsseiten, wie z.B. auf [Schriftarten und Farben, Umgebung, Dialogfeld „Optionen“](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), treten erst in Kraft, nachdem Visual Studio geschlossen und wieder geöffnet wurde.  
  
### <a name="show-all-settings"></a>Alle Einstellungen anzeigen  
 Das Aktivieren oder Deaktivieren von **Alle Einstellungen anzeigen** wendet alle von Ihnen vorgenommenen Änderungen im Dialogfeld **Optionen** an, auch wenn Sie noch nicht auf **OK** geklickt haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen des Editors](../../ide/customizing-the-editor.md)
