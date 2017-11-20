---
title: Barrierefreiheit in Office-Projekten | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4636e55fa2bc20ba9ff958a897ef7898099cb5c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="accessibility-in-office-projects"></a>Barrierefreiheit in Office-Projekten
  Microsoft Visual Studio und Microsoft Office enthalten zahlreiche Funktionen zur Barrierefreiheit, mit denen Sie benutzerdefinierte Lösungen zu erstellen, die die standard-Barrierefreiheit erfüllen. Microsoft veröffentlicht Richtlinien für Eingabehilfen im Web. Einzelheiten finden Sie in der [Website für Barrierefreiheit](http://go.microsoft.com/fwlink/?LinkID=37113).  
  
 In den meisten Fällen entsprechen die Office-Projekte in Visual Studio Accessibility Standards oder macht-Eigenschaften, die Sie festlegen können, um Ihre Lösungen zugänglich zu machen. Es gibt jedoch einige Funktionen, die Barrierefreiheit begrenzt ist.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="accessibility-at-design-time"></a>Eingabehilfen zur Entwurfszeit  
  
### <a name="using-shortcut-keys-in-document-level-projects"></a>Verwenden von Tastenkombinationen in Projekten auf Dokumentebene  
 Wenn Microsoft Office Word-Dokument oder einer Microsoft Office Excel-Arbeitsmappe in Visual Studio geöffnet ist, empfängt nur eine Anwendung zu einem Zeitpunkt Befehle der Tastenkombination. Standardmäßig erhält Visual Studio alle Befehle für Tastenkombination, Sie können jedoch Word- oder Excel, die sie erhalten, wenn das Dokument durch Auswahl den Fokus besitzt **dynamische Folgendes zusätzliches Tastaturzuordnungsschema** auf die **Tastatureinstellungen** Seite von der **Optionen** (Dialogfeld). Weitere Informationen finden Sie unter [Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Optionen (Dialogfeld)](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) und [Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Optionen (Dialogfeld)](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  
  
### <a name="displaying-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Anzeigen von Tastenkombinationen für das Menüband in Projekten auf Dokumentebene  
 Wenn ein Word-Dokument oder eine Excel-Arbeitsmappe in Visual Studio geöffnet ist, können nicht Sie Tastenkombinationen für die Registerkarten und Steuerelemente auf dem Menüband anzeigen die Alt-Taste drücken. Um die Tastenkombinationen anzuzeigen, während das Dokument oder die Arbeitsmappe im Designer geöffnet ist, können führen Sie die folgenden Schritte aus.  
  
##### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>So zeigen Sie Tastenkombinationen für die Multifunktionsleiste Registerkarten und Steuerelemente im Designer an  
  
1.  In Visual Studio auf die **Tools** Menü klicken Sie auf **Optionen**.  
  
2.  Erweitern Sie die **Office Tools** Knoten, und wählen **Microsoft Office Excel-Tastatur** oder **Microsoft Office Word-Tastatur**je nach Bedarf.  
  
3.  Wählen Sie **dynamische Folgendes zusätzliches Tastaturzuordnungsschema**.  
  
     Eine Meldung angezeigt, die besagt, dass Sie Visual Studio für die Änderung wirksam wird neu gestartet werden müssen.  
  
4.  Klicken Sie auf **OK**.  
  
5.  Starten Sie Visual Studio neu, und öffnen Sie das Projekt.  
  
6.  Öffnen Sie den Dokumenten oder Arbeitsmappen-Designer für das Projekt.  
  
7.  Drücken Sie F6, um die Tastenkombinationen für das Menüband angezeigt.  
  
## <a name="accessibility-at-run-time"></a>Eingabehilfen zur Laufzeit  
  
### <a name="windows-forms-controls-on-office-documents"></a>Windows Forms-Steuerelemente in Office-Dokumente  
 Windows Forms-Steuerelemente verfügbar machen, Eingabehilfeeigenschaften, um Informationen über das Steuerelement Eingabehilfen, z. B. die Bildschirmsprachausgabe bereitzustellen. Sie können nutzen diese Eingabehilfeneigenschaften, wenn die Steuerelemente in einem Office-Dokument in einer Anpassung auf Dokumentebene befinden. Weitere Informationen finden Sie unter [Informationen über Eingabehilfen für Steuerelemente in einem Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  
  
 Es gibt jedoch einige Einschränkungen für die Barrierefreiheit zur Laufzeit, wenn die Windows Forms-Steuerelemente auf einem Excel-Arbeitsmappe oder einem Word-Dokument gehostet werden:  
  
-   Sie können nicht von einem Steuerelement in eine andere Registerkarte.  
  
-   Steuerelemente in einem Dokument sind deaktiviert, wenn Sie die zoomeinstellung des Dokuments in etwas anderes als 100 % ändern.  
  
 Informationen zu Einschränkungen von Windows Forms-Steuerelemente für Dokumente finden Sie unter [Einschränkungen von Windows Forms-Steuerelemente für Office-Dokumente](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
### <a name="actions-panes-and-custom-task-panes"></a>Aktionsbereiche und benutzerdefinierte Aufgabenbereiche  
 Wenn ein Aktionsbereich oder einen benutzerdefinierten Aufgabenbereich den Fokus besitzt, greifen Sie auf die Steuerelemente die gleiche Weise die Steuerelemente auf einer Windows Forms-Anwendung. Um den Cursor zwischen dem Aktionsbereich und das Dokument zu verschieben, drücken Sie **F6**.  
  
 Weitere Informationen zu Aktionsbereichen und benutzerdefinierten Aufgabenbereichen finden Sie unter [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md) und [benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
### <a name="display-modes"></a>Anzeigemodi  
 Visual Studio verfügt über die folgenden Einschränkungen, die im Zusammenhang mit der Modi anzuzeigen:  
  
-   Steuerelemente in einem Word-Dokument oder eine Excel-Arbeitsblatt sind deaktiviert, wenn Sie die zoomeinstellung des Dokuments in etwas anderes als 100 % ändern.  
  
-   Die **neues Projekt** Dialogfeld zeigt keine Steuerelemente ordnungsgemäß, wenn ein Eingabehilfen auf dem Computer geändert **Verwendung von hohem Kontrast**.  
  
 Sie können die Bildschirmlupe verwenden, diese Einschränkungen umgehen. Bildschirmlupe ist ein Hilfsprogramm anzeigen in Windows, die von einem separaten Fenster erstellt, das einen vergrößerten Bereich des Bildschirms wird angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Eingabehilfen für Menschen mit Behinderungen](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Barrierefreiheitsfeatures in Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
  
  